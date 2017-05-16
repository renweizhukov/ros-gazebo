# ROS package ros_gazebo_rw

## 1. Build & Run

To build,

```bash
$ catkin_make_isolated --install --use-ninja
```

To run,

```bash
$ source install_isolated/setup.bash
$ roslaunch ros_gazebo_rw tortoisebot.launch
$ roslaunch ros_gazebo_rw magneticbot.launch
```

## 2. Launch files

### 2.1 tortoisebot.launch

This launch file simulates a tortoisebot without LiDAR in Gazebo, which is copied from https://github.com/osrf/rosbook/blob/master/code/tortoisebot/tortoisebot.launch

### 2.2 magneticbot.launch

This launch file simulates a magneticbot with LiDAR in Gazebo. It also visualizes its movement and laser scan results in rviz.

## 3. urdf files

### 3.1 tortoisebot.urdf

This urdf file specifies the tortoisebot without LiDAR, which is copied from https://github.com/osrf/rosbook/blob/master/code/tortoisebot/tortoisebot.urdf

### 3.2 magneticbot.urdf

This urdf file specifies the magneticbot with LiDAR.

## 4. config files

### 4.1 view_magneticbot.rviz

This is a rviz config file for visualizing the magneticbot in rviz.

## 5. Models

Basically follow the instructions given at http://gazebosim.org/tutorials?cat=guided_b&tut=guided_b3 to build a differential drive robot.

### 5.1 Differential drive without any sensor

See models/diff_drive.

### 5.2 Differential drive with a depth camera as a follower

See models/diff_drive_camera_follower.

## 6. Buildings

Import a floorplan from floorplans/floorplan.png and create two buildings based on the floorplan by following the instructions given at http://gazebosim.org/tutorials?cat=build_world&tut=building_editor#Savingyourbuilding.

### 6.1 House with one level

See worlds/HouseOneLevel.

### 6.2 House with two levels

See worlds/HouseTwoLevels.

## 7. Plugins

### 7.1 An example world plugin.

http://gazebosim.org/tutorials?tut=plugins_hello_world&cat=write_plugin

To run the world plugin,

```bash
$ source install_isolated/setup.bash
$ gzserver `rospack find ros_gazebo_rw_plugins`/world/hello.world --verbose
```

### 7.2 An example model plugin.

http://gazebosim.org/tutorials?tut=plugins_model&cat=write_plugin

To run the model plugin,

```bash
$ source install_isolated/setup.bash
$ gzserver -u `rospack find ros_gazebo_rw_plugins`/world/model_push.world
```

The option "-u" starts the gazebo server in a paused state.

In a separate terminal, start the gui

```bash
$ gzclient
``` 

Click on the play button in the gui to unpause the simulation, and you should see the box move.
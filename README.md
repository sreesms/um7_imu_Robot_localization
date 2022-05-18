# um7_imu & Robot_localization
### Robot localization with IMU (https://www.pololu.com/product/2764) and odometry data of the mobile platform

#### To run the um7 IMU and robot localization

clone this repository using the below command in catkin_ws.

`$ https://github.com/sreesms/um7_imu_Robot_localization.git`
 
`$ cd catkin_ws && catkin_make`

After successful make, run the following to lauch the um7 and robot localization packages. Here we are expecting the `/odom` is publishing the odometry data from the robot platform (such as Husky,Jackal). 

`$ roslaunch um7 um7.launch`

This will publish the imu raw data in /imu/um7 topic.
 
`$ rostopic echo /imu/um7`
 
To view the IMU data in rviz use the `imu_link` frame and add the `/imu/um7` topic.
![imu_data](https://user-images.githubusercontent.com/19260407/168959465-6cbe8a27-f6fc-4d00-91cb-6cc63dbec1b1.png)

imu_filter_madgwick is used to filter and fuse the raw data from the IMU devices. It fuses angular velocities, accelerations, and (optionally) magnetic readings from a generic IMU device into an orientation quaternion, and publishes the fused data on the imu/data topic.

#### To view fused data check the topic 

`$ rostopic echo /imu/data`

#### To view the output of the robot localization

`$ rostopic echo /odometry/filtered`

###### If the `/odom` and `/imu/data` is publishing the data properly, you can view the same in rviz in the `/odom` frame by adding the `/odometry/filtered` topic.
                        
  ![imu_odom](https://user-images.githubusercontent.com/19260407/168959836-a382663f-f580-4c2f-87c5-2151b219c43d.png)


 ##### References
1. https://github.com/ros-drivers/um7
2. https://github.com/CCNYRoboticsLab/imu_tools
3. https://github.com/cra-ros-pkg/robot_localization

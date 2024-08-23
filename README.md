# CNC Tending Bot: Kinematics of ABB IRB 1600

This repository contains the submission for Project2 by Group 2 members - Suhas (suhas99) and Swaraj (swarajmr). The project involves Kinematics of ABB IRB 1600 and Gazebo Simulation

## Repository Structure
- **suhas99_swarajmr_group2_Project2_Report.pdf**: Containes a detailed description of the project.
- **Assembly Folder**: Contains the part files of the robot links and the final SolidWorks assembly.
- **Package Folder**: Contains the ROS2 packages `industrial` and `invk`.

## Prerequisites
- Before running the code, ensure that you have the following installed:
  - ROS2 (recommended version: Humble)
  - Gazebo
  - Rviz
  - SolidWorks (for assembly files)

## Setup Instructions

1. **Create a Workspace**:
   ```bash
   mkdir -p ~/ros2_ws/src
   cd ~/ros2_ws/src
   ```
2. **Copy Packages**:
   - Paste the `industrial` and `invk` packages into the src folder of your workspace.
     
3. **Copy Models**:
   - Copy the contents from `/industrial/competition/models` and paste them into `~/.gazebo/models`.
     
4. **Modify World File**:
   - Open the `modelwithpart.world` file located in `/industrial/competition/worlds`.
   - Open a new terminal and type the 2 commands in sequence: "cd" and "pwd". Copy the address displayed.
   - Replace all occurrences of `/root/` in `modelwithpart.world` file with the path/address that you copied.
  
5. **Build and Source the Packages**:
   ```bash
   cd ~/ros2_ws
   colcon build
   source install/setup.bash
   ```
   
## Running the Simulation

1. **Launch Gazebo with Custom World**:
   ```bash
   ros2 launch industrial competition.launch.py
   ```
   
2. **Run the Factory Simulation Script**:
   - Run the Primary Simulation script:
   ```bash
   ros2 run invk control
   ```
   - OR Run the Inverse Kinematic Validation script:
   ```bash
   ros2 run invk ikval
   ```
   - OR Run the Forward Kinematic Validation script:
   ```bash
   ros2 run invk fkval
   ```
## Vacuum Gripper Service
- To control the vacuum gripper, use the following ROS2 service calls:
  - **Turn Gripper On**:
   ```bash
   ros2 service call /vacuum_gripper/switch std_srvs/srv/SetBool "{data: true}"
   ```
  - **Turn Gripper Off**:
   ```bash
   ros2 service call /vacuum_gripper/switch std_srvs/srv/SetBool "{data: false}"
   ```
## Troubleshooting
- **Path Issues**: Ensure that paths are correctly replaced in the modelwithpart.world file.
- **Dependencies**: Verify that all required libraries are installed.
- **Permissions**: Ensure you have the necessary permissions to write to the .gazebo/models directory.

---
title: "HowTO: Drivers Nvidia  8.04"
date: 2008-05-17
forum: Desktop Environments
---

### Post by Leetbumble on 2008-05-17
OK this is my first attempt at this so be warned. This is how I setup my system and I can NOT say the same way will work with yours. 

My system uses an Nvidia 8800gts 640mb GPU. After upgrading to 8.04 from a fully patched 7.10 I had major issues so I decided to do a full clean reinstall. 

MAKE SURE YOU BACK UP YOUR SYSTEM FIRST!!!

Because there are plenty of places on the forum about this, I wont be going through this process but I used DBAN and new cd of 8.04. 

With the system installed I went on to getting the drivers.

--Click System-> Administration -> Synaptic Package Manager 

--Go to the top bar and click on Search 

--Type " Envy " and hit enter. 

--You should see the following... 

	alsa-tools-gui 
	envyng-core 
	envyng-gtk 
	......
	......
	......

--I then selected ONLY: 

	envyng-core 
	envyng-gtk 

--Go to the top bar and click Apply. 

--Now go to you Applications -> System Tools -> EnvyNG 

--On the left side select the graphics card type (ati or Nvidia) 

--Select "Install the [brand] driver (Automatic Hardware Detection) 

-- Click Apply 



For Nvidia users with multiple monitors from here on out.... 
 
--Click Application -> Accessories -> Terminal 

--Type the following: 

	sudo /usr/bin/nvidia-settings 


???WHY??? 
This is because the Nvidia X Server Setting application will edit the /etc/X11/xorg.conf file which is beyond normal user access for good reason. 


--Click on the second menu item on the far left: 

	"X Server Display Configuration" 

--Here you can set up the position and order of you monitors. 

--If a monitor is "disabled" select it then click Configure and if you want one screen on two monitors select " TwinView " 

--When you have them setup as you want them and with the pictures being as the monitors are on your desk. 

--Then select one of the monitors as a primary display for the X screen This will be where your logon screen shows up [to the best of my understanding] 

--Click Apply 

--Click OK to accept the changes if your setup is correct, if it is not just wait 15 seconds and your system will revert and you can try again. 

--Click Save to X Configuration File 

--Click Quit 

--Click Quit 

--Restart your system and everything should be running.


------ 


If you have questions send me a message or post. I'll check as much as possible. Hope this helps and that it is not a double post.

---

### Post by Xiong Chiamiov on 2008-05-17
Many people (myself included) have had to install the latest beta drivers from NVIDIA to solve issues with the latest kernel.  Essentially, you have to get the driver from [this page]("http://www.nvidia.com/object/linux_display_archive.html"), then shut down gdm (or kdm for KDE users), then install.

---


---
title: "resolution setting problem"
date: 2009-04-09
forum: General Help
---

### Post by ninos_loves_u@hotmail.com on 2009-04-09
im trying to change my screen resolution to make everything smaller but from what i can see in the monitor resolution setting the maximum had aslready being selected 1366x768 but im sure i can increase that and i got a "unknown" where my screen model is meant to show and i think thats whats causing the problems maybe it doesnt know what my screen model is and what it can support.. i have a aspire 6920g - 16" HD LCD - 1791MB Nvidia geforce 9500m

---

### Post by khelben1979 on 2009-04-09
I believe your problem is related to that you have not installed the native graphics drivers from nVidia.

Get them [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us").

Or add a repos to your /etc/apt/sources.list file where it points to the official drivers from nVidia. Then all upgrades can be done by simply doing this:

```
sudo apt-get install nvidia
```

If it isn't added, the nVidia drivers which will get downloaded will be the open source drivers which is very, very slow in comparison.

---

### Post by ninos_loves_u@hotmail.com on 2009-04-09
> **khelben1979 said:**
> I believe your problem is related to that you have not installed the native graphics drivers from nVidia.

Get them [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us").

Or add a repos to your /etc/apt/sources.list file where it points to the official drivers from nVidia. Then all upgrades can be done by simply doing this:

```
sudo apt-get install nvidia
```

If it isn't added, the nVidia drivers which will get downloaded will be the open source drivers which is very, very slow in comparison.

its says "ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com." and when i press ok its says "  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at www.nvidia.com." iam kinda new to linux so i really dont know what xserver is and what it does, i disabled the nvidia drivers which were provided by linux (nvidia driver 180) so plz help

---

### Post by 3rdalbum on 2009-04-09
The Nvidia driver 180 is what you want if you want to get a higher resolution. It will be much better if you re-enable the 180 driver that was provided by Ubuntu.

Re-enable the driver, reboot, and make sure that you get the Nvidia logo appearing just before the login screen. Once you are running the Nvidia proprietary driver you should have access to higher resolutions, if these are supported by your monitor.

---

### Post by ninos_loves_u@hotmail.com on 2009-04-09
> **3rdalbum said:**
> The Nvidia driver 180 is what you want if you want to get a higher resolution. It will be much better if you re-enable the 180 driver that was provided by Ubuntu.

Re-enable the driver, reboot, and make sure that you get the Nvidia logo appearing just before the login screen. Once you are running the Nvidia proprietary driver you should have access to higher resolutions, if these are supported by your monitor.

but i just disabled it now to install the one i downloaded from the nvidia website but its showing me the above error messages ^^^ so i need to exit/disable what ever xserver is to install the propa drivers and maybe get my screen recognized

---

### Post by khelben1979 on 2009-04-09
You need to kill the x server.

From a text shell type this:
```
sudo top
```

and then you kill the x server:
```
kill -9 [process number]
```
where the process number is the Xorg process.

As it says in the error message, no x server should be running when you decide to install the graphics driver.

---


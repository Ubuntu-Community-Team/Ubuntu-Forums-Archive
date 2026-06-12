---
title: "Dual Monitor Setup Clones on Login"
date: 2011-06-29
forum: Desktop Environments
---

### Post by Atomic Fusion on 2011-06-29
I'm using the proprietery nvidia drivers on 11.04. I have a dual monitor setup with xinerama. The login screen appears to work fine, I can move my mouse between screens, and only one screen (right) has the login prompt. When I login, both screens show the same thing. While I can move my mouse across, I can only interact when it's on the left side.
I found this: [http://ubuntuforums.org/showthread.php?t=439712](http://ubuntuforums.org/showthread.php?t=439712), but I cannot start the display settings in the XFCE control center due to "missing randr extentions".
Yesterday, I was using Kubuntu 11.04 on this same machine, and the dual monitor setup worked fine.

---

### Post by Atomic Fusion on 2011-06-29
I can also interact with my right screen, I just can't see what's going on, unless I drag it over onto my left monitor.

---

### Post by Ozymandias_117 on 2011-06-29
Have you tried running Nvidia's program for setting up the monitors?

---

### Post by Atomic Fusion on 2011-06-29
I used it to generate the preliminary X configuration like I did on Kubuntu. I did do some manual edits, however (change resolution, change monitor refresh rate range, disable EDID).

---

### Post by Ozymandias_117 on 2011-06-29
I meant their GUI settings tool. It can be opened from the command line with ```
nvidia-settings
```

---

### Post by Atomic Fusion on 2011-06-29
I didn't directly modify the X configuration with it because I've had problems with saving with it in the past, but yes I used the screen positioning feature.

---

### Post by Atomic Fusion on 2011-07-01
Can't find policy on bumping, so bump.

---

### Post by Atomic Fusion on 2011-07-02
One last bump before I ragequit to Kubuntu for 5 months.

---

### Post by jeffers.r on 2011-07-31
While I might not be able to address your specific problem outlined in your initial post, I can try to give you a few options to try and perhaps one will solve your problem. I've had a number of issues using dual monitors with Xubuntu, and none when using Ubuntu. Not sure why the difference, but alas, it is what it is.
 
My primary issue is that the proprietary Nvidia drivers (all versions) refuse to function properly with my GeForce 7300 LE, constantly crashing X, sometimes recovering automatically with frequent and annoying flashes on the screen, other times crashing X to the point that I have to start a new session. Needless to say, this doesn't work well. That said, if the Nvidia drivers work for you, the Nvidia configuration tool is your best bet. In order to configure the proprietary Nvidia drivers, take these steps:
 
1. Run the following command in your terminal: ```
sudo nvidia-xconfig
```It may give you a "success" message, but more likely it will give you a parsing error warning and state that it's creating a new file. This is an important step, otherwise, as you've discovered, you can't save the changes you make in the following step.
 
2. Now that you've prepared the xorg.conf file with the previous step, run the following commange in your terminal (again as sudo): ```
sudo nvidia-settings
```This will open your usual Nvidia settings GUI, configure as desired, and then save the configuration file. I've always opted to merge the changes with the existing file, which seems to work fine for me.
 
3. Try restarting your computer and see if everything works as desired.
 
If you aren't gaming and performing tasks that require the enhanced features of the Nvidia proprietary driver, my ultimate solution was to stick with the default driver and configure my dual monitor setup with xrandr. This configuration takes place on a user/session basis, which I actually like better. So when I first turn on my computer I see cloned screens with the login menu. As soon as I login, my settings are then applied and my dual monitor configuration takes affect. There are several GUI interfaces for xrandr, but they don't to save your settings permanently. They are handy, however, to determine your monitor names for creating your own configuration file so you may want to explore those. Alternatively you can just run "sudo xrandr" to get this information.
 
So my final solution was to create a new file within your home folder called .xprofile and include the following contents, adjust according to your needs and monitor names:```
#Define monitors.
xrandr --output VGA-1 --mode 1680x1050 --rate 60
xrandr --output DVI-I-1 --mode 1680x1050 --rate 59.9
 
#Set DVI monitor as primary.
xrandr --output DVI-I-1 --primary
 
#Set VGA monitor to the right of DVI monitor.
xrandr --output VGA-1 --right-of DVI-I-1
```
Another option is to create/configure your own xorg.conf file. There are a number of threads related to this. You may find the following links helpful in your efforts too:
 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)
 
Hope that helps! I love Xubuntu, so the effort is worth it for me.

---


---
title: "change default display manager from kdm to gdm"
date: 2010-09-26
forum: Desktop Environments
---

### Post by fugai7 on 2010-09-26
I am rather new to ubuntu, I installed 6.04 LTS on my machine and the upgraded to 8.04 LTS, and then 10.04 LTS. I was playing around with appearance settings and chose the highest level of window animation but this seemed to cause some sort of problem with gnome (the top bar of windows disappeared including minimize, maximize and close buttons). So I used command line to *reinstall* gnome (*sudo apt-get update && sudo apt-get install ubuntu-desktop*) and this fixed the problem, but because i didnt realize what i had done to cause it i tried to do the animation settings again, which messed it up and became unfixable by using the above command, so i installed the kde desktop environment using command line and chose to use kdm as the default display manager because i thought i might have to uninstall gnome and didnt want to lose all display managers. Later on i had another idea of how to fix my gnome problem, i chose the highest level of animation again in the appearance settings but when it asked if i wanted to keep these settings or use previous settings i chose previous which reverted back to the lowest level and the window bar came back!

Because i got this fixed i didnt want to use the kdm display manager anymore, so i modified the */etc/X11/default-display-manager* file from */usr/bin/kdm* to */usr/**bin**/gdm*, at the time i didnt realize it was supposed to be ***s**bin*! so i restarted the computer and now it cant find the file for kdm or gdm because gdm is in sbin and kdm is in bin but its looking for gdm in bin. So i have been trying to use recovery boot up to edit the file, which is where my problem is: whenever i try to edit the */etc/X11/default-display-manager* file to read */usr/**s**bin/**gdm***, it displays that i do not have write permissions and that it is a read only file. I have used sudo with every command, and tried nano and vi text editors.

**Long story short** I need to edit the */etc/X11/default-display-manager* file to read */usr/**s**bin/**gdm*** but it will not let me due to "write permissions" even when im using root and sudo; any suggestions?

All help is greatly appreciated

---

### Post by tom4everitt on 2010-09-26
Use the following commmand to give yourself write permission:

sudo chmod +w filename

Then you will be able to write to it (using sudo). Since it is supposed to be read only, you might want to remove the write permission afterwards:

sudo chmod -w filename

---

### Post by ankspo71 on 2010-09-26
Hi,
Try booting into recovery mode then use this command to see if it will help fix things.
```
sudo /usr/sbin/update-alternatives --config x-session-manager
```

If it doesn't help you might have to boot into the ubuntu live cd and correct any mistakes you made on the hard drive. After doing that, restart you computer and boot into the the installed ubuntu on the hard drive then use the above command. It should work then.

---


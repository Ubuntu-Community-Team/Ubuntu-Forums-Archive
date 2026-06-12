---
title: "command runner applet for budgie"
date: 2017-09-05
forum: Desktop Environments
---

### Post by holiday2 on 2017-09-05
Mate has a panel item 'Command' which I think is command-runner-applet. 

I can't find this in Budgie 17.04. 

I've tried to install command-runner-applet but it is not found. 

Is this applet available in / for Budgie? If so where?

Thank you

---

### Post by Frogs Hair on 2017-09-05
All applets for the Budgie panel are in the panel settings. A Mate applet wont work in Budgie though it might help to explain how you use the applet. As I remember in Gnome 2 this was a small gui for running commands instead of using the terminal.

---

### Post by holiday2 on 2017-09-05
> **Frogs Hair said:**
> All applets for the Budgie panel are in the panel settings. A Mate applet wont work in Budgie though it might help to explain how you use the applet. As I remember in Gnome 2 this was a small gui for running commands instead of using the terminal.

Thank you for responding. 

I have looked through the applets in Budgie settings and don't see anything like it. 

In Mate I have a script that writes out hostname, IP address, Ubuntu version, kernel version. The command runner applet puts this output to the panel.

This is useful for me because I am working with a number of VMs for testing network utilities and this applet gives me ready information about which VM I have in focus, its IP address and so on.

---

### Post by Frogs Hair on 2017-09-05
It will run in Ubuntu 16.04 , but not budgie. I was thinking of something entirely different . :)

---

### Post by Habitual on 2017-09-05
Is this "command runner" Alt+F2?

---

### Post by holiday2 on 2017-09-05
> **Habitual said:**
> Is this "command runner" Alt+F2?


No. Alt-F2 opens a dialog. 

The panel applet I'm thinking of is like the panel applet that displays the time. It is always there. 

Though instead of displaying the time, this applet displays the output of a script -- or of any command.

---

### Post by davidmohammed on 2017-09-06
for 16.04/17.04 make sure you have enabled backports via budgie-welcome - recommendations. Fully update and reboot.

Then navigate to budgie-welcome - software - budgie applets and install budgie-sysmonitor-applet

This will allow you to display various sensors - or you can connect up your own script to display the output to the panel

---

### Post by holiday2 on 2017-09-06
> **davidmohammed said:**
> for 16.04/17.04 make sure you have enabled backports via budgie-welcome - recommendations. Fully update and reboot.

Then navigate to budgie-welcome - software - budgie applets and install budgie-sysmonitor-applet

This will allow you to display various sensors - or you can connect up your own script to display the output to the panel

Thanks. I had been ignoring the 'Welcome'. I see that it is worth exploring. 
--

Ok, I did as you suggest. In raven the applet displays as Panel System Monitor. This applet shows usage % for cpu and memory,  but has "No settings available". 

I found [https://github.com/fossfreedom/indicator-sysmonitor ]("https://github.com/fossfreedom/indicator-sysmonitor")

I installed via ```
apt install indicator-sysmonitor
```, but although it is said to work with Budgie, it does not show as an applet in raven.

---

### Post by Frogs Hair on 2017-09-06
holiday2, enter the following commands. logout or reboot and check the applet list. This will add more installable applets. 

```
sudo apt update 
```

```
sudo apt install budgie-haste-applet
``` For Scipts^

---

### Post by holiday2 on 2017-09-06
Thanks frogshair. I appreciate your effort. 

But the haste applet is for sharing via paste bin or some share service. There may be a way of warping it to my purpose but I don't see it.

---

### Post by again? on 2017-09-06
Perhaps you can use conky to display the info over the panel.
Don't use budgie but have installed and I can display on the panel.
If interested let me know and you can test a config.

---

### Post by holiday2 on 2017-09-08
Found this:

[https://github.com/kacperski1/budgie-script-applet.git](https://github.com/kacperski1/budgie-script-applet.git)

Close enough.

---


---
title: "Unity will not start up - System Is Running in Low Graphics Mode"
date: 2017-06-18
forum: Desktop Environments
---

### Post by Matt3223 on 2017-06-18
Hello all, I am having some difficulties on my ubuntu 16.04.2 install that seems to have started after a dist-upgrade I performed on 2017-06-17. (might be coincidence, but is the only thing of note I can think of).

I get the following pop-up box once ubuntu begins attempting to load:
> 
The System is running in low-graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

I am able to switch to terminal via ctrl+f1 and log-in. Upon logging I just now noticed that there was a message indicating the following:
> 
[    57.361112] systemd-logind[1526]: Failed to enable subscription: Launch helper exited with unknown return co... (I think that is supposed to be "command", my snapshot cut off...)
[    57.361165] systemd-logind[1526]: Failed to fully start up daemon: Input/output error

I did not see that during the irc troubleshooting I reference below, so that was not known at the time by the person assisting me.

History of the system:
Have had 16.04 installed for several months with no issues. I have an RX460 graphics card and have installed the AMDGPU-PRO-16.50.

I also have Solus and Windows installed on seperate partitions, they both boot up and function fine.

I have done some troubleshooting via #ubuntu on freenode, but we were unable to come up with much beyond the desktop is not starting up. I will post the relavant termbin.com links below.


info from cat var/log/apt/history.log info: [http://termbin.com/k272](http://termbin.com/k272)  (start-date: 2017-06-17 is when I believe the issues started. the 2017-06-18 entry I did today from the terminal.)

info from lshw -C display : [http://termbin.com/2dvc](http://termbin.com/2dvc)

info from cat /var/log/Xorg.0.log :  [http://termbin.com/28q1](http://termbin.com/28q1)

info from cat /var/log/gpu-manager.log : [http://termbin.com/sxdj](http://termbin.com/sxdj)

info form lsmod | grep amdgpu : [http://termbin.com/kg3j](http://termbin.com/kg3j)

info from cat .xsession-errors in ~ : [http://termbin.com/h48i](http://termbin.com/h48i)

I am just a user, thus have limited self-directed troubleshooting knowledge, but I know enough to follow some directions. :)

I also tried to restart lightdm, with sudo restart lightdm, but got a message stating:
> 
Restart:  Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: connection refused

Looking for some assistance, thanks!

---

### Post by again? on 2017-06-18
Are you getting to the unity greeter/login screen?
If so, you can install the flashback session to give an xsession to work in while you attempt to fix.
```
sudo apt install --no-install-recommends gnome-session-flashback
```
Then at the greeter see if you can log into the **Gnome Flashback(Metacity)** session.

---

### Post by Matt3223 on 2017-06-19
Nope, sorry, the system doesn't make it to the greeter. After hitting enter (or waiting) at Grub, a line will pop up like:
> 
/dev/sda6: clean ...### files, ...### blocks...

Then the screen will go blank again, then the window will pop up on the blank screen talking about low-graphics mode.

---

### Post by again? on 2017-06-19
> **Matt3223 said:**
> Nope, sorry, the system doesn't make it to the greeter. After hitting enter (or waiting) at Grub, a line will pop up like:


Then the screen will go blank again, then the window will pop up on the blank screen talking about low-graphics mode.

You mentioned you could login to a tty.
I had an experience recently where in Ubuntu-gnome the display manager gdm3 was failing to load.
If the issue is with lightdm you could try installing another display manager to see if it loads.

In my case I installed slim which enabled me to log in to a graphical session and troubleshoot.
```
sudo apt install slim
```
You should be presented with a dialog to choose your display manager.
If not run
```
sudo dpkg-reconfigure slim
```

If you still don't get a greeter must be graphics driver related and
I will leave for someone familiar with amd graphics.

You can switch back to the lightdm display manager by running
```
sudo apt remove slim
sudo dpkg-reconfigure lightdm
```

---

### Post by Matt3223 on 2017-06-19
hmm, no luck there, after choosing slim, I no longer get the pop up window about low-graphics, but the system hangs on a black screen with a blinking cursor and I can no longer access tty1
(off to bed now, will check back in a.m.)

---

### Post by again? on 2017-06-19
Oh sorry about that.
ctrl+alt+F1 still brought up a tty when I Installed slim.
You can remove slim and reconfigure lightdm in [**_Recovery Mode_**]("https://wiki.ubuntu.com/RecoveryMode").

---

### Post by Matt3223 on 2017-06-19
yeah no worries, was worth a shot. I'll try and reset via recovery mode and go from there... 

I have been trying to see what messages are going across during boot, but haven't succeeded... would those be in a log some where... ? I'll google around and try to find some systemd logs. Something is going wrong early in the process.

---

### Post by Matt3223 on 2017-06-19
OK, i have reconfigured lightdm and we are back to where we began.


here is the apport.log... anything informative in here? [http://termbin.com/reh6](http://termbin.com/reh6)

not sure what the no dbus session bus address means..

---


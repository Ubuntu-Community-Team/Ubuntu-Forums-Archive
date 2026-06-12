---
title: "dosnt work when installed"
date: 2011-06-21
forum: Desktop Environments
---

### Post by Bynw on 2011-06-21
Hi all. 

Ran into an issue I am unable to solve on my own and not sure even fully where to look at this time.

Been running the standard Ubuntu (Gnome) installation for some time and with 11.04 has come the Unity desktop. Giving it a fair shake and run through but not really liking it so I decided to switch to KDE. I had used KDE many years ago with another distro and on other computer.

To try out KDE on my computer, I used the LIVE CD for KUBUNTU. It booted fine. I was able to use the LIVE CD and thought I would go ahead and install it and make the switch from Ubuntu to KUbuntu.

Once I had Kubuntu installed on the harddrive. The system would not fully boot up. I would get the login screen. Would enter my username and password and then on the next screen where KDE has its set of 5 icons before you reach the desktop.

The system would just stop at the 4th icon. It would remain "out of focus" on that icon and then would lose all mouse and keyboard control. 

So I am wondering what could potentially cause that to happen when booting from the harddrive but not the LIVE CD.

(( I Have gone back and reinstalled the Unity/Gnome version of Ubuntu so I would have a working computer ))


Thanks

---

### Post by Bucky Ball on 2011-06-21
From the login screen in 11.04 you can click 'Sessions' and select 'Classic Ubuntu' and you will get the Gnome desktop environment if that is any good to you. You don't have to use Unity. You possibly already know that, though.

---

### Post by Bynw on 2011-06-21
Yep. Already knew that and do use that currently. But thinking ahead for the future when 11.10 comes out, and its alternatives are Gnome 3 which is similar to Unity. Then I will need to get something else.

---

### Post by Bucky Ball on 2011-06-21
10.04 LTS is supported until 2013. No rush. (Unless, for whatever reason, you just have to be on the cutting edge.) ;)

---

### Post by iclestu on 2011-06-22
you probably realise that you can have Gnome/Unity installed and KDE installed?

just do:

```
sudo apt-get install kubuntu-desktop
```

then you can choose which desktop at the login screen.

---

### Post by Bynw on 2011-06-22
Yes, same results. KDE crashes and will not run when installed to the harddrive. It will ONLY work when running from a LIVE CD.

---

### Post by Bucky Ball on 2011-06-22
Hmm. This is slightly off the OP's topic but there is no need to install kubuntu-desktop. In fact, in some instances, that is definitely *not* what you want as it installs *all* Kubuntu packages and you may get conflicts with existing Gnome ones. The preference would be to install kde (which is the desktop environment used by Kubuntu) *only* from Synaptic Package Manager. 

This installs kde desktop environment, *not* the multitude of possibly unwanted packages that you're gonna download with kubuntu-desktop.

---

### Post by iclestu on 2011-06-22
> **Bucky Ball said:**
> Hmm. This is slightly off the OP's topic but there is no need to install kubuntu-desktop. In fact, in some instances, that is definitely *not* what you want as it installs *all* Kubuntu packages and you may get conflicts with existing Gnome ones. The preference would be to install kde (which is the desktop environment used by Kubuntu) *only* from Synaptic Package Manager. 

This installs kde desktop environment, *not* the multitude of possibly unwanted packages that you're gonna download with kubuntu-desktop.

yeah, fair point

---

### Post by Bynw on 2011-06-22
How do you install just KDE from Synaptic?


I may give it another attempt but there is the perplexing problem that previous attempts have all failed. They cause the system to lock up on in the process of bringing up the KDE desktop. Unless I am using a LIVE CD on the same machine, that works correctly all the time.

---

### Post by iclestu on 2011-06-22
> **Bynw said:**
> How do you install just KDE from Synaptic?


I may give it another attempt but there is the perplexing problem that previous attempts have all failed. They cause the system to lock up on in the process of bringing up the KDE desktop. Unless I am using a LIVE CD on the same machine, that works correctly all the time.

you can just do

```
sudo apt-get install kde
```

---

### Post by iclestu on 2011-06-22
presumably it will be in the list for the synaptic gui too.... just search kde

---

### Post by Bynw on 2011-06-26
just a package named KDE is not in the synaptic gui at all.

---

### Post by Bynw on 2011-06-26
I'm going to go ahead and restate my issue. I want to run KDE on my desktop computer. 

So I tried out the KUBUNTU live cd. This worked fine. No errors, no problems. So I installed KUBUNTU to my harddrive, overwriting all previous settings and OS.

KDE does not load up when being ran from the harddrive. After inputting my username and password there is a screen that comes up with 5 icons as the desktop loads up. 

The first icon is a harddrive, 2nd is a settings icon, 3rd is a networking icon, the 4th looks either like desktop icon or a terminal icon and then finally the K icon. After these you get your destkop with all the widgits and the like.

I'm gonna drop a link here to that above screen. It is the 4th icon that never comes into focus, They all start blurry and then focus and then the next icon starts to come in. Everytime I run Kubuntu from the harddrive, the 4th icon never comes into focus and the entire system locks up.

Link to that image ... [http://www.anlarye.net/Screenshot.png](http://www.anlarye.net/Screenshot.png)

What makes this issue complex is that it WORKS from the LIVE CD. It works running as a Virtual Machine in VirtualBox on the same computer that it does NOT work from the harddrive directly.

Thanks

---

### Post by RHTopics on 2011-06-26
Bynm,

When the installed Kubuntu system locks up after trying to log in, see if you can do a "Ctrl-Alt-F1" key combination to bring up a virtual terminal.

If that works then log in and see if you can determine the problem.  One thing you could do is entered the "top" command to check if the CPU is being consumed by a particular application or process.

You could also check the /var/log/syslog file to see if a bunch of error messages are being written to it.  You can do the command "tail -n30 /var/log/syslog" to display the last 30 lines in /var/log/syslog.

---

### Post by zellis on 2011-06-27
I second the CTRL-ALT-F1 trick to get a login where you can do stuff at least (press F7 to get back to your graphical display after you do this). However, a file that will have more information about user-level X login will probably be .xsession-errors in your $HOME directory. It will have a LOT of entries iirc. 'tail .xsession-errors|less' will let you see the end of it.

Each of those icons on the KDE splash screen is supposed to represent a part of KDE starting up. I think the one you're getting stuck on is supposed to represent the KDE's plasma framework starting up (or failing to start up, in your case). Sorry I can't actually tell you why at this stage. I'm assuming the plasma-desktop package was automatically installed, if you installed kubuntu from CD?

---

### Post by ubume2 on 2011-06-27
Hi there,
I had same problem. I fixed with terminal. Seems to be bug with Kubuntu.

see my thread at Kubuntu forums:
[http://kubuntuforums.net/forums/index.php?topic=3117406.0](http://kubuntuforums.net/forums/index.php?topic=3117406.0)

From a terminal enter:
```
sudo nano /home/yourusername/.kde/share/config/kwinrc
```

and change OpenGLIsUnsafe=false

to true. Save. Reboot. The effects might not work, but you can then get to a workable desktop.
If you do this from rescue mode, I recommend text editor nano. (After edit Ctrl+o, press enter, Ctrl+x to exit)

---


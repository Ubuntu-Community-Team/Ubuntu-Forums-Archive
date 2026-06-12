---
title: "How to run a script after login (new version of startup applications will not)"
date: 2018-05-08
forum: Desktop Environments
---

### Post by pksings2 on 2018-05-08
I' m trying to start the Pulseaudio Equalizer automatically when my multimedia server is logged into.  (Bionic Beaver 18.04)   The new version of the "Startup Applications" app only lets you start apps that are officially installed apps. No obvious way to make it run a script.

---

### Post by monkeybrain20122 on 2018-05-08
In gnome shell you have to go through the exercise of writing a .desktop file for the script, put it in  .local/share/applications in order for tweak tool or whatever to detect it. It seems the "logic" is along the line of making you put an empty document in template in order for "create new document" to show up in nautilus's context menu. It seems much work in gnome development goes into making it more complicated and frustrating to do what used to be simple tasks.

---

### Post by pksings2 on 2018-05-09
Is there a version of 18.04 that does not require this?This is so not going to happen.Developers of Ubuntu, please take note. The machine this concerns is a multimedia server that has HDMI input to a 5 channel mixer that needs equalization to sound good.  Without some way to easily run a script to start the EQ this version of Ubuntu is no longer suitable to be the O/S of this server. (Running a script is required to start Pulseaudio Equalizer).   This used to work fine.  (16.04) and now it doesn't (18.04).  I have no choice but to install a different O/S that does easily let me do what I need.  Thanks for all your efforts, it's really much appreciated. But this ability change makes this unusable for me.

---

### Post by tinylagarto on 2018-05-09
I am not a Gnome user and understand that it is frustrating but yes, you could take another flavor where it is indeed easy to add startup applications the way you remember. 

Although I think it is possible even in Gnome either using the Tweak Tool, I hope still, or by starting gnome-session-properties from terminal or with Alt + F2.

---

### Post by monkeybrain20122 on 2018-05-09
> **pksings2 said:**
> Is there a version of 18.04 that does not require this?.

Startup Applications works in the old way in the [unity]("https://community.ubuntu.com/t/ubuntu-unity-experience-project-wiki/2553") session (install ubuntu-unity-desktop, make lightdm the default, install xserver-xorg-input-synaptics if you use a touch pad, reboot, that's it) I am using unity here. Use the unity maintainer[ ppa]("https://launchpad.net/~unity7maintainers/+archive/ubuntu/unity7-desktop") for best results

But writing a .desktop file is not hard, just annoying (copy template from a ,desktop file in /usr/share/applications, change the Exec= line to the path to your script, change the Name= line etc)

---

### Post by monkeybrain20122 on 2018-05-09
> **ivanovnegro2 said:**
> 

Although I think it is possible even in Gnome either using the Tweak Tool.


Yes, if you make a .desktop file for the script and put it in ~/.local/share/applications, tweak tool only allows startup applications with a .desktop file (aka launcher)

I have dualbooted with Fedora for a few years and played with 17.10 so I have some experience with gnome shell, it seems that each new release is getting more weird and more anti-users, they keep removing useful features and adding useless ones as if just to maximize user frustration intentionally,performance is always crappy, I am done with it. /end of rant

---

### Post by Dennis N on 2018-05-09
In Ubuntu 18.04, I have a startup script that runs on log in but I have the script in **~/bin** and the desktop file in **~/.config/autostart**. That works fine for me.

---

### Post by monkeybrain20122 on 2018-05-09
> **Dennis N said:**
> In Ubuntu 18.04, I have a startup script that runs on log in but I have the script in **~/bin** and the desktop file in **~/.config/autostart**. That works fine for me.

Script can be anywhere. Point is you need to make a .desktop file. I put my scripts in ~/bin too but that is optional.

---

### Post by Dennis N on 2018-05-09
And my way, I don't need tweak tool to make it work.

---

### Post by monkeybrain20122 on 2018-05-09
> **Dennis N said:**
> And my way, I don't need tweak tool to make it work.

Sure but still you need a .desktop file.

---

### Post by Randy_Bass on 2019-01-22
I run the XFCE desktop environment on Ubuntu. XFCE is the default DE for Xubuntu, but I prefer Ubuntu. I also had a lot of issues upgrading to 18.04, and came here looking for how to install a script to run on startup. After reading this, I poked around and discovered that XFCE makes it real easy. I select Menu, Settings Manager, Sessions and Startup, Application Autostart tab. I select the Add button at the bottom. This calls up a dialog box. I input a name, description, and click on the folder icon to navigate to the script to select it. Select OK, and I'm done.

---

### Post by dlfuller@ClientandFuller. on 2019-02-28
I have Ubuntu Server 18.04 and only the command line through SSH.  Also no ~/.config/autostart directory.

Can I simply create the autostart directory and put my little login script in there?  Do I still need a .desktop file?

---


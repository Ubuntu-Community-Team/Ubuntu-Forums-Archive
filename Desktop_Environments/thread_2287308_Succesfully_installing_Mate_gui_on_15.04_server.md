---
title: "Succesfully installing Mate gui on 15.04 server"
date: 2015-07-18
forum: Desktop Environments
---

### Post by c_xy on 2015-07-18
Hello,

How does one install mate as a gui on 15.04 server? We just want a lightweight desktop environment to on the server.

I've seen different ways to do it, but wasn't sure what is the correct way for 15.04 server.

Is it

```
sudo apt-get install mate-desktop
```

or

```
sudo apt-get install mate-desktop-environment-extras
```

With the  methods above, and then after rebooting, i did **not (edit)** get a login screen. Just the terminal command line without a gui.

I also tried

```
sudo apt-get install ubuntu-mate-desktop
```

Using the "ubuntu-mate-desktop",and then rebooting, I could not login to Mate at the login screen. Every time I entered my password it said Login incorrect, Failed to start session.

Thank you for your time.

c

---

### Post by Bucky Ball on 2015-07-18
Installing anything-desktop is going to drag in a whole lot of defaults. You only want the desktop environment, not that. 

Thought of xfce4 or lxde, both very lightweight and should be easy as:

```
sudo apt-get install xfce4
```

Replace xfce4 for lxde for that. Log out and in. Anyhow, doesn't sound like you found [this]("http://wiki.mate-desktop.org/download#ubuntu_1404_lts_trusty_thar"). As slim as you can get with Mate looks like this option:

```
sudo apt-get install mate-desktop-environment-core
```

That will drag in the least amount of defaults.

---

### Post by QDR06VV9 on 2015-07-18
This would be one of a few ways
The official MATE development team have [maintained PPAs]("https://launchpad.net/%7Eubuntu-mate-dev/+archive/ubuntu/trusty-mate") which when used, uplifts Ubuntu 14.04 to Mate 1.8.1
  In order to correctly install and configure MATE 1.8.1 on Ubuntu you will also need to add their PPAs:
  Open a terminal complete the following steps to enable the appropriate PPAs and install MATE 1.8.1 on Ubuntu .
  ```
sudo apt-add-repository ppa:ubuntu-mate-dev/ppa
sudo apt-add-repository ppa:ubuntu-mate-dev/trusty-mate
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --no-install-recommends ubuntu-mate-core ubuntu-mate-desktop
```
The Trusty part might have to be amended to vivid. I have never done this method of installing mate due to the large download size
around 300MB so be Aware of that.
Bucky Ball beat me slow typer I guess.(lol)
Kind Regards

---

### Post by Bucky Ball on 2015-07-18
@runrickus: OP only wants the desktop environment, which seems to be impossible with mate, and the mate-core is about as close as you'd get. That's why I gave the advice I did. According to the link I provided the command you provide installs the entire kit and kaboodle. The --no-install-recommends is definitely recommended, yes, but not sure if anything but the mate-core is if after just the desktop environment, or close too it.

---

### Post by QDR06VV9 on 2015-07-18
> **Bucky Ball said:**
> @runrickus: OP only wants the desktop environment, which seems to be impossible with mate, and the mate-core is about as close as you'd get. That's why I gave the advice I did. According to the link I provided the command you provide installs the entire kit and kaboodle. The --no-install-recommends is definitely recommended, yes, but not sure if anything but the mate-core is if after just the desktop environment, or close too it.
+1
Installing mate the way he was asking about is not the most ideal way! I would very much agree with your suggestion over mine.
So that being said if you want you can delete my thread.

---

### Post by c_xy on 2015-07-18
Wow! Thanks guys for the quick and helpful feedback.


```
sudo apt-get install mate-desktop-environment-core
```


I tried the method above.

After reboot, i just get the black and white terminal screen with the login.

I then updated my nvidia-drivers (I usually had to do this if with a xubuntu or unity install).

Rebooted.

And now during the reboot

It is currently hanging at 

> 

[OK]  Started Light Display Manager




Now, I didn't install the ppa since it says in the link provided above that:  "[COLOR=#000000][FONT=sans-serif]MATE 1.8 has been available in official repositories since Ubuntu 14.10."

[/FONT][/COLOR]On a side note, in the past I've used  for

xcfe4

```
sudo apt-get install xubuntu-desktop
```

And also for lxde


```
sudo apt-get install lubuntu-desktop
```

What is the difference between xfce4 vs xubuntu-desktop?  lxde vs lubuntu-desktop? When installing those DE's.
 
c

---

### Post by Bucky Ball on 2015-07-18
Yes, they don't work for mate. 

You should purge the nvidia drivers for the moment. Wrong way to go. Log in at the CLI after boot and try:

```
startx
```

or 

```
sudo start service lightdm
```

Any luck? If not, you might need to add 'nomodeset' to the kernel line. We'll go there if required.

* Actually, try this FIRST. When you are at the screen at boot, highlight your kernel and hit 'e'. Find the line that ends 'quiet splash'. After a space, add 'nomodeset'. Follow the instructions at bottom of screen to save and boot.

You will probably get to the CLI. Follow instructions at beginning of this post.

---

### Post by c_xy on 2015-07-18
I tried:

```
startx

The program 'startx' is currently not installed. You can install it by typing:

sudo apt-get install xinit


```


and


```
 sudo start service lightdm

sudo: start: command not found


```


I just tried 


```
 start
The program 'start' is currently not installed. You can install it by typing:

sudo apt-get install upstart



```


So, I installed xinit, and then tried startx

First error message:

(EE) Please also check the log file at "/var/log/Xorg.0.log" for additoinal information. (EE)  (EE) Server terminated with error (1). Closing log file.g...

xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error


I then tried install upstart

But then I received error messages about"

>>Warning<< Wrong ufstype may corrupt your filesystem, default is ufstype=old

And it kept repeating.

c

---

### Post by Bucky Ball on 2015-07-18
Sorry, that should have been:

```
sudo service lightdm start
```

:)

PS: I wouldn't start installing things randomly. You may cause breakage. Avoid if you're not sure what you're installing. Trying to install upstart was probably a bad idea. :|

---

### Post by c_xy on 2015-07-18
Yeah, i just did a fresh reinstall of 15.04 to clear things out.

So I ran the same installation:

```
 sudo apt-get install xubuntu-desktop 
```

Then rebooted.

Came back to the black and white terminal no login screen.

Then I typed:

```
sudo service lightdm start

Failed to start lightdm.service: Unit lightdm.service failed to load: No such file or directory


```

I was tempted to install lightdm, but didn't want to open another can of worms. :D

c

---

### Post by v3.xx on 2015-07-18
Try using the full path with startx.  I believe the correct command for your desktop is
```
startx /usr/bin/xfce4
```
I do not have xfce installed and cannot verify this, maybe Bucky can.

---

### Post by Bucky Ball on 2015-07-18
As I mention, you install xfce4, not xubuntu-desktop if you want just the desktop environment. Now you have Ubuntu plus Xubuntu pretty much. Bloat, duplicated programs and a lot of stuff you don't need. You may also find some conflicts between apps and dependencies. 

If you install xubuntu-desktop, you may as well have installed Xubuntu from the start or tried it from install media.

---

### Post by c_xy on 2015-07-19
Okay, so i've kinda given up trying to install Mate at this point. Appears to be too much trouble trying to install.


I tried installing lxde and xfce4 as suggested earlier in this thread.  Those work.

However, we are transitioning from Ubuntu 10.04 were we really like the old gnome-2 desktop environment. Quite simple, easy to use, and not hard on resources. This is why we wanted to try mate because it is similar to gnome-2, correct?

Is there a way to install metacity gnome-flashback by itself.

I tried using:

```
sudo apt-get install gnome-session-flashback
```

Seems like it would only work if I had unity (ubuntu-desktop) installed first.

But it failed to come up with a gui after reboot. Does  the gnome-session-flashback depend on having gnome-3 installed with it? Does it always install both with metacity and compiz? Can you just install metacity only?

c

---

### Post by v3.xx on 2015-07-19
To get around installing most (not all) Unity packages when installing the Flashback desktop..
```
sudo apt-get install xinit && sudo apt-get install --no-install-recommends gnome-session-flashback
```
Either us startx (I think better) or a display manager to boot.

[http://packages.ubuntu.com/utopic/gnome-session-flashback](http://packages.ubuntu.com/utopic/gnome-session-flashback)

[http://packages.ubuntu.com/vivid/xinit](http://packages.ubuntu.com/vivid/xinit)

---

### Post by c_xy on 2015-07-21
Hello,

I tried installing the flashback with the commands above with no success.

After some issues with tyring to install metaciy-flashback and mate, I tried working with lxde. I had success installing that. It was a simple install. 

I installed lxde with the command:

```
sudo apt-get install lxde
```

It is a bare desktop. I had to install firefox and will eventually install libreoffice. But, what is also missing is the software updater and additional drivers options. I can't find them under system tools, preferences, accessories or other. Is there an apt-get install command I need to use?

Thanks,

c

---

### Post by v3.xx on 2015-07-21
You could install synaptic
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)
```
sudo apt-get install synaptic
```
The synaptic gui will look washed out (color & font).  This can be corrected with the package "obconfig".  Let the tweaking begin :)

---

### Post by Bucky Ball on 2015-07-21
```
sudo apt-get install update-manager
```

... will give you Update Manager. Synaptics can do it for you though, as suggested. Is that a default app in Lubuntu? Or just use a terminal whenever you decide. I never use Software Updater (update manager).

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

If you want to have a look at your Software Sources:

```
nano /etc/apt/sources.list
```

I think Software and Updates is:

```
sudo apt-get install software-properties-gtk
```

... but better check that. :)

If you install lubuntu-desktop that would probably drag in all the things you're familiar with along with a lot of other things you're probably never going to use. I'd learn a bit and add things as you need them rather than installing lubuntu-desktop. That will make a mess. It is generally very easy to install what you need as you go from the repos (especially if you use Synaptics).

Once you've got it how you want it, create an .iso with Clonezilla and you have created your own unique spin! Good luck. :)

---

### Post by c_xy on 2015-07-21
Thanks guys. 

I think I'll stick with the lxde installation for now.

This command

```
sudo apt-get update-manager
```

Was exactly what I was looking for.

So far so good with lxde. Just had to install a few things like update-manager, firefox, etc.

That should be more than suffice.

A few things I noticed:

If I select software updates from the selection panel or indicator bottom panel, I can't install updates even though I am logged in as root user on the server. I can only do this using the command:

```
sudo update-manager
```

On our old system (10.04), I could click the update-manager icon or select software updates on the panel, then implement the updates while logged into the server machine. I could never do this logged in remotely from a nomachine client. But could do it logged directly into the server. I could even do it experimenting with  metacity gnome-flashback on this newer machine. But under lxde, i can't do this. Is that how it functions using lxde?


My xorg runs the CPU pretty high on the server machine. Sometimes close to 100% when moving or resizing terminal windows. Or if the screensaver pops up. It really drives the CPU.  But this overworking of the CPU by xorg does not occur if I connect remotely to the server using nomachine. Why is this the case?

Thanks again.

c

---

### Post by Bucky Ball on 2015-07-21
Please mark this thread as solved and create a new thread(s) for any further issues. (See first link in my signature.) Your original support request has been resolved, if not solved, and it will greatly improve your chances as the title of your thread has nothing to do with you new issues. Post a link to the new thread here if you wish. Thanks and good luck.

---


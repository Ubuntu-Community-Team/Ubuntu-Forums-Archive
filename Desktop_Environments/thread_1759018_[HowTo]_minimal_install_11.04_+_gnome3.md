---
title: "[HowTo] minimal install 11.04 + gnome3"
date: 2011-05-15
forum: Desktop Environments
---

### Post by -unseen- on 2011-05-15
Since I'm not a fan of default distributions, since they leave me with a bloated system of programs I don't really want or need, I tried a minimal install of ubuntu and gnome3. I also like a clean system without remains of gnome2 which I no longer use right now. The system works surprisingly well so far, so I thought I'd share how to install it that way.

If you are going to try this,make sure you have some knowledge of the package system and know how to install a command line system from the alternate cd. So if things get messed up, you're not immediately lost (since there won't be a gnome2 classic or unity on your system after this).

You will need a network connection at all times for this.

- Ok, the first thing is to install a command line system from the alternate cd. The command line system is in the F4 menu of the installer right before you start installation.

- After it is installed and rebooted I was left with a blank screen. For some reason it boots into tty7 where usually the graphical login manager comes up. Since its not there, ctrl+alt+f1 to tty1 and login.

- First thing to do is to update sources and bring the system up to date:

sudo apt-get update
sudo apt-get upgrade

- Then we need to install a package which lets us add ppas to the sources:

sudo apt-get install python-software-properties

- Next is to add some repositories:

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:ricotz/testing    (add this if you want to use the gnome3 network manager and more up to date gnome-shell builds)

- Ok lets update the sources again:

sudo apt-get update

- Now install the system:

sudo apt-get install xorg
sudo apt-get install gnome-session gnome-shell gdm

if you use any other graphics driver than the xorg ones install them now (e.g.):

sudo apt-get install nvidia-current

- At last install the gnome terminal:

sudo apt-get install gnome-terminal

- Ok, now lets reboot. If all went well you should be greeted by gdm. Select ubuntu gnome shell session and login. Goto system settings and change that ugly brown desktop background ;)

- Now for the network manager. This is a bit more tricky, but it gets you a working gnome3 network-manager (only with enabled ricotz ppa, otherwise just install the network-manager-gnome package, it will give you a version just a little bit older, but it will not work with the gnome-shell black and white menus).

Install some browser and download the following two packages for your architecture and put them in a new directory (so there are only these two files in it):

UPDATE: The wpasupplicant package made it to the ricotz ppa, so there is no need to install it manually anymore.
[http://packages.ubuntu.com/oneiric/net/wpasupplicant](http://packages.ubuntu.com/oneiric/net/wpasupplicant)
[http://packages.ubuntu.com/oneiric/libs/libssl1.0.0](http://packages.ubuntu.com/oneiric/libs/libssl1.0.0)

They are in the natty repositories, but versions are too old.

Then:

sudo apt-get install libnl1 libpcsclite1
goto the directory with the oneiric packages
sudo dpkg -i *.deb
sudo apt-get install network-manager-gnome

- reboot. If you are using DHCP this should be it, if you manually assign your IPs do the following:

sudo vi /etc/network/interfaces
comment out any reference to your network interfaces (for me this always is eth0).

- reboot. start nm-connection-editor from a terminal and add your connection. Done.

- for locking the screen we need one more package:

sudo apt-get install gnome-screensaver

- for printing:

sudo apt-get install cups cups-pk-helper
sudo apt-get install system-config-printer-gnome

For me adding printers from the new cc didn't work (this is not a minimal install issue), so launch system-config-printer from a terminal and it should work from there.

- archive manager for zipped files

sudo apt-get install file-roller


- After installing everything you can do a

sudo apt-get clean

to clear all downloaded *.debs. Baobab shows an installation size of roughly 2.5gb.


And this is it you are now left with a working gnome3.

I'll be happy about comments, or further hints on how to sort out problems with this.

---

### Post by Frogcrush on 2011-05-17
Hi

I keep getting this error when trying to log in:

"Failed to load session "gnome"". 


Any thoughts?

---

### Post by -unseen- on 2011-05-17
Hi, I only get an error like this if I select "ubuntu" in the gdm dropdown menu. "gnome shell session" and "user defined" are working ...

Is a working 3d graphics driver installed? Are all the dependencies of gnome-session and gnome-shell installed?

---

### Post by Frogcrush on 2011-05-17
Thanks!

I was running it in VirtualBox, and I didn't know I had to have 3D acceleration (or maybe it was how much vram i allocated). 


Thanks for the quick reply!

---

### Post by philnice on 2011-05-21
**-unseen-**, i'm not sure if i'm going to try it since my hardware is pretty old and i'm using ati also, so..., but this is a great post.=D>
Of course, i'll let you know if i decide to move on with this.

---

### Post by -unseen- on 2011-05-21
Thanks, I'd be happy if more people tried this :)

I did this install on a 5 year old notebook with an ati x700 mobile, and it works quite well. It gets a little choppy if there are lots of open windows, but it is very usable. There are only the xorg drivers running which automatically get installed during xorg installation.

---

### Post by LarsKongo on 2011-05-21
That's the way I install all my desktops. I can't stand all the bloat I don't need. :p 

Btw, for those who are trying this in VirtualBox 4.0.8 (or later.) You need to install the guest additions in the terminal to be able to login. Also make sure that you've allocated 128MB Video RAM for the machine.

Here's how: (If you're using the normal version and not OSE.)
1. If you're in tty7 (GDM running.) Press CTRL+ALT+F1 to switch to tty1.
2. Click on the menubar and select Install Guest Additions.
3. Then type this in the guest machine:
[I]sudo mount /dev/scd0 /media/cdrom
sudo sh /media/cdrom/VBoxLinuxAdditions.sh[/I]

Then restart/start GDM or just reboot.
*sudo reboot now*

I can also point out a bug in the Alternate CD installer. Before you select F4+Cli+install you should press F3 and select your keyboard layout. Otherwise you'll get an US keymap.

---

### Post by philnice on 2011-05-21
> **-unseen- said:**
> Thanks, I'd be happy if more people tried this :)

I did this install on a 5 year old notebook with an ati x700 mobile, and it works quite well. It gets a little choppy if there are lots of open windows, but it is very usable. There are only the xorg drivers running which automatically get installed during xorg installation.
Well, now that i know you're using ati also, i'm thinking of it even more... :)
I quited upon all of my natty - gnome3 attempts because i ended up with a cpu running at 100% for common tasks like, firefox. Additionally some programms useful to me like mixxx, wouldn't work either. 
But having a clean install like this, reduces the chances for such problems to come up.
Ok, i have a spare partition with ugr on it which i don't use. 
I'm gonna try.

---

### Post by TunaCanTommy on 2011-05-22
Just did a successful install on an ASUS EeePC 701.
No glitches . . . but I used WICD for network manager.

---

### Post by satanselbow on 2011-05-22
Hi all - 

The minimal install is my preferred route and I have been writing a bash script (a simple wget and off you go)  to automate the process. I also prefer to use the gnome3team ppa exclusively as it erm... less experimental, shall we say - I find it less buggy than the alternatives ;)

I will try and get it online over the next couple of days - just some minor debugging (to cover a few common config possibilities) and away we go :popcorn:

This particular post is sent from OneIric (64-bit) + Gnome 3 (just to be really flash) which was installed by the same scripted method.

**If you are having trouble with logging into Gnome3 Shell you may need to create correctly formed .desktop files in /usr/share/xsessions**

You can call the actual .desktop file anything you like - the entry you see in the greeter list is taken from the "Name" entry in the .desktop file itself ;) 

For "Full" Gnome 3 Shell:

```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME 3 Shell
Comment=This session logs you into GNOME with GNOME 3 Shell
Exec=gnome-session --session=gnome
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0

```For Gnome 3 Shell (Fallback) - assumes you installed "gnome-session-fallback" from the ppa

```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME 3 Shell (Fallback)
Comment=This session logs you into GNOME with the traditional panel without any 3D effects.
Exec=gnome-session-fallback
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0

```For Xterm Recovery Console:

```

[Desktop Entry]
Encoding=UTF-8
Name=Recovery Console
Comment=Failsafe session with only xterm
Exec=xterm
TryExec=xterm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm

```
To start gdm from a terminal:

```

sudo service start gdm   * restart / stop are also valid ;) 

```Happy Hacking :popcorn:

---

### Post by leemaster81 on 2011-06-24
This is one of the best howto's I've googled up. I first tried installing gnome3 alongside of natty(unity). Then build from source... No luck. Alternate Ubuntu 11.04 has bugs, as gnome3 does but I made it through the hurdles. With a clean minimal install. Once I get. All resources together maybe  I will make an addition to this great how to!

---

### Post by xekon on 2011-07-30
Thank you. I just installed using this guide.

for this step:
```
sudo apt-get install nvidia-current
```

I did this:
```
sudo add-apt-repository paa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

EDIT:
Decided to give KDE a try, I have altered this install method for KDE: 

[http://ubuntuforums.org/showthread.php?p=11104014](http://ubuntuforums.org/showthread.php?p=11104014)

---


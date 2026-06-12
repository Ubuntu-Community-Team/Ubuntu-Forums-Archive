---
title: "Low graphics mode after update- ruined"
date: 2009-01-31
forum: Desktop Environments
---

### Post by alexham on 2009-01-31
Hi, Guys,

I have just "updated" my system and I now have low resolution display - absolutely awful.  The error message on boot up says: "Low graphics mode - screen card could not be detected".  Also the keyboard setting have changed.

I have installed the developer's menu.lst during the update, thinking like any logical person that the update will not be "out of date"!!!

I have a copy of my old menu.lst on an USB stick but cannot copy it - permission denied.

Can anyone help me get back to the pre-"downgrade" position?

By the way, I have just noticed that I have about 4 options on the grub screen at boot up. The top one gives me poor resolution; next one down is the recovery mode and one below that is the one that gives me back the "Quality" that I have lost.  

How do I make the system reboot on that option?

Alex

Thanks,

Alex

---

### Post by Blackdragon1400 on 2009-01-31
I have the exact same problem!

Yet i have tried to re-load my old graphics drivers (worked last time that I broke them) and yet to no avail everything is still jacked up. I am pretty much barred from my graphical interface i cant even see some most of the windows the resolution maxes out at 640*480!!!!

PLEASE HELP!!!!!!!

!!!!! 
i just tried the option (fix X server or whatever) in the recovery list. It seems to have at least partially fixed it. I get my resolution back but no drivers, ill try to install the nvidia drivers again...

---

### Post by Blackdragon1400 on 2009-01-31
Ok, this seems to have fixed it, 
boot into the recovery mode. 
Repair X
Boot back into normal mode
Reinstall your old graphics drivers
reboot, and tune ur settings

try that! it worked for me

---

### Post by alexham on 2009-01-31
> **Blackdragon1400 said:**
> Ok, this seems to have fixed it, 
boot into the recovery mode. 
Repair X
Boot back into normal mode
Reinstall your old graphics drivers
reboot, and tune ur settings

try that! it worked for me
Blackdragon, you are a genius!!!
It worked for me too and I did not even have to reinstate old drivers nor adjust anything. As I booted back into normal mode after Repair X it was restored to what it was before.

Many thanks indeed,

Alex

---

### Post by mustard675 on 2009-03-17
i have this problem except it doesn't give me an option to recover.. updated the system and now this mess.

booted with the cd but apparantly it doesn't have recovery mode on it. so i allowed it to boot from the cd to see what would happen and everything is acting normal. so now what do i do with the harddrive boot? why did the update futz everything up and how do i fix it?

CTRL - ALT - BKSP 
doesnt do anything

sudo dpkg-reconfigure -phigh xserver-xorg

gives me error: 

$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for jd:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090317213746

Found this guy's solution and am currently trying to use it to fix the problem:
[http://groups.google.com/group/honyaku-linux/browse_thread/thread/664641c73f067368](http://groups.google.com/group/honyaku-linux/browse_thread/thread/664641c73f067368)

---

### Post by mustard675 on 2009-03-18
SOLVED!

[http://groups.google.com/group/honyaku-linux/browse_thread/thread/664641c73f067368](http://groups.google.com/group/honyaku-linux/browse_thread/thread/664641c73f067368)

basically when the upgrade is done it doesn't pull the updated nvidia packages for whatever reason. get these and you'll be good to go!

i'll quote the post here just incase that website doesnt work in the future. all credit goes to the guy jon. thanks!

[QUOTE="jon"]These are notes to myself, buy in case anyone runs into the recurrent
problem of losing their desired video configuration after doing an
Ubuntu update, it may be helpful.

Today was a typical Ubuntu 8.04 update. The update-manager wanted to
update files, including those listed below. When I see files like these
a red flag goes up and I know I'm going have to do some work to get the
video to work properly after the update. I have an NVIDIA GeForce FX
video board with dual outputs,  and I want to enable hardware
acceleration, which means I use the "nvidia" driver instead of the
built-in "nv" driver in my /etc/X11/xorg.conf file, and I want to enable
TwinView to support my two LCD monitors, etc.

linux-headers-2.6.24-19
linux-headers-2.6.24-19-386
linux-headers-386
linux-image=2.6.24-19-386
linux-image-386
linux-restricted-modules-common
linux-ubuntu-modules-2.6.24-19-386
nvidia-glx-new

I let the update-manager do it's thing, downloading and installing
updates. It'll ask you to reboot to install the updated kernel modules,
etc.

But the requisite reboot will also have the effect of rudely ignoring my
X configuration (xorg.conf) and defaulting back to its bare-bones
minimum, awkward but usable VGA video configuration.

At the "Ubuntu is running in low graphics mode" screen, I just hit
'continue' having found that trying to detect or configure anything from
this screen is a waste of time. So I log into my big kindergarten
800x600 (or whatever it is) screen. (Sometimes my tool bar is so huge
that I have to delete some of the applications to get at the Main Menu.)

First I check the status of my HW drivers
(System/Administration/Hardware Drivers). It tells me there are no
proprietary drivers in use. This is a casualty of the update because
they were installed and in use just before I did it, thank you very
much. And this is the crux of the problem.

I run synaptic to see what the hell happened. Search for "nvidia" to get
a list of everything (except the linux kernel versions) that pertains to
my nvidia video. I find

jockey-common [That's good.]
jockey-gtk ['cause I'm running gnome desktop and gnome apps]

And there are some left-over linux-restricted-modules, such as
-2.6.24-16-386, -2.6.24-17-386, and -2.6.24-18-386 to take the current
case. Sometimes I'll mark some of the older ones for deletion, leaving
only the last one or two in case I need to revert to them for some reason).

But there is NO -19 to correspond to the "linux-image=2.6.24-19-386"
package which was one of the red flag files mentioned above! No
linux-restricted-modules-2.6.24-19-386. And therein lies the problem.
Somehow, whatever is supposed to be smart enough to grab the latest
restricted modules to match the updated kernel, isn't.

So I mark linux-restricted-modules-2.6.24-19-386 for installation. [Of
course if I were running a 64bit machine or something else, I'd get the
appropriate version here.] Other things, such as nvidia-new (whether you
use this or nvidia-glx or nvidia-glx-legacy will depend on your specific
video card requirements), and nvidia-kernel-common and nvidia-settings
are still installed okay. I check to see that xserver-xorg-video-nv is
installed just in case I have to revert to that plain Jane driver if all
else fails. Then I tell synaptic to Apply the changes I've made which is
simply to add the -19 restricted-modules.

I've probably got something checked somewhere that says "Don't
automatically install any non-free modules, or something, and that may
be why I have to go through all this crap.

After synaptic downloads and installs
linux-restricted-modules-2.6.24-19-386, I close synaptic and check my
hardware drivers again. Now the list shows the NVIDIA driver as
installed and enabled BUT NOT IN USE. So I will need to either reboot or
just restart X which I will do by logging out and in again, to force the
system to use my xorg.conf file instead of the failsafe X configuration
file that it is now using.

But first, just to be sure it doesn't ignore my xorg.conf file and use
its own fail safe kindergarten video fallback file again, I open a
terminal and check that my xorg.conf is still in its proper place
(/etc/X11/) and that in Section "Device", the Driver is "nvidia" [not
"nv" or something else], and that my BoardName is "NVIDIA GeForce FX
(generic)", that "glx" and "v4l" are being loaded in Section "Module"
and a few other things. Convinced that it's still the same old xorg.conf
that I've learned to love, an acquired taste, as with fine whiskey and
feisty women, for good measure I rashly delete all other xorg.conf
files, including the fail safe files, and old backups. (I usually keep
one of my own (not automated by Ubuntu) backups of the precious xorg.conf.)

After logging out and back in, BINGO! This time my two screens are
nicely configured as one big sweep of unbroken real estate 3200 pixels
across and 1200 pixels high, as I like 'em. Gnome comes up, my single
tool bar across the top is endowed with its app and applet goodies and
every thing's right with world. After a disconcerting 30-minute
interruption, I can get back to ah, work.

But the real question is: Should Ubuntu be preceded by an "a" as in "a
YOUbuntu update" or an "an" as in "an OObuntu update"?

Jon [/QUOTE]

---


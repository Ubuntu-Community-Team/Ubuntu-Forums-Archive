---
title: "Attempting Dual Monitor w/ NVidia"
date: 2009-02-20
forum: General Help
---

### Post by ahop on 2009-02-20
I have two video cards in my computer.  One of them is an NVidia GeForce MX 420 that I have two monitors hooked up to (nothing is in the second card right now).  I am trying to get dual monitors setup, and I have tried several tutorials on the web.  

Where I am getting hung up is that I don't think the right drivers are setup.  When I go into the Administrative section, I see there is an option to activate one of two NVidia drivers.  I do that, and restart, both thiw the same issue: GNOME won't start.  Here is what I get.

```
Starting up . . .
Loading, please wait . . .
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/bd536c96-2dc3-49ad-97ff-34ae1f3c8195) = 
ev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/bd536c96-2dc3-49ad-97ff-34ae1f3c8195
kinit: No resume image, doing normal boot
Ubuntu 810 ubuntu tty1
```

Followed by the normal login.  I tried to run

```
sudo /etc/init.d/gdm start
```

But that doesn't work either.

Any thoughts?  How can I find out which driver it is that I will need?  I guess this is really two separate questions here. I appreciate any thoughts or comments anyone might have.

---

### Post by Herman on 2009-02-20
My best freind is a grader operator and he installed Ubuntu in a new laptop which belongs to a professional machinery operator trainer and safety expert. 
This man's business depends on being able to run his projector from his laptop to show machinery training and safety videos. Luckily my friend didn't delete Windows when he installed Ubuntu, (as he normally loves to do), because we weren't sure at first if we could get this particular laptop's VGA port working at first. It has an nvidia graphics card.

We succeeded in getting the laptops' nvidia card set up for two monitors (or a projector) without too much trouble after only a little bit of time, but I'm sorry I can't remember the exact details I used. I did something like the following.

First, make sure all your repositories are enabled in 'System'-->'Adminstration','Software Sources', then open 'Applications','Add/Remove' and set the spinbox in the top middle to 'Show: all available applications'.

Then, in the search field, type: nvidia
Install the NVidia binary X.Org driver ('new' driver), and NVIDIA X Server Settings at least, and maybe a few more items you'll see there that look like they might be helpful or interesting.

Then if you have Hardy Heron do this:[1.8.2 Configuring multiple monitors with a nVidia graphics card]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Configuring_multiple_monitors_with_a_nVidia_graphics_card")- Hardy Heron Ubuntuguide.org
If you have a different version of Ubuntu than Hardy Heron, look for equivalent instructions in the appropriate ubuntuguide for your version of Ubuntu, [UbuntuGuide Main Page]("http://ubuntuguide.org/wiki/Main_Page").

Finally, look for the icon for your Nvidia X Server Settings program in one of your menus and find the settings to set up more than one monitor. 

That worked for us and now we have another new Ubuntu enthusiast. We resized his Windows down to a minimal size as it will probably never be needed, and increased the Ubuntu partition to dominate the laptop's hard disk. :D

Regards, Herman

---

### Post by ahop on 2009-02-20
First off, thanks.  I am a Windows convert, just frustrated one day, backed up all my files and wiped the system clean.  I feel so fresh and alive with Ubuntu (8.10-and yes I found the applicable wiki you referred me to) :D

Now, I got to this point before, and I am there again.  When I open the nvidia settings, it says that I need to run nvidia-xconfig.  I did that, made a backup and a couple of minor tweaks, and all looked right, just needed to restart.

Then, I get back to the same messages as below, and the GDM won't load.  I am not even sure how to undue the driver change, so my only other option (that I know of) is to reinstall Ubuntu!

There's got to be A) a better way to get around this; and B) a step in the driver installation process that I am missing.

---

### Post by rjstep3 on 2009-02-21
Hello World

my first post in this forum, and I am trying to do what the original poster wants to do.

I have a desktop, with nvidia GeForce 7950 GX2, connected to two flat screen panels.

By default, the second didn't work, but by going to the X server settings tab, I can enable the second screen by clicking on the "dead" screen and going to "Configure ...". There I enabled the screen, BUT I ended up with Twinview, rather than "Separate X Screen". This latter just tried to save settings to some sort of X configuration, and wouldn't let me when I tried to do it anyway.

TwinView gives me what I want, so far.

The only glitch is that when hovering with the mouse over the top bar of an application, it tends to do funny things to the bar, which sort of blinks and loses its colour. It seems to be worse with some apps than others. More testing required I suppose.

Don't know if this helps, but a big thank you to Herman who pointed me in the right direction.

rjstep3

---

### Post by ahop on 2009-02-21
Unfortunately, it is still not working for me.

I ran **startx**, and this is what I get

```
Primary device id not PCI
(EE) No devices detected.

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such provess (errno 3): Server error.
```

---

### Post by rjstep3 on 2009-02-21
hmmm, beyond me I am afraid.

Why not go to the nvidia settings panel, under Administration and try setting from there? 

rjstep3

---

### Post by ahop on 2009-02-21
Apparently you actually have to download the ***right*** drivers for your video card (yes that was sarcasm).  Idiot that I am, I kept trying the driver for my second card that I am not using rather than the Geforce FX 5200.  Oops. :oops:

---

### Post by Herman on 2009-02-22
A useful command for finding out what video card a computer might have in it (if we don't already know and if we don't want to open the computer case and shine a light in to take a look) is,
```
lspci -x | grep -i "vga\| display"
```
Did you get it working yet?

---

### Post by ahop on 2009-02-22
> **Herman said:**
> Did you get it working yet?

I did, thanks. I was trying to install the Driver 96 and not 173.  I have it set on Twinview now, but with a 1024x768 and 1280x1024 setup, it kind of stinks that you can't get a FULL representation of the desktop, and that new apps open in the middle of the two. I will play around some more and see what I can do to work around these issues.

---

### Post by Herman on 2009-02-23
If you click 'mirror' or 'mirrored view', or something like that, you will have the full picture in both monitors simultaneously, otherwise you will have half a picture in either monitor.

When it's not in mirror view mode, (split view I guess you might call it), you can drag the icons for the monitors around so they're side by side or one above the other to change the way the way the image is displayed, (whether it's the left or right or top or bottom half of the screen.

You should be able to find some settings also to make the display upside down or turned 90 degrees on it's left or right-hand side. I suppose that's in case you have a ceiling mounted projector, or a monitor on the ceiling or on a wall (sideways).

'Mirrored' is the setting I like best, and I think that would be the same for most people.

---

### Post by ahop on 2009-02-23
Why is it that you like mirrored the best? I have been mostly using Twinview. What do you personally see as the advantages?  Thanks for the thoughts.

---

### Post by Herman on 2009-02-23
I should have explained myself better, (sorry), I mean the setting called 'mirror screens'.
When you go 'System'-->'Preferences'-->'Screen Resolution', do you see a setting right at the top right-hand corner called 'mirror screens?
If you have a check in the box for 'mirror screens and click 'apply', you should be able to have the same picture in both monitors. You may be asked for your password and asked to log out and to log back in again before the changes will take effect.

I don't have the computer with the Nvidia card here anymore, it belongs to someone else, but I have my Eeepc, so now I have it plugged in to a second monitor instead, just to see what settings I'm describing to help you. I'm hoping yours is similar enough for my advice to make sense.

---


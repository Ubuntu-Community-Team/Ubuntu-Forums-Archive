---
title: "Change your Dell XPS m1710 leds..."
date: 2007-11-18
forum: Dell  Ubuntu Support
---

### Post by Nunslaughter on 2007-11-18
[SIZE="6"][COLOR="RoyalBlue"]**[CENTER]XPS Led Changer 0.5.2[/CENTER]**[/COLOR][/SIZE]

[CENTER]This version is tested and proved working on:
[LIST]
[*]Ubuntu 8.04
[*]Ubuntu 7.10
[*]Ubuntu 7.04 live-cd
[*]Linux Mint 4
[*]Mandriva 2008
[*]OpenSUSE 10.3
[/LIST]
Your distro not listed? Contact me and I'll see what I can do.[/CENTER]


**_[SIZE="4"]Requirements[/SIZE]_**

Libsmbios and the unsupported bins.

[LIST]
[*]Ubuntu 8.04
```
sudo apt-get install libsmbios1 libsmbios-bin
```
Libsmbios1 should be already installed by default, but check for it anyway!


[*]Ubuntu 7.10 & Linux Mint 4
```
sudo apt-get install libsmbios1 libsmbios-bin
```

[*]Ubuntu 7.04
I have included dellLEDCtl in the package, so you should only install libsmbios.
```
sudo apt-get install libsmbios1
```

[*]OpenSUSE 10.3
Install this package:
Libsmbios-unsupported-bin


[*]Mandriva 2008
These 3 packages need to be installed:
  libsmbios1
  libsmbios-bin
  pygtk2.0-libglade
[/LIST]


**_[SIZE="4"]Installation[/SIZE]_**

[LIST]
[*]Download the package for your distro
```
[[COLOR="DarkOrchid"]Download XPS Led Changer]("http://xpsledchanger.sourceforge.net/download.html")[/COLOR]
```

[*]Start the program by going to Applications=>System Tools (Depends on distro & desktop environment)
[/LIST]


**_[SIZE="4"]Known Issues[/SIZE]_**

**No known issues with this version yet. Contact me if there's something wrong!** 


**_[SIZE="4"]Help & Contact[/SIZE]_**
[LIST]
[*]You can ask for help in this thread, I check it atleast once a day.


[*]Or you can contact me by [EMAIL="timovwb@gmail.com"][COLOR="SeaGreen"]e-mail[/COLOR][/EMAIL]
[/LIST]



[http://xpsledchanger.sourceforge.net](http://xpsledchanger.sourceforge.net)

---

### Post by showgun22 on 2007-11-19
I must say thank you very much it is a nice little tool IT seems to work fine if I had only one thing to add it would be an intensity control for each option.
But again my thanks to you for taking the time to do it...

---

### Post by Nunslaughter on 2007-11-20
Thank you very much! 

I'm also working on intensity control, but I don't know yet what would be the easiest way to do...
I'll have a look at it this week...maybe I can fix something already!

---

### Post by Nunslaughter on 2007-11-22
new version available...a big code cleanup, also no need to modprobe dcdbas yourself, and the same comboboxes for gutsy and feisty...

intensity control isn't that easy (or i just didn't find a good solution yet), but i'm still working on it...

---

### Post by wataboutbob on 2007-11-28
hey thanks! this worked out very well for me.

---

### Post by d0wser on 2007-11-28
TNX! Thats great tool! very impressed - it worked for me too.

---

### Post by Nunslaughter on 2007-12-07
Thanks for the reply's!
I just uploaded a new version that will allow you to change the color intensity! It's not possible to change the intensity for each zone seperate, but I don't think that works with the Dell tool on windows either...

---

### Post by bladerunner2019 on 2007-12-07
Awsome job ! 
Thanx a lot ! 
Big Time ! ... bye bye Vista ! 

where can i find your new version ? 

and ........ can you make the subwoofer work ?

---

### Post by Nunslaughter on 2007-12-07
I editted my first post, see the attached file there, it's version 0.4.

I don't know about the subwoofer, I never looked at it. But I think I read something somewhere about the alsa mixer, maybe on this forum...

---

### Post by showgun22 on 2007-12-07
I just tried it and in my case the intensity change only work if you select it first before opening a color and to change it you need to turn off the color first and then select your the intensity and after turn on the color.

But it does work.

Thanks

---

### Post by Nunslaughter on 2007-12-08
> **showgun22 said:**
> I just tried it and in my case the intensity change only work if you select it first before opening a color and to change it you need to turn off the color first and then select your the intensity and after turn on the color.

But it does work.

Thanks

Yes I know, that's why there's a default value in the intensity combobox when you start the program.
You don't need to turn the colors of when switching intensity, just select the intensity you want and reselect your color.

I'll have a closer look to it, maybe I can write the code so you won't have to choose the intensity value first.

---

### Post by oni5115 on 2008-01-05
Just wanted to post a thanks.  =)   I didn't know how to get the command line stuff working right until I noticed your instructions mentioning to modprob dcdbas.

Also wanted to mention the script works great on an XPS m170 as well.

---

### Post by Nunslaughter on 2008-01-10
And thank you for posting :). 

This program will automaticly modprobe dcdbas for you on startup. So, actually you don't have to worry about a thing, but install libsmbios first.

Also good to know that it works on a m170 as well.

---

### Post by Nunslaughter on 2008-01-15
> **showgun22 said:**
> I just tried it and in my case the intensity change only work if you select it first before opening a color and to change it you need to turn off the color first and then select your the intensity and after turn on the color.

But it does work.

Thanks

Ok, it took a while, but it is fixed now. The intensity isn't linked anymore to the color so you can change everything separate.

---

### Post by boomix on 2008-01-28
Just quick one from me. I have been messing with command line tool ever since I've been pointed over to it. But I want to say great job and yes it works on XPS2 like a charm.

Keep up the good work.

---

### Post by Nunslaughter on 2008-02-05
Thanks boomix, great that it also works for you!

I uploaded a deb file for easy installation!

---

### Post by drsaamah on 2008-02-12
okay maybe there's something wrong me...
I've installed libsmbios1 and libsmbios-bin straight from the repository (ie sudo apt-get install...) and when i run 'sudo dellLEDCtl' i get nothing.  Not even an error...  Could you please guide me through this?  Sorry to be a pain.  Im running an M1330, and I want the wifi LED to work properly.  The Bluetooth works fine.  Thank you.

---

### Post by Nunslaughter on 2008-02-13
> **drsaamah said:**
> okay maybe there's something wrong me...
I've installed libsmbios1 and libsmbios-bin straight from the repository (ie sudo apt-get install...) and when i run 'sudo dellLEDCtl' i get nothing.  Not even an error...  Could you please guide me through this?  Sorry to be a pain.  Im running an M1330, and I want the wifi LED to work properly.  The Bluetooth works fine.  Thank you.

I'm sorry, but this is not for wifi or other LEDs.

Some XPS notebooks (m1710, etc) have 3 "zones", speakers, fans and backpanel. In these zones they have LEDs that can change into 16 different colors. So thats what this program does.

You can always try to type in the terminal:
sudo dellLEDCtl -h
or:
sudo dellLEDCtl -i
to get some info, but I don't think it will be usefull for you.

I see you have the N-card fom Dell. Is it the Intel 4965AGN card? Because that indicator LED doesn't work for others either, I even upgraded to the Hardy kernel (2.6.24-5), now the card works a lot better but the light still doesn't work.

---

### Post by drsaamah on 2008-02-13
ohh im sorry i misunderstood.  Yes my wifi card is the Intel AGN card.  I wasn't totally surprised that the wifi led didn't work because on my old Dell laptop it also didn't work (on every version since Edgy).  What do you mean though about the card working "better"?  Did you have connection issues with Gutsy?

---

### Post by Nunslaughter on 2008-02-13
No problem :)

Well, in Gutsy with the default kernel, I had problems when there wasn't any network activity for about 10 minutes, then it wouldn't connect back. I had to reboot to get my connection back...
Then I tried Wicd instead of Network Manager and it worked better, but still not good. So I upgraded to the latest kernel with this how-to: [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)
Now the card works ALOT better than before, I also have about 40-50% better connection.

---

### Post by drsaamah on 2008-02-13
interesting.  fortunately i havent had that problem (maybe because i used the dell-version ubuntu disk image?) so im gonna stay with the gutsy kernel until hardy comes out.

---

### Post by FreeSoul on 2008-02-23
First, looks like a great piece of software, I'm glad I stumbled upon it. This will make sleeping when the computer is running a lot easier, with no need to throw a shirt over it. :guitar:

My problem, I'm running 7.04, I installed both "dependency" libraries (edit - Through synaptic) and I still get the message:

> Error: Dependency is not satisfiable: libsmbios1

Any ideas?

Thanks,
FreeSoul

---

### Post by Nunslaughter on 2008-02-23
Hey FreeSoul, thanks for the kind words! Too bad you couldn't get it running yet, but I know what the problem is.
The deb-package is actually for 7.10, so you should download the tar.bz2 instead..

The problem is that the installer checks for libsmbios 0.13.5 or above, and I think in the Feisty repo's it's only 0.13.2.  Thats why it's giving you that message.

So, if you follow these steps, everything should work for you. Ofcourse if you get any errors, you can post them here and we'll try to figure it out!

First, get these three things done:
Download [this](http://linux.dell.com/libsmbios/download/libsmbios/libsmbios-0.13.6/libsmbios-0.13.6.tar.gz) and [this](http://downloads.sourceforge.net/xpsledchanger/xpsledchanger-0.5.1.tar.bz2?modtime=1202082909&big_mirror=0) and unpack them in your home folder.

Open up the terminal and type:
sudo apt-get install build-essential
wait untill it's done, then typ:  (each line seperate)
cd libsmbios-0.13.6/
./configure
make
sudo make install

Make sure there aren't any errors with these steps.

Then -still in the terminal- type:
cd
cd xpsledchanger0.5.1/
sudo ./install_xpslc  (You'll see some stuff that is done and it asks you to make a menu entry, just press "y")

Now, if everything went ok, you go to Applications=>System Tools=>XPS Led Changer to start the program.

Hope this helps you out!


[COLOR="Red"]EDIT: This isn't usefull anymore for Feisty users, I uploaded a special deb-package for you people![/COLOR]

---

### Post by Nunslaughter on 2008-03-24
I have uploaded a new version, it fixes two major things and some little code changes.

So enjoy!

---

### Post by Nunslaughter on 2008-04-25
For Ubuntu 8.04 the package for 7.10 works just fine.

I'm also working on a new version that has some new features (CPUtemp/color, notification colors). But I don't know when it will be released.

---

### Post by trinity.treize on 2008-05-14
Thank you for this Project. I'm using Ubuntu 8.04 64-Bit Version and had to force the dep Package to install due to wrong architecture.

For those who don't know how to do it:

```

sudo dpkg --install --force-architecture /path/to/32-bit-package.deb

```

It works just as it says on the box ;-)

Keep the good work!
A 64-Bit Deb would be nice.

---

### Post by Nunslaughter on 2008-05-15
Yep sorry for that. I noticed it too that it wouldn't install on 64-bit. I'm not sure what went wrong with making the deb-package. I'll have a look at it (maybe today). Anyway, it's just the deb-package that doesn't install on 64-bit, but the tar.bz2 should do it fine.




EDIT: new 32 and 64-bit packages uploaded for Ubuntu 8.04.   (Naming is just to clarify. 7.10 and 8.04 package should be the same.)

---

### Post by trinity.treize on 2008-05-15
> **Nunslaughter said:**
> Yep sorry for that. 
EDIT: new 32 and 64-bit packages uploaded for Ubuntu 8.04.   (Naming is just to clarify. 7.10 and 8.04 package should be the same.)

Yay! Just mentioned it for the non-geeky guys 8-)

---

### Post by Guruji on 2008-06-24
to enable subwoofer, open the volume control panel, check that "device" is "HDA Intel (Alsa Mixer)", then go to the preferences and enable "LFE"... and feel the baaasee..

(not about the leds... but someone asked about it in this tread)

---

### Post by Guruji on 2008-06-24
very nice piece of software, is it possible to enable/disable the trackpad led as well?

(M1710, ubuntu 8.04)

---

### Post by Nunslaughter on 2008-06-25
You're correct about the subwoofer, found that out too when I was messing with the sound again some time ago.


The touchpad led is not controllable. I think it worked on 7.04, but I'll have to check that out to see if I wasn't dreaming.
Or maybe it's just my system, you can check it yourself by typing this:
sudo dellLEDCtl -z4 0
and
sudo dellLEDCtl -z4 1

It doesn't do anything here.

---

### Post by Guruji on 2008-06-25
hmm... the commands are not doing anything..

i turned the leds off by default in in the bios.. so maybe it might interfere with the command, but your soft is working on the other leds (that are also disabled in the bios).. so i don't know.. i'll try to activate the trackpad led in the bios and see if the command is working.

---

### Post by Nunslaughter on 2008-06-25
It probably won't. I'll send an e-mail to the guy who actually wrote the dellLEDCtl program and see what he knows about this. I will also boot from a Feisty cd and see if I'm right about the touchpad led working there.

---

### Post by Guruji on 2008-07-10
i activated the trackpad led in the bios... and yeh.. as expected... no change...

---

### Post by Nunslaughter on 2008-07-17
Sorry for the late reply, but I got it to work. I don't know if this really is the right solution, cause I played alot with libsmbios and dellLEDCtl. But you can try to download and compile the [latest libsmbios version](http://linux.dell.com/libsmbios/download/libsmbios/libsmbios-2.0.2/) (install with ./configure, make and sudo make install) and then try this in a terminal:

sudo /usr/local/sbin/dellLEDCtl -i

Be sure to use this path and not the old /usr/sbin. If you get this it should be ok:
Libsmbios version      : 2.0.2
Then try this:
sudo /usr/local/sbin/dellLEDCtl -z4 0  (turn off)
sudo /usr/local/sbin/dellLEDCtl -z4 1  (turn on)


If this works for you also, I'll do a little update so you can change the touchpad LED from the GUI.

---


---
title: "How can I change the look of 12.10?"
date: 2013-01-21
forum: Desktop Environments
---

### Post by rayray519 on 2013-01-21
Hello I am in the process of installing 12.10 but I want the look of 10.10.  What is the easiest way to do this?  Any help would be appreciated.

Thanks,

---

### Post by meteorrock on 2013-01-21
I went into the settings of my 12.10 and selected the 'autohide' feature to tuck away that side launcher on the left. Just gets in the way, shrinks your working screen on a landscape monitor to a square box and its buggy. You will see after trying to drag and drop icons onto your desktop out of that launcher during use. 


Another option is to download Docky. You can autohide that mistake of a launcher in the system settings >> appearance >> behavior tab. It will still be there but out of the way. To bring it back, just hit your superkey, the windows emblem key on your keyboard. It will appear for a few seconds to get into the main default launcher that comes by default with Ubuntu 12.10. Here is the link for docky, if you want to take a look over that app. It will put a launcher at the BOTTOM of your screen if you want it there. [http://wiki.go-docky.com/index.php?t...the_Docky_wiki](http://wiki.go-docky.com/index.php?t...the_Docky_wiki)

 ~~~~~~~~~~~~~~~~

 To get into the options on docky, as it will install itself at the bottom of your screen running the code below,straight after its done after you input that code below, just hit on the anchor icon, there are options in there to change your docky to a taskbar with glass effects if you want. It is really customizable out of the box. It even starts up with what apps you had in your launcher by default. It can not get any simpler or more beautiful. It even has an autohide feature if you want in its options for a full screen experience and ACTUALLY works when you mouse over it, unlike the default launcher with Unity. 

 It even comes with a "Window Dodge" option, where it will appear when you exit out of your web browser, and hides itself when you open up your web browser. Quite the amazing program. Great job by the developers for that app, I say.

 Here is the terminal code for docky. 

```
sudo add-apt-repository ppa:docky-core/stable
```

```
sudo apt-get update
```

```
sudo apt-get install docky
```

With the ppa, it will update with sudo apt-get update. 

~~~~~~~~~~~~~~~~~~~~~~~~~~
Don't forget about development options up in XDA developers forums at this link here for their flagship device. [http://forum.xda-developers.com/forumdisplay.php?f=860](http://forum.xda-developers.com/forumdisplay.php?f=860)

---

### Post by 3rdalbum on 2013-01-21
This wont be an option much longer, so I highly recommend getting used to the Unity interface that comes with Ubuntu now. It's rather good, very different to old Gnome 2.

If you still want something that emulates the Gnome 2 layout, install the gnome-panel package and then you can choose Gnome Fallback from the cog menu on the login screen.

---

### Post by aspergerian on 2013-01-22
> **rayray519 said:**
> I want the look of 10.10.  What is the easiest way to do this?

You might consider Xubuntu. I too wanted a 10.x look. 
See [SOLVED] wanting top/bottom bars as in ubuntu 10.04
here: [http://ubuntuforums.org/showthread.php?t=2098800](http://ubuntuforums.org/showthread.php?t=2098800)

---

### Post by oldfred on 2013-01-22
I use fallback or gnome-panel in 12.04, not sure how well it works in 12.10. A few things have changed location and a few things are different, but not much more than any upgrade. 

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by sontag on 2013-01-30
(newby question!)

Sorry, I wasn't sure where to post -please redirect if appropriate.

I had installed gnome classic on my new ubuntu 12.04, and everything was fine, until I changed some settings (snap-back and such) in 
gconf-editor
-> apps --> compiz-1 --> plugins --> grid_screen0 --> options

While making changes, gnome crashed, and when rebooting:
my startup console and emacs open, but there are no menu bars, and there are no panels (top nor bottom).  System is completely unusable!!!!
[I also see messages regarding my nvidia card having problems determining the precise monitor specs... I believe that I never saw any such messages before.  However, the monitor and x settings seem to be fine, see below.]

Now, if I reboot and now as for gnome classic WITH NO EFFECTS, everything looks normal.

So, I could work from now on on gnome classic no effects.  However, I feel that my system is unstable, and I would have liked to get back to normal.  I don't like it that I broke something.  (If I try to log into X as gnome or gnome classic (with effects), I have the same problem.)

Perhaps there is some system-wide gnome file that I could rest to default?

Note: I changed my
/home/[my username]/.gconf/apps/gconf-editor/%gconf.xml
to be basically empty, but this changed nothing.

So I am looking for some more global file that seems to have some bad settings.

THANKS!!!

---

### Post by kansasnoob on 2013-01-30
> **sontag said:**
> (newby question!)

Sorry, I wasn't sure where to post -please redirect if appropriate.

I had installed gnome classic on my new ubuntu 12.04, and everything was fine, until I changed some settings (snap-back and such) in 
gconf-editor
-> apps --> compiz-1 --> plugins --> grid_screen0 --> options

While making changes, gnome crashed, and when rebooting:
my startup console and emacs open, but there are no menu bars, and there are no panels (top nor bottom).  System is completely unusable!!!!
[I also see messages regarding my nvidia card having problems determining the precise monitor specs... I believe that I never saw any such messages before.  However, the monitor and x settings seem to be fine, see below.]

Now, if I reboot and now as for gnome classic WITH NO EFFECTS, everything looks normal.

So, I could work from now on on gnome classic no effects.  However, I feel that my system is unstable, and I would have liked to get back to normal.  I don't like it that I broke something.  (If I try to log into X as gnome or gnome classic (with effects), I have the same problem.)

Perhaps there is some system-wide gnome file that I could rest to default?

Note: I changed my
/home/[my username]/.gconf/apps/gconf-editor/%gconf.xml
to be basically empty, but this changed nothing.

So I am looking for some more global file that seems to have some bad settings.

THANKS!!!

This might be helpful:

[http://ubuntuforums.org/showpost.php?p=11968600&postcount=40](http://ubuntuforums.org/showpost.php?p=11968600&postcount=40)

---


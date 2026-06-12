---
title: "New User, Complicated Problems ^^"
date: 2009-05-25
forum: General Help
---

### Post by Mr. O on 2009-05-25
Edit: I just noticed that this should have probably been put into the absolute beginner's section. I don't see any option to delete it though so I can paste this over there. My bad... :/ anyways...back to the original message!

Hello! I'm a new user that has recently taken the knee-deep plunge into the world of Linux and I am here to share with you all of my problems. If you hate noobs and use us for target practice, this is all a lie and I'm really just testing how nice you guys are :P

I recently switched my old laptop from XP Home to Xubuntu Jaunty Jackalope, as that should be the code name for the latest one at the time of this post (9.04?). It's an interesting change of pace and has impressed me with the battery life. Problem I did solve: Getting my wireless card to work (Yay! :D ). Of course I just did a Applications > hardware driver thingy, activated madwifi, updated everything, and restarted.. but it's a start ^^

Before we begin, here's a detailed page of my old machine: [http://shopping.yahoo.com/p:Toshiba%20Satellite%201405-S151%20Laptop%20Computer:1990907564:page=details](http://shopping.yahoo.com/p:Toshiba%20Satellite%201405-S151%20Laptop%20Computer:1990907564:page=details)

_**Problems that need to be solved:**_
**Problem #1)** Change resolution from its standard max of 800x600 (or whatever) to 1024x768

The problem I'm having is that when I enter the sudo dkpg-reconfigure xserver-xorg (I wrote that from memory!) and manage to get to the monitor settings it surprisingly has none. Here is someone else's settings I googled:

```
[B]Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation Geforce 7300GT AGP 8x"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection[/B]
```Not only is my terminal message not so nicely aligned, but it doesn't give me any hardware information (no Trident. In his case it was NVIDIA) or resolutions. It's just the titles (ie. Identifier, Device, Monitor, etc.) and then commands at the bottom of the Terminal like ^O, ^G for help, etc. The problem is that there doesn't seem to be anywhere on the page to type them. After EndSection? Before Section? Inbetween? New Tab? >.<

So am I supposed to input my graphics card device manually (Trident Microsystems CyberBlade XPAil (rev 82) I believe) or is my system just missing a driver and not being detected? If that is the case, where could I find something so old and unsupported?

**Problem #2)** Audio is not working. As you can see from my specs, the system just has "Sound Card". I have my Vista here for multimedia purposes, but it would be cool if I could get that working for my new Xubuntu ^^

How can I go about that? I'm not too tech savvy and the manual might teach me the basics of Ububtu/Xubuntu, but I'm not really a programmer that can sudo hardware-repair find-drivers and magically get things working just from a bit of Googling. Ubuntu might have been the easier option, but what better way to learn something than installing over a working OS and having to repair everything? Everyone else probably did the same ;)

**Problem #3)** This is a LOT less priority, but it's still something I need to know. I just wanted to know how to install those directory-maze files that Linux programs seem to like. When you go to a site and install a Windows file - *Heavenly chorus* An install Wizard. When you look for Linux files to install, and perhaps compile, you tend to have a url that says something like [FTP://Blah.blah/](FTP://Blah.blah/) which has folders. Lots of folders. With various files in them. >_>

I take it that I'm supposed to make a directory, place them all there, and then assemble them myself? Are there instructions for that? And do I need them all or is it just allowing me to pick features I want and leave out what I don't?

Yes, I know about .deb, .rpm, and tar.gz. I can find docs on those easily enough. Perhaps I could even search for problem #3 here if I knew what term I would have to Google :lolflag:

Thanks if you got this far in my message. I tried not to bore you and to be as informative as possible. If you need more information just let me know and I'll be glad to help you help me :mrgreen:

---

### Post by CatKiller on 2009-05-25
Welcome to the community.

Problem 3:

Most open-source projects will use a version control system like SVN or git. You would use one of those to check out the code if you wanted to compile it yourself. Each project will have instructions on how to check out their code. But if you just want to install software, use package management. System -> Administration -> Synaptic.

Problem 1:

Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by Mr. O on 2009-05-25
Thanks! I managed to get the sound working. Turns out I had to manually unmute the volume (next to time click on the speakers, click on the option to Select Controls, and check Master volume. Headphones and PC Speaker might help too). Just in case anyone stumbles across this and has the same problem ^^

Your gksudo gedit command doesn't work on my Xubuntu for some reason. Adminstrative rights appear to be loading in a new window that I can't see (next to the Terminal bar on the bottom of the screen) but then it closes like a failed command line. It happens ^^

How can I get around it?

And for my Graphics settings, my computer is old.  Laptop = Monitor+Hardware, so what information I gave you is all I know.. xP

How can I find what my card can do? Besides testing its limits - Runescape under the old Java was the max extent and could only go so far for so long ^^

A site that says the name of the card I supposed have uses: HorizSync - 28-51 and VertRefresh 43-60, so I can try that if there's no documentation somewhere in the depths of the internet ;)

Edit: I've been trying this: [http://ubuntuforums.org/showthread.php?t=806835&page=2](http://ubuntuforums.org/showthread.php?t=806835&page=2) but I continue to get errors when it reboots. Do I just need to put in the HS and VR manually? It shouldn't be such a trial to put in a simple configuration file and for it to be read :)

---

### Post by CatKiller on 2009-05-25
> **Mr. O said:**
> Your gksudo gedit command doesn't work on my Xubuntu for some reason.

My mistake. I hadn't registered that you were running Xubuntu. Replace GEdit (Gnome's text editor) with mousepad (Xfce's text editor) and the command should work.

Glad you got your sound working.

Those values might work for you. They aren't too high, so hopefully they won't damage anything. You should just need to put those values in.

In an ideal world, it wouldn't be necessary; the monitor would just identify itself using EDID (which has been around for 15 years). As a crappy workaround, Windows users get a "monitor driver" that just puts the values into the Windows registry that the monitor should have given out itself. Us Linux users don't even get that much love from the hardware manufacturers.

---

### Post by Mr. O on 2009-05-26
Dude, you're a genius! I have fullscreen Xubuntu and those really were my settings. I just had to type them in :D

I'm so glad that's fixed that I don't even know what to do \\:D/ Maybe I'll just rock out for ya :guitar:
Cheers 8-)

---


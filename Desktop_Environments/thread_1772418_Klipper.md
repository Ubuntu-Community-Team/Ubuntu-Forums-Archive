---
title: "Klipper"
date: 2011-05-31
forum: Desktop Environments
---

### Post by 1stnoob on 2011-05-31
I took a look and couldn't find anything on this.  I finally made the break from Windoze and installed Ubuntu 11.04 with the Unity desktop.  I needed a clipboard program and installed Klipper through Ubuntu Software Center.  But I can't get it to come up or even see it in applications.  I'm sure this is simple to do, but I'm just not getting it.  Do I have to install KDE Plasma desktop to use Klipper?

---

### Post by jerrrys on 2011-05-31
open a terminal and enter

klipper

---

### Post by 1stnoob on 2011-05-31
> **jerrrys said:**
> open a terminal and enter

klipper

Thanks Jerry.  However, I tried that.  I hit Alt and F2 at the same time and get a window at the top that says Run a Command.  The two items below the command line are Synaptic and Run with a picture of gears.  I type in Klipper and hit enter.  Then the window disappears.  When I bring the window back up, I see a picture of gears with the name Klipper under them.  I click it and the window disappears and nothing happens.  I'm glad I haven't tried Linux when it was all command line. :)  I downloaded some Linux tutorials, I'm going to have to break down and read them, I guess.

---

### Post by jerrrys on 2011-05-31
alt F2 is your app launcher, but hang in there for a few while i load [B]Klipper and see what the deal is.  be back
[/B]

---

### Post by jerrrys on 2011-05-31
ok, klipper will pull up with your app launcher,  its a little clipboard in your notification area.  and this is assuming unity has a notification area.  i do not run unity so im guessing on that.  take a look around and let me know

---

### Post by 1stnoob on 2011-05-31
> **jerrrys said:**
> ok, klipper will pull up with your app launcher,  its a little clipboard in your notification area.  and this is assuming unity has a notification area.  i do not run unity so im guessing on that.  take a look around and let me know

I found this page on notification area:
[http://www.addictivetips.com/ubuntu-linux-tips/enable-system-tray-notification-for-all-applications-in-ubuntu-11-04/](http://www.addictivetips.com/ubuntu-linux-tips/enable-system-tray-notification-for-all-applications-in-ubuntu-11-04/)
So I guess it doesn't show up natively.  I did as the author said and inserted this in terminal:[FONT=monospace]
[/FONT]gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

After I did that I got a little gear box in history that has the number:
00
16
under it.  I was looking for the tray, I think it's in the upper right, and noticed what looks like a clipboard showed up in it.  When I left or right click or double click or hover over it nothing happens, except a left or right click will produce a gray bar under it, and that's all.  Now what?
As an aside, I don't know why no Linux flavor has emulated the way Windoze functions (except for the slowness and crashing), it's used by 99% of the people in the US, they would kick microsofts @ss if they did.  Just thinking out loud here...

---

### Post by jerrrys on 2011-05-31
well your making some progress.  here's what your looking for

[ATTACH]193801[/ATTACH]

good luck

---

### Post by 1stnoob on 2011-05-31
> **jerrrys said:**
> well your making some progress.  here's what your looking for

[ATTACH]193801[/ATTACH]

good luck


Thanks for your help.  I will try a reboot, maybe that will fix it.

---

### Post by 1stnoob on 2011-05-31
Ok, I rebooted, didn't see Klipper show up in the tray.  I did alt-f2 and typed terminal, saw it there, clicked on it and there it was in the tray.  That's all it does, though, no matter what I do it just won't open.  Not even a gray bar at the bottom now, just a shadow when I click on it. Does anyone else have any ideas?  Do I have to install KDE Plasma for Klipper to work?  I'm running it on a Inspiron 1720, but that shouldn't matter.

---

### Post by ugm6hr on 2011-06-01
Unity may be the issue. I'm using standard Gnome.
But maybe glipper might be a better option [http://askubuntu.com/questions/41785/how-do-i-enable-a-clipboard-manager](http://askubuntu.com/questions/41785/how-do-i-enable-a-clipboard-manager)

---

### Post by 1stnoob on 2011-06-01
> **ugm6hr said:**
> Unity may be the issue. I'm using standard Gnome.
But maybe glipper might be a better option [http://askubuntu.com/questions/41785/how-do-i-enable-a-clipboard-manager](http://askubuntu.com/questions/41785/how-do-i-enable-a-clipboard-manager)

 I want to use Klipper, as I use the clipboard extensively, and Klipper has all the features I need.  Surely someone else is using Unity and Klipper?

---

### Post by jerrrys on 2011-06-01
good morning 1stnoob...

glipper and klipper should be the same program.  just that one is design for gnome and one for kde.  i would follow that link ugm6hr gave you and give it a try.

---

### Post by 1stnoob on 2011-06-05
> **jerrrys said:**
> good morning 1stnoob...

glipper and klipper should be the same program.  just that one is design for gnome and one for kde.  i would follow that link ugm6hr gave you and give it a try.

 They're not the same program.  Has anyone successfully installed and used Klipper while using the Unity desktop?  I'm about to install KDE Plasma, I don't think Unity and Klipper mix.  BTW, how do you uninstall Unity without messing anything else up?  Never mind, I can probably do a search for that...

---

### Post by 1stnoob on 2011-06-18
In case anybody is still interested, here's what I found out, no thanks to anyone on this forum. :)  Klipper can only be used on the Kubuntu desktop, even if you install Ubuntu 32 bit (I started with 64 bit, tried 32 bit to see if that helped, and eventually reinstalled 64 bit again, as it seemed slightly faster).  You'd figure they would be usable no matter what desktop is used, but that was not my experience (well, rekong browser will open in Ubuntu Classic).  I don't know how to use the command line, perhaps there is a way to do it that way, but it's beyond my current experience.  I also discovered that the Network Manager installed as a default with Ubuntu 11.04 is the only one I could get to connect to the internets. I installed WiCD, but it could never get the IP address.  The Unity desktop is ok, but when I open Firefox, I could not access the Import and Backup buttons; they simply were not there.  When I booted up in Ubuntu Classic, the buttons magically showed up.  When I switched to Kubuntu Plasma desktop, I could not get on the internets at all, and the only application I saw available was Wicd.  No Network Manager in Plasma.  I'll eventually play around with it some more, but I know my way around the Ubuntu Classic desktop fairly well now, and Plasma doesn't seem to offer any extraordinary benefits over Classic.  The Ubuntu Software Center is great, it's easy for an idiot like me to download software without having to know the command line.  Though far from perfect, I will stick with Ubuntu, even though a friend would give me Windoze 7 for free.  It's simply faster than Windoze, and I expect it to be able to do most of the things I was able to do before, like browse the internets, open docs, pdf's, videos, and the like.  Hope this helps someone, and thank you all for your help.

---

### Post by Sarteck on 2012-03-09
Just a note to Xubuntu users who stumble on this thread like I did, **xfce4-clipman-plugin** is the XFCE version for us.

```
sudo apt-get install xfce4-clipman-plugin
```

---


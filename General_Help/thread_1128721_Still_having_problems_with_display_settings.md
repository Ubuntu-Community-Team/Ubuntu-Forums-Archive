---
title: "Still having problems with display settings"
date: 2009-04-17
forum: General Help
---

### Post by hurstdaj on 2009-04-17
I have been back and forth with this for a few days, trying different things.  I finally was able to set up the driver for the video card, but I am still only getting a screen resolution of 800X600.  When I was using Windows, I never had a problem with 1024X768 resolution.  Now that I decided to make the switch to Ubuntu (because I cant stand Microsoft), It seems nearly impossible.

I tried adding the following to xorg.conf
 ```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection
```

That made the monitor flash "Out of range", so I had to manually restore xorg.conf.

With the new driver installed, I tried to edit display settings by clicking on Screen resolution, and I got an error that the video card could only be modified by the publishers software, but there was no option on that screen that came up with that software.

I did go into my monitor menu.  It's an Avidav lcd monitor.  It says on the menu 800X600, but this wasn't a problem with Windows.  What do I need to do to resolve this?

---

### Post by Daisuke_Aramaki on 2009-04-17
what is your graphic card? post the output of the command lspci by executing the command in a terminal

---

### Post by hurstdaj on 2009-04-18
Here is the output of lspci

```
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
00:0b.0 IDE interface: nVidia Corporation nForce2 Serial ATA Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
02:08.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (Worldwide) (rev 08)

```

Any help anyone can give would greatly be appreciated.

I realize that it's an older system, but cant really afford a new one right now.  One of the reasons I changed was that I heard that Ubuntu doesn't slow down after time like Windows does.  I'm really hoping to get this working!

---

### Post by DJonsson2008 on 2009-04-18
HorizSync       30-95
        VertRefresh     50-160

The upper ranges in the above lines seem a bit high.

It seems you should start with lower refresh rates
and work up from there.

As well it would help if you could find a table of 
what refresh rates are available for your brand
of Monitor, and inch up towards that.

---

### Post by CatKiller on 2009-04-18
> **hurstdaj said:**
> I tried adding the following to xorg.conf

Those refresh ranges are **far** too high for your monitor. That's a 1600x1200 range, which your monitor can't do.

As I said when I told you to put the ranges for your monitor in xorg.conf,

> **CatKiller said:**
> 
Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.


Your monitor. Not mine.

What's the model number of your monitor?

---

### Post by DJonsson2008 on 2009-04-18
I think it is important to decouple the idea of an entry level 1024 wide resolution and the use of the nvidia driver by first getting something at 1024 or wider that works with vesa. 

The nvidia jockey, displayconfig and other GUI's seem to
be self defeating in this sort of effort.

Start with a 600 wide screen, and then dropping to careful incremental
edits of xorg.conf with nano or gedit has been the most robust 
base line method for many. 

Unfortunately the only way tweak vesa to use the larger resolutions
and higher refresh rates that I've found is in manually editing the xorg.conf. 

Care must be given to have your monitors specs and 
horz / vert ranges on hand 

Once that's done and you have backed up the functioning xorg.conf
then attempt engaging your nvidia driver, by logging in and out
again or rebooting as needed.

In my /etc/X11 directory then based on the configs tested
has built a set of files I've created and named using SAVEAS
or cp to rename each tested xorg.conf file.

xorg.basic.conf.tested.bak
xorg.vesa1024.conf.tested.bak
xorg.nvidia1024_76refresh.conf.tested.bak
xorg.nvidia1024_80refresh.conf.tested.bak

This enables one to work as far into where you are going in
conservative steps, all which are roll back-able from
the command line. The file names are self explicit rather
that the automated backups you will see being made with
non-friendly numerical names in /etc/xll by the GUI's, 

Bookmarking the /etc/X11 directory in gksu nautilus 
gksu konqueror or another file browser can help the
process along. Gedit also has a session saver plugin
enabling you to reopen a set of files for comparison
and editing.

For now my
"xorg.vesa1024_76refresh.conf.tested.bak" 
is as solid as a rock, and enables me to get my work done. 

As time allows I'm exploring getting nvidia 8400GS to
work with Hardy, but experiments so far show that only 
driver 169 will work in my scenario, and the attempts to
load later drivers has disabled the capacity to roll back
to 169 at this point in time. 

I'm going to want better control of my drivers later on for
google earth, but for now I can do what I need to do and
wait for perhaps a kernal update, 9.4 stable or a fresh 
install, to roll back to 169.

---

### Post by hurstdaj on 2009-04-19
Well, I don't know where to go from here.  I downloaded and installed Mandriva, and my display settings are 1024X768.  For some reason, I cant get those settings in Ubuntu.  Is there anything I can do to fix this.  I really don't like the layout and speed of Mandriva, and would rather be with Ubuntu.

---

### Post by CatKiller on 2009-04-19
> **hurstdaj said:**
> Well, I don't know where to go from here.

You could put your monitor's refresh rate values in your xorg.conf.

---

### Post by hurstdaj on 2009-04-19
I tried putting my monitors refresh rates in, but I'm not even sure exactly where to find this information.  I'm not sure what the model number is and I don't have a manual for it.  I have now tried 2 other Linux distributions and don't like either, but my screen resolution works fine with both of those.  Mandriva and Gentoo...  This would be the best one out there if I could just get this to work correctly.

---

### Post by CatKiller on 2009-04-19
> **hurstdaj said:**
>  I'm not sure what the model number is and I don't have a manual for it.

There's nothing written on the back that might help you to track down what it is?

Otherwise, you could try DJonsson2008's suggestion of starting with a conservative set of ranges, and then gradually increment the upper limits of the ranges until you get the resolutions that you want. 31-40 & 50-90 might be a reasonable place to start.

You could also inspect the xorg.conf that comes with Mandriva or Gentoo, and see if it has anything in there that's different from your Ubuntu one that might make the difference.

---

### Post by hurstdaj on 2009-04-21
Well, I was able to get it working.  I hope it's not going to cause any problems, but I installed the driver from the nvidia website.  The settings added to xorg.conf automatically, put the monitor out of range.  So, I restored the previous settings to get the computer to boot.  I then updated xorg.conf with the same settings found in the xorg file in Mandriva, and I now have 1024X768.

It does seem to have slowed down a little bit, so I'll keep playing with it.  This has been a big issue, and one that has been very difficult to work through.  The developers should take note of this and take it into consideration for future releases.

---


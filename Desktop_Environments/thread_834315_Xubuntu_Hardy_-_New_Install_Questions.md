---
title: "Xubuntu Hardy - New Install Questions"
date: 2008-06-19
forum: Desktop Environments
---

### Post by hhh on 2008-06-19
Hi, I've been running Ubuntu Feisty since soon after it's release but wanted to see what XFCE was all about. I tried a whole slew of XFCE-based distros but liked the compromise Xubuntu offered of switching to XFCE while keeping a lot of the familiarity of Ubuntu/Gnome. But the learning curve has been steeper than I expected. I'm going to post a few major stumbling blocks I've had together here. I've searched the forums here on all my problems, so I'm aware of previously offered solutions, but they haven't worked either because of differences in Hardy, differences in XFCE or my own incompetence. The questions are blunt, meant to illicit practical solutions and not to slam or flame the distro. Moderators, please split the thread as you see fit. On to the questions...

1) [http://www.xubuntu.org/help](http://www.xubuntu.org/help) says "You can find the official Xubuntu forums at ubuntuforums.org." but there is no "Xubuntu" forum category. Why is that? It's confusing. Gnome is not XFCE is not KDE and shouldn't really be lumped together IMO.

2) My desktop is hooked to a small network via a cheap Belkin wireless G antenna (F5D7050), a not uncommon setup. Xubuntu recognized my device and connected no sweat, something most of the other distros I tried were unable to do. The connection speed lists at only 1 Mb/s using the provided Xubuntu-provided rt73usb driver though. "sudo iwconfig wlan0 rate 54M" results in Network Manager showing the new rate, but download speeds remain the same. I tried to get Ralink's rt73 driver to work, no go on Hardy. I have a fine connection using ndiswrapper. What are the disadvantages of using ndiswrapper rather than a native Linux driver, and does anyone have steps to install rt73 on Hardy?

3) When I insert an audio CD into the drive with a fresh Xubuntu install, Totem opens and immediately gives a "Location not found" error. The Play Disc "Audio Disc" submenu is greyed out. Opening Thunar doesn't show the disc nor does an icon appear on the desktop. Data CDs are recognized just fine, icons appear. Zuh? So I installed BMPx and can play a CD from there. I went to Settings>Settings Manager>Removable Drives and Media>Multimedia and changed the cd command line to beep-media-player-2 cdda:/ . This makes the player open when I insert a CD, but it won't autoplay. I tried Exaile, Xfmedia and Amarok and the best I could get was the player to open and autoplay the first song on the disc. How come no icon appears on the desktop or in the file manager when a cd is inserted? How do I configure BMPx to be my default player for audio cds?

4) I like to view web pages as the site designer intended, so installed msttcorefonts. The install seemed to go fine, but gave a warning about msttcorefonts using defoma, and needing to configure that through x-ccidfont-conf. I followed the steps in the Read Me and added the necessary font paths to xorg.conf. That didn't work and my display resolution went fubar, stuck at 800x600 and below. No amount of messing with xorg.conf has gotten me back, I've reinstalled Xubuntu. My out-of-the-box xorg.conf file looks completely benign, everything is listed in generic terms like "Default Monitor" and "Default Screen". What are the steps to get MS fonts to display in Xubuntu Hardy?

---

### Post by hhh on 2008-06-20
bump - looking for support

---

### Post by logreeval on 2008-06-21
i have the same problem....

in the xorg.conf there aren't even any numbers to change...

---

### Post by hhh on 2008-06-23
Ahem, bump.

---

### Post by hhh on 2008-06-24
Bump. Again.

---

### Post by bluepowder7 on 2008-06-24
2 - i hate network manager.  first thing i do is replace it with wicd, even on a desktop that doesn't have a wireless interface.

4 - i installed msttcorefonts but did NOT do the defoma stuff or anything after the "sudo aptitude install msttcorefonts", and when i open up an openoffice document, i seem to have the fonts listed and stuff shows / displays properly.  maybe you were better off not doing the defoma stuff?  is there a way to undo it?

---

### Post by hhh on 2008-06-24
Thanks for the reply. I'll try your suggestions and post back tomorrow.

---

### Post by hhh on 2008-07-01
Just posting back, I"ve given up on Xubuntu for now do to the lack of online documentation and out-of-the-box wireless configuration.

Not too thrilled with this entire forum either, guys. Check out forums.Mozillazine.org to see how it's done.

---

### Post by Carl H on 2008-07-02
The stuff about using the font manager and adding things to paths is just advice; you don't have to do it. 

I didn't, and all the fonts work just fine.

---

### Post by hhh on 2008-07-02
Thanks Carl, that's good to have verified. Knowing that, I'm going to reinstall Xubuntu today.

Any idea what's going on with not having an icon appear on my desktop when I insert an audio cd insto the drive?

---

### Post by bluepowder7 on 2008-07-02
mine doesn't place an icon either.  no big deal.  i just dicked around with stuff, and now it at least auto-plays the audio disc when i jam it in using vlc.

on empty desktop, right-click and go "settings" - "settings manager"
under "removable drives and media", the 2nd tab is "multimedia"
check the "audio cd" box, and i had to write this in the command box:

```
/usr/bin/vlc cdda:///dev/scd0
```

i figured out the cdda: part by manuall opening up vlc, going "file"-"open disc", going to the 2nd tab, clicking the "audio cd" box, and looking what it spits out on the bottom for the "customize"

give that a whirl...

might have to do the same for dvd's

---

### Post by hhh on 2008-07-02
Both of those worked.

Thanks to both of you, gents. I have a working Xubuntu install. Much obliged.

---

### Post by bluepowder7 on 2008-07-02
> **hhh said:**
> Both of those worked.

Thanks to both of you, gents. I have a working Xubuntu install. Much obliged.

yer welcome!  personally, i'm loving Xfce much more than GNOME.  it's a bit different, with more setting up to do and less icons all over the place, but when it comes down to FUNCTION i like it much more.  it does what needs to be done, quietly and without making itself obvious.

i'll say this, though - starting off with GNOME makes it easier to learn how to do stuff since there's less that HAS to be done.  good way to get your feet wet, but not as adventurous a swim.

---

### Post by jaygo on 2008-07-12
1) the forums now have an option to prefix your post with distro-specific headings [xubuntu], etc. It's a step in the right direction.

2) If ndiswrapper works, just stick with it for now. The only downsides I know of are that it won't work with many wifi testing tools. I was trying to test the wireless signal with three different scanning utilities and none of them could work with ndiswrapper.

3) Icons on the desktop ... xubuntu doesn't do it, afaik. As for your default player ... I don't remember.

4) I don't recall tweaking the fonts for my xub install but from what I've read, you don't have to tweak xorg.conf just to get mst fonts. I certainly didn't have to in KDE/mepis/kubuntu.

GLHF & WB

---


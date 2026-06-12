---
title: "Fraggin's complete experiences with Kubuntu"
date: 2005-04-11
forum: Desktop Environments
---

### Post by F for Fragging on 2005-04-11
First of all, I'd like to thank the (K)Ubuntu developers for their work. It's a nice distro, but in the three days that I'm using it I've encountered tons of problems.
I think that it would be a good idea to start a Kubuntu counterpart of ubuntuguide.org. For example to explain how we need to install the windows codecs for kaffeine, flash for konqueror and such things. Is such a thing already in the works?
I've written a long story about my experiences with Kubuntu. I don't know who are to &#8220;blame&#8221; for the many bugs I describe here, the Kubuntu team or KDE. I think it's both, so I'll post this here and in the KDE bugzilla/mailinglists as well.  I hope the Kubuntu developers check this forum, or do I have to post in some mailinglist then? 



Installation 

The installation could be easier with a GUI. Most of the other distro's have a Gui installer by now, but Kubuntu still uses a text based one. Not that I had much problems, but I this scares of newbies. 
I also noticed a bug in the installer, when I wanted to select my keyboard layout, I was looking for &#8220;Dutch&#8221; in the alphabettically sorted list. I was looking near the &#8220;D&#8221;, but I didn't found it there. So I scrolled down to the &#8220;N&#8221; for &#8220;Netherlands&#8221;, and there I found &#8220;Dutch&#8221; between &#8220;Norwegian and Polish&#8221;.
After that I had to do the partitioning. Maybe it would be a good idea to let the installer do this automatically? Please at least let it recognize the partitions of already installed Linux distro's. I had Fedora Core 3 installed, but I had to manually edit the partitioning scheme so it would use those partitions. Maybe it would also be possible to implement the resizing of NTFS partitions, like the SuSE Linux installer?
After the base system was installed, I had to type my user name. I typed some letters, pressed Backspace because I made an error, I kept Shift pressed because I wanted to type a capital letter, and then the installer froze. It didn't respond to anything, except Ctrl+Alt+Delete for a reboot. I had to install a second time, but now everything went fine, fortunately.

amaroK

amaroK freezes when I try to play a stream, a winamp .pls file. I had this problem when I tried to play the stream of [http://addictivebeat.com/](http://addictivebeat.com/) I haven't tried any other streams though.

Enemy Territory

I installed Enemy Territory. It works fine, but when I exit it, my desktop &#8220;doesn't fit in the screen&#8221; anymore. I run my desktop on 1280 x 960 and Enemy Territory runs in 1024 x 786. I thinks that's the cause, the different resolutions. But I've been doing the same on Fedora Core 3 and then I didn't have this problem. So in other words, before I start & exit ET, my desktop is fine. I can see it completely. When I exit ET, I can't see it completely anymore, and I have to move the mouse pointer to the bottom of the screen so that I can open the menu and end my session. When I log in again my desktop looks normal again. I fixed this with setting a custom resolution of 1280 x 960 in a .cfg file (can't choose that resolution in game), then this problem doesn't occur.
Another problem is the &#8220;jumping icon&#8221;. When I start programs in Kde, their icons jump near the mouse cursor. The problem is that that this jumping icon doesn't stop when ET is loaded, I can still see it in the menu. Fortunately it disappears when I'm playing, but it's quite annoying.
Another thing which is driving me mad is the permissions. I noticed I didn't have the permission to write to /.etwolf in my users home dir because I couldn't edit my config file! If that directory is installed in my home dir I'd expect that root wouldn't be the owner. I installed ET with sudo sh et-linux-2.60.x86.run, could be that the cause of the strange permissions? On Fedora I used su, gave my password and then used the same command, and with Fedora I didn't have any problems with permissions.

Fonts

After installing I installed a font, I could use it in OpenOffice, but I could not use it in the KDE Control Center. After I rebooted they did appear in the Kde Control Center and they were usable. Why is it not mentioned that you have to reboot first then?

Fonts anti aliasing

With anti aliasing on my fonts don't look very good. Check this [http://www.xs4all.nl/~vanlonen/antialiasing.png](http://www.xs4all.nl/~vanlonen/antialiasing.png) screenie. Look carefully and you'll see that in Konqueror, the &#8220;W&#8221; in &#8220;Window&#8221; is very pixelated. It looks like this everywhere in all KDE apps. But in the OpenOffice window, the fonts are perfect, and the &#8220;W&#8221; is not pixelated. So anti aliasing doesn't work very well in KDE, but in non-KDE apps like OpenOffice it does work? How can this be fixed so anti aliasing looks better in KDE? I googled for an answer on this, I tried disabling &#8220;Hinting style&#8221;, but it doesn't make any difference.

Mouse cursors

I didn't like the default cursor theme, so I decided to install the Grounation cursor theme which can be found on kde-look.org. I tried the cursor installer which can be found in the KDE Control Center under Peripherals -> Mouse -> Cursor Theme. I selected the tar.bz file I downloaded to install it, but it told me that 14484-Grounation-0.3.tar.bz2 wasn't a valid cursor theme. I googled for a solution and extracted the cursor theme to /usr/X11R6/lib/X11/icons/. Now it appeared in the KDE Control Center and I could use it. But why is the installer telling me that the cursor theme was invalid? Did I have to extract the tar.bz file first?

Setting my Logitech Dual Optical to 800 cpi

In Linux my Logitech Dual Optical Mouse is always defaulted to 400 cpi, but it is capable of 800 cpi. I've always used this program - [http://freshmeat.net/projects/logitech_applet/](http://freshmeat.net/projects/logitech_applet/) - to switch it to 800 cpi. But I also noticed thisin the KDE Control Center - [http://www.xs4all.nl/~vanlonen/kde_800cpi.png](http://www.xs4all.nl/~vanlonen/kde_800cpi.png) &#8211; so it seems that KDE can switch it to 800 cpi for me now, which is a useful feature. Unfortunately it won't work yet, as you can see.

Instability

Kubuntu is so very unstable for me. I removed an MSN contact group in Kopete, and it immediately crashed. When I close Kaffeine when it's playing a video file, it crashes. Konqueror crashes when I go to trailers.apple.com and watch a trailer and press the back button. I've never had this with any other Linux distro.

Kaffeine

I followed the instructions mentioned in some forum posts, and extracted the codec pack essential-20050216.tar.bz2 to /usr/lib/win32 so that I could use Kaffeine to watch windows media, real and quicktime streams. Now I can view the quicktime streams on trailers.apple.com, but when I try to view windows media streams, for example on this page &#8211; [http://www.nos.nl/nosjournaal/archief/index.html](http://www.nos.nl/nosjournaal/archief/index.html) (click on &#8220;(BB)&#8221; there) &#8211; Kaffeine says that there is &#8220;no plugin to handle this resource&#8221; (that happens with the windows media streams on that website, but there also are real media streams which give the same result), and Konqueror crashes.



I've mentioned a lot of problems here, some are driving me so mad that there have been moments that I considered switching back to Ubuntu/GNOME, but I do appreciate Kubuntu. I just hope these bugs get fixed soon..
BTW, is there any KDE bittorrent client available which can compare to Azureus? Or aren't there any serious alternatives available and am I forced to use Azureus? I've searched a bit but I haven't found any mature projects.
One last thing, I noticed the useful Google search bar in Konqueror. Is it also possible to add search plugins for wikipedia, like it is possible in Firefox?

---

### Post by dermotti on 2005-04-11
Well, Kubuntu is very new, but i will agree, l8ly it has been very unstable. :-( Im hoping these issues get resolved soon.

Back to Mepis....Kubntu will be sitting on my test box so i can check periodically for a fix.

---

### Post by weeguy on 2005-04-11
I'm having some other problems with Kaffeine. After viewing a clip and closing the program,  Kaffeine seems to reside in memory and refuse to go away. After some time, this instance of Kaffeine would then start to consume massive amounts of resources. :( Had to manually KILL each of these instances before the resources were reclaimed.

---

### Post by dermotti on 2005-04-11
Same problem weeguy :-( I need a stable os for pr0n viewing

---

### Post by bobmitch on 2005-04-11
[QUOTE=dermotti]Same problem weeguy :-( I need a stable os for pr0n viewing[/QUOTE]

LOL!  Honesty beyond the call of duty. :D

NB.  A chipped xbox with Xbox Media Center installed is a godsend in times of PC woe. ;)

---

### Post by dermotti on 2005-04-11
yea ive been thinin gbout modding my xbox, been to lazy tho hehe. Fortunatly i have a second box that had HDTV out setup.

---

### Post by gaboo on 2005-04-20
[QUOTE=F for Fragging]
Fonts anti aliasing

With anti aliasing on my fonts don't look very good. Check this [http://www.xs4all.nl/~vanlonen/antialiasing.png](http://www.xs4all.nl/~vanlonen/antialiasing.png) screenie. Look carefully and you'll see that in Konqueror, the “W” in “Window” is very pixelated. It looks like this everywhere in all KDE apps. But in the OpenOffice window, the fonts are perfect, and the “W” is not pixelated. So anti aliasing doesn't work very well in KDE, but in non-KDE apps like OpenOffice it does work? How can this be fixed so anti aliasing looks better in KDE? I googled for an answer on this, I tried disabling “Hinting style”, but it doesn't make any difference.
[/QUOTE]

Did you manage to fix the anti aliasing pb ?

---

### Post by F for Fragging on 2005-04-20
No, I still didn't solve the anti aliasing problem. I posted an entry in bugzilla - [https://bugzilla.ubuntu.com/show_bug.cgi?id=8959](https://bugzilla.ubuntu.com/show_bug.cgi?id=8959) - a week or so ago, but I still haven't received any comments on it.

---

### Post by Ironi on 2005-04-20
The fonts are ugly in KDE applications because they're *not* being antialiased. From your screenshot:

**Konqueror** (no antialiasing)
[img]http://img195.echo.cx/img195/1962/konqfont9yj.png[/img]

**OpenOffice** (antialiasing)
[img]http://img191.echo.cx/img191/4138/oofont7vo.png[/img]

To enable antialiasing, run **kcmshell fonts** and check *Use anti-aliasing for fonts*. You may also want to click *Configure...* and customize the other options. I recommend unchecking *Exclude range* and setting *Hinting style* to "Full." If you're using an LCD monitor, check *Enable sub-pixel hinting*; otherwise (CRT) disable it or use "Grayscale."

---

### Post by Zakalwe on 2005-04-20
Look here for a solution to all your Kaffeine problems

[http://www.ubuntuforums.org/showthread.php?t=27670](http://www.ubuntuforums.org/showthread.php?t=27670)

---

### Post by F for Fragging on 2005-04-21
Ironi, I already noticed that they are not being anti aliased. That is exactly what I was trying to say, they are not being anti aliased while I do have anti aliasing enabled.

I opened the KDE Control Center (the command you gave me does the same, right?) and changed the anti aliasing settings as you suggested. I'm on a CRT so I tried both disabling sub-pixel hinting and setting it to greyscale, but I saw no difference.
But the anti aliasing still isn't working. I can tell because I still see a difference between GTK apps like OpenOffice and Azureus, where the fonts are anti aliased, and QT apps which still don't have anti aliasing.

Thanks for your help though. I guess I have to wait until some developers comment on my bugzilla entry, if they pay attention at all to what I have posted in the Bugzilla ten days ago...



Zakalwe, thank you. I read that topic earlier, but it didn't mention anything concerning the w32codecs. But if you say it will solve my problems I'll try.
EDIT: Nope, unfortunately this doesn't work either. I still get the error message "no plugin found to handle this resource" when I try to open Real/Windows Media streams,

---

### Post by F for Fragging on 2005-04-22
Hmm... strangely the anti aliasing is working now that I've restarted my computer. Thanks for the help.

---

### Post by linuxfanatic1024 on 2006-02-11
Well, all the "antialiasing" option in KDE does is change from the old X11 font selection system to the new Fontconfig system. It does not turn on antialiasing. To actually control antialiasing, run this in Konsole:
```
sudo dpkg-reconfigure fontconfig
``` In my opinion, running this and selecting the autohinter makes most fonts look a lot nicer.

---


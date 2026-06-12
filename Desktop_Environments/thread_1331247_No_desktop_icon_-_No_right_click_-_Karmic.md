---
title: "No desktop icon - No right click - Karmic"
date: 2009-11-19
forum: Desktop Environments
---

### Post by manolomanolo on 2009-11-19
Hi to all.

This morning my desktop shows no icon, I see no menu windows when right clicking on it and also I cannot see any selection area when trying to left-click and drag the mouse pointer.

Clicking on **Places -> Desktop** I can see all of my icons. I can select objects and I can see the right-click menu window.
I can run applications from **Applications** menu and both the upper and lower panes work fine.

I tried to reboot, to change desktop background, to unable and enable back desktop effects, to change desktop resulution, to change a couple of themes but I've been not lucky.
No *desktop* neither *video* nor *gnome* related updates or changes along those last days, AFASIR. Yesterday everything worked fine. I've just run the "update manager", updated my system and restarted: nothing changes.

The only "not ordinary" things that I can remark:[LIST]
[*]Yesterday I've been trying the SUSPEND and Hybernate functions from the upper panel, almost never done since upgraded from Jaunty to karmic
[*]Today Karmic advices to free some space on /media/Common partition (it's NTFS) since it's almost 2GB of free space left on that partition
[*]This morning I started the system without A/C power, just with the battery (fully charged)
[/LIST]

Any suggestion, please?
Thank you.

Ubuntu karmic Koala
Kernel 2.6.31-14-generic
Gnome 2.28.1 - Build date 11/03/2009

```
lspci | grep Graphic
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

dmesg.pdf is attached

---

### Post by manolomanolo on 2009-11-20
UPDATE. Desktop icons still does not appear. Sometimes it can happen that they do appear after some time (maybe one hour or half) of using my computer.

I supposed it was due to the execution of some specific application, but today I've been executing Firefox, OpenOffice and Nautilus with no luck.

Any suggestion, please?
Thanks.

PD: Am I the only one having this problem?

---

### Post by autonomy on 2009-11-20
That sounds like Nautilus isn't drawing your desktop...at least not for an hour or so, so my idea is to run (Alt + F2) gconf-editor, expand apps and nautilus, click on preferences and make sure show desktop is checked.

---

### Post by taavipalo on 2009-11-20
I have a similar problem, but my desktop and icons always appear after starting nautilus.
Haven't found a solution yet.
And in gconf show desktop is checked.

Might it be possible that there's a conflict between nautilus and compiz?
I have tried reinstalling both - no result.

---

### Post by manolomanolo on 2009-11-20
Reinstalled both nautilus & compiz (and related packages).
The "show desktop" was already checked: I unchecked and checked it back.

Still no solution.
Thanks for your time :)

---

### Post by autonomy on 2009-11-20
> **taavipalo said:**
> my desktop and icons always appear after starting nautilus.
That makes sense b/c that's just the way that Nautilus works especially if you start it as root. It will draw the desktop and its icons whether you like it or not, but it doesn't do that when I start it as myself.
> **taavipalo said:**
> nautilus and compiz?
I have tried reinstalling both - no result.
I wouldn't have thought this would have worked, but I'm sorry *show desktop* didn't work.
Good luck you two.

---

### Post by manolomanolo on 2009-11-20
"Starting nautilus" ???

Do you mean "opening whichever directory using nautilus"???

---

### Post by autonomy on 2009-11-20
Yes, when I started Nautilus as root (opening whichever directory I opened, doing whatever I was doing last weekend) it had the inadvertent effect of drawing my desktop.

---

### Post by manolomanolo on 2009-11-20
Pressed ALT + F2 and executed "gksudo nautilus".
The result is me still connected as normal user but karmic showing the root desktop icons and a nautilus window allowing me to browse folders.
After closing the nautilus window I can still see root desktop icons!

I suppose it's a security issue :shock::?

---

### Post by autonomy on 2009-11-20
Switching to the super user is always the worst way to do everyday things that your user should be able to do, so maybe you lost permission to use the desktop. That's a long shot, but there are two ways that you can check: first, in Nautilus, go to your home folder, right-click the Desktop icon, click Properties, click on the Properties tab and make sure the top drop-down list says Create and Delete Files. The other way is open a Terminal emulator, type ls -l, press Enter and make sure drwx are the first four letters on the line for Desktop.

---

### Post by manolomanolo on 2009-11-21
Almost there, baby!!! :)

Running nautilus from ALT+F2 and executing ***nautilus*** as normal user does the job! My desktop icons appear magically!

On the other hand, running 
[INDENT]***Applications*** **->** ***Other*** **->** ***Open Folder***[/INDENT]

executes ***nautilus --no-desktop %U*** which just opens a nautilus window without managing desktop icons. See ***man nautilus***.

I've been running ***gksudo gnome-search-tool*** from terminal and searched for all files containing the ***--no-desktop*** word into their text. The result is:
[LIST]
[*]/var/lib/gconf/defaults/%gconf-tree.xml
[*]/var/log/auth.log
[*]/home/.wine/dosdevices/c:/windows/profiles/manolo/Desktop/new file
[*]/home/.wine/dosdevices/c:/windows/profiles/manolo/My Documents/Desktop/new file
[/LIST]

---

### Post by manolomanolo on 2009-11-21
Notice those 2 last results.
I uninstalled wine almost a month ago, AFASIR, and also removed the ~/.wine folder almost a week ago.

Actually, I created that "new file" just today just copying the "--no-desktop" word in it.

It's strange, isn't it?

---

### Post by manolomanolo on 2009-11-23
Bump

---

### Post by william_nbg on 2009-11-23
I have the exact same problem.

I started my own thread before finding this one.

I have also tried many things, but haven't found the solution.

But logging in as root the desktop works, and when I log out as root, I get an error message??

---

### Post by manolomanolo on 2009-11-25
Still no suggestions?

william_nbg, could you please link your thread here?

Thank you.

---

### Post by william_nbg on 2009-11-25
My thread is here:
[URL="http://ubuntuforums.org/showthread.php?t=1335084"]
http://ubuntuforums.org/showthread.php?t=1335084[/URL]

OK, I found a work around, but it's not a solution. I was thinking about a fresh install so I can upgrade to ext.4 and I'd also like to change my partitions a bit.

Work around, added a new startup application:

name: Nautilus fix

command: nautilus --no-default-window


Like I said it works, but it's only a work around. I'd like to know where the real culprit lies hidden.

---

### Post by manolomanolo on 2009-11-26
The workaround allows desktop icon to appear and right-clik on mouse to show the related window.

Waiting for the "real" solution.

Thank you.

---

### Post by william_nbg on 2009-11-26
Well, Obviously, I did something which wrote over/new a nautilus config somewhere. 

Though, like I said, as soon as I get a few hours of time/motivation I'm going to do a fresh install.

:popcorn:

---

### Post by manolomanolo on 2009-11-26
Hope you could tell here how a fresh install is as for the troubles you've been showing in this thread.

See you after your fresh install ;)

---

### Post by xhunter00 on 2009-11-28
Hi, I was having that same issue but it starting after I pluged an external monitor into my Dell Inspiron 640m Laptop (I'm runing Karmic upgraded from Jaunty).

After that all my desktop icons disapeared, after severals attempts of Alt+F2 gconf-editor >Nautilus>Preferences>Desktop still no icons.

Finally I press Alt+F2 and run "nautilus", no sudo no other command, the desktop icons where drawn and after reeboting they were again on desktop, issue resolved, I don't think this would be the final solution for your same issue, but if didn't worked on reboot again I was thinking into add the nautilus comand to the applications at start up list.

---

### Post by lavadisco on 2009-11-29
Bump because I am having this same problem.

---

### Post by manolomanolo on 2009-12-04
Bump.

---

### Post by itsjustarumour on 2009-12-09
Bump, because I'm having the same problem!  On Jaunty, 32-bit.  I'd been working for a couple of hours, and system got sluggish.  I noticed Banshee was using 63% CPU...then Screenlets crashed, then Firefox and other programs.  I tried rebooting, and got this problem as soon as I rebooted.

I've tried all the fixes and suggestions in this thread, but no joy...

---

### Post by sando on 2009-12-11
Had the same problem. After hours of troubleshooting I found out it was caused by a .svg file in my desktop -I replicated the problem by copying the file to other folders and nautilus crashed every time I opened them.  Deleted it, problem solved. I don't know the reason but hope this is useful info.

---

### Post by itsjustarumour on 2009-12-12
> **sando said:**
> Had the same problem. After hours of troubleshooting I found out it was caused by a .svg file in my desktop -I replicated the problem by copying the file to other folders and nautilus crashed every time I opened them.  Deleted it, problem solved. I don't know the reason but hope this is useful info.


I've found in the log files that a crash was happening due to a missing .svg file on my Jaunty 9.04 box.  In my case, it was /usr/share/icons/screenlets.svg that was missing.  Whether that was what caused the original corruption in my case I don't know... added another icon in, and at least that was part of the problem solved.

---

### Post by manolomanolo on 2009-12-12
i've got no .svg files on my desktop.
just a symbolic link, some .png and a .pdf

Where can I see such log informations you've been mentioning in the last two posts?

Thanks.

---

### Post by itsjustarumour on 2009-12-12
I'm having real problems with my Jaunty 9.04 Desktop not loading properly.  I'm posting on this thread here:

[http://ubuntuforums.org/showthread.php?t=1352747](http://ubuntuforums.org/showthread.php?t=1352747)

Perhaps that could be related to the problems on this thread...

---

### Post by jorge1969 on 2010-03-27
I had the same problem. To fix it press ALT-F2 and enter gconf-editor then run then expand apps and nautilus and make sure that always_use_location_entry is set. 
This worked for me.

---


---
title: "PCManFM won't open files"
date: 2009-01-16
forum: General Help
---

### Post by Dirjel on 2009-01-16
I've been using pcmanfm for a while now, instead of nautilus, for file/folder browsing.  About a week ago, though, pcmanfm decided it didn't want to open files anymore.  I can navigate through different directories, drag and drop, use tabs, everything.  It just won't open a file or launch an application when I double-click on something, or even if I right click --> open with.

I've gotten into the habit of just opening yakuake (now using Tilda instead) and using the cli to run programs and view/edit files.  I have no idea at all what caused it to stop working.  When I try and open something, say, a song, it shows totem opening in the window list on the panel, but the program dies somewhere before it actually opens, and it disappears from the list.

Another thing, is that it's not 100% consistent.  Sometimes, when I boot the computer pcmanfm works properly.  Most times, though, it doesn't.  Nautilus seems to always work, but I haven't really thoroughly tried it.

---

### Post by kerry_s on 2009-01-16
try running it from the terminal so you can see what kind of errors it throws up.

pcmanfm uses ~./local to keep track of what programs you assign to things, when i want to clean up i delete that, you can try renaming it, don't worry it will create a new 1 on its own, but it will be like a fresh install, so you will have to tell it what you want to use for what.

---

### Post by Dirjel on 2009-01-16
I tried running it through the terminal, but it just spits out a new command prompt, so I can't get the error messages that way.  Of course, I'm rather inexperienced with the cli, so there may well be something I'm missing.

Anyway, I'll try and dump that local file thing, see what happens.

---

### Post by Dirjel on 2009-01-16
ANNNNND...

It didn't do anything.  All my files now open with the defaults (Nautilus was set as the file browser again, had to fix that real quick).  PCManfm still won't open anything besides folders.

Maybe I should just reinstall it?

---

### Post by kerry_s on 2009-01-16
you mean you haven't tried to reinstall it yet. ;)
yeah that a good idea, you should try that.

---

### Post by Dirjel on 2009-01-16
> **kerry_s said:**
> you mean you haven't tried to reinstall it yet. ;)
yeah that a good idea, you should try that.

Yeah, it just didn't occur to me until I was already typing up the message XD

Anyway, I reinstalled it, and it's working fine, for now.  If it starts acting up again, I'll probably revive this topic.  Thanks/sorry! XD

---

### Post by TheMyself on 2009-01-16
I've had a similar experience and when I rebooted the computer the problem was resolved.

---

### Post by Dirjel on 2009-01-16
Alright, so after the reinstall I can now open files that run in mirage, open office, and totem.  However, wine and gedit won't open from pcmanfm still.  Again, I tried both double-clicking and right click --> open with.  Doesn't work.

---

### Post by Dirjel on 2009-01-18
Yeah, well... I give up.  Back to Nautilus for me.  It's sooooo slow, though, now that I'm used to pcman XD

Is there another file manager that's as fast (or nearly as fast) as pcman was?  Nautilus has no problems at all opening anything, whereas pcman is still having issues even after reinstalling it.

---

### Post by edyeeh on 2009-01-27
> **Dirjel said:**
> Yeah, well... I give up.  Back to Nautilus for me.  It's sooooo slow, though, now that I'm used to pcman XD

Is there another file manager that's as fast (or nearly as fast) as pcman was?  Nautilus has no problems at all opening anything, whereas pcman is still having issues even after reinstalling it.

Try thunar filemanager

I had the same problem with pcmanfm. I liked it but its useless if it cannot open files. If I could find out how to rectify that one problem I would use pcmanfm

---

### Post by Surfrock66 on 2009-03-01
I'm having the same problem.  I have Nautilus fully uninstalled and PCmanFM is my replacement.  It works fine, then all of a sudden once in a while it'll go to screensaver, and when it tries to come out I get vertical lines on the screen and i have to hard reboot.  When it comes back, PCmanFM won't open files, either from the desktop or from a file folder.  I can open programs from gnome do and open files that way, but when I try to run a program by clicking a file I get a "waiting" pointer for about 20 seconds and then nothing happens.  I have reinstalled, and it didn't work.  It snaps out of it sometimes after an un-regular number of reboots, sometimes 2, sometimes 3, etc.  Let me know what output you'd need to see, could someone re-describe the way to output errors from pcmanfm?

---

### Post by kerry_s on 2009-03-01
ditch pcmanfm, thunar is far more stable, everything works like it's suppose to.

---

### Post by cannonfodder on 2009-04-28
I am also experiencing this problem. 

I have found next to nothing about this online, no bug reports that I know of. Must not be a lot of us out there using PCManFM.

Nautilus is not an option I am willing to consider. 

Thunar is good - much lighter than Nautilus - but has no tabs and the over-sized icons of the 'toolbar style' Location Selector option is really annoying, even if it doesn't affect functionality.

I have found that starting PCManFM from a console/terminal 'pcmanfm &' launches an instance of PCManFM that **does** open files using the appropriate application.

---

### Post by cannonfodder on 2009-04-28
Compiling from source took care of the problem.

---

### Post by cannonfodder on 2009-04-28
Spoke too soon... 

I was able to open a few text files in Mousepad from PCManFM but after that the same old problem came back: click on a file and PCManFM just hangs for a while without actually opening anything.

Running ```
update-mime-database /usr/share/mime
``` and ```
update-desktop-database
``` as suggested in the README didn't help.

---

### Post by Graeme Jackson on 2009-05-02
This issue has been bugging me for a while now. But the "pcmanfm &" from the terminal put me on track of the solution.

I changed the launcher string to "pcmanfm --no-desktop" and voila! It's working perfectly.

Thanks Canonfodder

---

### Post by Graeme Jackson on 2009-05-02
I apologise for creating false hope. After reboot it stopped working.

I have created a script to run it and am using that in the launcher. That worked and has survived a restart:
      #!/bin/bash
      /usr/bin/pcmanfm --no-desktop

G

---

### Post by lykeion on 2009-05-20
Upgraded to Jaunty today and I've noticed the same problem with pcmanfm. Launching pcmanfm from a terminal (or via a bash-script) solved it.

But the problem doesn't seem to be with pcmanfm because I noticed other applications behaving strange when launched from applications menu or with a panel launcher.
 
Example: I have a secondary tv-out display (separate x screen) with a panel launcher for VLC. This have worked fine in intrepid but now VLC opened in my primary monitor display instead. Starting VLC from terminal solved it.

Do I really have to write bash-scripts for every application that doesn't launch like it should in jaunty???

---

### Post by em4g.3ht on 2010-04-09
Hey guys, I know this is a real old topic, but I just recently had this problem on my arch system, and like most of u said, nothing worked and there's not documentation on the interweb. The only thing that I found was going to preferences and checking the box that says 'open files and folders with single click' ... this seams to work and it's pretty neat too, makes browsing a lot faster just remember to pause on files to select them ;)

---


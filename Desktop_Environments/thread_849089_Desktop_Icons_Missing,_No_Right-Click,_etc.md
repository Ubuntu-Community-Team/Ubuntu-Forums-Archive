---
title: "Desktop Icons Missing, No Right-Click, etc"
date: 2008-07-04
forum: Desktop Environments
---

### Post by Norri on 2008-07-04
Hi :)

For some weird reason, my Ubuntu 8.04 installation no longer has a desktop.  My desktop image is there but my shortcuts and files aren't.  I also can't right-click the desktop any more.

How can I fix this?  I've already tried changing nautilus settings in gconf-editor to no avail.  It's as if some process in a normal Gnome session isn't starting up.

---

### Post by mrbowlingalley on 2008-07-04
I just went through this about 20 minutes ago. This was after uninstalling Evolution. The fix is in the forums. Basically I did this. CTRL-ALT-Backspace.

sudo apt-get install ubuntu-desktop

It started the download of lots of things, including Evolution - or parts of it. Booted again. Everything was how I had it before.

Hope this helps. My first post!

---

### Post by mcduck on 2008-07-07
> **Norri said:**
> Hi :)

For some weird reason, my Ubuntu 8.04 installation no longer has a desktop.  My desktop image is there but my shortcuts and files aren't.  I also can't right-click the desktop any more.

How can I fix this?  I've already tried changing nautilus settings in gconf-editor to no avail.  It's as if some process in a normal Gnome session isn't starting up.

HAve you tried actually starting Nautilus? (As that sounds like for some reason or other Nautilus wasn't started).

Just open a terminal and run "nautilus &".

---

### Post by Norri on 2008-07-07
That did it!  Thanks mcduck :)

Now I just need to fix my session issues.  Looks like the Gnome sessions are being loaded from an old file instead of loading what I want them to load.

Anyways, again, huge kudos to you for finding the answer :)  Can't believe I never tried that!

---

### Post by vijaym on 2008-07-10
thanks this helped me also.
i messed up my setting fiddling with compiz

---

### Post by F W Adams on 2009-03-19
I seem to have exactly the same symtoms as above:

no right-click on desktop
no icons or short cuts on desktop

Desktop folder looks fine
mouse works fine in other areas

Tried all of the above with no improvement, "nautilus &" when run in terminal displayed "[1] 8200" at terminal and ran fine.

Any help?

---

### Post by v1nsai on 2009-05-22
This has been happening to me intermittently, sometimes after program crashes and sometimes for no reason.  I ran 'nautilus &' but that only fixed the problem until I closed the terminal.  

I hit alt+f2 and ran it from that window and it all came back, but I think my video is off, the theme on my windows is the same but the buttons look funny, kind of reminds me of windows 98 actually, the font is different and the shape is more rigid.  Video seems to be pretty choppy when before it was smooth.

I'm gonna look further into this I'll post if I find anything.

---

### Post by RoboRutt on 2009-06-18
AAaaarrrggh.

I am getting the same (or very similar) problem too.  Using Intrepid, dual screen with Nvidia drivers etc.. Been working a treat for months, then this morning I boot & get no desktop icons.  All other panels & programs are fine.  

All variations of running nautilus just start a file browser/nautilus window, with no recovery of icons.

VERY frustrating.  Been using Ubuntu for a couple of years now, but finding this version (Intrepid) very flakey.

Just adding my voice to the issue - Will post if find an answer.

---

### Post by RoboRutt on 2009-06-18
OK - I feel like a goose, but at least it's working!

I decided to start with reinstalling nautilus & tried mrbowlingalley's suggestion:

> I just went through this about 20 minutes ago. This was after uninstalling Evolution. The fix is in the forums. Basically I did this. CTRL-ALT-Backspace.

sudo apt-get install ubuntu-desktop

..... and as soon as I restarted X (CTRL-ALT-BKSPACE) everything was back to normal.  Presto  I have no idea why - I had tried reboots, but a hard restart of X was all that was needed in my case.

None the wiser as to why - but gotta get on with work now :)

---

### Post by Darkpegasus333 on 2009-09-27
I had the same problem. Running 'nautilus &' worked until i closed the nautilus window that popped up or the terminal. Running nautilus using alt+f2 worked. Running nautilus using 'nohup nautilus' in a terminal also worked.

---

### Post by rwigle on 2009-10-08
I have had this problem for most of this week. I have tried several things and the one that `worked' was restarting X.

If I restart X (Ctrl-Alt-Back) I fix the problem, but only temporarily. Each time I reboot, the desktop is blank again.

I deleted (well moved) various config folders as someone suggested, but this just gave me the opportunity to put items back on my panel. The folders I removed are .gonf, .gconfd and .gnome2

This is Hardy Heron.

Any suggestions?

---

### Post by anujb on 2010-03-07
I had the same problem after installing Compiz. Restarting X server did not work for me. This is what worked:

Do Alt+F2 and then simply run 'nautilus' (not 'nautilus &'- this was throwing some error).
Then re-login.
:)
Done!

---

### Post by ebcovert3 on 2010-03-30
Ok, I think I have tried every potential solution listed here and all to no avail e.g CTRL-ALT-Backspace, Alt+F2, nohup nautilus, etc. My issue might be different; not really sure. I have no File, Edit, etc. menu options on nautilus (see attached image). 

I have gone through gconf-editor and reviewed every option but can't seem to find the one that turns things back on. The images used to be there, but they just disappeared awhile again. I also have no right-click ability in nautilus (but do in other applications).

I have even tried to reinstall ubuntu-desktop: no joy.

```
Reading package lists...
Building dependency tree...
Reading state information...
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Any ideas?

---

### Post by bamo on 2010-05-10
[FONT=Palatino Linotype]   Thanks, guys.
   Your comments helped me.  I lost my Gnome desktop icons and right click menu a couple of days ago.  There was no instance of nautilus running and trying to start it with 'nautilus &'  simply got a report of a segmentation fault.  However, in those two days I had not rebooted my computer.  I did and all is well now.
   I am wondering what caused the problem, however.  Any ideas?[/FONT]

---

### Post by dddw on 2010-05-18
I got the same issue.
I do see my desktop with icons and folders. I can open them, but I cannot right-click them. 
Not the end of the world, but sometimes a bit annoying nevertheless.

---

### Post by klikevil on 2010-08-09
> **F W Adams said:**
> I seem to have exactly the same symtoms as above:

no right-click on desktop
no icons or short cuts on desktop

Desktop folder looks fine
mouse works fine in other areas

Tried all of the above with no improvement, "nautilus &" when run in terminal displayed "[1] 8200" at terminal and ran fine.

Any help?


killall -1 nautilus


lol

---

### Post by woodbrick on 2010-09-10
> **Norri said:**
> That did it!  Thanks mcduck :)

Now I just need to fix my session issues.  Looks like the Gnome sessions are being loaded from an old file instead of loading what I want them to load...


I don't know if I'm missing something in this thread and others covering similar issues, but the 'big picture' problem (quoted above) still seems unsolved. 

I have had this same problem for a few days now. typing "nautilus &" in terminal works, OR "killall nautilus" then "nautilus" works. But I cannot find anyway to start nautilus as it should from bootup. 

Any suggestions????

---

### Post by woodbrick on 2010-09-10
> **woodbrick said:**
> ... But I cannot find anyway to start nautilus as it should from bootup. 

Any suggestions????


I should not need this spelled out for me, sorry. For others who are getting this problem and if typing "nautilus &" in the terminal restores your folders and right-clicks... 

*System->Preferences->Startup_Applications* Then ADD:

Name: Nautilus 
Command: Nautilus
Comment: Folder viewer (or whatever comment you like) 

The only remaining question, then, is why?? 

How does something so central to the Gnome desktop "just break" like that???

---

### Post by Tempelton on 2010-09-19
I think I have the very same thing on a my new Ubuntu installation. Every single login I find my desktop icons missing. The "nautilus &" command doesn't help in my case. I have to "killall nautilus" to make the desktop icons reappear and to re-enable right-desktop-clicking. :(
I really hope that eventually someone will come up with a solution to that problem or at least find what is causing it.

---

### Post by kaspar_silas on 2010-09-19
On a clean install that's very weird. For now can't you just use the solution in the above post. Thou maybe just alter the command to be 

command: killall nautilus; nautilus

to exactly match your current fix.

---

### Post by Tempelton on 2010-09-22
> **kaspar_silas said:**
> On a clean install that's very weird. For now can't you just use the solution in the above post. Thou maybe just alter the command to be 

command: killall nautilus; nautilus

to exactly match your current fix.
I've added the *killall nautilus; nautilus* command to my *System->Preferences->Startup Application*s but it doesn't do a thing. Same as always, my desktop icons are missing and I have to kill nautilus manually via the console to repair that.
It's not a pure clean Ubuntu install in a full meaning of the word. I've installed a few applications from the repository after I've set up my system, but that's about it. I think I've begun to see those missing icons after GeForce 420 Go drivers installation (on old Toshiba 1410-303) but I'm not quite sure of that, for at first it was happening only occasionally, so I didn't pay too much attention to that weird behavior

---

### Post by stark dar on 2010-09-23
I am a Linux noob and having this problem. I have been going through this entire post for two days and have tried everything. Twice. Nothing has ever changed anything. Got any more ideas?

---

### Post by nh7o_hi on 2010-09-24
I ran into this, and haven't figured out why. It persisted after upgrade to 10.04. I did add just "nautilus" to my Startup Applications list, and that fixed things for me. Previously, I always noted that there was a nautilus instance showing up in the process list after boot, so having to add it manually is not so bad. Why the script that started nautilus at log in got changed is the mystery.

I am wondering if it is related to sreadahead and ureadahead. I had both on my system, and noticed that software installation would generate errors in sreadahead. The sreadahead package said it was "safe to remove" as it was transitional to ureadahead. I think my problem started when I uninstalled sreadahead, but am not sure as I made several changes. But I did notice that my boot up memory use, before loading any apps, had become quite large. Now it is back to normal again.

---

### Post by kaspar_silas on 2010-09-27
> **Tempelton said:**
> I've added the *killall nautilus; nautilus* command to my *System->Preferences->Startup Application*s but it doesn't do a thing. Same as always, my desktop icons are missing and I have to kill nautilus manually via the console to repair that.
It's not a pure clean Ubuntu install in a full meaning of the word. I've installed a few applications from the repository after I've set up my system, but that's about it. I think I've begun to see those missing icons after GeForce 420 Go drivers installation (on old Toshiba 1410-303) but I'm not quite sure of that, for at first it was happening only occasionally, so I didn't pay too much attention to that weird behavior

Sorry I was being a fool. "killall nautilus; nautilus" will not work as a command for a start up launcher. Try this  

If you don't have a bin folder in home folder make one. 

Then add this line to the end of file /home/[yourname]/.bashrc

PATH=$PATH:~/bin

make a file called NAUTILUSFIX in the bin folder and put 

killall nautilus; nautilus

in that. Then change the start up application command to NAUTILUSFIX.

---

### Post by sd73ta on 2010-10-14
> **kaspar_silas said:**
> Sorry I was being a fool. "killall nautilus; nautilus" will not work as a command for a start up launcher. Try this  

If you don't have a bin folder in home folder make one. 

Then add this line to the end of file /home/[yourname]/.bashrc

PATH=$PATH:~/bin

make a file called NAUTILUSFIX in the bin folder and put 

killall nautilus; nautilus

in that. Then change the start up application command to NAUTILUSFIX.

Scratch my original post.  Ive got it thanks : ) Had reread it

---

### Post by yaye on 2011-01-31
Right-clicking on the desktop stopped working a few days ago, and changing the settings and trying the commands listed before didn't work. For me, the solution was to reset my GNOME settings to default by renaming .gnome .gnome2 .gconf .gconfd .metacity folders with a .bak extension.  I logged out and logged back in.  The desktop was back to the default and right-click worked.  I customized the desktop and, after I was satisfied that everything was working as I wanted, I deleted the .bak folders.

I found this solution in a post by Martin Owens here: [http://askubuntu.com/questions/13140/gnome-panel-and-menu-bar-cant-be-clicked/13311#13311](http://askubuntu.com/questions/13140/gnome-panel-and-menu-bar-cant-be-clicked/13311#13311)

---

### Post by vxd240 on 2011-03-26
For me, the problem was installing Nautilus Elementary.  After uninstalling ([http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html](http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html)) with
{code}
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
{code}
I also had to add nautilus into System > Perfernces > Startup Applications

---

### Post by zeroseven0183 on 2011-05-12
I recently installed Faenza Icons PPA and the icons package and had this problem immediately. I already forgot how to restore the right-click on desktop.

---

### Post by zeroseven0183 on 2011-05-12
Ok, now I remember. I installed gTweakUI and launched gTweakUI-Nautilus, checked the box that says Draw Nautilus on desktop. That fixed it.

---

### Post by cshark on 2011-09-10
> **klikevil said:**
> killall -1 nautilus


lol

Yeah! the best answer! worked perfectly for me (Linux mint 11 but for thoose who don't know it's debian-ubuntu based).

---

### Post by kedmond on 2013-01-18
> **zeroseven0183 said:**
> Ok, now I remember. I installed gTweakUI and launched gTweakUI-Nautilus, checked the box that says Draw Nautilus on desktop. That fixed it.


Thank you for posting this.

I'm running Ubuntu 12.04 with Unity.  I went to "Tweak Tool" and under "Desktop" I ticked on "Have file manager handle the desktop".  I do not know why that was turned off, but now the desktop is back.

Thanks again.

---

### Post by alokmahor on 2013-02-22
> **Norri said:**
> Hi :)

For some weird reason, my Ubuntu 8.04 installation no longer has a desktop.  My desktop image is there but my shortcuts and files aren't.  I also can't right-click the desktop any more.

How can I fix this?  I've already tried changing nautilus settings in gconf-editor to no avail.  It's as if some process in a normal Gnome session isn't starting up.
read case 1 in this post
[http://www.fossguru.in/content/resetting-settings-applications-linux](http://www.fossguru.in/content/resetting-settings-applications-linux)

---

### Post by alokmahor on 2013-02-22
> **Norri said:**
> Hi :)

For some weird reason, my Ubuntu 8.04 installation no longer has a desktop.  My desktop image is there but my shortcuts and files aren't.  I also can't right-click the desktop any more.

How can I fix this?  I've already tried changing nautilus settings in gconf-editor to no avail.  It's as if some process in a normal Gnome session isn't starting up.
read case 1 in this post
[http://www.fossguru.in/content/resetting-settings-applications-linux](http://www.fossguru.in/content/resetting-settings-applications-linux)

---

### Post by codemaniac on 2013-02-22
Old thread closed.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---


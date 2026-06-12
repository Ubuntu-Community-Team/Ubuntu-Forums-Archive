---
title: "KDM becomes unresponsive after upgrade to KDE 4.2.1"
date: 2009-03-07
forum: Desktop Environments
---

### Post by superwad on 2009-03-07
I just installed the packages to upgrade to KDE 4.2.1, and ever since, the entire GUI has become unresponsive. 

After booting, I can use the system for a little while.  This is usually anywhere from 5 minutes to half hour, depending on what I'm doing.  After that, everything becomes sluggish.  The mouse cursor jumps around the screen as I'm moving it, and I can't produce any input.  I can't Ctrl+Alt+Backspace to restart X, nor can I Ctrl+Alt+F1-F6 to change to a terminal.

However, I can SSH into the machine (slowly).  Once in, I do `top` and I see that the process Xorg uses anywhere from 90-120% of my CPU (I have a P4 3.0GHz with hyper-threading, so this value is likely double what it actually is).  Along with that process, hald-addon-stor is also using a very large amount of CPU time (anywhere from 40-90% by top's guess).

I tried to stop KDM by `sudo /etc/init.d/kdm stop`, but I get the error message "Stopping K Display Manager: kdm not responding to TERM signal (pid 8618)".  I've made sure it's running, and it certainly is, but I just can't kill it.

I also tried to kill -9 the process ID for Xorg.  It doesn't die, but I notice that the CPU usage for Xorg remains constant 100%, and the hald-addon-stor is no longer taking up cycles.

The only other things that have changed since upgrading to KDE 4.2.1 is that my sound card (Creative Audigy2 ZS) stopped working ([see my thread about this](http://ubuntuforums.org/showthread.php?t=1089910)) and I upgraded the firmware on my Seagate 1TB drive.

Does anybody know what might be going on here?  I can provide anything necessary to help troubleshoot.

Thanks!

---

### Post by Skripka on 2009-03-07
1st things-what Xorg, what driver for what card-and what linux are you using?

---

### Post by superwad on 2009-03-07
Xorg - 1.5.2-2ubuntu3.00~ppa1
Driver - Open source driver (unsure which version).
Card - ATI Radeon 9500 Pro
Linux - 2.6.27-12-generic

---

### Post by superwad on 2009-03-10
I noticed that my Xorg just got upgraded to 1.5.2-2ubuntu3.1, and I'm still getting this problem.

Just a bit more information on when this occurs.

I can be using the computer a little bit, such as to chat through Pidgin, or have a document open.  But when I start doing anything too quickly, such as start typing a lot into a chat window or word processor, then I start having issues again.  The most jumps around the screen, but doesn't interact.  No keyboard input works (not even the Function key changes the receiver status).

However, if I'm doing a lot of work on the computer in a remote session (SSH, FTP), I don't get the issues.  Clearly, this should indicate that the problem lies with Xorg or the graphics system in some way.

Is there any more information I can provide that would shed some light on the problem?  Log files, top output, running processes?  Let me know and I'll provide it.

Thanks.

---

### Post by superwad on 2009-03-13
I'm still not having any success with this.  The problem keeps happening whenever it seems I'm "using" the computer too much.

That being said, just yesterday after I rebooted to clear the issue, my computer froze during start up.  But that may have been an unrelated problem, since it seemed my RAID card decided to become dislodged.

I'm almost ready to format and re-install clean to see if that resolves it.  It would be a shame too, since I've been running this particular install (not counting upgrades as new installs) since 6.04.  But perhaps it is time to clean it up.

My next post will likely be the results of my format if nobody responds with a course of action.

---

### Post by Zorael on 2009-03-14
You could try downgrading to 4.2, I guess, and see if that helps. Not really sure what could be causing it.

I would suggest you try backing up and wiping your /etc/X11/xorg.conf, for good measure. If you suspect the driver, you could explicitly tell it to use vesa and see if the issue remains. Also, you could create a new user and see if it happens when logged in as him, as well.

---

### Post by superwad on 2009-03-19
Sigh.  I formatted, reinstalled everything, and I'm still having the problem.  I've only installed software such as Pidgin, Firefox, OpenOffice, and done no configuration aside from the configuration of my FTP and Samba services.

The KDE version is now 4.1.4.  This time though, the mouse doesn't go all jumpy and slow on me.  The mouse will continue to work at the usual pace, but nothing else responds.  I cannot drop to a shell, I cannot restart X.  I'm using a KVM, and when I switch to another computer and back to this one, the mouse no longer responds.

I have made no hardware modifications since reinstalling.  I've checked all my existing hardware.  The temperatures are within my normal operating ranges, all fans are working fine, low dust levels, no blown capacitors on any components, no leaks.  I'm at a total and complete loss.

I've even disconnected all my hard drives other than my boot drive (paranoia from an unfortunate install years ago, and even then I still forgot to backup my /var/www :().  

As far as I can tell, I've removed all possible software and all hard drive conflicts.  Unless the other hardware has failed partially, what else could it be?  Am I going to have to switch to Gnome until I can figure this out some more in detail?  Is there some diagnostic I can do or provide that would shed some light on the situation?

Many thanks.

---

### Post by superwad on 2009-03-20
OK, I've just ran a battery of hardware tests.  The good ones passed (memtest86, Sea Tools).  I take out all hardware except my video card (no onboard video) and run glxgears for a while.  I first of all get the best performance out of the card.  Then, I turn it off and start using Firefox, then it locks up again.

I'm going to keep trying to diagnose hardware issues.  I don't think at this point it is software, given that I've formatted the entire machine and it still persists.

Perhaps I'll take the system drive out and put in in another machine and see if it still locks up.  If it doesn't, then I know I have a hardware issue *somewhere* in the computer.  If it still locks up in another computer, I'll come back here for more abuse :(

---

### Post by superdif on 2009-03-23
I have the same problem with the plain KDE 4.2 (got by following [http://www.kubuntu.org/news/kde-4.2]("http://www.kubuntu.org/news/kde-4.2")) and Nvidia drivers 180.29 on Kubuntu 8.10 64bits.

---

### Post by superwad on 2009-03-23
> **superdif said:**
> I have the same problem with the plain KDE 4.2 (got by following [http://www.kubuntu.org/news/kde-4.2]("http://www.kubuntu.org/news/kde-4.2")) and Nvidia drivers 180.29 on Kubuntu 8.10 64bits.
I believe I may have found my problem; not sure if it will help you or not.  It seems that somehow my video card became broken in some manner, which caused the system to lock up.

I first tested plain Ubuntu, which had the same issue.  Then I installed Ubuntu on a different hard drive, to eliminate possible hard drive issues, and I had the same problems.  Since I'd removed all additional hardware other than the bare basics to run the system (video card included), a friend suggested I replace my video card.  I had another AGP video card from a spare computer (trying to keep as much of the configuration the same).  I put it in (NVidia is the replacement, ATI was the original), and after detection and installation of third party drivers, everything seems to be working just fine.

I've been running it for about a day now without any problems.  I've done as much as I can to force it to freeze on me (playing games, videos, switching workspaces, multiple windows, fancy effects), and everything appears stable so far.

So try looking at your video card.  Make sure the fan is still spinning (if it has one), that the heat sink doesn't have any dust build up (if it has one), and that there are no blown capacitors.  If all those check out, just try putting in a different video card and see if that works any better.

Good luck!

---


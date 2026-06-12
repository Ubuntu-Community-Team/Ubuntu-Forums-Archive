---
title: "Latest Humble Bundle Disappointment"
date: 2011-04-15
forum: Gaming &amp; Leisure
---

### Post by dardack on 2011-04-15
Granted I'm not one of those paying thousand or couple hundred.  And this bundle was gifted to me from my wife (kids) for my bday.  My daughter had $5 to spend for me.  I hadn't purchased any previous bundles, tbh had never heard of this.  My wife found it and thought hey your dad likes games, loves linux (only OS in house), let's try this.  I had previously purchased World Of Goo during the pay what you want promotion.  

When my wife told me, I was like, cool, I'll probably go back and drop $60 that i would spend on a new game to say ty for supporting linux (new games are usually for my xbox360).  However, not 1 of the 3 games works for me.

No error message, just aborted.  I know FB is busy according to their message boards, but 2 days for email no response, 1 day in forums no response.  Just kinda sux.

(and if anyone cares, I have gtx260 1gig ram with nvidia binaries installed, so it should run, I have turned all settings to lowest and still aborted message.)

Hopefully, this will be resolved, but so far not a fan of this humble bundle thing.

---

### Post by sakuramboo on 2011-04-15
What are you doing?

I haven't had any problems with any of the games I've got from the HIB and I've gotten every single one from all three.

---

### Post by dardack on 2011-04-15
> **sakuramboo said:**
> What are you doing?

I haven't had any problems with any of the games I've got from the HIB and I've gotten every single one from all three.


What am I doing? Nothing but trying to run it:

Laptop:~/Programs/trine$ ./trine-bin64
Got signal 11 at (nil) from (nil)
./trine-bin64[0x433c98]
/lib/libc.so.6(+0x33c20)[0x7fc99aa99c20]
Aborted

:~/Programs/trine$ ./trine-bin32
Got signal 11 at (nil) from (nil)
./trine-bin32[0x8078188]
[0xf777b410]
Aborted

Same error if I click launch from the launcher.


Laptop:~/Programs/survivor$ ./survivor-bin 
Got signal 11 at 0xc from 0x838a1cf
Aborted


-Laptop:~/Programs/survivor$ padsp ./survivor-bin 
Got signal 11 at 0xc from 0x838a1cf
Aborted

Just aborted.  I mean I've seen other people say it runs fine even with the signals, but it just aborts.

---

### Post by ExileAmongYou on 2011-04-15
You could try uninstalling, then reinstalling by running the installer .run file with sudo. That's what I did, and both Trine and Shadowgrounds start no problem.
Also, are you sure you're trying to run the right file? When I looked in the Trine folder, I saw a few different files that *might* have been the way to start it, like trine-launcher.sh. If you have an entry in your main menu for Trine, try running it from there, or at least check what file the menu shortcut is trying to run.

---

### Post by sakuramboo on 2011-04-15
Have you done anything unique to your installation of Ubuntu? Are you running 64-bit? Did you do anything strange with pulseaudio? Did you install any non-standard libraries?

> **dardack said:**
> What am I doing? Nothing but trying to run it:

Laptop:~/Programs/trine$ ./trine-bin64
Got signal 11 at (nil) from (nil)
./trine-bin64[0x433c98]
/lib/libc.so.6(+0x33c20)[0x7fc99aa99c20]
Aborted

:~/Programs/trine$ ./trine-bin32
Got signal 11 at (nil) from (nil)
./trine-bin32[0x8078188]
[0xf777b410]
Aborted

Same error if I click launch from the launcher.


Laptop:~/Programs/survivor$ ./survivor-bin 
Got signal 11 at 0xc from 0x838a1cf
Aborted


-Laptop:~/Programs/survivor$ padsp ./survivor-bin 
Got signal 11 at 0xc from 0x838a1cf
Aborted

Just aborted.  I mean I've seen other people say it runs fine even with the signals, but it just aborts.

---

### Post by Ctrl-Alt-F1 on 2011-04-16
I don't know what kind of system you're using, but almost always when I can't get a game to run on my system it's because I'm on a 64bit machine and I'm trying to run a 32bit game without the proper libraries.

sudo apt-get install ia32-libs usually does it for me.

However, I noticed that you have tried both a 32bit and 64bit binary for trine, so it's probably something else for that one game at least.

Post a little more about your hardware?

---

### Post by philipballew on 2011-04-16
i confirm this error on a dell 1558 i5 with intel graphics ubuntu 10.10 64. also i have ia32-libs installled

---

### Post by R33D3M33R on 2011-04-17
You could use padsp to run it. But with intel cards this games aren't playable atm. Drivers are in the works.

Source: [http://frozenbyte.com/board/viewtopic.php?f=15&t=3312](http://frozenbyte.com/board/viewtopic.php?f=15&t=3312)

---

### Post by dardack on 2011-04-17
I have an nvidia card with 260.19.44 binary drivers.  I am on a 64bit machine with ia32 libs installed.

AFAIK I have everything normal installed, nothing overerly special.

Does same thing with padsp ./trine-bin64.

As for different things, ./trine-launcher after I clicck launch same error, same error ./trine-bin32 and  ./trine-bin64.

Core Duo 2.4ghz, GTX260m 1gig mem, 6gig memory.  Every other game works, even got trine running under steam, but not how i really want to play TBH.  I don't know I may just give up, kinda sux tho.

---

### Post by handy on 2011-04-17
> **dardack said:**
> I have an nvidia card with 260.19.44 binary drivers.  I am on a 64bit machine with ia32 libs installed.

AFAIK I have everything normal installed, nothing overerly special.

Does same thing with padsp ./trine-bin64.

As for different things, ./trine-launcher after I clicck launch same error, same error ./trine-bin32 and  ./trine-bin64.

Core Duo 2.4ghz, GTX260m 1gig mem, 6gig memory.  Every other game works, even got trine running under steam, but not how i really want to play TBH.  I don't know I may just give up, kinda sux tho.

Contact the developers.

---

### Post by Perfect Storm on 2011-04-17
Could it be a that the file is corrupted. Try a re-download.

---

### Post by Technophobia on 2011-04-18
Anything in ~/.frozenbyte/trine/logs

You have to select Western encoding in gedit to view the text.

---

### Post by philipballew on 2011-04-18
unfortunately not, heres a more overall explanation of others facing this problem 
[http://frozenbyte.com/board/viewtopic.php?f=16&t=3303]("http://frozenbyte.com/board/viewtopic.php?f=16&t=3303")

---

### Post by dardack on 2011-04-18
Had to reinstall Ubuntu, now works flawlessly.  Although now i get a NVIDIA splash screen, i didn't before, so maybe the install of drivers was messing up.

EDIT: Also, very happy with the game trine.  Very addicting.  Sure it took me like 3hrs to reinstall/set everything back up, but that's why i Keep my home partition separate.  So imo worth it to have it running and now i feel that even wow is running better by like 5-10 FPS now.  So maybe the upgrade from 10.04 to 10.10 and install of nvidia drivers something was happening that wasn't 100% right.

---

### Post by Technophobia on 2011-04-19
You have to add a line to the xorg.conf to disable the nvidia logo.

something like 

Option  "NoLogo" "true"

look it up if you want

---

### Post by dardack on 2011-04-19
> **Technophobia said:**
> You have to add a line to the xorg.conf to disable the nvidia logo.

something like 

Option  "NoLogo" "true"

look it up if you want

Yea I know that.  My point was I never added it before, I always clicked "Yes" Do I want the nvidia installer to create my xorg.conf file.  SO after upgrading from 9.10 to 10.04 to 10.10 when installing the Binary something went wrong, it worked for most things, but again no Logo and these 3 games didn't work.  Full reinstall of 10.10 from a disc and works flawlessly.

---


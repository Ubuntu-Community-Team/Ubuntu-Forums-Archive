---
title: "Boot Help Please!"
date: 2009-05-23
forum: General Help
---

### Post by AltAero on 2009-05-23
Help please! 
I'm fairly new to Ubuntu- been using it for less than a month. I tried to boot up my laptop this morning, running Ubuntu Jaunty Jackalope, and after the loading screen (the ubuntu logo with the small bar underneath it :)) had finished loading, my screen went completely black besides a pixelated blue bar at the top and random lines of colour in the middle of my screen. I can't do anything from here :S I tried restarting my laptop, but the same thing just keeps happeneing :(
Any ideas on how to fix this? I need my laptop- it holds all my documents and music in, so I can't really re-install Ubuntu.
By the way, I'm running it on a Sony VGN-FW21E (Very nice laptop if I may say so ;)) and I'm not dual-booting with anything.
 
Thanks, all help appreciated :)

---

### Post by QIII on 2009-05-23
Restart.

When you get the GRUB menu, select "recovery mode" and see if you can run from there.

I've been up far to late, so I can't stick around.  But if you could try that and leave a post for someone else, they'd have a bit of information to work from.

---

### Post by Legace on 2009-05-23
What did you do prior to the boot failure?
Did you install anything (applications, drivers, etc.) or did you edit any (system) file?

---

### Post by QIII on 2009-05-23
Sorry --

When you get the message in the upper left corner that GRUB is loading, hit the escape key to get into the GRUB menu.

THEN select recovery mode...

... tired ...

---

### Post by AltAero on 2009-05-23
So, I'm in Recovery Mode- do you want me to click 'Resume Normal Boot'? If so, the same thing happens :S
And yesterday, all I did was download an episode of Heroes (^^), install the VLC player thingy, watch my Heroes, then leave my laptop on over night (kinda fell asleep without turning it off)
 
Thanks for the replies

---

### Post by AltAero on 2009-05-23
I just loaded up my BT4 disk, and that runs perfectly- so at least it's not computer hardware failure ^^

---

### Post by QIII on 2009-05-23
Good to hear.

But I have to repeat Legace's question:  Did you install any new packages, update any drivers or do any thing that would have changed your system?

I guess I was just too tired to make sense a couple of hours ago.

Recovery mode does not get you in to the Gnome desktop.  What it does is give you access to several tools to attempt to fix problems like broken references and fix X, which may be your problem.  I say "may" because that depends on whether or not you might have changed something like a driver by mistake, which we still may be able to recover from.

Ubuntu (like all Linux distributions) is a chimera (a mythical beast made of the parts of multiple animals.)  Each of those parts is controlled by different organizations that work cooperatively in the open source world to bring all the different distributions of Linux to the world.

You are using Ubuntu, so we'll stick with that.

You have the linux kernel, which is the basic underlying structure and "operating system" more or less common to all Linux distros.  Each distribution may have it's own little bits added, but the whole thing is still controlled by Linus Torvalds and a band of volunteer developers who work hard to keep it updated and modernized regularly.

You have Ubuntu wrapped around that, which provides the higher-level operating system called, well, Ubuntu.  Ubuntu is the product of efforts by Mark Shuttleworth and some very dedicated people around the world.  Its corporate sponsor is Canonical Ltd, which Shuttleworth, a South African entrepreneur, founded.  Ubuntu is an African word that means something along the lines of "Humanity to others" or "we're all in this together".  That philosophy is what attracted me to Ubuntu.

You have X.Org, which provides an open-source implementation of the X Window System which is the engine the talks to your monitor, keyboard, mouse and input/output devices in general.

Finally you have (in plain Ubuntu) the Gnome interface that provides you with all the pretty stuff you actually see on the screen.  (There are other flavors of Ubuntu, like Kubuntu and Xubuntu that use other interfaces.)

Anyway, it is important to know exactly what you last did before you ran into this problem to know where to begin in recovery mode.

---

### Post by AltAero on 2009-05-23
Humm... the only thinkg I can remember doing was... using 'regedit' to tinker with something to do with Wine to try get my Guild Wars game working- all I did was add a couple of data strings though. Besides that, no, sorry, the only stuff I can remember is downloading a video, installing VLC, deleting wine and the GuildWars.exe (as I couldn't get it ro run properly) and watching the video :S
 
Thanks for the awesome reply though- you should work for wikipedia ^^

---

### Post by AltAero on 2009-05-23
I also downloaded the OpenSUSE 11.1 iso if that means anything? ^o)
 
thanks

---

### Post by QIII on 2009-05-23
By "regedit", I think you mean you did something from a terminal?

"regedit" is for editing the Windows registry.

A great deal of care must be taken with using the terminal, especially when you are fairly new at *nix systems.  You can have things go terribly wrong frightningly fast.  Now that I know you worked in the terminal, I highly suspect something like that happened.

Do you have access to another computer?  Can you find and post the instructions for what you were doing so I can look it over?  Or were you responding to something that appeared while you were working in Ubuntu?

---

### Post by QIII on 2009-05-23
Sorry.

Duh!

Obviously you have access to another computer, or we wouldn't be having this discussion.

I need to go back to bed.

---

### Post by Legace on 2009-05-23
> **QIII said:**
> "regedit" is for editing the Windows registry.

I think he used WINE's own regedit :)

---

### Post by AltAero on 2009-05-23
Yes I'm pretty sure I used Wine's own regedit. And as for instructions, I was following a guide on the internet which was supposed to make GuildWars game client run better... which it didn't. I've looked but I can't find it again on the internet. :(
 
Thanks

---

### Post by QIII on 2009-05-23
Errr... OK.  Don't mind my sheepish grin.  I don't use Wine.

Maybe that's not it, then...

---

### Post by AltAero on 2009-05-23
I still have my Ubuntu LiveCD- would it be possible for me to reinstall it on a separate partition (presuming you can do that via the LiveCD) then transfer my documents and music across?

---

### Post by QIII on 2009-05-23
Was GuildWars what you were editing in regedit in WINE, or did you do something in Ubuntu itself.

It would be really helpful if you could spend a little more time looking for the instructions so somebody can take a look at them -- reinstalling on yet another partition would be messy and you'd have to spend time afterwards resizing your partitions again to get that drive space back.

(If you were using a desktop and had another desktop with Ubuntu installed, it would be extremely easy to recover everything you wanted by slaving the borked drive onto the other machine.  Alas.)

---

### Post by AltAero on 2009-05-23
oooh found it :) this is what I was copying from:
 
[http://tombuntu.com/index.php/2007/04/01/guild-wars-on-ubuntu-with-wine/](http://tombuntu.com/index.php/2007/04/01/guild-wars-on-ubuntu-with-wine/)
 
Hope this helps =] and thanks for the assistance

---

### Post by AltAero on 2009-05-23
Oh and by the way, I uninstalled wine (via Add/Remove Prgram thing) and deleted my Guild Wars stuff after I realised it wasn't working.

---

### Post by QIII on 2009-05-23
I don't know enough about Wine to be sure, but it looks like everything you did would have been inside of Wine's "sandbox".

---

### Post by AltAero on 2009-05-23
Sorry but, what's a sandbox?

---

### Post by trench.me on 2009-05-23
> **QIII said:**
> I don't know enough about Wine to be sure, but it looks like everything you did would have been inside of Wine's "sandbox".

Agreed. 

**AltAero** - Your system seems to have great specs, I would suggest once you get this resolved, not messing with wine at all. Go the [VirtualBox route]("http://www.ubuntugeek.com/how-to-install-virtualbox-220-in-ubuntu-904-jaunty.html") to do your MS things. 

*~ not a fan of wine.* *(Then again, not a fan of MS or their proprietary games either. But I digress...)*

---

### Post by trench.me on 2009-05-23
> **AltAero said:**
> Sorry but, what's a sandbox?

[A sandbox.]("http://en.wikipedia.org/wiki/Sandbox_%28computer_security%29")

---

### Post by QIII on 2009-05-23
I'm speaking of a generic term meaning a virtual space where things like Wine run inside another OS.

Wine, if it works like other things, should have been installed on a portion of your disk and all changes you have made to its registry should be stored there.

When it runs inside Ubuntu, its in its own little workspace, or "sandbox", or "virtual machine"...

---

### Post by QIII on 2009-05-23
OK.

I'm going to recommend against reinstall at the moment.

I think you should try some of the tools in recovery mode.

I have to go at the moment, but I'm sure someone can point out a tutorial if you can't find one.

---

### Post by AltAero on 2009-05-23
All tutorial-pointing appreciated ^^ and thanks for your help QIII, and, I tried using VirtualBox, but when I tried to load GW in, it said I lacked the necessary Video Drivers :S
 
thanks =]

---

### Post by trench.me on 2009-05-23
Okay, so get back to basics, your situation is:

- Running Ubuntu
- Installed Wine
- Attempt at running Guild Wars in wine failed, chaos ensued, Ubuntu graphics are now fail
- Uninstalled Wine
- Ubuntu now fails to load 

Correct? If so, you need to follow through with the recovery mode originally suggested by **QIII**. On boot, wait for the grub loading prompt, hit esc, select the recovery mode kernel and hit enter. Once the recovery mode menu pops up you'll have several options. 

Select **dpkg**   **Repair broken packages**, hit enter, let the command line stuff do what it needs to do. This is to make sure wine didn't break something along the way. You might be asked to remove, repair, or install a new package, if so, at each prompt, type "y" (minus quotes), hit enter.  You might have to do this several times. Command line will continue to fetch, repair, remove, and/or install new packages and will ultimately end at "Finished, please press ENTER". Do so to return to the recovery mode menu. 

Running **fsck** might eventually be needed, but not yet. So skip it.

Still at the **Recovery Menu**, select **grub   Update grub bootloader**. This should be a fairly quick option with no interaction required because I doubt this is the problem but it hurts nothing to run it, and it gets the possibility of a grub issue out of the way. You should be automatically returned to the **Recovery Menu**.

Finally, scroll with arrow keys down beyond **netroot** and **root** (leave them alone for now), and the last option should be **xfix**   **Try to auto repair graphic problems**. Hit enter. This will auto-repair your xorg.conf file. If you've ever had to make any manual changes to the file (located at /etc/X11/xorg.conf) they will be lost. Given you are on a new system with spiffy specs I doubt you'd ever need to manually alter xorg.conf. So let **xfix** do its job. Again you'll be returned to **Recovery Menu**.

Finally you can scroll up, again with arrow keys, to **resume   Resume normal boot**. This will resume boot with all the new changes now in place. Your problem at this point should hopefully be fixed. If not, we'll go from there 

Hope this helps.

---

### Post by AltAero on 2009-05-24
Ah, I've tried that, but it didn't work.

Instead I followed QIII advice and just reinstalled Ubuntu- but I managed to transfer all my music and documents across to my new partition, which I will save onto disks, then re-reinstall Ubuntu and completly wipe my drive, leaving me with one big Ubuntu partition + all my documents. :D

But thanks for the help from everyone- really appreciated :D

Danny =]

---

### Post by trench.me on 2009-05-24
Actually, **Q111**'s last comment was recommending *against* a reinstall. 

As much as I dislike wine I can't imagine a scenario where it would force the user to reinstall/reformat. It would've been nice to find out what actually went wrong. Nice for you, in-case you re-encounter the problem - Nice for Ubuntu & Wine developers, because I can assure you they'd love keep whatever went wrong from happening again - and nice for anyone else that might have the problem in the future. No offense but I'd hate to be the guy trying to install Guild Wars on Ubuntu, losing the ability to boot, and winding up at this thread looking for answers.

Reinstall should always be a last resort.

Either way, I'm glad you didn't lose anything important.

---

### Post by Peaches491 on 2009-06-06
Hello all! As you can probably see, this is my first time looking to these forum's for help. I am having an eerily similar problem to AltAero (i.e. Boot failure and the strange warped load screen)

After a rather speedy boot, i see the loading bar come up as normal, but then just before it finishes, it goes blank. After which, I can see a mostly black screen with what looks like the ubuntu load splash inverted and shrunk. There is a garbled mess of pixels at the top of my screen and a string of seemingly random text trailing off the right edge of my screen. 

Needless to say, i have done something wrong. I an very new to Ubuntu, but i feel i am rather computer-literate. I built this computer from the case up, so my HW setup is as follows:

2 HDD's
   disk 1 = windows XP
   disk 2 = Ubuntu 9.04 Jaunty Jackalope, with the GRUB Booloader on the same drive.

and an ATI Graphics Card

After a fresh install less than an hour ago, i installed the restricted graphics drivers and it called for a reboot. This error presented itself after this reboot. 

Do you need any more details? 

Please, any help would be greatly appreciated!

Ciao

---

### Post by DitchingMS on 2009-06-09
Hi, Having almost the same problem with a single boot, dual hdd Jaunty setup. Worked fine for a few days and then after a few updates etc it falls over when it's about to show the GUI. I can't repair it. My thread's at [http://ubuntuforums.org/showthread.php?p=7429529#post7429529](http://ubuntuforums.org/showthread.php?p=7429529#post7429529) if anyone would care to share info!

Thanks!

---

### Post by Gnusboy on 2009-08-07
Same Boot problem: runs through startup, gets to splash page, appears to load and then goes black before logon.
Kinda weird.
Ubuntu Jaunty 9.04 installed about 3 weeks ago and functioned fine until today. Shut it down when I left for work, but when I booted later, There was no display and after teh Ubuntu splash page, it went dark. No user or password space - just dead.
Reconnected other machine, read forum. tried recovery mode solutions including kernels 2.6.28-14, 13, 11-generic and recovery things from Grub.
None of the recovery options generic or recovery modes got me past initial splash screen.
Also tried repair modules - nada.
Everything worked fine until today. I made 1 change in the morning in keyboard assignment - turned off Caps Lock, with shift-caps enabled. (can't recall exact phrase)

Did nothing else that I can recall.

------------------------------------------------------------------------------------------------------
System: ASUS M3A78-EM, AMD 4-Core 9850, 4 GB 800 mhz ram, 640 HDD, Ubuntu 9.04,
------------------------------------------------------------------------------------------------------

Any ideas?
Thanks

---


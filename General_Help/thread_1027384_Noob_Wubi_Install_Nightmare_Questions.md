---
title: "Noob Wubi Install Nightmare Questions"
date: 2009-01-01
forum: General Help
---

### Post by scudrunner on 2009-01-01
Background:
It's not the PC (I don't think) because at one time I used Wubi to install 8.04 (Hardy Heron) and it worked fine. I had to uninstall it due to disk space. Got a second HD and want to re-install it on the new HD; of course now it's 8.10 Intrepid Ibex. (nothing special about the box, Intel 2.6, 2GB ram, XP Pro SP1; the only thing that is different is that I added a GeForce video card)

So, DL Wubi and the Ubuntu iso file, put them both in a newly created Ubuntu directory on the new HD. Start Wubi, go through the startup stuff and then Wubi starts DLing the same Ubuntu file that is already in the same directory! WHY??? I even put the file on CD and it did the same thing! (everything I have read says that Wubi will look for the file in either the parent directory or the CD ROM)

So...
Uninstall everything, clean the registry, starting fresh, going to let Wubi DL the file.

Go through the startup process again, get to the re-start, Windows starts, re-start again and start Unbuntu. The difference now, where HH went straight to its desktop, II goes to what I call the 'DOS' page with a "grub>" prompt on the command line (no quotes)

Maybe this not a bad thing...it's just that I don't know what command(s) to enter to continue the installation, as I don't 'think' Ubuntu has been installed yet. (I tried some things but apparently the DOS commands that I can remember from almost a couple of decades ago don't work in this!)

I did start over again and tried to install it to the C: drive just to see if it made any difference since that is where Win is installed; it didn't, same results.

I have now tried to install this on my second PC, no joy there either. Doesn't even make it to the DOS page. Flashes something quickly (think it's that BLD or something file name) and then hangs with a blinking cursor in the top left corner. Will try my laptop eventually too, I guess.

Any help, ideas, suggestions greatly appreciated.

---

### Post by linux_tech on 2009-01-01
you may want to try searching registry again for wubi and delete everything you find in that search
If you want to install clean, then search and delete all wubi files folders, and empty temp directory.
reboot then try install again

as alternative you can also set up a dual boot

---

### Post by abn91c on 2009-01-01
it the prompt something like this [COLOR="Red"]initramfs>[/COLOR]
or [COLOR="red"]ubuntu@ubuntu$>[/COLOR]
if its the second one did you try[COLOR="red"] startx[/COLOR]
By the way in Linux NO DOS COMMANDS will work and before you try Wubi again windows must be **defraged**

---

### Post by creek23 on 2009-01-01
> **abn91c said:**
> By the way in Linux NO DOS COMMANDS will work and before you try Wubi again windows must be **defraged**

With that, I suggest [Defraggler]("http://www.defraggler.com") -- not FOSS but it defrags faster than the default Window's program.

---

### Post by scudrunner on 2009-01-02
Thank you for trying, no luck so far.

To abn91c, the prompt is grub> that's it. None of the ones you mentioned.

I did degrag, I use Defraggler, but I keep my drives in good order and they or never over 1-2% fragged. Defragging didn't do anything. Besides, even if it was really fragged, it shouldn't prevent the program from installing, may make it slower than molasses but shouldn't keep it from running.

Also, as far as setting up dual booting, that is what Wubi does. (or is suppose to, my choice of starting XP or Ubuntu)

---

### Post by scudrunner on 2009-01-02
Thanks to everyone for trying, no luck so far.

To abn91c, the prompt is grub> that's it. None of the ones you mentioned.

I did degrag, I use Defraggler, but I keep my drives in good order and they or never over 1-2% fragged. Defragging didn't do anything. Besides, even if it was really fragged, it shouldn't prevent the program from installing, may make it slower than molasses but shouldn't keep it from running.

Also, as far as setting up dual booting, that is what Wubi does. (or is suppose to, my choice of starting XP or Ubuntu)

---

### Post by lakeyboyben on 2009-01-02
Hi there.. i did the same thing.. go into windows where you installed wubi and delete everything. also, go to your Master Boot Record in windows and delete the Ubuntu line... now.. go to WUBI.. install and just let it download ubuntu 8.10 and (DO NOT SPECIFY A FILE)... now this is done... restart your computer and when you reboot... ubuntu will be as good as new... i read a tutorial on it and basically, when you install a wubi installation, if you try to reinstall, any record of a previous installation will clash with it so it will not work correctly.

Hope this helps... if not, let me know and ill see if i can find the tut i used. :)

---

### Post by scudrunner on 2009-01-03
Thanks for the reply!

Two questions.....

> also, go to your Master Boot Record in windows and delete the Ubuntu line

How do I do this??? There is no MBR file. (or at least I couldn't find one)

Also,
> install and just let it download ubuntu 8.10 and (DO NOT SPECIFY A FILE)

Don't understand what you mean by a file...the only thing I can specify at the beginning of the installation is the drive to put it on. It automatically DLs the Ubuntu file based upon my system specifics which it determines on its own.

Thanks again. Would like to view the tut. if you can find it.

---

### Post by creek23 on 2009-01-03
> **scudrunner said:**
> > also, go to your Master Boot Record in windows and delete the Ubuntu line

How do I do this??? There is no MBR file. (or at least I couldn't find one) You have to run the Windows installer then choose **Repair**. Then type-in, **fixmbr**.

> **scudrunner said:**
> > install and just let it download ubuntu 8.10 and (DO NOT SPECIFY A FILE)

Don't understand what you mean by a file...the only thing I can specify at the beginning of the installation is [COLOR="Red"]the drive to put it on[/COLOR]. It automatically DLs the Ubuntu file based upon my system specifics which it determines on its own.

Can you post a screenshot of your WUBI installation screen? I'm thinking maybe it's trying to ask you where do put the file-to-be-downloaded.

---

### Post by scudrunner on 2009-01-03
creek23,

Thanks for the reply.

You and lakeyboyben are definitely on the right track!

>You have to run the Windows installer then choose Repair. Then type-in, fixmbr.

No, I found it, actually all you have to do is go into Startup & Recovery and you can edit boot.ini in Wordpad from there. But, there was nothing there to edit...everything was the way it should be.

I found that little Wubi bugger in another file, boot.ini.backup, which is where it must have been getting it. Opened it in Wordpad and took the Wubi line out, it was the last one.
(haven't tested this yet, and still have to clean the registry, probably not until tomorrow; grandson commandeered it to play online games)

As far as a screenshot, check out the first box in the first pic at the following link.
[http://www.dedoimedo.com/computers/wubi.html](http://www.dedoimedo.com/computers/wubi.html)
No talk of files, just choice of HD location for the Ubuntu program.

What I haven't decided is this: (and it may not make any difference now that the .ini file is clean)
1. DL Wubi, put it in my C:\Temp-Downloads folder, execute it, chose F: drive during the install and see what haappens, or...
2. Create an Ubuntu directory on the F: drive, DL Wubi to that, chose F: during install and see what happens...

Any suggestions as to which way would be the better way to start and I'm all ears. (errr....eyes!  :)

---


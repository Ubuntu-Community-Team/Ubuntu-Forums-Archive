---
title: "[SOLVED] How do I install Quake 3 Arena?"
date: 2008-05-19
forum: Gaming &amp; Leisure
---

### Post by Fazz Munkle on 2008-05-19
Backstory: Ok, I've been using Linux for the better part of 6 years now. But, BUT, I've only used the graphical part of Linux. Gnome, KDE, etc. Anything that was end-user friendly. I'll avoid using the CLI whenever possible. Especially when instructions aren't clear enough and I run into roadblocks. Often this happens when I'm asked to compile something and the instructions are obviously dated before the current release of the distro I'm using. I'll try the instructions to the best of my ability but scrap it when errors arise that I can't find a solution for. Oftentimes I'll abandon installing something and wait for a user friendly graphical installer for it to come out (in which case often means never).

I have absolutely no patience for incomplete and dated instructions for compiling programs from source. I come from a history of not using a CLI for my daily computing needs. I get the feeling that for some this is incomprehensible, but it's true. Remember, I'll avoid the CLI (ie: terminal) whenever possible. That is not to say that I haven't launched programs and installers from the CLI. The Loki Quake 2 installer was just a double click in Ubuntu 8.04 where then I clicked the Run button and it ran. I'd imagine that I'd just type ./quake2_3.21-r0.16.1-english.run in any other distro. That's fine. I can handle that. It's total automation without any Linux terms I'm assumed to know by the programmer.

Now, with that out of the way, with my level of compiling knowledge and impatience with incomplete (or Engrish) instructions is there an easy way to install ioquake3? I've tried other installers (the Loki installer, the official id installer) but I run up against various errors obviously because they're old installers and 8.04 has changed things. **I know 8.04 has changed things because I tried installing older Windows games like Starcraft through Crossover Games and WINE and keep getting errors which I'm explained, from searching Google, are security measures put into the latest Ubuntu that prevent malicious code from accessing some lower whatsiwhozit of memory. Ok, I'm fine with that. There's a workaround that apperently doesn't work on my computer because it's automatically changed back for some reason (I'm guessing more of the security thingamabobber put into 8.04), so I'll wait for updates to WINE and Crossover Games that deal with 8.04. So WINE based installs of Quake 3 Arena are out for now.** So I tried going with the only thing I've found that's up to date (ioquake3) and I'm running into problems. The only answers I get from searches in Google are RTFM. Great! Thanks! That freakin' helps a lot (no it doesn't). :roll: Double clicking on the x86.run file brings up the graphical installer but when it asks me for the CD (which is already in the drive) the Yes button just drops me back to the "put the CD in the drive" window. So I went online to look for answers, but I find that there's something wrong with the .pak files on the CD and I need to download some updated .pak files and do some compiling. Fine, I've followed directions before and compiled programs. So I try to follow the instructions for compiling this from svn (or whatever it's called, you know what I'm talking about), but I hit a roadblock I'm not completely sure I understand (yet apparently I'm expected to know :roll: ). There are no errors I can see yet nothing is done. So I give up. No results, no play.

My question is, is there an easier way to install Quake 3 Arena that doesn't involve advanced knowledge in Linux compiling that assumes you know what Linux vets are talking about? IE: graphical user interface installer like the Loki installers. That's it. That's my question. I figured all that text before would head off any RTFM BS from vets tired of the n00b influx to Linux. ;) And if you haven't guessed yet, I'm frustrated with all this.

Bolded: What's the deal on this? I can't install older Windows programs because of this (So long Oddworld: Abe's Oddysee. j/k Just needed an older game as an example). Has Canonical addressed this? If they have is there a news article I can read on it and people's reaction to it? I'm not sure what to look for on Google (what it's called what they did).

---

### Post by Fazz Munkle on 2008-05-19
Ah, found a more sane explanation of the WINE/Hardy problem:

[http://ubuntuforums.org/showthread.php?p=4799519](http://ubuntuforums.org/showthread.php?p=4799519)

I sure hope it gets ironed out.

---

### Post by Fazz Munkle on 2008-05-19
Ok, I found the solution. I still think there's something wrong with WINE/Hardy for older pre-98 games, but at least this works.

Here's the message I sent another member who wanted to know a way to install Q3A when the native installs didn't work. And surprise surprise surprise it's done with a WINE variant:

> What you have to do is:

Load up Wine if you don't have it already. I suggest CrossOver Games, but if you think you can configure Wine yourself that's fine. I installed Q3A through COG.

Then run the setup.exe file in the Quake3 folder in the QUAKE3 CD-ROM (ie: /media/cdrom0/Quake3/setup.exe). Don't run the setup.exe file in the root of the CD-ROM because that will kick you out of the installer, doing nothing for you.

From there it should bring up the Q3A installer window and you install Q3A like normal.

I'll be posting this in the topic I posted in the Games & Leisure forum.

If you try to install from the setup.exe file in the root of the CD-ROM you'll think that it's doing the same thing the other installers do. I've tried this trick with other games, but I run up against the WINE/Hardy security problem as explained in the link I posted. Though I'm willing to guess that it's mainly a problem with older games with older installers trying to access the lower mumbojumbothingawhozit in memory.

So it turns out that end user friendly native Q3A installation is going the way of the dodo, that is if the dodo were to be co-opted by God's programmers never to see a nature friendly recreation. ;) Then again Q3A is an old game. ;)

---

### Post by Awareness on 2008-08-14
I cant belive how easy it was...

It took me 5 mins just get the .run from here [http://ioquake3.org/get-it/](http://ioquake3.org/get-it/)
And then copy your pak0.pk3 from your quake3 cd or even some old installation... and voila... its working with sound and everything

Ive been using open arena... and tried several methods to install q3a in linux... but ioarena was just the solution i was looking for... :)

Ive not tried mods yet tho or my old settings but it seems it will work smoothly  :)

---

### Post by mitza on 2008-08-15
ioquake 3 installed in 5 min and in 15 sec i copyed the pack0.pk3 in the corect folder and voila quake 3 is running fine !! tank you for thi hint

---

### Post by mickeykool on 2008-09-15
Can't figure how to execute the run file?  I tried using "sh ioquake3-1.34-rc3.run" in the terminal screen but doesn't work. Btw I"m new to Linux world.

---

### Post by noerrorsfound on 2008-09-16
> **mickeykool said:**
> Can't figure how to execute the run file?  I tried using "sh ioquake3-1.34-rc3.run" in the terminal screen but doesn't work. Btw I"m new to Linux world.
"Doesn't work" isn't specific enough for us to help. Just taking a guess, make sure that you have changed directory (cd) to whatever folder the **run** file is located in. Also make sure it's executable (chmod +x ioquake3-1.34-rc3.run).

For better assistance please copy and paste the error message.

---

### Post by mickeykool on 2008-09-16
Thanks for the reply, I did what you told me as the file is on my desktop.  

mickeykool@mickeykool-desktop:~$ chmod +x ioquake3-1.34-rc3.run
chmod: cannot access `ioquake3-1.34-rc3.run': No such file or directory
mickeykool@mickeykool-desktop:~$

---

### Post by Perfect Storm on 2008-09-16
are you sure it's in the right directory?

---

### Post by mickeykool on 2008-09-16
First of all the error was on my end, wasn't in the correct directory. Now that I have executed the .run I now run into an error, "no write allow in user/games/ etc".  how do I allow the directory to become write privilege.

---

### Post by Perfect Storm on 2008-09-16
```
sudo sh ioquake3-1.34-rc3.run
```

Note: Do not launch the game directly from the installer window, you end up messing the permission of the game. Exit the installer, then launch.

---

### Post by mickeykool on 2008-09-17
Thanks for the help, now the last issue I'm having is that i can't seem to get my cd rom drive to mount but i can read the disc from it.  Anyway I tried copying pak0.pk3 in the game baseq directory, but i get an error saying permission declined.   How can I allow that to copy over?

---

### Post by Perfect Storm on 2008-09-17
```
sudo cp -r <path>/<file> <distination path>
```

---

### Post by safarj on 2008-11-17
Use [http://ioquake3.org/](http://ioquake3.org/). Works like charm. Install and copy datafiles. Thats all, folks!

---


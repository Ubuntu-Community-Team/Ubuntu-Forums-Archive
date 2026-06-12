---
title: "DO NOT BUY UNREAL ANTHOLOGY--NO Linux installer on disk"
date: 2007-02-17
forum: Gaming &amp; Leisure
---

### Post by alinuxfan on 2007-02-17
Damn box shows the penguin, but I have been scouring the web trying to find out how to install it, but there is no linux file on the disk.  It seems Midway didn't put them on the disk.  Supposedly there is a file I can download somehwere on the internet but I have yet to find it.

And I was looking forward to playing some ut2004 tonight

alinuxfan

---

### Post by alinuxfan on 2007-02-17
ok, I found this link to manually install...
[http://utforums.epicgames.com/showthread.php?t=558146]("http://utforums.epicgames.com/showthread.php?t=558146")

However, I am a little bewildered at all the stuff that needs to be done to get it installed!

Wish me luck!

---

### Post by Kelnoky on 2007-02-17
There's no luck involved. UT will run natively under Linux. You have to download a file and copy some stuff, run a command and that's it.

---

### Post by alinuxfan on 2007-02-17
Do you know where the file is?
There is no loki installer for the anthology DVD.  
Midway packaged the game using .cab files which is different from how it used to be done.

I found a manual install method that is supposed to work. (My previous post)

I will try it here in a bit

---

### Post by po0f on 2007-02-17
alinuxfan,

How did your manual install go?  I was thinking of picking up Anthology for myself.

---

### Post by alinuxfan on 2007-02-18
by building my own unshield for x86_64 and then using it to extract the cab files, I got to the point where I can now start it from the script but it crashes shortly after...still working on getting the game working...
something about 
```
/ut2004-bin-linux-amd64: munmap_chunk(): invalid pointer: 0x00000000052bb930 ***
Signal: SIGSEGV [segmentation fault]
Aborting.
```
Once I find a fix for that I hope I get it working then will post in more detail

alinuxfan

---

### Post by alinuxfan on 2007-02-18
bah, thought maybe I had done something wrong so I went back through the whole process
went to run and got

```
Xlib: unexpected async reply
```

Now I am back to the old error again with my screen and mouse messing up so that I have to ctrl+alt+backspace

hmm

---

### Post by buttons on 2007-03-12
This is kinda dredging an old thread but since there's been no mention of it anywhere on these forums I thought I'd post my results.

I bought the Unreal Anthology from gogamer for $15 figuring hey, cheap ut2k4 and I get linux support, too, right? Nope.  Even has tux on the box.  Bastards.

I followed the directions in this post: [http://utforums.epicgames.com/showthread.php?t=558146](http://utforums.epicgames.com/showthread.php?t=558146) which was mentioned earlier, and it DOES work.  You may need to scroll down a bit for mentions of what to do specifically for the anthology version, such as joining like-named folders.  Most of that info is in [this post]("http://utforums.epicgames.com/showpost.php?p=24730477&postcount=16").

The only time I diverged from the guide is in the addition of openal.so, which is at the bottom of my summary.

Summarized steps for clarity:
If you have AMD64, your unshield is broke, follow the directions there to unbroke it.
Copy the cabs over to a temp folder
Unpack cabs to your install folder
Delete temp cabs
rm -rf _* 1_* 2_* 3_* OCXFILES and the Launcher folder (kill everything that isn't ut2k4)
Remove 4_UT2004_ from every folder name
Join folders that sound alike into the proper names, e.g. the contents from Help and Help_English => Help... the contents from Sounds_English and Sounds_All => Sounds, etc
Once you've got the right directory structure (sans "directx," it isn't needed anyway) apply the patch
Copy libSDL-1.2.so.0 into your System directory
Add your CDKey

Now, the guide says to copy libopenal straight into your System directory and run the bin.  Well I did that on my up-to-date Edgy system, and instant segfault.  On a hunch, I deleted openal.so and tried again.  Voila! Game, no sound.

Following the directions by Shamanu [here in our forums]("http://ubuntuforums.org/showthread.php?t=366789"), I installed libopenalpp-cvs1, and copied the resulting libopenalpp.so.1.0.0 to my System directory as openal.so.

Note that you have to start the game from the System directory (or write a script to do so) or the game will complain about not being able to find any libs.

I'm a little annoyed with this process, hence the lack of a complete guide here.  However, for the brave and thrifty, this does work.

Hope that helps someone

---

### Post by ammiel on 2007-03-30
I got UT2k4 working fine from anthology following those directions, I did all the work in a 32-bit chroot environment then just moved to the /usr/local/bin outside of the chroot, works fine as long as i run in root otherwise I get an error about not being able to find Entry or something.

Also, Does anyone know how to get UT or Unreal working? (basically where I can find a patch with a linux executable in it)

---


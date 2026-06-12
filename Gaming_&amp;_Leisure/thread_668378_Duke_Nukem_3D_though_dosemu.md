---
title: "Duke Nukem 3D though dosemu?"
date: 2008-01-15
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2008-01-15
How do I setup dosemu to actually work with midi sound?Duke Nukem 3D works much faster with dosemu then dosbox but I can't get the music to work.I think I need actual midi support in Ubuntu but I can't get Timidity to work with dosemu.Any ideas,I've tried eduke and some of the other Duke nukem ports but the only thing I have got the game to work with so far is dosemu.Also is there a way to test to see if midi is working in Ubuntu because I may have midi sound working but may have miss configured dosemu some how.

Has anyone had any luck with any other port because I have not.

---

### Post by disturbedite on 2008-01-15
i could be wrong, but i think i remember reading that there was a linux port made.  so *if* that is the case, why emulate it when you can run it natively?

---

### Post by ChEeZeBaLL on 2008-01-15
> **disturbedite said:**
> i could be wrong, but i think i remember reading that there was a linux port made.  so *if* that is the case, why emulate it when you can run it natively?

That's correct. You can run Duke Nukem 3D natively in Linux using JonoF's JFDuke3D port.

[http://jonof.id.au/index.php?p=jfduke3d](http://jonof.id.au/index.php?p=jfduke3d)


here's another thread about getting the source port to work:

[http://ubuntuforums.org/showthread.php?t=187396&page=2](http://ubuntuforums.org/showthread.php?t=187396&page=2)

---

### Post by mister_k81 on 2008-01-15
> **ChEeZeBaLL said:**
> That's correct. You can run Duke Nukem 3D natively in Linux using JonoF's JFDuke3D port.

[http://jonof.id.au/index.php?p=jfduke3d](http://jonof.id.au/index.php?p=jfduke3d)


here's another thread about getting the source port to work:

[http://ubuntuforums.org/showthread.php?t=187396&page=2](http://ubuntuforums.org/showthread.php?t=187396&page=2)

JFDuke works well, but I would also suggest trying Eduke32, which is more up to date: 

[http://ny00123.sitesled.com/files.html](http://ny00123.sitesled.com/files.html) (there are a few deb packages if you scroll down)  

Also, if you're interested, there's a package of fan made high resolution textures and models that can be used with Eduke32 or JFduke: 

[http://hrp.duke4.net/download.php](http://hrp.duke4.net/download.php)

---

### Post by Dark Aspect on 2008-01-15
I tried eduke32............See my post about it here:

[http://ubuntuforums.org/showthread.php?t=627686]("http://ubuntuforums.org/showthread.php?t=627686")

I doubt JFDuke port will work any better but I'll give it a try.I don''t think eduke32 works on 64-bit Ubuntu.

---

### Post by Dark Aspect on 2008-01-15
Oh ok I see the deb files for the JFduke port now,I thought the deb files were only for eduke32 sry.Ok as usually it did not work heres the error:

> There was a problem initialising the Build engine: Failed to load TABLES.DAT!

---

### Post by mister_k81 on 2008-01-15
Hmm... I dunno if I can really help much, but I will take a few guesses. 

The TABLES.DAT is a file located in the duke3d.grp.. the file that contains all the games level, sound and graphics data. Did you rename the DUKE3D.GRP file to duke3d.grp? And is the GRP located in the '/usr/share/games/duke3d' directory? 

> **Dark Aspect said:**
> I tried eduke32............See my post about it here:

[http://ubuntuforums.org/showthread.php?t=627686]("http://ubuntuforums.org/showthread.php?t=627686")

I doubt JFDuke port will work any better but I'll give it a try.I don''t think eduke32 works on 64-bit Ubuntu.

Looking at that thread I noticed this: 

> Initialising SDL system interface (compiled with SDL version 1.2.11, DLL version 1.2.11)
Loading libGL.so
Failed loading OpenGL driver. GL modes will be unavailable.

Do you have your OpenGL video card drivers installed? 

And do you have the timidity midi sequencer installed? If not, you can find that in the repositories. Other than that, I dunno what it could be.

---

### Post by Dark Aspect on 2008-01-16
Yes I have my Nvidia drivers installed but I don't have the openGL runtime???Theres a package in the repositories that says openGL runtime but it wants to uninstall my nvidia driver and the ubuntu-desktop package.....wtf.Clearly I am not going to install that,its package name is libgl1-mesa-swx11.

I renamed the grp file to lower case letters but still no go,its the atomic  of duke nukem version 1.5 is that my problem?

EDIT:No wait I completely fixed my problem now....I Have high res Duke nukem 3d now WOOT.My problem was I am using 64-bit Ubuntu and I ran the deb files though getlibs so it looked for the libGL.so file in my lib32 folder not my user/lib folder.I fixed this by downloading the 32 bit Nvidia driver form packages.ubuntu and extracted the files with "ar xv somepackage.de".Then I just moved the files to my lib32 directory and boom it works.I probably fixed the problem with eduke too.the Failed to load TABLES.DAT error was I had the grp file in the wrong directory (home directory).Thanks for all the replies.

---

### Post by disturbedite on 2008-01-16
> **mister_k81 said:**
> JFDuke works well, but I would also suggest trying Eduke32, which is more up to date: 

[http://ny00123.sitesled.com/files.html](http://ny00123.sitesled.com/files.html) (there are a few deb packages if you scroll down)  

Also, if you're interested, there's a package of fan made high resolution textures and models that can be used with Eduke32 or JFduke: 

[http://hrp.duke4.net/download.php](http://hrp.duke4.net/download.php)
cool, thanks for that info.  now i just have to find my old DN3D CD somwhere in my collection of ancient discs!

---


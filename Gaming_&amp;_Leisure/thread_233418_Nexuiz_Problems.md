---
title: "Nexuiz Problems"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by JoshHendo on 2006-08-10
I have searched the forums and Google, but I can't seem to find a answer to this, or anyone else who has the same problem.

Ok, so my problem is that with Nexuiz 2...
[LIST]
[*]I can't quit. I try to quit, and I press yes when prompted, and then it freezes up. The only way out is to restart the computer.
[*]It is small in the screen. I know that this can be overcome by changing to a lower res, but that is just annoying. In Windows it does that auto and then changes back (I don't like comparing Ubuntu to Windows, but I tried it in Windows and that is the way that it does it).
[/LIST]

Those are the only problems that I have. These problems did not happen in 1.5, which is why I said 2 above.

Any help with this would be great :)!

---

### Post by darkchron on 2006-08-11
i have the same problem, is there any ? ](*,)

---

### Post by DoktorSeven on 2006-08-11
When it freezes, can you hit CTRL+ALT+F2 to get to a terminal, then login and kill the offending process? (ps aux to view processes, killall -9 [name of program] to end it)  CTRL-ALT-F7 gets back to X afterwards.  

Or as a quick escape (and this will kill X and all programs you're running), CTRL-ALT-backspace (not delete)?

Not sure what you mean by "small in the screen".

---

### Post by JoshHendo on 2006-08-12
Small in the screen... meaning it doesn't take up the entire screen.

---

### Post by sharperguy on 2006-08-12
I also had the small screen problem and the game is juttery, but i can exit fine, I think it is to do with XGL

---

### Post by MaximB on 2006-08-12
what ?!
there is Nexuiz 2 ???
were ???
I've searched the net and did not find it 
were ?were ? were ?

---

### Post by MaximB on 2006-08-12
aaaaaaa.........it's just version 2....damn
I already have it.
I got no problems att all with it
it runs perfectly on my ubuntu !

---

### Post by mihaiv on 2008-11-04
In my case Nexuiz freezes up on exit if I use the fglrx driver. If I use the default open source driver I can exit but it randomly freezes while playing the game. This problem came with 8.10. I haven't had it in 8.04.

---

### Post by alanwalterthomas on 2008-12-01
No one's found a solution to this in 2 years??
My Nexuiz hangs on exit & the only way out is the reset button, but at least while playing there are no issues & it runs in full screen.
NO - Ctrl+Alt+Backspace does nothing
NO - I cannot access a tty to kill the process
The system becomes so unresponsive that I can't even turn Num Lock on or off.

8.04. Effects are disabled. ATI 4670 with Catalyst 8.10.

Thanks for any help

---

### Post by KingHanco on 2008-12-01
Try Ubuntu 8.10 and see it hang from there. I have found no problem at my end.

---

### Post by detrate on 2008-12-03
If you're using Nexuiz from the official package repo, it may not be up to date and I'm not even sure if it includes both sdl and glx versions.  Depending on your hardware, either sdl or glx may run better.

I recommend downloading a fresh copy from [source forge](http://downloads.sourceforge.net/nexuiz/nexuiz-242.zip) and testing the difference between nexuiz-glx and nexuiz-sdl to see if that solves anything.

I've never heard of the computer becoming unresponsive but just in case it's not TOTALLY so, F10 is the quit hot key.  You may want to say something in the [Nexuiz Support and bugs forum](http://alientrap.org/forum/viewforum.php?f=3).

---

### Post by jenkinbr on 2008-12-03
I personally prefer the sourceforge version.  I noticed in Ubuntu 8.04 that the repos used Nexuiz v.2.4, when 2.4.2 was out.

This unfortunatly, has to do with the package maintainers not dealing with version upgrades in favor of a more stable system.  Applying that to nexuiz (and other multiplayer games is rather unfortunate and silly, when *all* the servers upgrade as soon as the new release is issued and often the server and client require the same version.

---

### Post by jhansonxi on 2009-03-06
I have found that Quake-based games including Alien Arena, Nexuiz, and Open Arena will hang on exit and during video resolution changes if another application is using the audio device (like TeamSpeak).

---


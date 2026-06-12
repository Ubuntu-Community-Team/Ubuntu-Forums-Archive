---
title: "Starcraft Won't Read CD!"
date: 2006-09-16
forum: Gaming &amp; Leisure
---

### Post by Lazar on 2006-09-16
I've looked around on the net for the answer to this problem, and found that a lot of people have gone through it, but I never really found an answer.  I installed Starcraft and Starcraft: Broodwar and am trying to get to load it through Wine, but it won't read the CD.  I get the same error you'd get if you didn't have the cd in and tried loading Starcraft.

I've heard a crack could solve this, but I was wondering if there was any way to solve this without using a crack.  I've been told that Cedega would run it, but I also heard that you have to pay to get it, so I really don't want to do that.  If someone could help me out with this that would be great!:lol:

---

### Post by Oxin on 2006-09-16
When I was trying to install D2;LOD with wine I ran into the same problem and I found that I needed to run winecfg and had to make sure that the cd mount directory it used was the one I used to mount. For example: wine was trying to use /cdrom but my cd mount directory was /cdrom0

Hope that helps some.

---

### Post by voidvector on 2006-09-16
StarCraft doesn't have copy protection. Most likely, so you need to go into "winecfg" and change the CD mount point to CD (not auto). I can assure you StarCraft runs on Wine, I just did it myself last night. 

Diablo 2 has copy protection, so the only solution would be no-cd patch.

---

### Post by Lazar on 2006-09-17
> StarCraft doesn't have copy protection. Most likely, so you need to go into "winecfg" and change the CD mount point to CD (not auto).

I'm not sure what you mean.  In the "Drives" tab I have the E: drive labelled as my CD ROM drive.  It goes to the cdrom0 directory, so that's not a problem.  Also, the "type" was originally set to Local Hard Disk.  I changed that to CD ROM drive and it didn't work still.  I'm not sure what the problem is.:(

---

### Post by Lazar on 2006-09-17
Is anyone able to help me with this?  It's driving me nuts!

---

### Post by inverarity on 2006-09-25
Hey all: I just installed wine using apt, and got starcraft working in a couple seconds.  My first move was to try ```
wine starcraft.exe
``` immediately but that generated the no-cd error.  After reading this forum I was able to put together the pieces and did the following:

1. Run winecfg (I ran it from my home directory, not sure if this matters)
2. Go to the "Drives" tab

Now, when I first did this, the default config only defined the C: and Z: drives.  Obviously this isn't right, so I tried:

3. Press the "Autodetect" button.

This looked like it worked, because 3 new drives showed up in the list, a D: drive, mapped to /media/windows (my windows partition), an E: drive mapped to /media/cdrom0 (so far so good...) and an H: drive mapped to my home directory.  I thought that I was done at this point because it looks as if it had autodetected the drive, however based upon voidvector's post I realized there's one more step necessary.  Still inside the "Drives" tab in winecfg try the following:

4. Press the "Show Advanced" button
5. Select the cdrom drive from the list at the top of the window (in my case this was the one autodetected & set to the E: drive.)
6. In the "Type:" drop down menu that appeared after clicking the "Show Advanced" button, set the type to "CD-ROM".
7. Hit "Apply" and exit winecfg.  I assume hitting "OK" does the same thing.

After this I'm able to run Starcraft in wine.  Since I just got it working about five minutes ago, I haven't played a game yet, but just running through the menus & the intro to a single player game it seemed quite a bit more responsive and snappy than it does when I run it natively under windows.  So I can't promise that this will make starcraft run well once the game starts, but at least it should help fix the no cd error.

As a final addendum, I copied the Starcraft folder from my windows partition onto my ubuntu Desktop, so I'm not sure if that makes any difference compared to running it straight off the windows partition.

Hope it helps.

---


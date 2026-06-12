---
title: "Burning Crusade upgrade in Linux!"
date: 2007-01-16
forum: Gaming &amp; Leisure
---

### Post by toupeiro on 2007-01-16
I did this in ubuntu edgy, but it is most likely cross distro compatible.  If you have wow installed and working you have done the hardest part.  I will briefly cover the steps I took to get the expansion working in Linux.


1.  Create a directory and drop the contents of the CD's into the directory.

2.  execute installer.exe through wine, perform the online account upgrade.

3.  After upgrade is complete, exit out, (Do not start the game yet) and change winecfg settings to NT4.0

4.  execute WoW.exe through wine and let it auto-update. (159MB patch required)

5.  execute WoW.exe again through wine and let it auto-update (2.82MB patch required)

6.  change winecfg settings back to win98, and enjoy!

For me, it was seriously this easy.  Enjoy the long awaited Burning Crusade expansion in Linux!

---

### Post by zdotz on 2007-01-16
Great to hear!

Thank you for being so timely with this information.

---

### Post by toupeiro on 2007-01-16
No Problem.  Just knocked out the first couple of quests before I head to bed.  Runs beautifully!

---

### Post by willskills on 2007-01-16
Indeed it does, I actually got home late from work, and my flatmate had already installed & patched - I just whipped his client over the network and bingo - TBC! 

Runs like a greased baby thrown down a slide - just we had support for all the extra glow effects :/

---

### Post by toupeiro on 2007-01-16
It could be my imagination, but I went ahead and linked this installation into Cedega, and started playing with some of the render and video options and I could swear it made a difference, but the only way I will know for sure is when I install it in Windows :P

---

### Post by willskills on 2007-01-16
I use wine..... and they don't; yet!

---

### Post by Elvish Legion on 2007-01-16
Anyone know online stores that will send you the key? I was planning to pick it up today, but Austin is shut down due ot weather...

---

### Post by willskills on 2007-01-16
I don't beilve there are any doing so in Europe - pretty sure that is against the law in some way.

Might be different your side of the pond mind you...

---

### Post by justin whitaker on 2007-01-16
> **Elvish Legion said:**
> Anyone know online stores that will send you the key? I was planning to pick it up today, but Austin is shut down due ot weather...

I haven't seen any. You were able to purchase a key after your 14day trial ended...I doubt they are allowing that at this point.

---

### Post by Poka64 on 2007-01-16
> **toupeiro said:**
> 
1.  Create a directory and drop the contents of the CD's into the directory.


Do I copy all the contents from all the CDs to the same folder or do I have to have seperate folders for each CD?

---

### Post by hikaricore on 2007-01-16
> **Poka64 said:**
> Do I copy all the contents from all the CDs to the same folder or do I have to have seperate folders for each CD?

Should probably be all in the same folder, different folders will just not work for the installationg process.  The IMPORTANT files will have different files names, random unimportant files like autorun.inf can just we overwritten as you go.  :)

---

### Post by rj686 on 2007-01-16
Worked fine with me, just from the cd, actually didn't work when i copied to the computer lol

---

### Post by rj686 on 2007-01-16
WHen using cedega though it crashes at log-in :(

---

### Post by Z3n0s on 2007-01-17
> toupeiro-It could be my imagination, but I went ahead and linked this installation into Cedega, and started playing with some of the render and video options and I could swear it made a difference, but the only way I will know for sure is when I install it in Windows :P

I just upgraded under Cedega and I have to admit it looks much better. Their is a noticeable difference. :mrgreen:

---

### Post by cgrenier on 2007-01-27
The original game works fine, but when running Installer.exe after I've copied all the disc contents, I get the error "No installer data could be found. If this problem persists, please contact Blizzard Technical Support."  What should I do?

---

### Post by Naegling23 on 2007-01-28
why are you bothering to copy the cd images?

I installed the game by just clicking on the install.exe file.....or maybe I did it by going to the cd's directory and typing wine install.exe, I cant remember.  Anyway, when it asks for a new cd, just enter wine eject into a terminal and stick the next one in.  Its a lot easier then copying everything, then installing it.  Burning crusade installed just like it would in windows.

---

### Post by cgrenier on 2007-01-28
My cd-rom drive has big issues in Ubuntu for some reason, so I had to grab the ISOs from 'another source' (I did buy the game of course, I have already upgraded my account from another machine running windows).  So I copied the contents of the ISOs into one folder, but wine gives me that error.  Given that I cannot use my cd-rom drive, is there anything I can do?

---

### Post by windowskilla on 2008-06-29
> **cgrenier said:**
> My cd-rom drive has big issues in Ubuntu for some reason, so I had to grab the ISOs from 'another source' (I did buy the game of course, I have already upgraded my account from another machine running windows).  So I copied the contents of the ISOs into one folder, but wine gives me that error.  Given that I cannot use my cd-rom drive, is there anything I can do?

You should be able to mount the ISOs one at a time and install it from the mounted images.

---


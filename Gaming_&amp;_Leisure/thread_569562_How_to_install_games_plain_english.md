---
title: "How to install games plain english"
date: 2007-10-07
forum: Gaming &amp; Leisure
---

### Post by dark-insignia on 2007-10-07
hi im a relative 'noob' to this whole ubuntu thing and i want to be able to play my old games such as age of empires.

i have ,so far, installed wine using the synaptic package manager.

can someone tell me in plain english how to install and play it step-by-step.

would be much appreciated.

---

### Post by Cannaregio on 2007-10-07
Have a look [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795")

And scroll down and head this:
```
After getting everything installed using wine 0.9.33 ( 
copied mfc42.dll to windows/system32/, 
copy all CDs content to /home/patrick/aoe3, 
changing the D: drive in winecfg to /home/patrick/aoe3, 
cd-ing to /home/patrick/aoe3 in terminal, 
THEN typing wine setup.exe
```

Wine is working better and better. Gutsy beta and the new nvidia drivers also help a lot.
I managed today to have trainz's "[JTTrainDriver]("http://www.gamespot.com/pc/sim/traindriver/index.html")" running through wine BETTER than in my windows xp partition :-)

---

### Post by TidusBlade on 2007-10-07
You could use Cedega, I would imagine it's much simpler but it's not free...
Using WINE, I think you can install it by running the setup.exe found in the CD assuming your talking about AoE 1... I dunno much, but seeing that it worked once for me, you can try that ;)
EDIT: Cannaregio posted something that should work perfectly so no point of this post now :P

---

### Post by dark-insignia on 2007-10-07
After getting everything installed using wine 0.9.33 ( 
copied mfc42.dll to windows/system32/, 
copy all CDs content to /home/patrick/aoe3, 
changing the D: drive in winecfg to /home/patrick/aoe3, 
cd-ing to /home/patrick/aoe3 in terminal, 
THEN typing wine setup.exe

huh? how do you copy it?

sorry i'm really dense and this probably should be in another section but huh?

---

### Post by Cannaregio on 2007-10-08
> **dark-insignia said:**
> After getting everything installed using wine 0.9.33 ( 
copied mfc42.dll to windows/system32/, 
copy all CDs content to /home/patrick/aoe3, 
changing the D: drive in winecfg to /home/patrick/aoe3, 
cd-ing to /home/patrick/aoe3 in terminal, 
THEN typing wine setup.exe

huh? how do you copy it?

sorry i'm really dense and this probably should be in another section but huh?


The list is just intended as a guide.
Basically:
You copy all CD content from the CD directly to a new folder ao3 in your home directory.
You copy mgc42.dll from your windows partition (or from another windows box) to any usb stick or external hard disk.
You copy the dll from the stick or disk to your own .wine subdirectory, in the virtual system32 folder:
[COLOR="Blue"]~/.wine/drive_c/windows/system32$ [/COLOR]
BECAUSE wine has created a virtual "c: drive" inside your home/user folder, explore it
then cd to your new aoe3 folder
and run wine setup.exe

---


---
title: "doom and wolfenstein???"
date: 2006-11-23
forum: Gaming &amp; Leisure
---

### Post by crashtestway on 2006-11-23
i am a new ubuntu user and want to get doom and wolfenstein for my pc where can i t get them and can i run them on linux???:mrgreen: also i wanted some more games what well run on ubuntu???

p.s. be easy on me i am new and clueless:KS

---

### Post by PartisanEntity on 2006-11-23
Hello and welcome,

I am new too, I have seen quite a few threads about the two games you mentioned as well as others. I don't have direct links, but if you check out the search feature you should find more than enough threads with info.

:)

---

### Post by mediax on 2006-11-23
Have a look in the Gaming and Leisure forum.

---

### Post by taurus on 2006-11-23
Move to Gaming & Leisure.

---

### Post by tocleora on 2006-11-23
I've gotten the Wolfenstein 3D demo working in either Dosbox or Dosemu before, I can't remember which one (I think dosbox).  I want to say something *was* different, but overall playable.  To get those:

sudo apt-get install dosbox
sudo apt-get install dosemu

Although these instructions are for Windows, it gives you an idea of what is involved in getting it working. I'll try to set it up again here in a few minutes if you don't have a response by then on how to do it I'll post more specific instructions:

[http://www.wolf3d.co.uk/board/read_msg.php?msgid=000339]("http://www.wolf3d.co.uk/board/read_msg.php?msgid=000339")

---

### Post by tocleora on 2006-11-23
Hmmm, I was faster than I thought I was gonna be! ;)

1. Create a folder called "dosbox" in your home directory.
/home/username/dosbox where username is your username.

2. Download 1wolf14.zip from [http://www.wolf3d.co.uk/downloads/](http://www.wolf3d.co.uk/downloads/).  Extract in /home/username/dosbox

3. download and install dosbox: sudo apt-get install dosbox

4. start dosbox: dosbox

5. mount the dosbox folder as your c drive: mount c /home/username/dosbox

6. Run install.bat

7. run wolf3d.exe

EDIT: I just realized you may be talking the newer versions. :)  Yeah there are plenty of threads on the new Wolfenstein, I'm sure there are threads on the new Doom too.  But in case anyone wants the classic Wolfenstein, there are the instructions...

---

### Post by findus on 2006-11-23
Return to Castle Wolfenstein also runs very well using Wine.  Just run the setup.exe on the CD with Wine and you should be away!  Doom 3 also runs, but i think it is a bit more complicated in that there is a linux version that uses the Windows CD from wht I remember.

---

### Post by tocleora on 2006-11-23
Classic Doom Demo installed very close to the way Wolfenstein installed, there were a few differences, I selected gravis as my sound card, the effects were there but not the music.  And I had to press Ctrl+F12 to speed it up as it was pretty slow.  I still didn't get it to perfect speed but didn't try very hard. :)  You can get the Doom Demo download here:

[http://www.doomwadstation.com/doom_reviews/doom19s.zip]("http://www.doomwadstation.com/doom_reviews/doom19s.zip")

---

### Post by CatKiller on 2006-11-25
You can run RtCW natively - you only need to install it in Wine to get at the .pk3 files. The install script can't do that for some reason. I think you get it from the id FTP site, but it's been a while.

---

### Post by dmn_clown on 2006-11-25
> **tocleora said:**
> Hmmm, I was faster than I thought I was gonna be! ;)

1. Create a folder called "dosbox" in your home directory.
/home/username/dosbox where username is your username.

2. Download 1wolf14.zip from [http://www.wolf3d.co.uk/downloads/](http://www.wolf3d.co.uk/downloads/).  Extract in /home/username/dosbox

3. download and install dosbox: sudo apt-get install dosbox

4. start dosbox: dosbox

5. mount the dosbox folder as your c drive: mount c /home/username/dosbox

6. Run install.bat

7. run wolf3d.exe

EDIT: I just realized you may be talking the newer versions. :)  Yeah there are plenty of threads on the new Wolfenstein, I'm sure there are threads on the new Doom too.  But in case anyone wants the classic Wolfenstein, there are the instructions...

Or you can just go [here]("http://icculus.org/wolf3d/") and choose your dead project poison ;)

---


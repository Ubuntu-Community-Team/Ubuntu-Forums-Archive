---
title: "there is no substitute"
date: 2008-05-25
forum: Gaming &amp; Leisure
---

### Post by zfolwick on 2008-05-25
I want to play X-com in Gutsy.  I *need* to play x-com.  It's my reason for existing in this crazy world.  

So I found a version and downloaded x-com, and then dosemu-1.4.0.  Now my question is. . . how the hell do I get dos programs to run in my dos emulator?

Thanks,

linux gnoob

---

### Post by Sammi on 2008-05-25
Substitute: [FONT=Arial][SIZE=2]**[UFO Alien Invasion]("http://www.getdeb.net/app/UFO+Alien+Invasion") **[/SIZE][/FONT]

[http://www.getdeb.net/release.php?id=1947](http://www.getdeb.net/release.php?id=1947)
[http://ufoai.sourceforge.net/](http://ufoai.sourceforge.net/)

hehehehe ;)

---

### Post by zfolwick on 2008-05-25
that's a big negatron megatron!

---

### Post by Perfect Storm on 2008-05-25
[UFO 2000](http://gaming.gwos.org/doku.php/games:alphabetical:u:ufo2000) - might be something

---

### Post by zfolwick on 2008-05-25
perhaps I'm not clear.. .  I have the original xcom installed, however I don't know how to access it from the dos prompt.  right now it's sitting in a folder in ubuntu, but I need to get dos to talk to linux. . .  how would you do that?

Also. . . right now I seem to only be able to access dosemu from the command line.  ideas?

---

### Post by RIchard James13 on 2008-05-25
X-COM I used to play this heaps in dosbox. Lets see if I remember the right command. In the xcom directory type ufocd. At least that is the right command for my install. If in doubt type dir *.bat then *.com then *.exe one of the resulting files should be ufosomething. Execute that file.

---

### Post by zfolwick on 2008-05-25
erm . . . where's the ufo directory?  Here's where I'm at right now:

C:\> __


that's pretty much where I am.


** note:  DOSemu was found in applications > system tools


****THE REAL QUESTION****

is how do I get *any* programs to run under dosemu?

---

### Post by meborc on 2008-05-25
you need to mount the dir where the game is located to the dosbox 

a simple "howto play dosbox games ubuntu" google search gave me this - [http://blog.mypapit.net/2007/05/dosbox-how-to-play-dos-games-in-ubuntu-linux.html](http://blog.mypapit.net/2007/05/dosbox-how-to-play-dos-games-in-ubuntu-linux.html)

;)

---

### Post by Sammi on 2008-05-25
I have absolutely no experience with DOSEmu. And I doubt there are others here who have.

Most people use Dosbox. It's easier to use.

---

### Post by zfolwick on 2008-05-25
alright so I caved and installed dosbox.  Fine you're right it is much awesomer.  However, now it's saying that the program can't be run in Dos.   I mounted the folder as:

mount c ~/ufogold

and changed to C: then did dir/w

I saw the .exe file named ufodef~1.exe

I just typed that into the cmd line and it said that it can't be run in dos.

am I missing something?

---

### Post by B0rsuk on 2008-05-25
[http://www.dosbox.com/comp_list.php?showID=239&letter=X](http://www.dosbox.com/comp_list.php?showID=239&letter=X)

---

### Post by DirtDawg on 2008-05-25
> **zfolwick said:**
> alright so I caved and installed dosbox.  Fine you're right it is much awesomer.  However, now it's saying that the program can't be run in Dos.   I mounted the folder as:

mount c ~/ufogold

and changed to C: then did dir/w

I saw the .exe file named ufodef~1.exe

I just typed that into the cmd line and it said that it can't be run in dos.

am I missing something?

Hey. My copy of the game has a file called UFO.BAT that runs the game perfectly with dosbox. It sounds like you have a version packaged specifically for modern Windows(XP). You could try using [wine]("https://help.ubuntu.com/community/Wine"). If that doesn't work, maybe you can get your hands on a version that includes the UFO.BAT file.

---

### Post by zfolwick on 2008-05-25
"This program cannot be run in DOS mode"

---

### Post by DirtDawg on 2008-05-25
> **zfolwick said:**
> "This program cannot be run in DOS mode"

I assume this post is meant to be addressed to me. Please try to be clear as it helps the volunteers here help you. 

Let me try explaining this another way. The version of UFO that you are running, "UFO Gold", has been packaged for Windows XP. If you want to run that version, you will need to try wine. If I remember correctly, I tried that a couple years ago and it did not work (in fact, according to the [Wine Database]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4011"), it will probably still not work). 

So, you will need to get your hands on a copy of the game that runs under Dos, then use Dosbox to run it with the UFO.BAT file. I understand that's not ideal, but I think it's your only course of action short of booting into Windows when you want to play.

EDIT: Looks like the last time someone tried to run the game with Wine was [under Gutsy]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6007"). You may want to give it another go. It *might* work.

---

### Post by zfolwick on 2008-05-25
I m so sad. . . :-(

I don't have windows!

---

### Post by zfolwick on 2008-05-25
thought you'd like to know that I got it to run, however it's somewhat unstable right now and there's no sound. . .

---


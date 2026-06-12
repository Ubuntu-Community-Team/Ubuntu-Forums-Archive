---
title: "Quake 4 problem"
date: 2006-06-28
forum: Gaming &amp; Leisure
---

### Post by underworld288 on 2006-06-28
I download the linux version of Quake 4 and installed it but when I go to launch it from the terminal it says "Sys_Error: Couldn't load default.cfg  -  Check your working folder.", can anyone help me I want to play Quake 4.

---

### Post by digimars on 2006-06-28
You are sure that you copied all of the pk4 files from your cd that you were supposed to ( pak000.pk4 - pak018.pk4 ) without overriding the ones that the Linux installer placed there?  It sounds like it is missing one.

---

### Post by crane on 2006-06-28
Also, check your ~/.quake4 folder. Make sure no part of it is owned by root.
How did you install? Sudo or as user?
If nothing is working you could just create a blank file labeled default.cfg and try that.

---

### Post by underworld288 on 2006-06-29
ok, i messed up the whole thing because i installed it as root and i didn't copy any files from my quake 4 disc. where do i put the .pk4 files that i extract?

---

### Post by crane on 2006-06-29
[QUOTE=underworld288]ok, i messed up the whole thing because i installed it as root and i didn't copy any files from my quake 4 disc. where do i put the .pk4 files that i extract?[/QUOTE]
Look here,
[http://zerowing.idsoftware.com/linux/quake4/]("http://zerowing.idsoftware.com/linux/quake4/")
That should give you an idea what files to get and some other help.
The pk file need to be put in 
/usr/local/games/quake4/q4base

Good Luck!

---

### Post by Hg80 on 2006-06-29
after installing patch 1.2 my game runs once then on restarting the game i get the first screen then it crashes to the desktop and kills the mouse, anyone know what this is? Using 64bit 6.06

---

### Post by underworld288 on 2006-06-29
ok since i installed for root i there a way i can uninstall the game and start over?

---

### Post by crane on 2006-06-29
[QUOTE=underworld288]ok since i installed for root i there a way i can uninstall the game and start over?[/QUOTE]
Just because you installed as just is not a problem. When you run the game as a user it will create a file in your home directory called .quake4 (hidden file)
That is where you can add configs maps and what not.
Just be sure to copy the files from CD to /usr/local/games/quake4/q4base.
If you are not sure of how to do this from terminal just type:
sudo nautilus in the terminal. Then you will be able to copy the file using graphical interface.
 Once you done coping files you should close nautilus so you don't accidently move something else as root.

 The great thing about this is if you play the game and add files and tweaks, then screw up something you can just delet the .quake4 file in you home directory and Boom, back to a stock install of quake4.

Good Luck.

---

### Post by crane on 2006-06-29
[QUOTE=Hg80]after installing patch 1.2 my game runs once then on restarting the game i get the first screen then it crashes to the desktop and kills the mouse, anyone know what this is? Using 64bit 6.06[/QUOTE]
Try running it from terminal. then when it crashes, you will be able to see what errored out.If you still need help post the errors listed.

---

### Post by underworld288 on 2006-06-29
thanks guys that worked i can finally play Quake 4, although i have another question is there any other installers (like this one) for any other of the newer games?

---

### Post by underworld288 on 2006-06-29
i also have no sound, well acually i have no sound for the peaple talking (i can hear the gun and music).

---

### Post by crane on 2006-06-29
Voice chat does not work for quake4 in linux.

---

### Post by underworld288 on 2006-06-29
i was talking about the AI in the game when they talk I cant hear what they are saying.

---

### Post by crane on 2006-06-29
I had the same problem a while back, but I'll be darned if I can remember the fix.
What sound card do you have. I was running an audigy. 
I would try reinstalling patch, also double check and make sure you have copied All the pak files required from the CD.

---

### Post by underworld288 on 2006-06-30
i dont have a sound card i have intergrated sound, Realtek ALC850 w/8 Channels. And I am positive that I installed all of the packages, I guess I will reinstall the patch.

---


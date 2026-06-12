---
title: "Problem with Quake III"
date: 2004-10-28
forum: Gaming &amp; Leisure
---

### Post by Neo40 on 2004-10-28
Hi,

I have installed Quake III (binary for linux) without problem. I can play it but when I exit the game, Ubuntu kicks me out of my session and I'm  to the login screen. Any idea how to solve this problem?

Thanks

---

### Post by mrf on 2004-10-28
I had this exact problem too. I think it happens because you've used the gnome resolution applet thing to select a resolution, and then quake 3 has changed it to another resolution. When you exit out of the game the X doesnt return to the desktop's resolution and if you move the mouse it crashes, dumping you to the gdm screen.

What I did to fix it was undo the selecting of the resolution with the gnome applet, then editted XF86Config removing the modes I dont use, and adding modelines to force it to use 1152x864@85 on the desktop and 800x600@125hz in quake3. Now when I exit q3 it returns to 1152x864 without crashing.

---

### Post by Neo40 on 2004-10-28
[QUOTE=mrf]I had this exact problem too. I think it happens because you've used the gnome resolution applet thing to select a resolution, and then quake 3 has changed it to another resolution. When you exit out of the game the X doesnt return to the desktop's resolution and if you move the mouse it crashes, dumping you to the gdm screen.

What I did to fix it was undo the selecting of the resolution with the gnome applet, then editted XF86Config removing the modes I dont use, and adding modelines to force it to use 1152x864@85 on the desktop and 800x600@125hz in quake3. Now when I exit q3 it returns to 1152x864 without crashing.[/QUOTE]


Thanks for your reply! But I don't understand  what you did exactly. Could you show me your Section "Screen". I use too 1152x864 for my desktop and 800x600 when I play Quake3.

---

### Post by adbak on 2004-10-28
Where can I get me some of this Quake 3?

---

### Post by mrf on 2004-10-28
I'm not at my ubuntu machine at the mo (home/work)... I'll post the screen section when I get home in a few hours. You should be able to see the "Modes" line in the screen section thou, its should look sometime like : "1600x1200" "1280x1024" "1152x864"... etc . If you  remove the resolutions you dont want it should default to the first one you leave behind.

---

### Post by mrf on 2004-10-29
If its any help : 

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Monitor 	"PF790"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "800x600" 
	EndSubSection
EndSection

I only want 24bit 1152 and 800. so meh, works for me.

---

### Post by crashd on 2004-10-29
in that way you are successful to install it?  to me from problems of permissions
thanks

---

### Post by fng on 2004-10-29
[QUOTE=adbak]Where can I get me some of this Quake 3?[/QUOTE]

Quake3 isnt in apt :/

You can download the install-binary from id software's ftp : [ftp://ftp.idsoftware.com](ftp://ftp.idsoftware.com).
The file is called linuxq3apoint-1.32b-3.x86.run and can be found in the idstuff/quake3/linux directory.

after download: chmod 755 linuxq3apoint-1.32b-3.x86.run.
Now run the install program wth sudo: sudo ./linuxq3apoint-1.32b-3.x86.run
Change the instalation path to /usr/share/games
Change thw symbolic links path to /usr/games
Check all the 4 checkboxes :) (they are allready checked)

After the installation, copy the pak0.pk3 from the cd or another quake3 installation into /usr/share/games/quake3/baseq3/

then start quake3 by the comand : quake3 

enjoy! :)

---

### Post by Viktor Machek on 2005-02-09
Hi,

I followed your installation manual about Quake. Everythink seems ok. I  moved pak0.pk3 from my win demo folder ti usr/share/games... like you. After start quake3 I got this message:

Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/viktor/.q3a/baseq3
/usr/share/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/share/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/share/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/share/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/share/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/share/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/share/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/share/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/share/games/quake3/baseq3/pak0.pk3 (1387 files)
/usr/share/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
1921 files in pk3 files

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/viktor/.q3a/demota
/usr/share/games/quake3/demota
./quake3.x86/demota

----------------------
1921 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg


May I have to copy some other files to adequatelly folders?

Could you help me?

Thanks

Viktor

---

### Post by kamstrup on 2005-02-09
You need the pk3 files from your *original* quake 3 game. Make sure you have path_to_q3a/baseq3/pak0.pk3 . If not you can find it on your quake 3 cd.

---

### Post by Viktor Machek on 2005-02-09
Yes I did it. I moved pak0.pk3 to the folder /usr/share/games/quake3/baseq3/ like user FNG first.

Nothing happenes, so I wrote a question here...

Anybody could help me?

Viktor

---

### Post by kamstrup on 2005-02-10
Assuming you moved the file as root. - Did you make sure that ordinary users have read-rights to it? "sudo chmod a+r  /usr/share/games/quake3/baseq3/pak0.pk3" ought to do it.

My pak-file is called PAK0.pk3 (notice the big letters...) I don't know if quake bothers about letter casing, but you might try renaming it to this, if the above doesn't work.

---

### Post by Viktor Machek on 2005-02-11
Ok.

I will check it all again.

Thank you!!

V.

---

### Post by fakie_flip on 2006-11-06
I'm confused about what everyone is saying. It seems that all of the package files are needed, so why are some saying that pak0.pk3 is needed when we need them all?

---

### Post by mrf on 2006-11-06
The pak0.pk3 is the 457 megabyte file you have to copy off the q3 cd. All the other files are created by the linuxq3apoint-1.32b-3.x86.run script.

---


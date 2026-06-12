---
title: "quake3"
date: 2005-05-15
forum: Gaming &amp; Leisure
---

### Post by ultima2k on 2005-05-15
I downloaded some pointrelease for Quake3:
[ftp://ftp.idsoftware.com/idstuff/quake3/linux/](ftp://ftp.idsoftware.com/idstuff/quake3/linux/)

I have copied pak0.pk3 into the baseq3-folder, but when I try to start the game it's just a black screen and you can se some of the desktop.

I think you have to do some stuff with the graphics..

Need help....

(I've got a 6800LE)

---

### Post by jdodson on 2005-05-15
[QUOTE=ultima2k]I downloaded some pointrelease for Quake3:
[ftp://ftp.idsoftware.com/idstuff/quake3/linux/](ftp://ftp.idsoftware.com/idstuff/quake3/linux/)

I have copied pak0.pk3 into the baseq3-folder, but when I try to start the game it's just a black screen and you can se some of the desktop.

I think you have to do some stuff with the graphics..

Need help....

(I've got a 6800LE)[/QUOTE]

run glxgears and let me know what the results are.  can you run other 3D games?  did you install the nvidia binary driver.  if you did not check out this howto:

[http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

---

### Post by ultima2k on 2005-05-15
[QUOTE=jdodson]run glxgears and let me know what the results are.  can you run other 3D games?  did you install the nvidia binary driver.  if you did not check out this howto:

[http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)[/QUOTE]

Ran glxgears and got around 9300fps with the standard sized window and with maximun size I got around 1500-2000fps.

Actually I havn't tryed any other 3d-games yet. I got Doom3 demo for linux on my kaptop but it's recharger is broken and battery empty :S

Well about the nvidia-driver I used the ubuntu addon which had some including, that's all. I have tryed installing the drivers that you download from nvidia.comm but it just says it need some speciel kernel to install which I don't know anything about.

---

### Post by bazh on 2005-05-15
the default rez for quake3 is 640x480, unless you have that supported in the xorg.conf it wont run.

All you have todo is either open q3config and replace the line that says

"r_mode 3" to r_mode 4 (800) or r_mode 6(1024)

i think you can also do it via the command line with

$quake3 +set r_mode 6

If neither of those work, create a file called "autoexec.cfg" in your /home/urname/.q3a/baseq3 folder

and put in the line r_mode 6 into this autoexec file.

Hope this helps

Ive got a blog entry on quake3 here - [http://ubuntuforums.org/journal.php?do=showentry&e=81](http://ubuntuforums.org/journal.php?do=showentry&e=81)

---

### Post by Wardhog on 2005-05-15
I had the same problem, black screen that you could see some of the desktop.

Do a 'killall esd' first, before running Quake3.  It worked for me.

---

### Post by crane on 2005-05-16
[QUOTE=bazh]the default rez for quake3 is 640x480, unless you have that supported in the xorg.conf it wont run.

All you have todo is either open q3config and replace the line that says

"r_mode 3" to r_mode 4 (800) or r_mode 6(1024)

i think you can also do it via the command line with

$quake3 +set r_mode 6

If neither of those work, create a file called "autoexec.cfg" in your /home/urname/.q3a/baseq3 folder

and put in the line r_mode 6 into this autoexec file.

Hope this helps

Ive got a blog entry on quake3 here - [http://ubuntuforums.org/journal.php?do=showentry&e=81](http://ubuntuforums.org/journal.php?do=showentry&e=81)[/QUOTE]

Interesting, I have never seen that happen. Every insatll I do seems to start up fine ar the default res.
I have seen the black screen before caused by esd but that was generally when teamspeak was running.

---


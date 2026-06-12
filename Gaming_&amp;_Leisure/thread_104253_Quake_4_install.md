---
title: "Quake 4 install"
date: 2005-12-15
forum: Gaming &amp; Leisure
---

### Post by Kobra on 2005-12-15
Ok, well.  I just got Quake 4, and I was looking for the Linux installer of it, and found it on linux-gamers.com.  But when I clicked on the link to download it, it just came up to a text screen with some funky text.  It did the same exact thing with my attempted download of the Doom 3 installer.  What seems to be the problem here?

---

### Post by tburns on 2005-12-15
[QUOTE=Kobra]Ok, well.  I just got Quake 4, and I was looking for the Linux installer of it, and found it on linux-gamers.com.  But when I clicked on the link to download it, it just came up to a text screen with some funky text.  It did the same exact thing with my attempted download of the Doom 3 installer.  What seems to be the problem here?[/QUOTE]

right click and save as

---

### Post by Kobra on 2005-12-15
No dice brother

---

### Post by tburns on 2005-12-15
[QUOTE=Kobra]No dice brother[/QUOTE]


[ftp://ftp.idsoftware.com/idstuff/quake4/linux/](ftp://ftp.idsoftware.com/idstuff/quake4/linux/)

right click and save link as...

---

### Post by tburns on 2005-12-15
[QUOTE=tburns][ftp://ftp.idsoftware.com/idstuff/quake4/linux/](ftp://ftp.idsoftware.com/idstuff/quake4/linux/)

right click and save link as...[/QUOTE]


it is because Apache (I assume) doesn't know how to handle the file (wacky .run extension)

---

### Post by Kobra on 2005-12-15
When I do that, it says that the link could not be saved because it might of been removed or had it's named changed.  I'm downloading it off of another Linux gaming site.  Thanks for your support

---

### Post by tburns on 2005-12-15
[QUOTE=Kobra]When I do that, it says that the link could not be saved because it might of been removed or had it's named changed.  I'm downloading it off of another Linux gaming site.  Thanks for your support[/QUOTE]


Try the idSoftware site download. I just tried with firefox (right click and save as...) and it worked. Sometimes the site says it is 'full'...

---

### Post by Kobra on 2005-12-15
Could you point me to the idSoftware site download?  I know the full message (from downloading the Quake 3 point release.  hehe)

---

### Post by tburns on 2005-12-15
[QUOTE=Kobra]Could you point me to the idSoftware site download?  I know the full message (from downloading the Quake 3 point release.  hehe)[/QUOTE]


There is a lnk at message #4 this thread

[ftp://ftp.idsoftware.com/idstuff/quake4/linux/](ftp://ftp.idsoftware.com/idstuff/quake4/linux/)

---

### Post by Kobra on 2005-12-15
Ah.  Even when I go to there and right click, I have no save-as option

---

### Post by tburns on 2005-12-15
[QUOTE=Kobra]Ah.  Even when I go to there and right click, I have no save-as option[/QUOTE]


Try using firefox (am using windows firefox now...at work;)  but I think linux firefox has same right click menu) and right click on the link. If not what are the options when you right click on the link?

---

### Post by Kobra on 2005-12-15
I am on FireFox (wouldn't use anything else).  I get:
Bookmark This Link...
Save Link As...
Send Link...
Copy Link Location...

---

### Post by Kobra on 2005-12-15
Meh, My friend downloaded it for me.  I guess it's just me, I dunno

---

### Post by gil-galad on 2005-12-15
I usuallly just download the torrent.  :)

---

### Post by Kobra on 2005-12-15
Ok, new problem.  The first disk read fine, but it's saying that I don't have permissions to view the second disk.  WTF?  I already tried a sudo mount, but no dice

---

### Post by tburns on 2005-12-15
[QUOTE=Kobra]Ok, new problem.  The first disk read fine, but it's saying that I don't have permissions to view the second disk.  WTF?  I already tried a sudo mount, but no dice[/QUOTE]


Have you tried 
[http://zerowing.idsoftware.com/linux/quake4/#head-55969ff8b38fad088ee915b4e7da3480efcf5046](http://zerowing.idsoftware.com/linux/quake4/#head-55969ff8b38fad088ee915b4e7da3480efcf5046)

Quoted:
File permissions on install CDs

The install CDs have Rock Ridge extensions which may get in the way of copying the files to your hard drive. You should make sure to mount the CDs ignoring the extension ( "-o norock" ) or setup appropriate mounted partition ownership / copy files as root and fixup manually.

---

### Post by Kobra on 2005-12-15
Ok, I got it up and running, but I still have problems.  In game, I have no buttons.  Where all the buttons are supposed to be, I have "#str" strings in their place.  Also, when it loads the first level, if I try to skip the cinematic, the whole game locks up and I can't do anything.  I'm forced to Ctrl-Alt-Backspace out

---

### Post by tburns on 2005-12-15
[QUOTE=Kobra]Ok, I got it up and running, but I still have problems.  In game, I have no buttons.  Where all the buttons are supposed to be, I have "#str" strings in their place.  Also, when it loads the first level, if I try to skip the cinematic, the whole game locks up and I can't do anything.  I'm forced to Ctrl-Alt-Backspace out[/QUOTE]


This might have something to do with the crashing:

[http://zerowing.idsoftware.com/linux/quake4/#head-a0995b8d4f543e7cd8ceec66965708479f9ad7dc](http://zerowing.idsoftware.com/linux/quake4/#head-a0995b8d4f543e7cd8ceec66965708479f9ad7dc)

Quoted:
Crashes on startup when loading the game module

Some Debian and Debian-based distributions ( like Ubuntu ) are crashing during startup. It appears this is caused by the SDL packages selection. You need to install libsdl1.2debian-alsa or libsdl1.2debian-oss instead of libsdl1.2debian-all.

FYI, it is not clear what happens with this crash. Happens during initialization of static variables, has to do with a cvar named g_log and goes away if renamed to something else. So it would look like this version of SDL has g_log already defined from somewhere else and the dynamic loader getting confused over it.

---

### Post by Kobra on 2005-12-15
I had the oss installed, but I switched to alsa.  and it still does it.  I have sound, and it's pretty crisp.  I've went through that how-to with a fine tooth comb and it still hasen't helped the crashing or my buttons missing

---

### Post by Kurt Dodrill on 2005-12-15
are you sure it crashed or its just taking a bit, cause i just installed it today and thought it crashed but it just took a sec to load.

---

### Post by Kobra on 2005-12-16
[QUOTE=Kurt Dodrill]are you sure it crashed or its just taking a bit, cause i just installed it today and thought it crashed but it just took a sec to load.[/QUOTE]
Ok, now I know it's not crashing.  But now I can't hear the people talking, and the buttons are still missing

---

### Post by Kobra on 2005-12-16
```
WARNING: Playing default sound sound/vo_english/airdefense/1_1_1_30_3.ogg
WARNING: Unknown string id #str_400289
```
That's the kind of stuff that's going wrong

---

### Post by Fibre on 2005-12-17
Save link as and then it will download I just tried it then

Sorry igonre me I forgot about the other 2 pages on this thread  SORRY

---

### Post by Kobra on 2005-12-17
No problem.  now I'm starting to feel disapointed that I can't play Q4 on my Linux...

---

### Post by Starn on 2009-12-25
sorry to bring back such an old post but this was only thing related i could find on google i spent around 30 mins to find a fix

go to your installed location for quake 4 Quake 4\q4base and look for the config file Quake4Config or something
edit it and look for this line seta sys_lang "X"
where the X is should be a language like english spanish or something it depends on the copy of game you have my copy is english and the config file was set for spanish after changing it to 
seta sys_lang "english"
from
seta sys_lang "spanish"
it started working again no issues this also works under windows. for ya dual booters like me

---


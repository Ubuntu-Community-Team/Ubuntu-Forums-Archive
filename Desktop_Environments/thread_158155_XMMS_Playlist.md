---
title: "XMMS Playlist"
date: 2006-04-10
forum: Desktop Environments
---

### Post by jdavis on 2006-04-10
hello,

I am using XMMS to play my mp3's and it is excellent, especially since you can use winamp skins! which makes the change from windows a lot easier for people!

The only thing missing is the option below "Open with XMMS" to "add to playlist" or "enqueue in xmms" or something like that, which i am used to with winamp. After having a quick look at the XMMS documentation I have managed to add this to the open with menu using "xmms -e, --enqueue" although this just shows up as xmms in the "open with" menu.

Is there any way this could be placed below the "Open with XMMS" link (perhaps named appropriately) to make things a bit easier?

thanks, Jonathan :)

---

### Post by ubernoob on 2006-04-10
you can make a script:

```
gedit ~/.gnome2/nautilus-scripts/enqueue_xmms
```

```

#!/bin/bash
for X in $*
do
xmms -e "$X"
done

```
You have to find out if you want:
 -e, --enqueue                 Don't clear the playlist
 -Q, --queue                   Add file(s) to playlist and queue

I'm not very good in english so i don't get the diffrence, and i'm not home, so i can't test it.

```
chmod +x ~/.gnome2/nautilus-scripts/enqueue_xmms
```

Then you can rightclick on the file, choose script and then choose it.

Edit: fixed script in case someone else need this and they aren't reading all the posts.

Edit 2: fixed the script so you can mark several files, and not just one file.

---

### Post by jdavis on 2006-04-10
Sorry to sound like a total newbie, but where do i go from there? how can i add the script to the right click menu?

thanks, Jonathan

---

### Post by MarioFrick on 2006-04-10
It's very easy.
Open a console ad write what ubernoob wrote, i.e.:
```
gedit ~/.gnome2/nautilus-scripts/enqueue_xmms
```

Gedit will open and paste this code in it:
```
#!/bin/bash
xmms -e $*
``` 

Save and close, then write in the console:
```
chmod +x ~/.gnome2/nautilus-scripts/enqueue_xmms
```

And it's done. Now go to the directory where the mp3s are, select them, right clich and choose Scripts -> enqueue_xmms

---

### Post by ubernoob on 2006-04-10
open a new nautilus window (file browser) and rightclick on the file. There should be "Scripts", and under "Scripts" you find the script that you made above.

---

### Post by jdavis on 2006-04-10
This works ok with filenames with no spaces in it but otherwise only loads in the last word. EG: "my thing.mp3" only loads onto the playlist as "thing.mp3".
Any Idea's?

thanks for all the help guys!

Jonathan

---

### Post by ubernoob on 2006-04-10
sorry, my fault.

change: xmms -e $*
with xmms -e "$*"

---

### Post by jdavis on 2006-04-10
excellent! thanks lots guys!!!

I'm starting to get to grips with ubuntu now, only been using it for a few days, although i have attempted using it (and other linux distro's) in the past and had given up!!! i'm really a M$ nerd, so it's all a bit new to me!!! but all the support (forums, irc etc..) are brilliant! and pretty much everything i had setup on Xp i've now got working on ubuntu! so it's my full time PC now and my XP one is my backup! I'm picking things up pretty quick now!

Jonathan

---

### Post by ubernoob on 2006-04-10
No worries. I'm glad ubuntu fits your needs. If you don't give up, you will find yourself booting more and more seldom into windows. And after a while, you wouldn't change back for anything in the world. (Except for some cool games ;))

---

### Post by jdavis on 2006-04-10
Thats the plan! the only thing missing for me now is full read/write to NTFS. Although hopefully that will come soon.... I hope!

I'm picking up stuff quite fast, I have certifications from M$ and Comptia so i'm no newbie to computers (although only 20 years young). It's all pretty new to me though! I've been needing to learn linux for ages though so i'm determined this time! 

Jonathan

---

### Post by Jose Catre-Vandis on 2006-04-10
Useful howto on getting enqueue working in XMMS, many thanks

What edit do you need to make to the script to allow multiple files to be enqueued? (either SHIFT select or CTRL select)?

---

### Post by ubernoob on 2006-04-10
i updated the script so you can drag around several mp3's and add them all to the playlist, instead of marking one at the time. Check my first post. I updated that one.

---

### Post by Jose Catre-Vandis on 2006-04-11
[QUOTE=ubernoob]i updated the script so you can drag around several mp3's and add them all to the playlist, instead of marking one at the time. Check my first post. I updated that one.[/QUOTE]

Thanks. It won't quite work for me though. Just puts up the last word of each file and the .mp3?

I reverted to the original script, and now right clicking on a single file puts up the whole directory :-?

---

### Post by ubernoob on 2006-04-12
I know. I didn't test it before i posted it. I'll update it when i get the chance.

---


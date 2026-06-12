---
title: "Backing up Steam saved games"
date: 2014-02-12
forum: Gaming &amp; Leisure
---

### Post by Kymus on 2014-02-12
I gotta do a system wipe; last time I somehow missed backing up my steam games despite copying my home folder.

I'm looking to backup saves from the WINE and Ubuntu clients.

Suggestions?

---

### Post by mastablasta on 2014-02-13
wine is in hidden folder in home (along with other hidden folders). i guess you didn't back up all the files.

why do you need to do a system wipe?

---

### Post by dannyboy79 on 2014-02-13
if you truly backed up your home directory, than most likely the .local folder within your home was backed up as well, it's just that it's hidden normally. any folder with a dot in front of it is hidden.

---

### Post by Kymus on 2014-02-13
Interesting. Not sure what I did wrong, previously then o_O

---

### Post by Kymus on 2014-02-13
> **mastablasta said:**
> why do you need to do a system wipe?

[My system locked up in the middle of an update]("http://ubuntuforums.org/showthread.php?t=2200064") and I can not access a terminal. Seems like my only option.

---

### Post by dannyboy79 on 2014-02-13
you can't even get to tty1? do you see a grub boot menu? if so, have you tried using the recovery option? If you truly need to performa a system wipe, than just boot up a livecd of any kind and using 
```
rsync -avxP /path/to/directory/to/backup/ /path/to/directory/for/storing/backup/
``` to make a copy of your home directory onto another safe partition before performing the new install. that should have your entire steam library within .local/share/Steam/

---

### Post by Kymus on 2014-02-13
> **dannyboy79 said:**
> you can't even get to tty1? do you see a grub boot menu?

If I recall correctly, I don't think GRUB is showing up... but I could very well be wrong. My system has been stable for only about a few weeks to a month; I did a wipe at that point due to some strange issue having to do with nVidia or something (I left the issue alone for too long and ended up not remembering where I left off etc. etc., so I just wiped things so I didn't have to deal with the hassle of going back to that complex problem).

Either way, I'll double check, thanks! 


> If you truly need to perform a a system wipe, than just boot up a livecd of any kind and using 
```
rsync -avxP /path/to/directory/to/backup/ /path/to/directory/for/storing/backup/
``` to make a copy of your home directory onto another safe partition before performing the new install. that should have your entire steam library within .local/share/Steam/

I see. Yeah, last time (I think) I just went in to nautilus and dragged and dropped the home folder on to my external HD.

---

### Post by dannyboy79 on 2014-02-14
yeap, dragging and dropping would only work IF you had hidden files/folders shown. that's why you use rsync, it also keep the owner:group and permissions as well.

---

### Post by mastablasta on 2014-02-14
i see the issue in mentioend thread is still not resolved. usually it is rare a reinstall is needed. 
however if you wish to do it i would suggest to just install without formating. that way the current system will be overwritten, but you should be losing any data or settings.

---

### Post by Ranko Kohime on 2014-02-20
As a response to the OP question, there really is no answer as far as WHERE the game saves are, because each individual game saves somewhere else.

I've gone so far as to build a table of the games I personally own, and they're all over the map.  Some in my home directory, some under ~/.config, others under ~/.local/share, some are in the Steam cloud folder, and even others will save directly into their own install folder.

And that's just as far as the Linux client.  The Windows client is no better, with each game picking it's own folder in which to dump saves, and a few games even dumping their saves outside of the ~/.wine folder, due to the "Documents" folder handling.

---


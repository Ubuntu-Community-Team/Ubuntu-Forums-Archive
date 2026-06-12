---
title: "Rhythmbox not responding"
date: 2005-02-01
forum: Desktop Environments
---

### Post by zeus on 2005-02-01
Rhtymbox not responding when i import from menu...there are no errors, just freeze.
Anyone having the same problem?? 

The only way to load files is drag and drop from nautilus to Rhythmbox playlist..

---

### Post by clparker on 2005-02-01
I wanted to use rythbox because of it's more advanced media library features, but it does damn near the same for me, i think it's because it's getting stuck loading a directory and something other than an .mp3 file throws it off. just use XMMS 
 
  ```
sudo apt-get install XMMS
```

---

### Post by valadil on 2005-02-01
I had a hellish time getting Rhythmbox to recognize my collection.  I eventually ended up deleting all my album art and more importantly all the desktop.ini files that made the album art into the folder's background in Windows.  Have fun.

---

### Post by zeus on 2005-02-02
so this is ubuntu bug.
I gues i have to install XMMS afterall...damn!

---

### Post by clparker on 2005-02-02
well get rid of all the .ini files in the folders and you should be ok, any album art should go too,  but hey XMMS is good, i dig it.

---

### Post by zeus on 2005-02-02
[QUOTE=clparker]well get rid of all the .ini files in the folders and you should be ok, any album art should go too,  but hey XMMS is good, i dig it.[/QUOTE]
 Okay, i will tyr it...

Installing XMMS that's means i have to install GTK+ , meen!! i want to keep my system from old GTK thingie.. :p , if your suggestion doesn't work. It's mean i dig XMMS...

---

### Post by darrenadams on 2005-02-02
[QUOTE=zeus]Okay, i will tyr it...

Installing XMMS that's means i have to install GTK+ , meen!! i want to keep my system from old GTK thingie.. :p , if your suggestion doesn't work. It's mean i dig XMMS...[/QUOTE]


There's always Beep Media Player. It was initially a fork of XMMS to use GTK+2 but it's coming along nicely as a player in its' own right. If you have the universe repository set up, just type sudo apt-get install beep-media-player

---

### Post by Buffalo Soldier on 2005-02-02
What I usually do when I want to add mp3 songs from a folder to Rhythmbox library is:

I view the folder in "Vies as List" then I arrange according to file type. Click on the first mp3 file and shift-click on the last mp3 file. Right click and "Add to Music Library".

That way I can add the whole folder without deleting other files that my family need to use when they logon to WinXP.

---

### Post by valadil on 2005-02-02
Buffalo, that doesn't work so well when you're music is organized into genre, subgenre, artist, album folders and you're adding some 13,000 songs.

---

### Post by DougInKY on 2005-02-02
[QUOTE=clparker]I wanted to use rythbox because of it's more advanced media library features, but it does damn near the same for me, i think it's because it's getting stuck loading a directory and something other than an .mp3 file throws it off. just use XMMS 
 
  ```
sudo apt-get install XMMS
```[/QUOTE]

I have used Rhythmbox in Mandrake for a long time. I come to Ubuntu and see that Rhythmbox has a problem with importing. The version I used to use in Mandrake imported fine and just ignored the files in the directories that it couldn't use. I wonder what is different between the two versions?

Doug

---

### Post by valadil on 2005-02-02
Ubuntu uses Rhythmbox 0.8.8.  See if you can find out what mandrake uses.  Maybe they changed out Rhythmbox imports files between versions.

---

### Post by mpie on 2005-02-03
believ its version 0.8.5 but alot of mandrake's packages have specific mandrake fixes  aswell so could just be something they've done as the same verion was in fedorecore3 and that would not load my collection :-|

---

### Post by Buffalo Soldier on 2005-02-03
[QUOTE=valadil]Buffalo, that doesn't work so well when you're music is organized into genre, subgenre, artist, album folders and you're adding some 13,000 songs.[/QUOTE]
Yeah, I have to agree on that. Its too much of a hassle when you start dealing with more than 3-4 folders.

---

### Post by DougInKY on 2005-02-04
[QUOTE=valadil]Ubuntu uses Rhythmbox 0.8.8.  See if you can find out what mandrake uses.  Maybe they changed out Rhythmbox imports files between versions.[/QUOTE]

Sorry. That would require me reinstalling Mandrake over my Ubuntu to see what version they use and then I would have to reinstall Ubuntu and go through all the hassle of getting my multimedia all running again.

 [-(  Doug

---

### Post by llamakc on 2005-02-05
I'm using Version: 0.8.8-4ubuntu2 from Hoary and I no longer have this problem. Rhythmbox isn't hanging on album art or non-music files any longer. Also, streaming started working again. My last update && upgrade was a day or two ago.

---

### Post by WirelessMike on 2005-03-09
I have a different problem...  Hope someone can help.

I'm on hoary and using rhythmbox 0.8.8 and can add whole directories to my library with no problem.  I can delete individual music files, as well.

The problem is, I have no option to add individual music files, only directories.  Anyone else run into this?  Is there something more I need to install...  Some permission settings I've overlooked?

Please help.

---


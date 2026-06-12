---
title: "Amarok messes up track sequence"
date: 2007-05-28
forum: Desktop Environments
---

### Post by fdimmling on 2007-05-28
I installed Amarok from Feisty to load the ogg files of my music collection to my iRiver IGP-100 player. The file names are of the type 

01 - name of track

When Amaork transfers the data to the player it removes the leading 01 - , which causes the IGP-100 to play the tracks in alphabetical order which is not what I want it to do, of course.

Is there any way to avoid this behaviour?

Friedrich :(

---

### Post by orb9220 on 2007-05-28
> The file names are of the type 01 - name of track

Yes but do the ID3 tags have the Track imbedded in the mp3 file?
Most software reads the mp3 Tag which is info imbedded in the mp3 file.

Are you sure it is not the player? Some players may not support or like the numbers.

From their website:

> Q. How does the iGP-100 sort files?
A. By default, the iGP-100 will sort files and folders numerically or alphabetically based on a f**older's title or file's iD3 tag**.

[http://www.iriveramerica.com/support/hd/iGP_100_FAQ.aspx](http://www.iriveramerica.com/support/hd/iGP_100_FAQ.aspx)

---

### Post by fdimmling on 2007-05-29
> **orb9220 said:**
> 
Are you sure it is not the player? Some players may not support or like the numbers.
[/url]

If I copy the data directly to the player using Nautilus the track numbers are preserved and the tracks sorted accordingly, if Amarok does the file transfer the leading numbers of the track names are removed and the tracks sorted by alphabet. The ID3 tags do not contain the leading track numbers. Actually the ogg files were created by SoundJuicer from Gnome. 

Friedrich

---


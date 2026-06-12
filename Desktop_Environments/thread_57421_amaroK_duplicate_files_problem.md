---
title: "amaroK duplicate files problem"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Movikun on 2005-08-16
It seems that even though i told amaroK NOT to scan for playlist files, only music files, it displays double files, for example

Album 1:
Song 1
Song 1
Song 2
Song 2
Album 2:
Song1
Song1
etc...

any way to fix this ?

Also, can amaroK work like iTunes, eg. have a media library, which lists all of my files, and when i press play on a tune, when that tune finishes it plays the next one in the playlist. I don't want to play from a playlist, but from my whole music collection.

Thanks for any help!

---

### Post by odrop on 2005-08-16
[QUOTE=Movikun]It seems that even though i told amaroK NOT to scan for playlist files, only music files, it displays double files, for example

Album 1:
Song 1
Song 1
Song 2
Song 2
Album 2:
Song1
Song1
etc...

any way to fix this ?

Also, can amaroK work like iTunes, eg. have a media library, which lists all of my files, and when i press play on a tune, when that tune finishes it plays the next one in the playlist. I don't want to play from a playlist, but from my whole music collection.

Thanks for any help![/QUOTE]
 From the menu bar... Playlist->Remove Duplicate and Dead Entries

should remove all the duplicates.
And for all of your music in your collection, Click on Playlists in the left side bar then Smart Playlists->All Collection

But this is from Amarok 1.3, so might be a bit different for you.

---

### Post by Movikun on 2005-08-16
See the problem is, that i don't have duplicates in the playlist (which this option is for) but in my "Collection". And yes, i have amaroK 1.3, downloaded a .deb someone posted over here somewhere :)

---

### Post by Movikun on 2005-08-16
Ah, nevermind now, i just fixed the problem myslef by deleting the dirs which amaroK used in ~/.kde 

No duplicates now :)

---

### Post by Valir on 2008-01-16
> **odrop said:**
> From the menu bar... Playlist->Remove Duplicate and Dead Entries

should remove all the duplicates.
And for all of your music in your collection, Click on Playlists in the left side bar then Smart Playlists->All Collection

But this is from Amarok 1.3, so might be a bit different for you.

Hi, 

But now I wonder: removing duplicates from the playlist as All Collection, does that remove the excessive files on the disk? Which is what I need to do to save space.

Best regards, 

V.

---

### Post by Chessmaster on 2008-01-20
> Ah, nevermind now, i just fixed the problem myslef by deleting the dirs which amaroK used in ~/.kde 

How did you do this? I have the same problem but don't know how to fix it.

Cheers

---

### Post by Chessmaster on 2008-01-21
Ah, just worked it out. Delete the amarok folder: /home/[name]/.kde/share/apps/amarok

Then start up Amarok again. You have to load the cover images again etc but all is good now! :)

---

### Post by rosencrantz on 2008-05-12
Actually, you needn't delete the complete ~/.kde/share/apps/amarok, just the files collection.db, collection_scan.files and playlistbrowser_save.xml in case of duplicate playlists. Blogged this [here]("http://greekbitches.blogspot.com/2008/05/duplicate-entries-in-amarok-collection.html").

---

### Post by ExBuM on 2008-05-15
I fixed this problem by doing Rescan Collection

---


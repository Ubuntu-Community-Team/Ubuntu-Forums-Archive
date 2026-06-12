---
title: "XMMS ID3v2"
date: 2005-08-26
forum: Desktop Environments
---

### Post by fortytwo on 2005-08-26
Is XMMS capable of reading ID3v2?  (I'm hoping no, since all of my songs are coming up as gibberish on the xmms playlist).  Is there a plugin for ID3v2 support?  I would think for sure there would be, but I can't seem to find one.  I've got XMS 1.2.10.

Thanks

---

### Post by twelvegates on 2005-08-26
[QUOTE=fortytwo]Is XMMS capable of reading ID3v2?[/QUOTE]

I have 1.2.10-2ubuntu and it displays some of the ID3v2 tags such as author and title.

---

### Post by fortytwo on 2005-08-26
[QUOTE=twelvegates]I have 1.2.10-2ubuntu and it displays some of the ID3v2 tags such as author and title.[/QUOTE]
 Hmm, interesting.  On all of my mp3's, I have the artist and title fields set up in ID3v2.  When I open them in XMMS, all I get is a bunch of square ascii characters, and when I try and edit the ID3v2 tags, both the artist and title of the song are in the 'title' box (which still isn't even being read).  The tags are read fine in other programs.

Any other ideas?

---

### Post by twelvegates on 2005-08-26
[QUOTE=fortytwo]Hmm, interesting.  On all of my mp3's, I have the artist and title fields set up in ID3v2.  When I open them in XMMS, all I get is a bunch of square ascii characters, and when I try and edit the ID3v2 tags, both the artist and title of the song are in the 'title' box (which still isn't even being read).  The tags are read fine in other programs.

Any other ideas?[/QUOTE]
 Does *`id3v2 -l file.mp3`* look reasonable?

---

### Post by fortytwo on 2005-08-26
[QUOTE=twelvegates]Does *`id3v2 -l file.mp3`* look reasonable?[/QUOTE]
 When I run 'id3v2 -l file.mp3' I see tha the id3v1 tag shows both the artist and the title of the song in the 'title' box, but the id3v2 tag looks correct.

---

### Post by twelvegates on 2005-08-26
[QUOTE=fortytwo]When I run 'id3v2 -l file.mp3' I see tha the id3v1 tag shows both the artist and the title of the song in the 'title' box, but the id3v2 tag looks correct.[/QUOTE]

I have no experience with id3v1. 
What happens if you remove the id3v1 tags and keep the id3v2 ones only?

---

### Post by fortytwo on 2005-08-26
[QUOTE=twelvegates]I have no experience with id3v1. 
What happens if you remove the id3v1 tags and keep the id3v2 ones only?[/QUOTE]
 Thanks for the replies.

The thing is that they don't even *have* ID3v1 tags, I brought them over from my Windows machine where I put only ID3v2 tags on the file, so I'm not sure where it's even pulling the ID3v1 tags from.

---

### Post by twelvegates on 2005-08-26
[QUOTE=fortytwo]The thing is that they don't even *have* ID3v1 tags, I brought them over from my Windows machine where I put only ID3v2 tags on the file, so I'm not sure where it's even pulling the ID3v1 tags from.[/QUOTE]
What happens if you try removing the ID3v1 tags: *id3v2 --delete-v1 file.mp3*?

---

### Post by fortytwo on 2005-08-26
[QUOTE=twelvegates]What happens if you try removing the ID3v1 tags: *id3v2 --delete-v1 file.mp3*?[/QUOTE]
 Thanks again for the reply.

I stripped off the id3v1 tag, and I still get the same problem.  I even opened it up in XMMS, and then looked at 'file info' with ctrl-3 and tried to erase it, and it said there was no tag to erase.  So it appears that it's not that id3v1 tags are being read, but that it's not reading the id3v2 tags, so it's just loading the filename (which is the artists and title) into the title tag as a default.  So, what needs to be done to get XMMS to read id3v2 tags?

Thanks again.

EDIT:  I just tried manually adding the tag through XMMS's own file info window, and it's still showing up, even though I checked afterward and the new data was still in there....what gives?

---

### Post by twelvegates on 2005-08-27
[QUOTE=fortytwo]I brought them over from my Windows machine where I put only ID3v2 tags on the file,[/QUOTE]

Maybe Windows is using a 16-bit charater set.
Could you try to feed this to XMMS:
[http://www.gemeinde-christi.ch/zurich/audiopredigt/files/050814-2.m3u](http://www.gemeinde-christi.ch/zurich/audiopredigt/files/050814-2.m3u)
It has id3v2 tags attached on Unix. They sould be 8-bit.

You could try deleting all tags from the file and attach some new ones.
```
id3v2 --delete-v1 --delete-v2 file.mp3
id3v2 --artist Artist --song Song file.mp3
```

---

### Post by fortytwo on 2005-08-27
[QUOTE=twelvegates]Maybe Windows is using a 16-bit charater set.
Could you try to feed this to XMMS:
[http://www.gemeinde-christi.ch/zurich/audiopredigt/files/050814-2.m3u](http://www.gemeinde-christi.ch/zurich/audiopredigt/files/050814-2.m3u)
It has id3v2 tags attached on Unix. They sould be 8-bit.

You could try deleting all tags from the file and attach some new ones.
```
id3v2 --delete-v1 --delete-v2 file.mp3
id3v2 --artist Artist --song Song file.mp3
```[/QUOTE]
 The file you gave me is still giving me garbage in the playlist.  When I strip the id3 tag and then re-enter it, the file *still* shows up as garbage...even though if I check the file info I can see the artist and title correctly placed in each of the fields!  So it seems that the playlist just isn't able to display it correctly or something?  Any more ideas?

Thanks again

---

### Post by fortytwo on 2005-08-27
The file you gave me is still giving me garbage in the playlist.  When I strip the id3 tag and then re-enter it, the file *still* shows up as garbage...even though if I check the file info I can see the artist and title correctly placed in each of the fields!  So it seems that the playlist just isn't able to display it correctly or something?  Any more ideas?

Thanks again

---

### Post by fortytwo on 2005-08-27
[QUOTE=twelvegates]Maybe Windows is using a 16-bit charater set.
Could you try to feed this to XMMS:
[http://www.gemeinde-christi.ch/zurich/audiopredigt/files/050814-2.m3u](http://www.gemeinde-christi.ch/zurich/audiopredigt/files/050814-2.m3u)
It has id3v2 tags attached on Unix. They sould be 8-bit.

You could try deleting all tags from the file and attach some new ones.
```
id3v2 --delete-v1 --delete-v2 file.mp3
id3v2 --artist Artist --song Song file.mp3
```[/QUOTE]
 The file you gave me is still giving me garbage in the playlist.  When I strip the id3 tag and then re-enter it, the file *still* shows up as garbage...even though if I check the file info I can see the artist and title correctly placed in each of the fields!  So it seems that the playlist just isn't able to display it correctly or something?  Any more ideas?

Thanks again

---

### Post by fortytwo on 2005-08-27
The file you gave me is still giving me garbage in the playlist.  When I strip the id3 tag and then re-enter it, the file *still* shows up as garbage...even though if I check the file info I can see the artist and title correctly placed in each of the fields!  So it seems that the playlist just isn't able to display it correctly or something?  Any more ideas?

Thanks again

---

### Post by pataphysician on 2005-08-28
i don't know if this will make a difference or not, but have you tried changing the font that the playlist is using?

---

### Post by twelvegates on 2005-08-28
Maybe there is realy something wrong with the XMMS installation or one of the libraries it depends on.

You could try to build XMMS from source and install it in a different location and then see if it behaves the same.

---

### Post by fortytwo on 2005-08-28
[QUOTE=pataphysician]i don't know if this will make a difference or not, but have you tried changing the font that the playlist is using?[/QUOTE]
 Yes! It turns out the font was the problem, I changed it and the playlist is now displaying the names fine.  Thanks very much for finally putting this one to rest....And thanks twelvegates for all of your help as well.

---

### Post by twelvegates on 2005-08-29
And what's the name of the nice font that caused the trouble?

---

### Post by fortytwo on 2005-08-29
[QUOTE=twelvegates]And what's the name of the nice font that caused the trouble?[/QUOTE]
 Unfortunately I didn't take note of the font that was causing the trouble.  I did notice that some fonts on the list had 'This is a 2 byte font and may not be displayed correctly...' so that may have been the issue.

---


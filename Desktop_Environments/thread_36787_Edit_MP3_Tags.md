---
title: "Edit MP3 Tags"
date: 2005-05-24
forum: Desktop Environments
---

### Post by dqsis on 2005-05-24
Hello Ubuntu friends!

I am using Rhythmbox to play my music files!!!

Do you know which program to use in order to edit their tags??

Thanks in advance

/DQ

---

### Post by angkor on 2005-05-24
The Rhythmbox homepage recommends [this one](http://easytag.sourceforge.net/) 

Never used it though, I use amarok in Ubuntu which already supports mp3 tag editing.

---

### Post by Sam on 2005-05-24
[QUOTE=dqsis]Hello Ubuntu friends!

I am using Rhythmbox to play my music files!!!

Do you know which program to use in order to edit their tags??

Thanks in advance

/DQ[/QUOTE]
Use Audio Tag Tool (package "tagtool"), it's a great application.

---

### Post by RastaMahata on 2005-05-24
[QUOTE=Sam]Use Audio Tag Tool (package "tagtool"), it's a great application.[/QUOTE]
 I second this. It's the cleanest tool I have found on ubuntu so far.
The only downside: You dont get a menu item for it, so you have to run it from console or a launcher.

---

### Post by electroglas on 2005-05-24
Is there an ID3 editor that will guess at ID3 tags based on the filename and other available info like Super Tagging in MusicMatch?

---

### Post by RastaMahata on 2005-05-24
[QUOTE=electroglas]Is there an ID3 editor that will guess at ID3 tags based on the filename and other available info like Super Tagging in MusicMatch?[/QUOTE]
 tagtool guesses the id3 tags from the filename.
For example, If I have several songs like:
artist - album - 00 - name.mp3

I just tell tagtool to rename several song from the filename, and set it to:
<artist> - <album> - <track> - <title>.mp3

good luck!

---

### Post by electroglas on 2005-05-24
"just tell tagtool to rename several song from the filename"

Do you mean that you have to guess that the filename is correct info or does Tagtool make suggestions based on the filename etc.

MusicMatch will take partial info and find several possible tags to choose from. Very nice for cleaning up mistagged songs.

---

### Post by RastaMahata on 2005-05-24
[QUOTE=electroglas]"just tell tagtool to rename several song from the filename"

Do you mean that you have to guess that the filename is correct info or does Tagtool make suggestions based on the filename etc.

MusicMatch will take partial info and find several possible tags to choose from. Very nice for cleaning up mistagged songs.[/QUOTE]
 I think you have to guess that the filename is correct :(

---

### Post by electroglas on 2005-05-24
I run strictly Ubuntu on my PC and laptop and I very much miss this feature...

---

### Post by RastaMahata on 2005-05-24
[QUOTE=electroglas]I run strictly Ubuntu on my PC and laptop and I very much miss this feature...[/QUOTE]
 but have you tried easytag yet? I haven't, but from the screenshots, it looks quite... complete.

---

### Post by electroglas on 2005-05-24
It does look very nice, but you still have to make educated guesses with the manual search capability.

Again, MusicMatch offers suggestions that can be applied to the file.

---

### Post by Gustav on 2005-05-25
from trying easytag and tagtool I would say that tagtool is the better.

---

### Post by caspar_wrede on 2005-05-25
[QUOTE=electroglas]Is there an ID3 editor that will guess at ID3 tags based on the filename and other available info like Super Tagging in MusicMatch?[/QUOTE]

Try MusicBrainz. It guesses the tags by creating an "audio footprint" and then comparing it with information on the server.

ANd I really would recommend Amarok as a player -- it has MusicBrainz support built in. OK, it's not gnome-themed but it does strike me as being superior in every way.

---

### Post by jcooper on 2005-05-25
Just read this thread and thought I'd add my £0.02.

I sat down and organised my mp3 collection lastnight. I was fed up with rythmbox displaying "track 02" etc, so took the plunge.

I started off with tag tool and found it to be good, but lacking in terms of powerful operations. I then moved on to Easytag and found it suited my needs. Using EasyTag I was able to select an album folder, select all the files in that album and remove the comments at the click of one button, update tag info from CDDB (a lot had missint track numbers), then rename the files with a right click > rename > select format > click apply.

I did about 80 albums in approx 3/4 hour. One thing that did annoy me was I coudn't find an "apply changes" button, so had to change directory for EasyTag to apply them. Perhaps this was me being a first-time-user?

All in all EasyTag has the powerful functionality if its mass-editing you want to achieve. It does need some UI work, as its not the friendliest of apps to work with, but achieves what it sets out to.

As its all free software though, use what you feel most comfortable with, and what suits the task in hand :)

---

### Post by foxy123 on 2005-05-25
[QUOTE=jcooper]Just read this thread and thought I'd add my £0.02.

One thing that did annoy me was I coudn't find an "apply changes" button, so had to change directory for EasyTag to apply them. Perhaps this was me being a first-time-user?[/QUOTE]
it  is a Save button which applies changes :-)

---

### Post by jcooper on 2005-05-25
[QUOTE=foxy123]it  is a Save button which applies changes :-)[/QUOTE]

D'oh! Well at least thats that annoyance fixed ;) hehehe.

Thanks!

---

### Post by remin8 on 2005-06-29
I have used both and for my 10000+ collection it is not the best. I wish there was a better gtk/gnome tag editor. :( I really liked the amaroK and juK tools for KDE, but I mixing the desktop environments has always led to trouble for me. If you are running Kubuntu try juK.

---


---
title: "Question About Mouse-Over Events"
date: 2006-11-08
forum: Desktop Environments
---

### Post by margni on 2006-11-08
Does anyone know how to get back this feature in Nautilus File Manager:

When I have a folder full of mp3's in Nautilus, I used to be able to rest my mouse on a particular song's icon, and it would begin to play.

I've lost this feature, and don't know how to get it back!  Anyone seen or experienced this besides me?

Regards, and thanks in advance...

Margni

---

### Post by ahaslam on 2006-11-08
The preview tab under preferences should look like this:

[ATTACH]19109[/ATTACH]

---

### Post by margni on 2006-11-08
> **Anthony Haslam said:**
> The preview tab under preferences should look like this:

[ATTACH]19109[/ATTACH]


I checked out my preferences, and it looks EXACTLY like your picture.  What am I doing wrong?

Thanks for the response...

---

### Post by ahaslam on 2006-11-09
Look what I stumbled across:

Audio Previewing -- Applies to all Ubuntu releases The Ubuntu File Manager Nautilus can preview music files if you hover your mouse pointer over the file. If you would like to add this functionality to your desktop, install the mpg321 and vorbis-tools. Note: If you experience jittery playback of MP3 audio previews, try installing mpg123-esd instead of mpg321. The mpg123-esd package is located in the Multiverse repository.

Wasn't even looking for it, lucky hey?

Tony.

---

### Post by margni on 2006-11-10
> **Anthony Haslam said:**
> Look what I stumbled across:

Audio Previewing -- Applies to all Ubuntu releases The Ubuntu File Manager Nautilus can preview music files if you hover your mouse pointer over the file. If you would like to add this functionality to your desktop, install the mpg321 and vorbis-tools. Note: If you experience jittery playback of MP3 audio previews, try installing mpg123-esd instead of mpg321. The mpg123-esd package is located in the Multiverse repository.

Wasn't even looking for it, lucky hey?

Tony.

Totally...  I'll give that a shot this morning, and report back!

Muchas Thank-ya's

Margni

---

### Post by margni on 2006-11-10
Well...  That fixed it completely...

From the terminal:

Sudo apt-get install mpg123-esd vorbis-tools
Added my password, and watched apt-get do it's thing.
Closed the terminal

Opened my folder of mp3's, and hovered the mouse pointer over it - and it started to play!

Thanks to A.H. for stumbling onto this - I got a fix...

BTW, where did you get this little tidbit of info at?

---

### Post by ahaslam on 2006-11-10
> **margni said:**
> BTW, where did you get this little tidbit of info at?
To find it in it's original context check the 'Restricted Formats' link in my signature, it's under MP3. 

Glad it helped ;)

Tony.

---

### Post by margni on 2006-11-13
Many thanks!

I'll check your link out...

margni

---


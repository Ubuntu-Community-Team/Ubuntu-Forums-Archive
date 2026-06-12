---
title: "Firefox wmv plugin"
date: 2006-06-28
forum: Desktop Environments
---

### Post by lnxquestions on 2006-06-28
Hi
Is there a plugin for firefox to play wmv files ? I am sure that the windows version of firefox can play this kind of files i saw it .. But on linux i am trying to open a page contain wmv file and a message appers says " additional plugins are required to display all the media on this page " and when i hit install firefox display message says that there is no plugin and i have to install manually and when i hit this button firefox open the same page again and again .....!!

---

### Post by oyvindaa on 2006-06-28
You could try this one: 

[https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

But I'm not sure if it applies for Firefox. Give it a go.

---

### Post by lnxquestions on 2006-06-28
ok thanks i will try

---

### Post by frodon on 2006-06-28
First install all the needed codecs : 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Then install a plugin to read the video stream like the mplayer plugin or the media player connectivity extension of firefox (it's the one i use).

---

### Post by lnxquestions on 2006-06-28
What do you mean with the all needed codecs ? Is to what in oyvindaa link ? And how  to install mplayer or others for firefox ?

---

### Post by frodon on 2006-06-28
I mean the codecs needed to read mpeg, avi, mp3, wmv, wma, realplater, dvd, ... which are not installed by default. The link i gave you explain how to install all these codecs.

For the media player connectivity extension, it is an extension of firefox so just go in the tool tab of firefox and click on extension then click on "get more extensions" and search the media player connectivity extension.
For the mplayer plugin, it's a package in the repositories called mozilla-mplayer or something like that, perform a search in synaptic and you will find it quickly.

---

### Post by lnxquestions on 2006-06-28
And if i downloaded those codecs will vlc play wmv too ? Because it play them just voice now .

---

### Post by mickutz on 2006-06-28
You could try with Automatix. You can install the codecs, players and plugins. You can remove what you don't need afterwards.

[http://www.ubuntuforums.org/showthread.php?t=190025&highlight=automatix+6.06](http://www.ubuntuforums.org/showthread.php?t=190025&highlight=automatix+6.06)

---

### Post by frodon on 2006-06-28
Don't know for VLC but in general all the players share the same codec libraries so that's worth to test.

---

### Post by FredB on 2006-06-28
[QUOTE=frodon]Don't know for VLC but in general all the players share the same codec libraries so that's worth to test.[/QUOTE]

VLC is using its own files for codecs.

And using automatix is sometimes a bad idea with Dapper.

---


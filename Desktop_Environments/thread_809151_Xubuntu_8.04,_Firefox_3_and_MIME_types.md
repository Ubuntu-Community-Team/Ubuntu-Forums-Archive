---
title: "Xubuntu 8.04, Firefox 3 and MIME types"
date: 2008-05-27
forum: Desktop Environments
---

### Post by librano on 2008-05-27
Hi all!

I installed Xubuntu 8.04 and I am facing a problem. The thing is that if I download a file, e.g. an mp3 in Firefox 3, I get the 'Open with' or 'Save As' dialog... but in the 'Open with' option no applications are listed with which to open the file. I have to manually browse the the /usr/bin/ directory and select the application... I know that MIME types are configured properly in the system because thunar selects the appropriate application automatically. This problem is only in Firefox 3.

what additional settings should I add? or what package should I install to get Firefox to properly recognize MIME types?

Thanks.

---

### Post by stiffmaster on 2008-05-27
I actually have the same error using gnome and ff3... I'd be curious to know the answer of that too!

---

### Post by librano on 2008-05-27
seems like its a Firefox 3 bug

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/185278](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/185278)

so annoying though...

---

### Post by BryanFRitt on 2008-06-21
How did this error get past testing to make it past the release Candidate(rc) stage of development?

---

### Post by starscalling on 2008-06-21
if you know the program you want it to use, its really easy
just click the button, and type the path to it.


say you want mplayer to play the audio:

in terminal do: which gmplayer
starz@kewl ~ $ which gmplayer
/usr/bin/gmplayer
and then just type that when that box pops up, you dont have to click click click lol

annoying, but it works.

---

### Post by BryanFRitt on 2008-06-21
Some don't even have the option to 'Open Containing Folder' nor to 'Open' the file.

---

### Post by jdarias on 2008-06-21
This partially fixes it:

sudo apt-get install firefox-gnome-support

---


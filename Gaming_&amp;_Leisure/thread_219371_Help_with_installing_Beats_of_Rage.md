---
title: "Help with installing Beats of Rage?"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by Xzallion on 2006-07-19
I wanted to try out [Beats of rage]("http://www.senileteam.com/") when I found it in the [Ubuntu game list]("http://doc.gwos.org/index.php/Beats_of_Rage"), but I can't figure out how to get it to work.  I downloaded the Ubuntu Executable and what I believe is the dos version (The pc download), and I copied the Ubuntu executable into the BOR folder, set it as executable, and tried to run it, and nothing happens.

Then I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=200715&highlight=beats+rage") that suggests using openBOR, but I can't find the site for openBOR on google or the official BOR site.

Does anyone know how to get Beats Of Rage working in Ubuntu? Or where to get openBOR?

---

### Post by DoktorSeven on 2006-07-19
Just tried it myself - apparently it expects the data file's filename (BOR.PAK) to be lowercase - so rename BOR.PAK to bor.pak and re-run bor.lxe.

---

### Post by Xzallion on 2006-07-19
Awesome!  Thanks DoktorSeven!

Edit: it works wonderfully, it just runs in a really tiny window, is there any way to make it run full screen?

---

### Post by DoktorSeven on 2006-07-20
Not that I could see.

---

### Post by Xzallion on 2006-07-20
Kay, thanks for checking DoktorSeven. :)

---

### Post by DoktorSeven on 2006-07-20
Ooh, actually there is:
./bor.lxe -res 1024 768 
(or whatever your desktop res. is)

---

### Post by kblood on 2006-08-30
Ok, I got it to run, but only with 11025Hz and 8bit sound. If I change that, sound is gone. Any ideas?

Also, it runs incredibly slow! Any tips on checking what could be causing it?
I am trying to run it on a laptop with Centrino 1.7Ghz, 512Mb RAM, and a GeforceGo 6400. Is this good enough?

Thanks!

---


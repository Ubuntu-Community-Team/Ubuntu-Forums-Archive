---
title: "Marathon AlephOne (20070525 release) in Ubuntu 7.04"
date: 2007-07-11
forum: Gaming &amp; Leisure
---

### Post by the_eternal_dark on 2007-07-11
Ok, I visited [http://source.bungie.org/get/](http://source.bungie.org/get/) and downloaded the Linux version of the free engine as well as the 3 original games so that I could play on my new PC. After downloading the required files and dependencies (sdl, lua, etc) and running ./configure and make, i received the error, "FATAL: Please be sure the files 'Map', 'Shapes', 'Images' and 'Sounds' are correctly installed and try again." I attempted to find the AlephOne directory (in /usr/local/AlephOne) so that I could copy those needed files to that directory from one of the three original games, but the directory did not exist and neither did the /bin files either. 

I followed this install walkthrough here: [http://ubuntuforums.org/showthread.php?t=261577&page=2&highlight=marathon](http://ubuntuforums.org/showthread.php?t=261577&page=2&highlight=marathon)

Are there dependencies missing or have I done something wrong? Or is there just a problem with the newest release of the AlephOne engine? 

:confused:

---

### Post by FoolsGold_MKII on 2007-07-11
If the directory doesn't exist, make it.

---

### Post by the_eternal_dark on 2007-07-11
I've tried it already too. It keeps giving the same error though, and nothing is being added to the directory after running make either. :-x

I have also made sure that it is the correct directory as well. I've also tried changing the prefix, but it's all turning the same error.

---

### Post by FoolsGold_MKII on 2007-07-11
I fear to ask in case it makes you look dumb (not my intention!), but...

according to your link [http://source.bungie.org/get/](http://source.bungie.org/get/)

did you even download the marathon data files they TELL you do download in the text at the top of the page? specifically the top-left link? I did it just now, have yet to run it though...

---

### Post by FoolsGold_MKII on 2007-07-11
Ok, I got it to work.

Download [http://trilogyrelease.bungie.org/files/M1A1.zip](http://trilogyrelease.bungie.org/files/M1A1.zip)

Unzip it somewhere. Inside the folder there will be a bunch of files and subfolders. Copy this all to /usr/local/share/AlephOne (a folder which DOES exist after you run make install - you stated the wrong folder)

Run alephone and it should work. I implore you to read files like the INSTALL.Unix file they gave you next time - they write these things for a reason. :)

---

### Post by luisromangz on 2007-07-11
In my case, the default folder that the installer creates and you have to put the datafiles in is /usr/share/AlephOne. You should use another if you specified it configure's prefix option.

Great ol' game btw!

---

### Post by the_eternal_dark on 2007-07-11
Sorry, I did not read the install.unix correctly. I typed my prefix incorrectly (hey, it was 4 am..). I just re-did everything and it works fine now.

Thanks guys.

---


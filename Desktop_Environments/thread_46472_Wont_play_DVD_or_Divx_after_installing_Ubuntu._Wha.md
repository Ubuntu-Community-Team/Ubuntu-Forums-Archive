---
title: "Wont play DVD or Divx after installing Ubuntu. What else I need?"
date: 2005-07-04
forum: Desktop Environments
---

### Post by braveerudite on 2005-07-04
Please help getting the right codecs for playing the most popular video  formats (DVD,Xvid,Dvix,...)  What/How could I get/need to play these on my Ubuntu system??? ](*,)

---

### Post by Bandit on 2005-07-04
[QUOTE=braveerudite]Please help getting the right codecs for playing the most popular video  formats (DVD,Xvid,Dvix,...)  What/How could I get/need to play these on my Ubuntu system??? ](*,)[/QUOTE]

Go to here and download and install MPlayer, its easy.
If you need any help let us know.
[http://www.mplayerhq.hu/homepage/index.html](http://www.mplayerhq.hu/homepage/index.html)

Also if you havent installed cc, gcc or the rest of the compiler tools then you will need to. You can get these using the Synaptic Packager Manager.

Cheers,
Joey

---

### Post by varunus on 2005-07-05
The guide has info on how to install codecs:

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) 

Enjoy.

---

### Post by braveerudite on 2005-07-05
I went to [http://amd64.ubuntuguide.org/#codecs](http://amd64.ubuntuguide.org/#codecs) and installed the codec's... Now I can hear but not see whats going on .... It would show me the title of the file and hear the audio but cant see whats going on... Plz help

---

### Post by varunus on 2005-07-05
That's strange...the amd64 doesn't seem to include as many packages as the 386 howto does.  I don't know if these packages (namely libdvdcss2 and w32codecs) are available for amd64.  Maybe try installing them from the command line and see if it works?  Can an AMD64 user help out here?

---

### Post by Bandit on 2005-07-05
[QUOTE=varunus]That's strange...the amd64 doesn't seem to include as many packages as the 386 howto does.  I don't know if these packages (namely libdvdcss2 and w32codecs) are available for amd64.  Maybe try installing them from the command line and see if it works?  Can an AMD64 user help out here?[/QUOTE]
The win32codecs should work. They are just codec files that are read for translation information. Also they just placed in the codec dir and are compiled for any system in perticular.
If you go with MPlayer installation is easier for the 64bit systems.
IMHO,
Joey

---

### Post by tseliot on 2005-08-04
If you want to use win32 codecs in Ubuntu 64bit just follow my HOWTO, it's easy:

[http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399)

---


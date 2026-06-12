---
title: "Realplayer10 - Pleeease"
date: 2005-10-14
forum: Desktop Environments
---

### Post by tkonicz on 2005-10-14
Hi. I am actually looking for a properly Working realplayer10 for my 5.10 Ubuntu. I have read the "Restricted Formats" Wiki and I have found the "Realplayer-Installer" in the contributions, which is not aviable on the realplayer-hompage any more. But I really would like to use the Realplayer10, which I am used to. :???:  So, pleeeeease, tell me someone of you proffesionals where to find a Realplayer10, which works with ubuntu and as a plugin in firefox. BTW... Is there something simmiliar like "apt-get.org" for Ubuntu, where the user can browse all the repositories, that are aviable for Ubuntu?
Thanks in advance, 
tkonicz

---

### Post by bin on 2005-10-14
Add the following to your sources

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

Reload and then you'll find Realplayer 10.0.6

Select and install

To get it going with Moz you may need to create a folder called plugins in your .mozilla/firefox folder. In that you put a couple of symlinks pointing to 

/usr/lib/mozilla/plugins/nphelix.xpt
/usr/lib/mozilla/plugins/nphelix.so

Away you go

in light

bin

---

### Post by jaypeesmith on 2005-10-14
You can also go to real.com and download the .bin file from there.

---

### Post by tkonicz on 2005-10-14
Thanks for the infos.

---

### Post by Trigger on 2005-10-14
[QUOTE=jaypeesmith]You can also go to real.com and download the .bin file from there.[/QUOTE]
What do you then do with the Bin?
Forgive me I am new, but very willing to learn.

---

### Post by dto on 2005-10-14
edit: whoa -- I totally responded to the wrong thread. Sorry. :)

---

### Post by Ampersand on 2005-10-14
[QUOTE=Trigger]What do you then do with the Bin?
Forgive me I am new, but very willing to learn.[/QUOTE]

The .bin is similar to a .exe in Windows. Firstly open a terminal (from the Accesories menu), use 'cd' to change directory to the folder that contains the bin (if you downloaded it with firefox, the command would probably be 'cd Desktop', then you need to make it executable. To do this, type 'chmod a+x' followed by the name of the file ('chmod a+x realplay-*version-name*.bin'. Note that it's case sensitive).

You can then run it by typing ./realplay-*version-name*.bin . The ./ means (in this directory).

---

### Post by cbudden on 2005-10-14
The bin worked fine for me, firefox plugin aswell.

---

### Post by Zarkoth on 2005-10-15
Oddly enough, after I installed everything, I managed to make it so that...well, it just doesn't work.  I click on realplay.sh and nothing goes down....same thing with realplay.bin, even after I throw chmod a+x at it.

Any ideas?

---

### Post by chajuram on 2005-10-15
A nice realplayer help post.

[http://www.ubuntuforums.org/showthread.php?t=7017&page=3&pp=10&highlight=real+player]("http://www.ubuntuforums.org/showthread.php?t=7017&page=3&pp=10&highlight=real+player")

---

### Post by manicka on 2005-10-15
[QUOTE=bin]Add the following to your sources

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

[/QUOTE]

Using the marillat repo will break your system. It is recommended not to use it. I'd recommend using the other methods. 

I've also had luck just downloading the rpm and using alien to make a deb. It works perfectly.

---

### Post by sbassett on 2005-10-15
[QUOTE=manicka]
I've also had luck just downloading the rpm and using alien to make a deb. It works perfectly.[/QUOTE]

Same. Just to note though,  this will install into /usr/local/Realplayer directory. But she works smooth as beans. :p

---

### Post by bionnaki on 2005-10-15
I got the .bin realplayer 10 installed. it loads just fine, however, there is no sound. any ideas?

---

### Post by gingermark on 2005-10-15
[QUOTE=manicka]Using the marillat repo will break your system. It is recommended not to use it. I'd recommend using the other methods. 
[/QUOTE]
Just to say I think using the marillat repository is the best way of getting Realplayer, just as long as you then remove it from your sources.list afterwards. The Debian version of Realplayer works fine, and is far easier to remove than using the .BIN file.

---

### Post by manicka on 2005-10-16
[QUOTE=gingermark]Just to say I think using the marillat repository is the best way of getting Realplayer, just as long as you then remove it from your sources.list afterwards. The Debian version of Realplayer works fine, and is far easier to remove than using the .BIN file.[/QUOTE]

Yes, that's fine if you have some experience with different repos. It's just important for newer users to understand that it _**must**_ be removed from the sources.list after use (as you've recommended :) ), hence the recommendation not to use it, just in case something goes wrong and it remains in there.

---


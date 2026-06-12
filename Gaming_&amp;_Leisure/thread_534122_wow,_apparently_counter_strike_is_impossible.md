---
title: "wow, apparently counter strike is impossible"
date: 2007-08-24
forum: Gaming &amp; Leisure
---

### Post by Valkyrie Wrath on 2007-08-24
i cant start steam, i get this message even after deleting the blob files

[IMG]http://i71.photobucket.com/albums/i141/Bodomshadow/Screenshot-ERROR.png[/IMG]

---

### Post by jacob01 on 2007-08-24
try to uninstall wine and delete the wine directory .wine   then start over and install wine  and follow this tutorial

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

yea  thats about all i know of but you could also try the wine irc. Install a irc client and then once logged into server just ask you question and some one will help you

i believe the easiest irc client is  chatzilla just seach it and you should find a link to install it on firefox and then let firefox install it for you

then once chatzilla is installed just type the irc address into the firefox address bar and it will bring you there

wine irc =  irc://irc.freenode.net/winehq

hope you get your problem resolved

---

### Post by Highbuzz on 2007-08-25
Whilst I am a total noob at Linux-Ubuntu I had a friend of mine install Steam and CS:S and 1.6. We ran into a little issue but fixed it easily. The games run great now. And I'm posting this to give you hope and maybe a little bump. :)

---

### Post by Valkyrie Wrath on 2007-08-25
ok guyz thanks,

also

what my problem is, is that the fake wine c drive is too small(i also do not want to reinstall counter strike[i already have it on my winblows partition]

i think this has somehting to do with it because wining the steam install was flawless

ill just do the irc ty

:guitar:

---

### Post by Mogurijin on 2007-08-25
You could always just try to play them off of you Windows partition ;). Add the partition to your list of drives in the winecfg and make sure you have ntfs-config if your windows drive is formatted NTFS. Also, you might want to make a script that cds to the folder and then runs the exe such as:

```
cd "/media/hda1/Program Files/etc/game folder/"
WINEDEBUG=-all wine game.exe
```

Then you could set up a launcher on your desktop.

---


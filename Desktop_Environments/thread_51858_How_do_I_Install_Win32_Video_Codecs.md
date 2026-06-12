---
title: "How do I Install Win32 Video Codecs?"
date: 2005-07-25
forum: Desktop Environments
---

### Post by Gimmie an A on 2005-07-25
I opened Kaffine for the first time,and read that I needed the win32 codecs and libdvdcss. I downloaded them, but what next? How do I install them? I'm a newbie, so please explain.
Thanks.

---

### Post by damonw5 on 2005-07-25
[QUOTE=Gimmie an A]I opened Kaffine for the first time,and read that I needed the win32 codecs and libdvdcss. I downloaded them, but what next? How do I install them? I'm a newbie, so please explain.
Thanks.[/QUOTE]
 You can install them using the command line.
Enabling extra repositories: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
Installing codecs: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
DVD Playback: [http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

Whenever the instructions say "gedit", rplace it with a KDE text editor such as "kate". Alternatively, once you enable the repositories you can install all the packages in a user-friendly way by using Kynaptic.


Someone had the exact same question here:
[http://ubuntuforums.org/showthread.php?t=51282](http://ubuntuforums.org/showthread.php?t=51282)

If you need more help, give us a holler! :)

---

### Post by Gimmie an A on 2005-07-25
> connor@Kubuntu:~$ sudo kate /etc/apt/sources.list
Password:
kate: ERROR: Communication problem with kate, it probably crashed.
connor@Kubuntu:~$ 

?????????
What now? Whats wrong?

---

### Post by manicka on 2005-07-25
See if you get the same error using kwrite instead of kate?

sudo kwrite /etc/apt/sources.list

---

### Post by Gimmie an A on 2005-07-25
Ahh...got it. Thanks!!!

---

### Post by Freddy on 2005-07-25
Kate seems to have some difficulties when you use it as root, don't know if this is Kubuntu related or not but Kate is working fine on my Fedora.

You can as earlier said use Kwrite or install Kedit another fine editor and a little more "slim" then the big Kate.

/Freddan

---


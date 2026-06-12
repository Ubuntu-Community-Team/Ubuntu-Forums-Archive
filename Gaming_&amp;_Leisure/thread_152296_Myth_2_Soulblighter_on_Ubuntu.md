---
title: "Myth 2: Soulblighter on Ubuntu"
date: 2006-03-29
forum: Gaming &amp; Leisure
---

### Post by Speque on 2006-03-29
Has anyone been able to make Myth 2: Soulblighter (port for Linux by Loki Games) work on Ubuntu? On my computer the game itself installs itself well, but starting the game results a crash.

One possible cause for this is that the game requires XFree86 3.3.x to work. If I have understood correctly, XFree and X.org have lots of common code, so could it be possible to get Myth 2 working with X.org?

---

### Post by Speque on 2006-05-10
Hello? Anyone?

---

### Post by patrick295767 on 2006-05-10
[QUOTE=Speque]Has anyone been able to make Myth 2: Soulblighter (port for Linux by Loki Games) work on Ubuntu? On my computer the game itself installs itself well, but starting the game results a crash.

One possible cause for this is that the game requires XFree86 3.3.x to work. If I have understood correctly, XFree and X.org have lots of common code, so could it be possible to get Myth 2 working with X.org?[/QUOTE]
  
Lucky boy, I just bought the Full CD one month ago (to one friend).
  
This game is working very very very well with Linux !
(no loki needed) (No lags due to wine )
Just wine
  
(Private Msg me if you would like more information about it)
  
Greetz !

---

### Post by Speque on 2006-05-11
[QUOTE=patrick295767]Lucky boy, I just bought the Full CD one month ago (to one friend).
  
This game is working very very very well with Linux !
(no loki needed) (No lags due to wine )
[/QUOTE]

That's a bit ironic, as the version I have does not include a Windows version of the game, just the Linux version. So Wine does not do any good for me. If only there was a way to make it work with Ubuntu and X.org... :(

---

### Post by slux on 2006-05-11
Last time I played my Linux version of Myth 2, the latest patch did the trick. That was with XFree86 4.2 or 4.3 so things may've changed though.

Try getting the update from here and see if that does the trick:
[ftp://sunsite.dk/mirrors/lokigames/updates/myth2/](ftp://sunsite.dk/mirrors/lokigames/updates/myth2/)

---

### Post by Speque on 2006-10-25
Got it working! :p Here is how:

1) Installed the game (installation option "full")
2) Applied this patch: [ftp://sunsite.dk/mirrors/lokigames/updates/myth2/myth2-1.3e-unified-x86.run](ftp://sunsite.dk/mirrors/lokigames/updates/myth2/myth2-1.3e-unified-x86.run)
3) Installed package libglide2
4) Renamed the directory cutscenes (under /usr/local/games/myth2/) to something else (game crashes if the cutscenes are shown)
5) Run the game

Got to love that game!

---

### Post by whirl on 2008-02-29
> **Speque said:**
> Got it working! :p Here is how:

1) Installed the game (installation option "full")


How does one actually install the game? I cannot launch this setup.sh with skills Ive been blessed with. Heres what Ive tried this far:

```
koti@paske:~$ cd /media/cdrom0/
koti@paske:/media/cdrom0$ sh setup
setup: 10: function: not found
x86
koti@paske:/media/cdrom0$ sh setup.sh
sh: Can't open setup.sh
koti@paske:/media/cdrom0$ sudo sh setup
Password:
setup: 10: function: not found
x86
koti@paske:/media/cdrom0$ sudo sh setup.sh
sh: Can't open setup.sh
koti@paske:/media/cdrom0$ 

```

So umm.. Would be great if I could actually install a game which has a native linux installer :p

Cheers!

---

### Post by whirl on 2008-03-12
*bumb*

So anyone here who got this baby working? Im using ubuntu 7.10 and I understand this is very old game but it would be cool to get it working.

Cheers!

---

### Post by Perfect Storm on 2008-03-12
Try copy the linux installer to your HDD.

```
cd <path>
chmod +x <installer>
sudo ./<installer>
```

---

### Post by whirl on 2008-03-13
Thanks for the help but that didnt seem to help me. Any other ideas? Ive send help request to tuxgames too but lets see what happens.

Heres what I did:
```
whirl@spinning:~/Myth2Soulblighter-Linux$ chmod +x setup
chmod: changing permissions of `setup': Operation not permitted
whirl@spinning:~/Myth2Soulblighter-Linux$ sudo chmod +x setup
[sudo] password for whirl:
whirl@spinning:~/Myth2Soulblighter-Linux$ sudo ./setup
./setup: 10: function: not found
x86
whirl@spinning:~/Myth2Soulblighter-Linux$ sudo ./setup.sh
sudo: ./setup.sh: command not found
whirl@spinning:~/Myth2Soulblighter-Linux$ sudo ./setup
./setup: 10: function: not found
x86
whirl@spinning:~/Myth2Soulblighter-Linux$ 
```

---

### Post by whirl on 2008-03-13
Thanks for the help but that didnt seem to help me. Any other ideas? Ive send help request to tuxgames too but lets see what happens.

Heres what I did:
```
whirl@spinning:~/Myth2Soulblighter-Linux$ chmod +x setup
chmod: changing permissions of `setup': Operation not permitted
whirl@spinning:~/Myth2Soulblighter-Linux$ sudo chmod +x setup
[sudo] password for whirl:
whirl@spinning:~/Myth2Soulblighter-Linux$ sudo ./setup
./setup: 10: function: not found
x86
whirl@spinning:~/Myth2Soulblighter-Linux$ sudo ./setup.sh
sudo: ./setup.sh: command not found
whirl@spinning:~/Myth2Soulblighter-Linux$ sudo ./setup
./setup: 10: function: not found
x86
whirl@spinning:~/Myth2Soulblighter-Linux$ sh setup
setup: 10: function: not found
x86
whirl@spinning:~/Myth2Soulblighter-Linux$ sh setup.sh
sh: Can't open setup.sh
whirl@spinning:~/Myth2Soulblighter-Linux$ 
whirl@spinning:~/Myth2Soulblighter-Linux$ 
```

edit: typos and forgotten lines

---

### Post by Perfect Storm on 2008-03-13
Try sudo infront of the chmod command.

---

### Post by whirl on 2008-03-13
I did mate ;)

---

### Post by alienjon on 2008-05-26
Try 'bash' instead of 'sh'.

The script requests usage of the 'sh' shell (which, if I remember my Unix history correctly, was the original shell)  Explicitly calling 'bash' fixed the problem for me. Try:

```
cd /pathTOcd/
sudo bash setup
```

This is assuming 2 things.  Firstly, that the 'setup' file has +x (execute) permissions (on my cd, it has that be default and I'd be kinda surprised if it was anything but, assuming you're using an original cd).  The second thing is that you want to do a system-wide install.  If you are installing the game locally (in a directory your user can write to (the default is /usr/share/games and is only writable by root)) then you can omit the 'sudo'.

---

### Post by eragon100 on 2008-05-26
Just use a virtual machine with an ancient linux distro in virtual box :)

---

### Post by whirl on 2008-07-08
> **alienjon said:**
> Try 'bash' instead of 'sh'.

The script requests usage of the 'sh' shell (which, if I remember my Unix history correctly, was the original shell)  Explicitly calling 'bash' fixed the problem for me. Try:

```
cd /pathTOcd/
sudo bash setup
```

This is assuming 2 things.  Firstly, that the 'setup' file has +x (execute) permissions (on my cd, it has that be default and I'd be kinda surprised if it was anything but, assuming you're using an original cd).  The second thing is that you want to do a system-wide install.  If you are installing the game locally (in a directory your user can write to (the default is /usr/share/games and is only writable by root)) then you can omit the 'sudo'.

Thanks for that it seemed to work. But now when I try to actually run the game it boots right away so something weird is happening. When I try start uninstall it wont start so any ideas how I could get rid of this installation so I could try installation again?

And secondly Ive read about these updates from loki but it seems there are no servers out there where you could download those files. Is there someone out there who would know more?

Thanks again o/

---

### Post by pofigster on 2008-07-11
[http://lokifiles.tuxgames.com/updates/myth2/](http://lokifiles.tuxgames.com/updates/myth2/)

But it's being stupid and not running.  I did and md5 check and it matched, but when I actually run it, it complains about failed integrity.
```
Verifying archive integrity...tail: cannot open '+6' for reading: No such file or directory
Error in check sums 3190307604 1860412617
```

Does anybody have any ideas on why I can't get this patch to run?

---

### Post by mudfly on 2008-08-03
Looks like there is quite a bit of info about this on the gentoo wiki.

[http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)

I haven't got this working on Ubuntu.

---

### Post by _march_ on 2008-11-02
At [http://wiki.ubuntuusers.de/Spiele]("http://translate.google.com/translate?u=http%3A%2F%2Fwiki.ubuntuusers.de%2FSpiele&hl=de&ie=UTF-8&sl=de&tl=en") a few articles can be found.

---

### Post by scorchedbysun on 2009-04-28
In case anyone is still interested, I compiled all the information about this I could find and put it here:

[http://www.ode2.com/?p=7](http://www.ode2.com/?p=7)

The game now runs without any problems, cutscenes, OpenGL and all.

---


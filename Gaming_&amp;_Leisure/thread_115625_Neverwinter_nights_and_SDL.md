---
title: "Neverwinter nights and SDL"
date: 2006-01-10
forum: Gaming &amp; Leisure
---

### Post by ravalox on 2006-01-10
Okay, so I got neverwinter nights and followed their install instructions; I untarred the resources for it then the binaries.  Now when I try to run the game, i.e. ```
./nwn
``` it errors with:
```
Failed to initialize SDL Video: No I/O port permissions
```

So I tried running it as root, and my video went all corrupted and I had to ctrl-alt-backspace.  I have a 5.10 install on a pentium4, ATI radeon 9000 computer.  I play Unreal Tournament 2004 on this machine so I know the drivers work.  Anyone have any practical advice?

---

### Post by leech on 2006-01-10
Which install instructions did you use, and which edition of the game are you using?  Last of all, which patch version do you have installed?  The latest version is 1.66

Leech

---

### Post by ravalox on 2006-01-11
Well I had to get a linux client from the jeuxlinux.com ftp since their Bioware's registration system appears to be down.  So I am trying this with version 1.29.  I bought Neverwinter Nights, Platinum which has everything but I don't think it has a linux client/installer so I just downloaded the resources and am trying to use the keys from the platinum edition.   But this has happened to me before with stellarium, so I suspect this is an Ubuntu issue, but it works for other people so maybe I need to try the latest client.  But if anyone has gotten the ```
Failed to initialize SDL Video: No I/O port permissions
``` please speak up now.

And also those instructions in your sig look helpful, I'm in hte thick of them now so we'll see if it works.

---

### Post by leech on 2006-01-11
They have worked here flawlessly every time I've tried it (about three or four times).

If you have an issue with the installer linked to in the HOWTO, then try the one at [http://thefnords.org/install-nwn.sh](http://thefnords.org/install-nwn.sh)

Leech

---

### Post by akurashy on 2006-01-12
[quote=leech]They have worked here flawlessly every time I've tried it (about three or four times).

If you have an issue with the installer linked to in the HOWTO, then try the one at [http://thefnords.org/install-nwn.sh]("http://thefnords.org/install-nwn.sh")

Leech[/quote]

Else if you run into errors with his .sh you can try the loki gamers installer it works smoothly, used it :D 

[http://liflg.org/?catid=6&gameid=65](http://liflg.org/?catid=6&gameid=65)

( NOTE: DO NOT RUN THE SH AS ROOT AS YOU WILL NOT BE ABLE TO LOAD MODULES LATER ) 

Enjoy!

---

### Post by leech on 2006-01-12
Yes, the loki installer is great as well, but doesn't support the Platinum edition, which the installer that I have posted does.  The Loki installers support the original, as well as if you have the original, along with the Shadows of Untertide and the Hordes of the Underdark separately.

For the Gold Edition installer, go to [http://icculus.org/~ravage/](http://icculus.org/~ravage/) There you can find loki installers for a lot of games, including the Gold edition of Neverwinter Nights.  

Hopefully eventually someone will create a loki installer for the Platinum and maybe the Diamond edition (currently the Diamond edition is just like the Platinum, but there is no known method yet to install the Kingmaker module)

Leech

---

### Post by akurashy on 2006-01-12
Yea I know about icculus.org/~ravage , its very handy too :D can't wait till i get my gold edition to play :)

---

### Post by leech on 2006-01-12
[QUOTE=ravalox]Well I had to get a linux client from the jeuxlinux.com ftp since their Bioware's registration system appears to be down.  So I am trying this with version 1.29.  I bought Neverwinter Nights, Platinum which has everything but I don't think it has a linux client/installer so I just downloaded the resources and am trying to use the keys from the platinum edition.   But this has happened to me before with stellarium, so I suspect this is an Ubuntu issue, but it works for other people so maybe I need to try the latest client.  But if anyone has gotten the ```
Failed to initialize SDL Video: No I/O port permissions
``` please speak up now.

And also those instructions in your sig look helpful, I'm in hte thick of them now so we'll see if it works.[/QUOTE]

Were you able to get this working?  Hopefully we can all put a game (or a few) together as a group to play.

Leech

---

### Post by ravalox on 2006-04-13
I did, there is a shell script that works beautifully, how would we form a group?

---


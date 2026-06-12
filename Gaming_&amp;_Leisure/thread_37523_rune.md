---
title: "rune"
date: 2005-05-27
forum: Gaming &amp; Leisure
---

### Post by Poul on 2005-05-27
i've installed loki version of rune but i doesn'tt want to start
Here's the output:
```
paul@paul:~$ rune
dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Rune (rune-bin). Is RUNE_DATA_PATH set?
paul@paul:~$

```

---

### Post by cdhotfire on 2005-05-27
lol, you play rune?

you should not play that linux version, it is 1.06 or .07 so you wont be able to play much.  Only way ull play 1.00 is with cedega.  But to awnser your question.

look for the rune start script here [font=Verdana, Arial, Helvetica, sans-serif][size=2]/usr/local/bin. i think its rune.sh

```

$ sudo gedit /user/local/bin/rune.sh

```

then look for somethin that looks like this:

[/size][/font][font=Verdana, Arial, Helvetica, sans-serif][size=2] export RUNE_DATA_PATH

and change it to

[/size][/font][font=Verdana, Arial, Helvetica, sans-serif][size=2] export UT_DATA_PATH=/usr/local/games/ut/System/


after that save the file, close the gedit.
```

$ sudo rune

```

and your rolling like a big dawg.:)
[/size][/font]

---

### Post by Poul on 2005-05-27
Does this mean that i have to have unreal tournament installed in order to be able to play rune ??

---

### Post by cdhotfire on 2005-05-27
Lmao, oops.:|

[font=Verdana, Arial, Helvetica, sans-serif][size=2] export RUNE_DATA_PATH=/usr/local/games/rune/System/

:)

Edit: onelss u have hov(halls of valhalla) expansion your not gonna be able to play much with this rune version.  Version 1.07 is considered hov, so if u install rune with version 1.07 and its not hov, your not gonna play much, onless someone was nice enough to change their rune.ini for your pleasing.:-?
[/size][/font]

---

### Post by dolny on 2005-05-28
...and if I have the Halls of Valhalla add-on. How do I install it on Linux?

---

### Post by cdhotfire on 2005-05-28
do you have linux version?

---

### Post by dolny on 2005-05-28
Nah... downloading the Linux version when I have the Windows version should be legal ;) Damn.

---

### Post by JonahRowley on 2005-05-28
Why **sudo rune**?  Why should rune be run as root?  And yeah, the loki scripts are kind of broken on modern distros.  I've had similar problems with other loki games.

---

### Post by cdhotfire on 2005-05-28
[QUOTE=JonahRowley]Why **sudo rune**? Why should rune be run as root? And yeah, the loki scripts are kind of broken on modern distros. I've had similar problems with other loki games.[/QUOTE]

yes, one should use sudo rune, onless you before install did **sudo chown user:user /usr/local**, this is because thats where installation files go.  So if your a total noob and your like. WHAT, THE SETUP DOESNT LET ME INSTALL!!!, this person problem says, O YA LET ME USE SUDO, BECAUSE IT TELLS ME THAT ITS RESTRICTED.  Then you do **sudo rune.sh**(in cdrom) then you install, so if you go **rune** ill say restricted then the person goes, O YA I SET IT WIT SUDO, so he goes **sudo rune**. And thats thats the end.:???:

---

### Post by cdhotfire on 2005-05-28
[QUOTE=dolny]Nah... downloading the Linux version when I have the Windows version should be legal ;) Damn.[/QUOTE]

im a frequent player in the rune world, if you have the original Rune, maybe we can play, o and im a real pro.;-)

---

### Post by JonahRowley on 2005-05-29
Are you sure about needing sudo?  I've played other lokigames before, and of course the installer needs to be run as root, but the program itself was fine.  It used dotfiles in $HOME to store data, and worked quite well..

---

### Post by cdhotfire on 2005-05-29
yes i know what u mean, but this one is diff i guess.  Ive installed it many times and everytime i run **rune** it starts loading the packages and then after the 10th one it says file cannot be access, so then i go like, "I must need sudo", i use **sudo rune** and then everythin goes fine.:-?

---

### Post by slux on 2005-05-30
[QUOTE=dolny]Nah... downloading the Linux version when I have the Windows version should be legal ;) Damn.[/QUOTE]

While with Rune the situation isn't so clear since the company that ported Rune went out of business anyway, this is generally **wrong** .

Owning the Windows version of a game that, for example, [Linux Game Publishing](http://www.linuxgamepublishing.com/)  has paid the original creator to be able to work on and tries to sell isn't legal or even moral and will certainly hurt the Linux gaming community.

<edit>
Since we're on a GNU/Linux forum anyway...

Ok, it might be moral if you believe the FSF arguments for free software (as I happen to do) but there are still issues with copying proprietary software even if proprietary software is unethical.

However, currently free software isn't supported by the business model of the games industry and it may be hard to find one that does suit it. I choose to support the companies doing work to give us Linux gamers' more to play by buying the games I play as there really aren't a whole lot of them for the time being.
</edit>

That company tries to offer more games to Linux by going thru the work of porting the code to the GNU/Linux platform.  They have nothing to do with the Windows version so you'll be ripping them off if you download one of their games even if you've purchased the Windows version.

Also, I recall playing rune thru with the Linux version so AFAIK it should be playable.

---

### Post by Jesus on 2005-05-30
I've got Rune too and the only way I could get it to run was by hacking the script.
Then I found that it wasn't saving my games. The only way I could get around this was by running with sudo. Still better than when I tried it under Gentoo - then it just crashed when I tried to save.

I completed it btw, very nice game :D
I didn't know there was an expansion, I'll have to look for that.

---

### Post by cdhotfire on 2005-05-30
[QUOTE=Jesus]I've got Rune too and the only way I could get it to run was by hacking the script.
Then I found that it wasn't saving my games. The only way I could get around this was by running with sudo. Still better than when I tried it under Gentoo - then it just crashed when I tried to save.

I completed it btw, very nice game :D
I didn't know there was an expansion, I'll have to look for that.[/QUOTE]

If you liked the game, you gotta play online, this is what rune is known for, not for its story but for its great online play.:)

As i said before i play it quite frequently and so does alot.

---

### Post by slux on 2005-05-31
There's also a coop mode online play installer available for Linux. Would be nice to try some time. :)

[Rune co-op installer](http://icculus.org/runecoop/)

---

### Post by Poul on 2005-06-04
[QUOTE=Jesus]I've got Rune too and the only way I could get it to run was by hacking the script.
Then I found that it wasn't saving my games. The only way I could get around this was by running with sudo. Still better than when I tried it under Gentoo - then it just crashed when I tried to save.

I completed it btw, very nice game :D
I didn't know there was an expansion, I'll have to look for that.[/QUOTE]

Can u give us this script  :grin:

---

### Post by cdhotfire on 2005-06-05
? u still cant get it to work? why would u his script, he said he made it for himself, because his didnt work.

---

### Post by BewareOfPoodle on 2010-11-08
I know that this is a necro-post, but Ima gona say it anyway... :mrgreen:

If you have the windows version of Rune Gold, you can install it through wine, go to prog files/rune/system folder and open rune.exe with wine without a disk in. This then allows you to run it in "safe mode" which is not dependent on Direct X by default (though it is crapier...)  it is playable and works well. It's probably wise to install both discs and restart before opening rune.exe from your wine files.

Also, you can move rune.exe to the upper bar on ubuntu as a application on the launcher in order to quickly access it.

Oh, and don't mind my gramatical errors. I realize that it needs work and I honestly dont care.

---


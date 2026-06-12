---
title: "Another Steam Install Issue"
date: 2006-06-22
forum: Gaming &amp; Leisure
---

### Post by Mr_HeNtAi on 2006-06-22
I'm Running:

Ubuntu 6.06
Wine 0.9.16

When I run the SteamInstall.exe I get the error at 26% like everyone else seems to get but then when  I goto ".wine/drive_c/Program\ Files/" there is no steam directory for me to try the other fixes I've read about. How long should I let the Steam Installer sit at 26%? Does it error out eventually? Any help would be greatly appreciated. Thank You in advanced.

---

### Post by ubu-for on 2006-06-23
Try this!

```
wine C:\Program Files\Steam\SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

---

### Post by Mr_HeNtAi on 2006-06-23
As I said in the post above, It doesn't create the C:\Program Files\Steam directory, therefore it can't find steamtmp.exe. This is a different issue then what I have found on the net. Thank You for the advice, but I must keep looking.

---

### Post by mkw87 on 2006-06-23
I ran into the same problem, I did the following to solve it:

```
cd ~/.wine/drive_c/Program\ Files/Steam
SteamTmp.exe SelfUpdate "Steam.exe" 14
```

To launch steam, for some reason I cannot just type
```
wine Steam.exe
```
I have to browse to the folder ~/.wine/drive_c/Program\ Files/Steam and then type
```
wine Steam.exe
```
before it will launch properly, so I created a script to launch it for me.  Hope this helps, because I went through the fixes you probably tried, even installing from the CD, and it didnt work.

I will say though, I can get CSS to launch, and I can edit the menu, but when I try to connect to a server it insta crashes and mentions something about not having enough memory or whatnot, I haven't had time to look into that, just been playing on my dual boot of XP instead.

---

### Post by Mr_HeNtAi on 2006-06-23
Again I would love to use any of these fixes....But I don't have a Steam directory to do it. The install gets stuck at 26% and never creates a directory.

---

### Post by der_joachim on 2006-06-23
[QUOTE=Mr_HeNtAi]Again I would love to use any of these fixes....But I don't have a Steam directory to do it. The install gets stuck at 26% and never creates a directory.[/QUOTE]

The HL2 GOTY edition installs in another directory than mentioned in the guide above. Type in the following two commands in your console:
```

sudo updatedb
sudo locate Steam | grep -i .exe

```

Your output should be something like this:
```

/usr/local/games/steam/Steam.exe
/opt/fake_windows/Program Files/Valve/Steam/uninstall_steam.exe
/opt/fake_windows/Program Files/Valve/Steam/Steam.exe
/opt/fake_windows/Program Files/Valve/Steam/Unwise32.exe
/opt/fake_windows/Program Files/Valve/Steam/WriteMiniDump.exe
/opt/fake_windows/Program Files/Valve/Steam/bin/makepak.exe

```

Note that the /opt/fake_windows path is my own doing. your fake_windows is probably somewhere in your home directory.

---

### Post by Mr_HeNtAi on 2006-06-23
ok, I love you guys! I couldn't find that until I did what der_joachim recommended. Then I followed some of the stuff that the rest of you told me. Thank You so much!!! Now if I can only get it so I could see the login stuff, but I know I read a work around somewhere.

---


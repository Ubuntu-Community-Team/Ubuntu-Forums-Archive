---
title: "TA Spring mods"
date: 2008-04-09
forum: Gaming &amp; Leisure
---

### Post by viperskunk on 2008-04-09
hi
i just downloaded Spring from the synaptic package manager, following the instructions on their website. however, it says i cannot play the game till i install some mod. i tried installing the CA mod, as instructed on their website. i downloaded the CA downloader and run it;and when it finished downloading stuff, i automatically closed the window.
however, then when i opened the spring lobby and clicked reload maps/mods option, nothing happened.
does anyone have any idea what i might be missing or doing wrong?
please help!
thanks in advance.

---

### Post by Stealth on 2008-04-09
If I remember correctly, all mods should be plaed in your .spring/mods folder (usually in a .sdz or .sd7 format). So you might want to check if you have anything in there.

---

### Post by Hobo Joe on 2008-04-09
If you set it to, the installer will download mods and maps for you. If you didn't do it the first time, you can simply run the installer again.

And IMO, BA is the best mod, I'd recommend it. :)

If you get it workin' let me know, I'll have a game with you.

---

### Post by Ozor Mox on 2008-04-10
From my experience trying to get this game to work, some mods require the original game data from Total Annihilation, and others don't, and it is not labelled on the website which are which. I've found if you don't have the original game it makes it quite tricky, because you end up with either mods that won't launch because of missing data, or very incomplete projects. Very annoying, because the game looks fantastic.

---

### Post by ELD on 2008-04-10
All the Mods with names like "CA" "BA" etc etc all need the total annihilation files to run.

Other mods like kernel panic and pure do not.

---

### Post by Hobo Joe on 2008-04-10
> **Ozor Mox said:**
> From my experience trying to get this game to work, some mods require the original game data from Total Annihilation, and others don't, and it is not labelled on the website which are which. I've found if you don't have the original game it makes it quite tricky, because you end up with either mods that won't launch because of missing data, or very incomplete projects. Very annoying, because the game looks fantastic.

Yes, they do. But there's a simple file you can download off of any of the download sites and place in your Spring folder.

---

### Post by Vadi on 2008-04-10
Strange that the CA downloader didn't work. That said, download the latest CA from here ([click]("http://spring.jobjol.nl/show_file.php?id=952")), and save into the **~/.spring/mods** folder.

Atm you'll need the OTA content too, instructions here ([click]("http://spring.clan-sy.com/wiki/Ubuntu_install#OTA_Content")). Great thing about CA is they're working on replacing all of it, so you'll actually be able to play the game legally (and tell your friends about it).

---

### Post by Ozor Mox on 2008-04-10
> **Hobo Joe said:**
> Yes, they do. But there's a simple file you can download off of any of the download sites and place in your Spring folder.

I haven't done that yet due to questionable legality, but I think I might give it a go. Why not, I expect the copyright holders care about as much as those of TTD!

---

### Post by viperskunk on 2008-04-11
hi guys!
thanks a lot for the replies.
with regards to the installer installing the mods for me...i downloaded spring maps through the synaptic. there was no option for mods there.
is there any other way to get spring working BA or CA that i can try?
i am willing to wait another few hours to download the whole thing, if only i can play this game, which looks really awesome.
and to Vadi:
that was exactly the site that i downloaded it from. and i got the OTA content throught the terminal also.
i am really lost.

---

### Post by Hobo Joe on 2008-04-11
Well, I've downloaded everything through the installer, not through the terminal or synaptic. It's probably the easiest way to do it.

[http://spring.jobjol.nl/download.php?maincategory=1&subcategory=9&file=spring-installer_76b1_2-3-2008.zip](http://spring.jobjol.nl/download.php?maincategory=1&subcategory=9&file=spring-installer_76b1_2-3-2008.zip)

Download that, and when you run it, it should have a checklist of different things you can download. You might as well leave the maps blank unless you want to spend hours downloading them, as it gives you a HUGE amount of them.

Good luck!

---

### Post by Vadi on 2008-04-11
> **viperskunk said:**
> hi guys!
thanks a lot for the replies.
with regards to the installer installing the mods for me...i downloaded spring maps through the synaptic. there was no option for mods there.
is there any other way to get spring working BA or CA that i can try?
i am willing to wait another few hours to download the whole thing, if only i can play this game, which looks really awesome.
and to Vadi:
that was exactly the site that i downloaded it from. and i got the OTA content throught the terminal also.
i am really lost.

Yes, unfortunately mods aren't included because of the OTA content (that would violate Launchpads policy).

So right now, as I understand, you have the SpringLobby (that's what you'll use to play single player / multiplayer), and a bunch of maps for it (not all - because there is over *800* maps for Spring).

To get CA, just paste these lines into the terminal:

```
mkdir ~/.spring/mods
cd ~/.spring/mods
wget http://files.caspring.org/snapshots/1604/ca-stable-1604.sdz
```

And you'll be on your way. Launch SpringLobby (either in Applications - Games or Alt+F2 and "springlobby"), and feel free to join a game online :)

Let me know if you'll be needing any help.

---

### Post by viperskunk on 2008-04-11
hi guys 
thanks a ton for your time and help.

---

### Post by viperskunk on 2008-04-11
i got the mod working through the terminal thing.
however, whenever i try to open the game, it says "cannot open wav file".
is there still something missing or left to do?
i really appreciate your help.

---

### Post by ELD on 2008-04-13
> **viperskunk said:**
> i got the mod working through the terminal thing.
however, whenever i try to open the game, it says "cannot open wav file".
is there still something missing or left to do?
i really appreciate your help.

That error is usually associated with missing content, like the content from TA.

@vadi
there are a few mods like kernel panic, p.u.r.e etc that could be included

---

### Post by Vadi on 2008-04-13
Try pasting these two commands in again:

```
wget http://ipxserver.dyndns.org/games/spring/mods/xta/base-ota-content.zip
unzip -d ~/.spring/base base-ota-content.zip
```

Do you get any errors? If no, try CA again.

---

### Post by viperskunk on 2008-04-16
hi somehow without doing anything now it started working.
thanks a ton guys.

---

### Post by Vadi on 2008-04-16
Cool :)

---


---
title: "How to make XMMS 'minimize' to 'systray'?"
date: 2005-09-01
forum: Desktop Environments
---

### Post by veraction on 2005-09-01
Not sure exactly what its called, but the default "Music Player" that comes with 5.04 will 'minimize' so it goes to top right corner in default gnome setup.

Any way I can do this with XMMS?

---

### Post by nad on 2005-09-02
The only way to minimize xmms is to click the down arrow just above and to the right of the "m" in 'X MULTIMEDIA SYSTEM". There is no way to config it where to minimize to.

---

### Post by nozey on 2005-09-02
Well ... u can minimize to tray. Just had to look on forum.

Here goes the how to:
[http://www.ubuntuforums.org/showthread.php?t=21789&highlight=xmms+tray](http://www.ubuntuforums.org/showthread.php?t=21789&highlight=xmms+tray)

---

### Post by bored2k on 2005-09-02
I think I have a better method. Install Beep media player, wich is more pretty than XMMS and still the same, and then install the bmp-docklet. [http://www.freewebs.com/bored2k/beep-media-player-docklet_1.3-1_i386.deb](http://www.freewebs.com/bored2k/beep-media-player-docklet_1.3-1_i386.deb)

---

### Post by woedend on 2005-09-02
[QUOTE=bored2k]I think I have a better method. Install Beep media player, wich is more pretty than XMMS and still the same, and then install the bmp-docklet. [http://www.freewebs.com/bored2k/beep-media-player-docklet_1.3-1_i386.deb](http://www.freewebs.com/bored2k/beep-media-player-docklet_1.3-1_i386.deb)[/QUOTE]
 why does everyone hate on XMMS...it's the best. BMP is a waste :p.  You can say XMMS is outdated, but thats what I LIKE about it.  I dont want to have every song on my computer have to load up to listen to an MP3, click it, bring up the window and play.

---

### Post by bored2k on 2005-09-02
[QUOTE=woedend]why does everyone hate on XMMS...it's the best. BMP is a waste :p.  You can say XMMS is outdated, but thats what I LIKE about it.  I dont want to have every song on my computer have to load up to listen to an MP3, click it, bring up the window and play.[/QUOTE]
 BMP does have to load "every song on your playlist", that's Rhythmbox's doing, not BMP's.

---

### Post by ssck on 2005-09-02
[QUOTE=bored2k]I think I have a better method. Install Beep media player, wich is more pretty than XMMS and still the same, and then install the bmp-docklet. [http://www.freewebs.com/bored2k/beep-media-player-docklet_1.3-1_i386.deb](http://www.freewebs.com/bored2k/beep-media-player-docklet_1.3-1_i386.deb)[/QUOTE]

hi,

i have installed the docklet .... how do i use it ?

thanks

---

### Post by veraction on 2005-09-02
Well, I wasn't using KDE but figured it out..

```
sudo apt-get install xmms-status-plugin
``` 

then open XMMS. Press Ctrl-P for preferences. Then go to General Plugin tab & activate status docklet plugin

---

### Post by bored2k on 2005-09-02
[QUOTE=ssck]hi,

i have installed the docklet .... how do i use it ?

thanks[/QUOTE]
 Go to BMP settings -- plugins and enable it.

---

### Post by bionnaki on 2005-09-02
yes, I have the docket plugin installed. I can enable it by checking under general. it shows up in the tray, but the player also shows up in my windows list...when I click on the system tray icon, the player closes.

any ideas?

---

### Post by ssck on 2005-09-02
[QUOTE=bored2k]Go to BMP settings -- plugins and enable it.[/QUOTE]

got it.thanks

---

### Post by bionnaki on 2005-09-02
working now.
nevermind.
bmp rules.

---

### Post by Lapse on 2005-09-02
I've got it to show up in tray and all, but when I click on in in order to minimize BMP it closes. Same thing when I rightclick on it and chooses to play a song.

---

### Post by bionnaki on 2005-09-02
I had to log out & log back in for it to work. try that.

---

### Post by Lapse on 2005-09-02
Nope, I've even rebooted the computer. It still closes when I click the BMP in tray.

---

### Post by bionnaki on 2005-09-02
no idea then.
thats what I did.

---

### Post by veraction on 2005-09-02
just noticed that when I try to 'minimize' to the tray, that XMMS stays in bottom list of windows open.

Anyone figure out how to fix that? so that when I minimize it, I can make it just go to the tray & not the bottom part?

[edit]just tried using beep-media-player from apt-get. it seems to lock up every time i try to play a mp3 after approximately 5 seconds (but doesn't play any audio)

oh well. i'd rather have xmms cause it plays music :)

[edit2] compiled newest stable version of bmp just now. same problem w/ crashing.
[B]
[edit3] damn, now my xmms doesn't work for some reason even though it did great before i messed with bmp :(  ](*,) [/B]

---


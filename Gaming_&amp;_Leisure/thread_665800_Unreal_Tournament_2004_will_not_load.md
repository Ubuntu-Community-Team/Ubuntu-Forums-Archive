---
title: "Unreal Tournament 2004 will not load"
date: 2008-01-12
forum: Gaming &amp; Leisure
---

### Post by timboellis on 2008-01-12
I installed it all okay then it asks do you want to run once installed from the term, however if I come out of the game then click on the shotcut in the menu the spash screen pops up for a fraction of a second then dissapears
Any suggestions

Also when you use the rocket launcher i get very pixalated squares any sugggestions

---

### Post by matthewschwimmer on 2008-02-01
hey i got the same thing. I found that if you open up a terminal window, navigate to the folder, and run the file as root via sudo, it should work. I dont know why I have to do that, but it works.

THIS CODE MIGHT NOT WORK. it is for my system, maybe yours too. Ive never posted code on the forums before, so do this at your own risk. it works for me tho.
> cd /usr/local/games/ut2004
sudo ut2004If anyone who reads this understands error messages, here is what ours, or at least mine, looks like.> $ ut2004 
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History: 

Exiting due to error

It only works when i sudo it.

---

### Post by Lord Illidan on 2008-02-01
You should **not** use sudo to launch ut2004. It makes no sense to launch a game as root.

Regarding the pixellated squares, are you using the latest Nvidia drivers? The 169 series? They have a known problem with ut2004.

What happens if you do this :

```
cd /usr/local/games/ut2004
./ut2004-bin
```

---

### Post by Cappy on 2008-02-01
If ut2004 only runs with sudo you need to run (copy and paste)
```
sudo chown -R $USER:$USER ~/.ut2004
```

---

### Post by timboellis on 2008-02-01
I sussed it I did not install it from my home Directory but the desktop

---

### Post by matthewschwimmer on 2008-02-01
Thanks cappy. Now it works! I'm wondering why I had to do that to get it working. Was it because I installed the game as root? I had to install it as root, or change the permissions of the ut2004 target folder.

---

### Post by Cappy on 2008-02-01
> **matthewschwimmer said:**
> Thanks cappy. Now it works! I'm wondering why I had to do that to get it working. Was it because I installed the game as root? I had to install it as root, or change the permissions of the ut2004 target folder.

Glitch in the installer. When you hit the "play now" button at the end it creates the local directory .ut2004 in the home folder but with permissions of root.  They shouldn't be root permissions on the folder. The most common ut2004 bug imo.

---

### Post by matthewschwimmer on 2008-02-01
Ok, thanks. Will i still be able to patch the game normally now, or do i need to do something different? Should i do [this?]("http://ubuntuforums.org/showthread.php?t=239182")

---

### Post by Perfect Storm on 2008-02-02
You can do like this (note this guide takes that the game is installed globally so if you have installed it elsewhere you need to make some changes from the guide): [http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd](http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd)

---

### Post by matthewschwimmer on 2008-02-02
I did exactly what the guide said, because I installed to the /usr/local/games/ut2004 folder, but now i get> ./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directoryNow what?

PS: I have libstdc++6 installed. Do i need libstdc++5?

---

### Post by Perfect Storm on 2008-02-02
Aye, you can have both.

---

### Post by kc2iel on 2008-02-02
I went to the guide AI so nicely linked to & I could not find ut2004 listed in other using the alacarte.

Also, how does one remove UT2004?  I found the uninstall in the directory & was unable to run it(?)

Thanks AI a bunch for writing the install guide.

Sorry for being such a noob.

---

### Post by Perfect Storm on 2008-02-03
If it's not there - you can make your own in alacarte.
The command to launch it is
**ut2004**


There's some problems with these uninstallers, I havn't located the problem. But you can manually remove ut2004 directory from /usr/local/games and its launcher/binary from /usr/local/bin
There's also .ut2004 folder in your home (note the dot infront of the name, it means it's hidden) which have your personal settings and save games for this user.

Then it's completly removed.

---


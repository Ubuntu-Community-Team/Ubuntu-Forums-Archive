---
title: "[SOLVED] ETPRO Mod in Linux?"
date: 2006-11-06
forum: Gaming &amp; Leisure
---

### Post by locky28 on 2006-11-06
Hi all,

I've installed enemy territory 2.6 but have had problems.
All the servers seem to be running the ETpro mod and I'm having trouble installing it on Edgy. Is it possible to install the etpro mod on a linux distro and if so how do i do it?

---

### Post by hikaricore on 2006-11-06
The only issue I ever had involed the punkbuster mod, which came packaged with my installer.

from: [http://www.3dgamers.com/dlselect/games/wolfensteinet/et-linux-2.60.x86.run.html]("http://www.3dgamers.com/dlselect/games/wolfensteinet/et-linux-2.60.x86.run.html")

I believe.  which installer did you use to setup the game?  Or did you build it from source or something?  I havn't run across any servers using any pro mod that I know of.

I did have an issue the first time I installed ET which was that I installed 2.5 (or something) and the package I downloaded was labeled as 2.6.  Just a thought incase you meant to download 2.6 and got the wrong version.  :)

Good luck.

---

### Post by locky28 on 2006-11-06
the package i downloaded was labeled as 2.6, when i get into the game i join servers but it gets the gamestate and the progress comes up for the map downloads but it doesnt seem to download anything it just stays on 0% and switches between downloads, anyone else had this problem or could I have the same problem with wrong version?

---

### Post by locky28 on 2006-11-06
Note: i know little abount linux

Ok, i read elsewhere that certain files need to have permission for the game to work properly, i ran et as sudo and it worked fine.

How do i change the permisions so i don't have to run it through console?

---

### Post by hikaricore on 2006-11-06
Ohhhh.... I had a really weird problem I forgot about with ET.  To install the game you need to be running as root, problem was that after installing as root I launched the game and it created the .etwolf folder in MY home directory as belonging to root.

Open a terminal and do:

```
ls -lR ~/.etwolf
```

If you see in the third/fourth column that the files belong to root, you'll need to use:

```
sudo chown yourusername:yourusername -R ~/.etwolf
```
and just incase
```
sudo chmod ugo+rw -R ~/.etwolf
```

hopefully that will solve your troubles :)

After I ran the game from command line I saw that it was getting permission errors writing files to this directory.

---

### Post by locky28 on 2006-11-06
I skipped that 'Is -IR ~/.etwolf' and it still worked, thanks mate your a champ, put me one step closer to making linux my main os ;)

---

### Post by hikaricore on 2006-11-06
NP good luck and I'm just glad to help.  Guess someone should file a bug report with the folks who made the installer and let them know that it root owns the damn user's files lol, i've been too lazy myself, hell even forgot about that bug til today. :P

have fun

---


---
title: "Problems with Enemy Territory - hunkusage.dat"
date: 2007-05-22
forum: Gaming &amp; Leisure
---

### Post by jmccnz on 2007-05-22
Hi there,

I am trying to play enemy territory but am having a few problems, the main one concerning hunkusage.dat

When connecting to a game (I even tried it by hosting my own) I am disconnected before I get in with the error message: Cannot write to hunkusage.dat

Does anyone know what is up with that?

Also, when I click to enable punkbuster, nothing happens and punkbuster is not enabled. The same when i try to create a profile. Nothing happens I have to create one each time I start up.

Would very much appreciate any help anyone has to offer.

Thanks very much.

---

### Post by jmccnz on 2007-05-23
No-one knows? :(

---

### Post by Nesnej Trick on 2007-05-23
Sounds to me like a permissions problem. Where do you have ET installed?

---

### Post by HEDGECORE on 2007-05-23
I run ET using sudo, most likely your issue is permission related.

Try this (substitute your own path if you installed it elsewhere)

cd /usr/local/games/enemy-territory
sudo ./et

(Fire in your PW and you should have no problems)

---

### Post by aldenhg on 2007-05-23
> **HEDGECORE said:**
> I run ET using sudo, most likely your issue is permission related.

Try this (substitute your own path if you installed it elsewhere)

cd /usr/local/games/enemy-territory
sudo ./et

(Fire in your PW and you should have no problems)

The better thing to do would be to find the hunkusage.dat file and change it's permissions so that you don't have to run the game as root. Running an online game as root seems like it's inviting trouble. Find the file and run ```
sudo chown yourname yourname hunkusage.dat
sudo chmod 655 hunkusage.dat
```

---

### Post by REDISISTone.nl on 2007-05-24
Here is some information, some other files need permission too so read on...  ;)
[URL="http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408"]
http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408[/URL]

---

### Post by jmccnz on 2007-05-27
Hi there,

I have attempted all of the suggestions you gave me.

The only one that gave me any form of success was running et using sudo as the root user.

The problem here mainly lies in the fact that there are many files that must be made root in order for it to function correctly.

What I want to know is: Is there a way I can make all of the files available to my user, as I was told to do with the hunkusage file? IE: change the permissions of the entire enemy-territory folder.

Thanks in advance

---

### Post by asipi on 2007-05-27
dumb... sorry to say, but really
if you installed et with sudo it lies in the correct place. linux is a multiuser os so linux binaries are designed to act so too. so when you run et as a normal user it will create a .etwolf directory in your home what used for to store all the game datas what need by a user. if u first run et with sudo, the datafiles will be created with root permissions in your user's .etwolf, what really mess the goal what is for. so I recommend to sudo rm -R /home/yourusername/.etwolf, and after start over et again with your normal user and everything will be all right.

in some rare cases could be happen that pb at first run also create files in your .etwolf/pb with root permission (very rare but I came across with that) in that case simply change the owner of them with command sudo chown -R yourusername .etwolf (while your current dir is your home dir)

that's all.
good luck and frag hard :)

---


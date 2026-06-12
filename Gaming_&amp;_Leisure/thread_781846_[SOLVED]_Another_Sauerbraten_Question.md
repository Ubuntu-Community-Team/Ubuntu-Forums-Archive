---
title: "[SOLVED] Another Sauerbraten Question"
date: 2008-05-04
forum: Gaming &amp; Leisure
---

### Post by imaligertamer on 2008-05-04
I know that there are a lot of these, but I couldn't find an answer that helped. When I'm running Sauerbraten in edit mode and try to save a map, I get a message that says, "couldn't write to /sauerbraten/packages/(name).ogz"
How do I fix that? Does it have something to do with permissions?

---

### Post by k33bz on 2008-05-04
may i ask where do u have ur game file saved?

---

### Post by imaligertamer on 2008-05-04
It's in /usr/lib/games

---

### Post by k33bz on 2008-05-04
ok, go ahead and check your permissions there.

---

### Post by imaligertamer on 2008-05-04
byron@byron-laptop:~$ cd /usr/lib/games
byron@byron-laptop:/usr/lib/games$ ls -l sauerbraten
total 940
lrwxrwxrwx 1 root root     37 2008-05-04 00:40 data -> ../../../share/games/sauerbraten/data
lrwxrwxrwx 1 root root     41 2008-05-04 00:40 packages -> ../../../share/games/sauerbraten/packages
-rwxr-xr-x 1 root root 956604 2007-05-24 11:40 sauer_client

---

### Post by Perfect Storm on 2008-05-04
In this case wouldn't it be better to grab sauerbraten and run it in your home directory?

---

### Post by k33bz on 2008-05-04
he could run it where it is at, but he would have to change the file and the folder permissions. and not install it as root. I have my games saved in that folder, but i also had changed my permissions there.

It saved my home folder from alot of clutter, have enough stuff in there now.

---

### Post by imaligertamer on 2008-05-04
I'm still learning, so how would I do that?

---

### Post by Perfect Storm on 2008-05-04
> **k33bz said:**
> he could run it where it is at, but he would have to change the file and the folder permissions. and not install it as root. I have my games saved in that folder, but i also had changed my permissions there.

It saved my home folder from alot of clutter, have enough stuff in there now.

All my games goes to **.Games** so it's hidden away. Then I made a script for everyone of them to diasble compiz and launch the game, theafter when exiting the game compiz starts up again. 


# imaligertamer

[http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)
I havn't tested it yet in 8.04 - should also work for 32-bit

---

### Post by imaligertamer on 2008-05-04
I've tried that already. With the assassin edition, though, after the map loads the game freezes and the only way for me to to exit is a hard shutdown. That's why I installed it from Add/Remove.

---

### Post by k33bz on 2008-05-04
> **Artificial Intelligence said:**
> All my games goes to **.Games** so it's hidden away. Then I made a script for everyone of them to diasble compiz and launch the game, theafter when exiting the game compiz starts up again. 


# imaligertamer

[http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)
I havn't tested it yet in 8.04 - should also work for 32-bit

think i can get a copy of that script AI?

---

### Post by imaligertamer on 2008-05-04
How do I do that?

---

### Post by Perfect Storm on 2008-05-04
# imaligertamer
Well then go with k33bz idea then. I havn't tested saubraten for a long time and none on the new Ubuntu.


# k33bz

```
[size=1]#!/bin/bash

metacity --replace &

cd ~/.Games/OpenTyrian
./tyrian

compiz --replace & [/size]
```

---

### Post by k33bz on 2008-05-04
> **Artificial Intelligence said:**
> # imaligertamer
Well then go with k33bz idea then. I havn't tested saubraten for a long time and none on the new Ubuntu.


# k33bz

```
[size=1]#!/bin/bash

metacity --replace &

cd ~/.Games/OpenTyrian
./tyrian

compiz --replace & [/size]
```


thank you, looks like i got me a lil project to work on when i get home next week.

---

### Post by imaligertamer on 2008-05-04
So how do I change the permissions? I'm serious, I'm a newbie. I've tried before, but I ended up messing up the game completely.

---

### Post by k33bz on 2008-05-04
if you want to do it my way

(and sorry i dont have alot of commands in memory just yet)

just leave the game where it is and go into the console. You will want to  change the folder permissions of where ever you have the game files, and make it recursive.

As i said before, i dont have the commands into memory just yet. So I hope AI, or someone else will let you know what the command is to change the permission of the folder, recursively.



or u can give me a second,i think i have it saved in one of these forums.

---

### Post by k33bz on 2008-05-04
i beleive this is the right command to put in there
open your terminal

```
sudo chown urusername:urusergropup -r /usr/lib/games 
```

a listing of commands to use in the terminal
but for future refrence you can go here:
[http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")


installing anything in ubuntu
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by imaligertamer on 2008-05-04
Hey, it's cool. Whenever you can.

---

### Post by imaligertamer on 2008-05-04
I get this:

byron@byron-laptop:~$ sudo chown urusername:urusergropup -r /usr/lib/games
[sudo] password for byron:
chown: invalid option -- r

---

### Post by imaligertamer on 2008-05-04
Wow, I'm an idiot. It works now. Thanks, man.

---

### Post by k33bz on 2008-05-04
sorry, was typing something in another thread., I am glad you got it to work, please dont forget to mark your thread as solved.

---

### Post by imaligertamer on 2008-05-04
Sorry. Spoke to soon. I still get the same message when I try to save my maps.

---

### Post by shreig on 2008-05-04
Just to be sure, the command you typed was similar to this:

```
sudo chown byron:users -R /usr/lib/games
```

?

---

### Post by imaligertamer on 2008-05-04
Yeah. It works now. For sure. I dunno what happened, it didn't work the first time, but I exited Suaerbraten and went back in and it worked. It's good now, though.

---


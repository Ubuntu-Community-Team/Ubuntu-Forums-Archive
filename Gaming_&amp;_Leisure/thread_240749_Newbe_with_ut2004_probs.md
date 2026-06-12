---
title: "Newbe with ut2004 probs"
date: 2006-08-21
forum: Gaming &amp; Leisure
---

### Post by kgls13349 on 2006-08-21
Hello people,
Im new to linux, i originally tried to use Mandriva linux on my new server but it didnt work with my Nforce4 chipset, Ubuntu works perfect im glad i tried it, i like it so much that im thinking of replacing winxp on my main pc with it, before i do that i wanted to try playing games on my server UT2004 was the first game i came across that has a linux installer, the only other one i can think of is Doom3,
Ive managed to install it fine with no major problems but when i go to run it it just quits at the first splash screen, when i run it from the shell it says

"Cant find `ini:Engine.Engine.GameEngine` in configuration file

History:

Exiting due to error"

I did search in the forms for similar problems but i couldnt find one with that exact error message :???: 

Any help would be greatly appreciated, Thanks!

---

### Post by Perfect Storm on 2006-08-21
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63)
This howto shows what you did wrong, read the "Cautions" part.

---

### Post by kgls13349 on 2006-08-22
Ahh ive found plenty of posts like this now, sorry to post something thats aready mentioned, dunno why i didnt find them yesterday, perhaps messing with linux all day had confused me lol

---

### Post by pollock.tar.gz on 2006-08-22
i dont know if you did find it yet, but running ut2004 as root/superuser worked for me with that exact same error.

---

### Post by Perfect Storm on 2006-08-23
Don't run it with sudo!
You can install it with sudo, but don't run the game with sudo, big mistake.
Take a look on the howto I linked in my previous post.

---


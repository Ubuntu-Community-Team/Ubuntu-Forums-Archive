---
title: "Installing Enemy Territory, &quot;No Write Permission&quot;"
date: 2007-04-23
forum: Gaming &amp; Leisure
---

### Post by Linewbie on 2007-04-23
Hi, I'm trying to install Enemy Territory
I have Ubuntu 7.04 
an HP with an AMD64, and a nVidia GeoForce 6100

When I try to install, the Enemy Territory 2.60 Installer runs,
I get past the license agreement

Then it says "please enter installer path
/usr/local/games/enemy-territory"

I hit enter and it says 
"Failed permissions  
No write permission to /usr/local/games"

Any ideas on what to do next?
:confused: 
Thanx.

---

### Post by lakersforce on 2007-04-23
Either specify a path in your /home/username/ directory or run the sh *.run command with a sudo before it.

---

### Post by Tragos on 2007-04-23
It looks to me that you are running ET installer with your user account. However, by default normal users doesn't have write access to that default installation directory (/usr/local/games/). This is due the regular Linux security policy.

There are two options for ET installation:

[LIST=1]
[*]Install ET to your own home directory. Instead of just hitting ENTER as you mentioned, write "/home/YOUR_USERNAME/enemy-territory" and then press Enter.


[*]Run installer using sudo ("sudo INSTALLSCRIPT.run").

[/LIST]

First option installs ET just for you. The second installs it system-wide, allowing other users of the computer play it, too.

---

### Post by crimsontide on 2007-04-23
Does anyone know how to apply the .49b patch?

---

### Post by lakersforce on 2007-04-23
> **crimsontide said:**
> Does anyone know how to apply the .49b patch?

I have never heard of that patch. Newest ET patch is 2.60b

---

### Post by crimsontide on 2007-04-23
sorry......... I am thinking of tc:e.:oops:

---

### Post by lakersforce on 2007-04-23
If it is a *.run file, you should be able to do a sh *.run. If it is a zipped file I would guess it is containing a readme with instructions.

---

### Post by crimsontide on 2007-04-23
It's a zip and I got it from the tc:e site. It's says TC:Elite All OS Update but when you open the zip it only has files for windows and mac users. No instructions for linux users.

---

### Post by lakersforce on 2007-04-23
The structure inside the enemy territory folder is the same as on windows, so you should be able to use those instructions. I have not played TC:E for a while, but as far as I remeber it is just a question of unzipping the content into the right folder.

---

### Post by crimsontide on 2007-04-23
Update successful !! Thank you so much! Spent all day doing google searches and found nothing. Glad that's over.

---

### Post by lakersforce on 2007-04-23
It was my pleasure! Happy fragging :D

---


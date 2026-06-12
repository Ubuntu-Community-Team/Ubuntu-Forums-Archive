---
title: "How do I install a .run file?"
date: 2007-06-24
forum: Gaming &amp; Leisure
---

### Post by supazio on 2007-06-24
I just downloaded Enemy Territory and now I have et-linux-2.60.x86.run sitting on my desktop and I can't figure out what to do with it. If someone could point me in the right direction, that would be great.

---

### Post by scxtt on 2007-06-24
**sh et-linux-2.60.x86.run** <--- should do the trick, may need to make sure it's executable - **chmod +x et-linux-2.60.x86.run** will fix that ...

---

### Post by louistan3 on 2007-06-24
i believe that file is an executable...

if the permissions on it is set to executable...

then you just 

```
./<name of the file to execute>
```

but it might also be necessary to use "sudo" with it.. 

i am not sure...

hope this helps.. :)

edit: woops guess the one before me got it right... mines probably for a script... lol... :P

---

### Post by Luke771 on 2007-06-24
Install alien (from repo) then do ```
alien packagename.rpm packagename.deb
```
Once you have a .deb package, you can install it with any package manager (I think double-clicking on it will launch the deafult Gnome package manager). Click on 'install package'.

---

### Post by scxtt on 2007-06-24
he's got a RUN file, not an RPM ...

---

### Post by Luke771 on 2007-06-24
woops!
than it is```
./filename.run
```

---

### Post by kvonb on 2007-06-24
There are 2 ways to install ET, if you don't run the script with "sudo" prefix, it will install for you current user only, and you will have to give it the pathnames for the install when it asks, use: ~/enemy-territory etc'.

If you want it available to ALL users, simply install it with this command:

```
cd folder-where-you-downloaded-it-to
chmod +x et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run
```[B]

You may find that you also need to update it to 6.06b, (it simply overwrites et.x86 with the updated version) and also update punkbuster as well ([www.evenbalance.com](www.evenbalance.com), and download the full version, it's easier)

Your next problem will be sound, follow my instructions here:

[http://wamrfixit.homeip.net/webshare/edgy/edgy-modification-instructions/teamspeak-and-ET.txt](http://wamrfixit.homeip.net/webshare/edgy/edgy-modification-instructions/teamspeak-and-ET.txt)

It says it's for TeamSpeak, but ET needs it anyway.

And if you create an icon to launch ET, make sure you don't have a launch sound, as will block ET from using the sound card!

I would also suggest installing "xqf" from add/remove, it is a gameserver browser/finder app

[/B]

---


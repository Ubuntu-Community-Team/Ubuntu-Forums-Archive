---
title: "Hi, new user with some questions."
date: 2009-03-03
forum: General Help
---

### Post by Adam25 on 2009-03-03
Hello,

So i got ubuntu 8.10 installed on a insperion 2650 1.7 p4m, 256mb ram, 30gb hdd, geforce2 go grfx... Totally new to linux and amd currently lost in all of this. When i installed ubuntu it said some error with my NIC and i cant get it online at all. So i got the linux drivers for the 3com tornado and have no idea how to install them or look for the NIC. 

#2. I downloaded sevral apps from the ubuntu deb page and i have no idea how to install them either can someone show me how?

#3. How do i run/install apps for my lappy that only come in windows files? Such as drivers and programs to update the lappy?

---

### Post by Jaded Misanthrope on 2009-03-03
...lappy? I'm going to assume you mean laptop, since I've never heard that before.

What do you mean by 'apps'? Chance are the drivers are unnecessary or there is an alternative available (though I believe there's a way to have Windows drivers work with Ubuntu, circuituous as it may be). As for the programs you want, that depends entirely on what they are. Games can sometimes be run using something known as Wine, though it's often a matter of luck, and a lot of other programs have a Linux-compatible equivalent. .exe files -- the executable files used by Windows -- do not work on Ubuntu or any Linux distro natively; they need a system such as Wine to emulate a Windows environment.

As for installing the programs, what extension does the file or files have?

---

### Post by Adam25 on 2009-03-03
Yea lappy=laptop :P

Well stuff like ubuntu tweak, starup manager 1.9, advgnomemenu etc.. all are deb files. But the drivers for my nic i have no idea how to set it up either, its a linux version i found 3c90x for a 3com tornado.. I dont know how to install nay of them.

EDIT
Fixed this my self, figured out i was trying to extract the files when i needed to double click.

---

### Post by Tek-E on 2009-03-03
For the deb files.
In the terminal type.
```

dpkg -i path/to/deb/file.deb

```

---

### Post by Ben Crisford on 2009-03-03
With 256MB of RAM some problems are bound to occur... (at least I think so, back in the ol' 6.10 days, I ran it with 256MB and had loads of difficulty :S).

---


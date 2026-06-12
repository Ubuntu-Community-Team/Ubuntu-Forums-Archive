---
title: "did something stupid...."
date: 2006-07-27
forum: Desktop Environments
---

### Post by GQed76 on 2006-07-27
I deleted the modprobe file out of my sbin directory.  it did not go to the recycle bin.  Now, obviosuly, my sound and mouse dont work on boot.

Is there anyway to recreate the file

---

### Post by jc750kwak on 2006-07-27
Re-install the module handling utilities

sudo apt-get install module-init-tools

John

---

### Post by GQed76 on 2006-07-27
Thanks john, but it said i had the latest and greatest installed. and didnt do anything :-/

---

### Post by nilfilter on 2006-07-27
I guess he would need to add the --reinstall switch: ```
sudo apt-get install module-init-tools --reinstall
```

---

### Post by jc750kwak on 2006-07-27
Yup - that should work !

---

### Post by GQed76 on 2006-07-27
lol except my network card isnt loading...so i have no network, and no mouse. 

i dont even know how to get to the menus via keybaord shortcuts. :(  thank god a terminal window was left open lol

I feel really dumb,,,, i was compilign the new ndiswrapper, and it suggested i replace that file.  i deleted it assuming i could restore it from the trash :-/

---

### Post by nilfilter on 2006-07-27
> **GQed76 said:**
> I feel really dumb,,,, Naww, I wouldn't go that far... ;)
Try downloading it from the [Ubuntu archive]("http://www.archive.ubuntu.com/ubuntu/pool/main/m/module-init-tools/") and install it locally. You might however be lucky and have the latest copy in your local archive in /var/cache/apt/archives.

---

### Post by GQed76 on 2006-07-27
great i downloaded that to my windows drive, i can move it once im in linux..but this is really hard without a mouse.

how do i get up to the menus via keyboard

---

### Post by nilfilter on 2006-07-27
> **GQed76 said:**
> great i downloaded that to my windows drive, i can move it once im in linux..but this is really hard without a mouse.
how do i get up to the menus via keyboardMouse? Menus? No mate, now it's time to roll up your sleeves and get your hands real dirty in command line grease ;)
Boot into Ubuntu and press crtl+alt+F2 (i.e. simultaneously) and log in with your normal user account.
Please make really really extra really sure you have downloaded the correct package, compare the version info of the downloaded file with what you get by typing:```
dpkg -l module-init-tools
``` If it matches the currently installed version, reinstall it by typing```
sudo dpkg -i /path/to/package.deb
```

---


---
title: "UT2004 Question"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by FusionXN1 on 2006-11-13
I got UT2004 on DVD. On the back it shos a linux logo and under system requirements it says (windows) - i got no manual or anything (it was brand new?!) but i hear that you can use it linux - does this apply to the DVD version? I dont see any more info just a linux logo.

---

### Post by Drezliok on 2006-11-13
It works.

you have to goto the CD in the terminal and run 

```
 sudo sh linux-installer.sh 
```

---

### Post by FusionXN1 on 2006-11-13
CD as in folder?

---

### Post by Drezliok on 2006-11-13
in the terminal:

cd /media/cdrom0              [or where the cd is mounted at]

sudo sh linux-installer.sh

---

### Post by FusionXN1 on 2006-11-13
ill try that when i format linux, i hope my dvd version has it as it only says play disk.

---

### Post by Drezliok on 2006-11-13
It's easier with one disk. I had my 5 to go through and it would not let me eject while I was installing to change disks. The installer was running off the disk so I had to move it to my desktop and run the installer there.


Works great.

---

### Post by FusionXN1 on 2006-11-13
Ok so i hope my DVD version works because as i said all i noticed was the linux logo on the box not on cd or in specs. Thanks :)

---

### Post by MrFSL on 2006-11-13
I can verify that the Linux installer IS present on the DVD. The same went with UT2003... linux installer but no documentation. Then I remember reading that the Unreal folk were going to make sure to make more public the linux installer in 2004 - but at least we got the logo on the box right?

If you are in not in Linux yet and want to verify you can simply open the disk and look for the install script. It should be in the root of the DVD.

---

### Post by FusionXN1 on 2006-11-13
ok what file am i looking for.

---

### Post by Drezliok on 2006-11-13
linux-installer.sh

---

### Post by FusionXN1 on 2006-11-13
yep its there, Thanks.

---

### Post by Hemmer on 2006-11-14
> **FusionXN1 said:**
> ill try that when i format linux, i hope my dvd version has it as it only says play disk.

Yeah thats the version i have - as long as you follow Drezliok's advice, you'll be fine:

[QUOTE=Drezliok]in the terminal:

cd /media/cdrom0 [or where the cd is mounted at]

sudo sh linux-installer.sh[/QUOTE]

---

### Post by FusionXN1 on 2006-11-14
Ya, thanks :)

---

### Post by rejser on 2006-11-14
Hmmm... got the dvd at my local food store, (9$). Issued the linux installer. After a while it asks me to put in cd2.....

---

### Post by Drezliok on 2006-11-14
thats different...

Hit retry and see what it does, beyond that I can't help. I only have the 6 disk set.

---

### Post by justin whitaker on 2006-11-14
You can copy all the files to a directory, and install from there. Also, try copying the installer onto your HD, then running it.

---

### Post by Drezliok on 2006-11-14
> **justin whitaker said:**
> You can copy all the files to a directory, and install from there. Also, try copying the installer onto your HD, then running it.

would that fix the problem? All his files are on the DVD yet it still asked for disk 2.

I dunno, join the [http://gaming.gwos.org/](http://gaming.gwos.org/) forums and ask them, they might be able to better help you.

---

### Post by justin whitaker on 2006-11-14
> **Drezliok said:**
> would that fix the problem? All his files are on the DVD yet it still asked for disk 2.

I dunno, join the [http://gaming.gwos.org/](http://gaming.gwos.org/) forums and ask them, they might be able to better help you.

I've seen several posts where it helped people that had that issue when installing from the 6 CD set. 

Dumping the disks helped me with  Doom III, Quake 4, and HL2, when I couldn't get the native installers or cedega to install the games. 

Worth a shot.

---

### Post by Drezliok on 2006-11-14
Never hurts to try everything.

---

### Post by rejser on 2006-11-15
Tried it, did not work (both copy the installer and copy everything to harddrive). Did not work, still asks for cd 2, strange
Somewhere I saw a post how to turn a windows install to a linux install, but can't find it. (Installed it on my gf laptop, but it was to slow, but still installed there.

Hmm... just saw an error message, "The Setup program seems to have failed on x86/glibc-1.2"
I have the libglib-1.2 packages, and 2.0 packages. 
I find documentation for glibc, but no glibc, isn't there suppose to be glibc packages? (in repos)

---

### Post by Muty-bg on 2006-11-20
Strange I have the DVD and it works fine

---

### Post by Drezliok on 2006-11-20
> **Muty-bg said:**
> Strange I have the DVD and it works fine

Perhaps your disk is newer than his.

Hey, email him or host the linux-installer.sh file so he can get it and try yours.

---

### Post by Muty-bg on 2006-11-21
here you go:
[click here"censored"]("http://muty.kicks-***.org/linux-installer.sh")
It doesn't look very new tho: 4th May 2004
I don't know if it will help but on my DVD there are folders for each cd like: CD1, CD3,.. etc. and the installer never asked me for the cd

---

### Post by Muty-bg on 2006-11-21
here you go:
[http://muty.kicks-***.org/linux-installer.sh]("http://muty.kicks-***.org/linux-installer.sh")
It doesn't look very new tho: 4th May 2004
I don't know if it will help but on my DVD there are folders for each cd like: CD1, CD3,.. etc. and the installer never asked me for the cd

EDIT:oops I see the board censored my domain :( nevermind the three letter word that is censored is buttocks but starts with an a and ends with s. I'm sorry for my vulgar domain name it was in the list of dyndns subdomains and looked cool 8)

---

### Post by [d3v] on 2006-12-07
If you want to be able to install from the DVD and not have to change disks (wtf???) you need to export a var from the console before running the installer

```

export SETUP_CDROM=/media/dvd/
sh installer.sh

```

Change the path to where your DVD is mounted and it will work fine.

---


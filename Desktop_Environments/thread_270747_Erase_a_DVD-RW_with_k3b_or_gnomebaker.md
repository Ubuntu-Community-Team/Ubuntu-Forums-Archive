---
title: "Erase a DVD-RW with k3b or gnomebaker"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Hellaxe on 2006-10-03
Hello people:
Can anyone tell me how do i erase a DVD-RW with k3b or gnomebaker.
The only option on both programs are:
"Format DVD+-RW"

Thank you

---

### Post by confused57 on 2006-10-03
I think gnomebaker has an option "Blank DVD +-RW", mine is located just to the left of the format option.

---

### Post by Hellaxe on 2006-10-04
Not mine.
only erase CD-+rw.

this is wierd: everybody tells me that has this option and i don't have it.

---

### Post by Hellaxe on 2006-10-06
Hello people:
give me a hand on this pleeeeeeeeeeeeeeeease.:mrgreen: 

thank you

PS: Is it possible that k3b was compiled without that option?

---

### Post by _simon_ on 2006-10-06
I don't think you can "erase" a DVD.

k3b lets you overwrite existing data, it's an option just before you start your burn.

---

### Post by Hellaxe on 2006-10-06
But it keep saying that the older data is there. Isn't that wright?

---

### Post by ahaslam on 2006-10-07
You don't need to erase the disc, you just over-write it. Try it & you'll see what I mean.

Tony.

---

### Post by galego on 2006-10-08
also make sure your libcdvd codecs are up to date. i was issues with K3b and Gnome baker with just the RW's and after an update, it all went good!

---

### Post by Hellaxe on 2006-10-08
> **galego said:**
> also make sure your **[COLOR="SeaGreen"]libcdvd[/COLOR]** codecs are up to date. i was issues with K3b and Gnome baker with just the RW's and after an update, it all went good!

I can't find this lib.........](*,)

---

### Post by galego on 2006-10-08
[https://help.ubuntu.com/community/RestrictedFormats#w32codecs]("https://help.ubuntu.com/community/RestrictedFormats#w32codecs")

that link should get you going. if you have easy ubuntu installed you can get them from there also. except i gave you the wrong discription Sorry! you are looking for ```
libdvdcss2
``` and also ```
libdvdread
```

hope that helps.

---

### Post by fatsheep on 2006-10-08
Try running K3B in super user mode:

gksudo k3b

---

### Post by Hellaxe on 2006-10-09
> **fatsheep said:**
> Try running K3B in super user mode:

gksudo k3b

It doesn't work. I've already try it.

---

### Post by Hellaxe on 2006-10-09
> **galego said:**
> [https://help.ubuntu.com/community/RestrictedFormats#w32codecs]("https://help.ubuntu.com/community/RestrictedFormats#w32codecs")

that link should get you going. if you have easy ubuntu installed you can get them from there also. except i gave you the wrong discription Sorry! you are looking for ```
libdvdcss2
``` and also ```
libdvdread
```

hope that helps.

I have it installed.

---

### Post by galego on 2006-10-09
re-install them and do the same for K3b. completely remove them and re-install. if you were able to install K3B with all dependencies and have the codecs it should work.(I know you are thinking ... Then why in the H*!! isnt it working?) unless you are using some obscure RW after the codecs the errors should stop. when you are trying to erease you will use the format button. if this doesnt work maybe try posting on the KDE site.
Good Luck :-k

---

### Post by Hellaxe on 2006-10-09
Ok I&#314;l try it.
Thank you.

---

### Post by confusimo on 2006-11-04
k3b does erase DVDs.  I have DD 6.06 64bit and k3bv was already in synaptic.  I didn't need to reinstall anything.  Just goto Tools and then Format DVD+-RW.  Say Force, and then quick format or uncheck it if you don't need quick format.  And then Start.  Without clicking Force it won't erase.  

Now I can reburn with it saying insert an empty DVD.

Thanks,
Confusimo

---

### Post by finite9 on 2006-11-23
I try to avoid Qt apps like the plague (just personal preference not grounded in any specific notion of Gnome being superior or any such), so I *don't* want to install K3B.  I use Gnomebaker, and I've tried Graveman (don't like this program...not as polished as Gnomebaker) and Nautilus.

Not one of the Gnome utilities can format a DVD.  AFAIK they all use dvd+rw-tools and growisofs at the backend, and if you read the man pages for these two programs (dvd+rw-format is the utility to man for instead of dvd+rw-tools which has no man page) then they both give instructions for 'formatting' a DVD, neither of which work!  I am starting to wonder if you can format a DVD in Ubuntu!!

Does anyone know which backend K3B uses?

---

### Post by carverj on 2007-02-01
Hmm, what's the matter here?

```
jeremy@jeremy-desktop:~$ sudo aptitude install libdvdcss2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jeremy@jeremy-desktop:~$ sudo aptitude install libdvdread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "libdvdread".  However, the following
packages contain "libdvdread" in their name:
  libdvdread-dev libdvdread3-dev libdvdread3 
The following packages have been kept back:
  xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jeremy@jeremy-desktop:~$ sudo aptitude install libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  xutils 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

Repo issue?

---


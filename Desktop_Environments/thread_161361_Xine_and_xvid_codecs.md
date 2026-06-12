---
title: "Xine and xvid codecs"
date: 2006-04-16
forum: Desktop Environments
---

### Post by Wiggums on 2006-04-16
How do you go about installing and troubleshooting codecs under linux?

I am trying to play a video file that is coded with Xvid.  I can load the file by typing: ```
xine myvideo.avi
```

Xine starts up and the audo plays but a dialog box comes up that says Xvid is an unsupported codec.  I've installed all the codecs from unbuntuguide.com.  I then complied and installed xvid.

How do I figure out what is going on?

---

### Post by nolan- on 2006-04-24
Hi,
I've been having the same problems in Dapper after an install yesterday.
I got things working by installing libxine-extracodecs but I couldn't find it in synaptic.
I got it here from a mirror :-

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fx%2Fxine-extracodecs%2Flibxine-extracodecs_1.1.1%2Bubuntu1-2_i386.deb&md5sum=5512ee45d3d0c9dd30f2588512729aa8&arch=i386&type=main]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fx%2Fxine-extracodecs%2Flibxine-extracodecs_1.1.1%2Bubuntu1-2_i386.deb&md5sum=5512ee45d3d0c9dd30f2588512729aa8&arch=i386&type=main")


I'm a noob, so just incase you are as nooby as me, download the file into your home folder, then open a terminal and make sure you are in the folder you downloaded the file to and do this :-

```
sudo dpkg -i libxine-extracodecs_1.1.1+ubuntu1-2_i386.deb
```


My xine now plays just about everything.

Hope this helps!

---

### Post by jswan on 2006-04-28
I was trying to install xvid codec and found your post

I typed in ```
sudo apt-get install libxine-extracodecs
```

and it found it on the 
```
http://archive.ubuntu.com dapper/multiverse
```
repository which you should definately have if you have Dapper.

Also, your way is incompatible if you dont have intel x86 (I have AMD64)

SOOOO this is the ultra noob way to do it  ;) 

Still love ya

---

### Post by nolan- on 2006-04-29
I have an AMD64 4gig San Diego chip..... I just dont run a 64bit system...

And trust me it wasn't in the repo's when I typed that message...

"[COLOR="Red"]I got things working by installing libxine-extracodecs but I couldn't find it in synaptic.[/COLOR]"

As I stated in the post i'm quite new to this, there's no need to be funny just because the file was not for your pc's chipset!

Don't assume people are stupid, perhaps it was just added to the repositories ?

love you too, I think....

---

### Post by jacqvo on 2007-10-28
just for your information.

the xvid codec is now in libxine1-ffmpeg

so the install command would be :

sudo apt-get install libxine1-ffmpeg

happy XUbuntu :-)

---

### Post by mishimasan on 2008-04-04
How do people find out these things?! :confused:

---


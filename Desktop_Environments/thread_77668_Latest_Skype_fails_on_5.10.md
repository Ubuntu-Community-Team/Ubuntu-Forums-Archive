---
title: "Latest Skype fails on 5.10"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dickmorrell on 2005-10-17
Latest Skype .deb fails miserably with dependancies on 5.10 although I did get an earlier running by using the Ubuntu guide and installing deprecated libraries (libqt3-mt) to replace  libqt3c102-mt which says is broken in 5.10.

However running latest is 1) secure (version I am using isn't) 2) better codecs and support for more features.

Anyone else got a solution ?

Richard

---

### Post by Alibloke on 2005-10-17
This is to do with Breezy using newer libraries and compilers, this link may be able to help out:

[http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/](http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/)

---

### Post by canglan on 2005-10-17
DIY:

$ sudo apt-get fakeroot alien

and then download the latest deb file from skype.com

$ fakeroot alien --to-tgz <the file you just downloaded>

It creates a tgz file for you.

$ fakeroot alien --to-deb <the tgz file it just created>

Now you have a working deb file. Install it. :)

---

### Post by dickmorrell on 2005-10-17
Ok so that didnt work 

dickm@apollo:~$ sudo apt-get fakeroot alien
E: Invalid operation fakeroot

---

### Post by Alibloke on 2005-10-17
Try apt-get install fakeroot alien instead  :P

---

### Post by canglan on 2005-10-17
Yeah sorry typo, I always do the stupid thing. :P

---

### Post by muszek on 2005-10-18
OK, I did install it the way mentioned in this thread:
```

muszek@muszek:~/Desktop/temp$ fakeroot alien --to-tgz skyp*
skype-1.2.0.17.tgz generated
muszek@muszek:~/Desktop/temp$ fakeroot alien --to-deb skype-1.2.0.17.tgz
skype_1.2.0.17-2_all.deb generated
muszek@muszek:~/Desktop/temp$ sudo dpkg -i skype_1.2.0.17-2_all.deb
Selecting previously deselected package skype.
(Reading database ... 64858 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.17-2_all.deb) ...
Setting up skype (1.2.0.17-2) ...

```

but when I try to run it, an error shows up:
```

muszek@muszek:~/Desktop/temp$ skype
skype: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

what should I do next?

EDIT: installing libstdc++5 helped... now I need to find a way to make skype look less ugly...

---

### Post by casper_2095 on 2005-10-22
Forget the deb.
Download the "static" version with qt builtin from skype, unroll it, and run the "skype" executable.
It works brilliant on 5.04.  What about 5.10?

---

### Post by AlP on 2005-10-22
The static version hangs without further comment ... I do not know what goes wrong there, but something does -- no gui, no cpu-load.

If anyone has got any ideas how to make skype tell me what makes it stop, tell me. 

(ESD ist killed of course)

Greetings, AlP

---

### Post by AlP on 2005-10-22
[https://wiki.ubuntu.com/Skype?highlight=%28skype%29](https://wiki.ubuntu.com/Skype?highlight=%28skype%29)

this works.

---

### Post by naomi on 2005-10-23
Unfortunately the wiki skype solution didn't work for me

```

Unpacking skype (from skype_1.2.0.17-1-fixed1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3-mt | libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

```

But I will have a look at all the skype related threads now...

---

### Post by easy_target on 2005-10-31
I think redebianizing the package works best until skype decides to fix their mess. If we have a number large enough of people confirming this temporary solution, can an administrator make it a Sticker please?

---

### Post by kontara on 2006-02-27
I am a Linux newbie.  Today, I installed Skype and libqt3-mt via Synaptic.  Looked for menu item to load, didn't find.  Searched location of Skype in the file system.  Found under /usr/share/ubuntu-docs/gnome/menus/C an XML file that said there should be an item in the menu under Applications>Internet>Skype.  Don't find anything there.  How does one start the program?

Thanks.

---

### Post by dunnerz on 2006-02-28
[QUOTE=Alibloke]This is to do with Breezy using newer libraries and compilers, this link may be able to help out:

[http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/](http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/)[/QUOTE]

that did the job!

cheers!

---

### Post by ronmarley1 on 2006-02-28
I installed Skype via Automatix and it works just fine.  Here's the link: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Caveat: Some folks don't like Automatix (I do), so read the whole thread before installing and using.

---

### Post by styven on 2006-02-28
Hi all,

Can anyone enlighten me as to why mac and linux users can't do "video call", is it down to skype or mac/linux?

steve

---

### Post by ronmarley1 on 2006-02-28
[QUOTE=styven]Hi all,

Can anyone enlighten me as to why mac and linux users can't do "video call", is it down to skype or mac/linux?

steve[/QUOTE]

The Linux and Mac versions don't have video call capability (yet).  The Linux and Mac versions don't have as many bells and whistles as the Windoze version.

---

### Post by megamania on 2006-03-01
[QUOTE=ronmarley1]The Linux and Mac versions don't have video call capability (yet).  The Linux and Mac versions don't have as many bells and whistles as the Windoze version.[/QUOTE]

This is not (only) a matter of bells and whistles. The linux version of skype sucks. 

I only use Ubuntu now (no windows anymore) and being a paying skype user I can say that this program is a shame to the linux world. Check the skype forums and see what even the developers themselves say about it.  :-(

---

### Post by speedsix on 2006-03-01
I agree the linux version is poor. I had to unpack the .deb and change the dependencies to get it to work as well.


Problem now is I get no sound (oss/esd/alsa works fine) everytime a sound plays  I get an error show in the terminal..


```
read error, res = -1 , handle = 26
```

---

### Post by ronmarley1 on 2006-03-01
megamania,
I agree, Skype on Linux does indeed suck!

---

### Post by megamania on 2006-03-02
[QUOTE=ronmarley1]megamania,
I agree, Skype on Linux does indeed suck![/QUOTE]

Yeah, we should probably start complaining on the skype forums. If we all get there and ask for a decent version, they'll probably realize that there's enough demand for one.

Maybe even downloading the program directly from their website would help (I'm pretty sure they have a download counter)...

---


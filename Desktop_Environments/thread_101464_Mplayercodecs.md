---
title: "Mplayer/codecs"
date: 2005-12-09
forum: Desktop Environments
---

### Post by slrafal on 2005-12-09
I've been successful installing the Mplayer but how do I go about installing codecs. 

I've downloaded the codecs and unzipped the folder. Now it's sitting on my Desktop; Just don't know where and how to install these. The readme file does not contain anything concrete.

Any help would be appreciated.

---

### Post by dcast on 2005-12-09
what format are the codecs?

---

### Post by slrafal on 2005-12-09
well there is a whole bunch of dll's, .acm files, I also saw a Quicktime.qts....

---

### Post by dcast on 2005-12-09
whoah are you sure those are linux codecs?

---

### Post by slrafal on 2005-12-09
I think so because the source I found it from was on a post in these forums.

---

### Post by nix4me on 2005-12-09
Yes, they are the W32codecs.

They should be in /usr/lib/win32.

They are necessary for playing restricted formats.  See the Wiki for docs on the subject.

nix4me

---

### Post by slrafal on 2005-12-09
nix, sorry I'm a newbie but do I just copy these files into a created folder in /usr/lib/win32? Do I need to change any settings in Mplayer? Could you also point me to the wiki.

Thank You.

---

### Post by jalanbuntu on 2005-12-09
Why don't you try to use w32codecs packages
you can download it [here]("ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb")

For complete guide may be you should see the wiki page [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by slrafal on 2005-12-09
Thanks for the link. But I successfully copied all the codecs into /usr/lib/win32 but when I go to apple.com/trailers its still telling me that I need to download a plugin?

---

### Post by jalanbuntu on 2005-12-14
Have you install mplayer plugin for firefox (mozilla-mplayer) ???????

---

### Post by ikki_72 on 2005-12-14
lets see, i've downloaded the mplayer, how'd i install it. n y did the ./configure failed? explain briefly please.

---

### Post by agger on 2005-12-14
[QUOTE=ikki_72]lets see, i've downloaded the mplayer, how'd i install it. n y did the ./configure failed? explain briefly please.[/QUOTE]

Did you use "sudo" to call configure?

If you're using Ubuntu you should go

```
sudo apt-get install mplayer
```

instead.

---

### Post by jalanbuntu on 2005-12-14
Yup  if you are using ubuntu you should install using apt instead

```
sudo apt-get install mplayer-586
sudo apt-get install mplayer-fonts
sudo apt-get install mozilla-mplayer
```
That would install mplayer and mplayer plugin for mozilla. Note that in that example my machine is 586. If you are using other machine may be you should try to find other package using

```
sudo apt-cache search mplayer
```
To install the codec,

```
wget -t0 ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```

May be you should also install other multimedia codecs. See the howto at [http://ubuntuguide.org/#codecs]("http://ubuntuguide.org/#codecs")

wish that would help

---

### Post by novabobogun on 2008-04-20
Uhmm, where do you get the codecs? 
How do you do the plugin thing in firefox?

---


---
title: "O3D Online Demo (3d browser game, no Java)"
date: 2009-07-23
forum: Gaming &amp; Leisure
---

### Post by gradinaruvasile on 2009-07-23
Have u guys seen this? It seems to be the future of gaming...

O3D is a 3d API/engine that can be accessed in a browser with a plugin (Firefox/Seamonkey and Midori too can use it)

[http://code.google.com/apis/o3d/]("http://code.google.com/apis/o3d/")

And the interesting part that its already functional...

The plugin:

[https://launchpad.net/~ubuntu-webtech/+archive/o3d-daily]("https://launchpad.net/~ubuntu-webtech/+archive/o3d-daily")

After adding the repository to your apt list, just type in a terminal:

```
sudo apt-get install o3d-plugin
```

Restart your browser. Go to the demo game url below

O3D Demo game:

[http://blog.largeanimal.com/demo/]("http://blog.largeanimal.com/demo/")

Edit: Added O3d Demos directory:

[http://code.google.com/apis/o3d/docs/samplesdirectory.html]("http://code.google.com/apis/o3d/docs/samplesdirectory.html")

It worked for me with Firefox 3.0/3.5.1, Seamonkey 2.0 beta1, Midori 0.18 - It didnt work in Chromium (_It works now as of 31 July build_). And some demos dont work in Opera 10 Beta2.
 I tried on 2 computers, both with Nvidia NVS cards and the latest Nvidia drivers (185.18.14).

Edit: Tried on my home comp with Jaunty /Nvidia 7600SGS - worked well.
       It didnt work with Ati x1600 / radeon drivers in Jaunty. It said the card is not supported...

---

### Post by zero777zero on 2009-07-23
i remember hearing about this, sounds great, but i think i'll wait for an easy installation method to become available

---

### Post by gradinaruvasile on 2009-07-23
Its as easy as it gets with Ubuntu. The only thing u have to do is to add the ppa tou your sources list.

---

### Post by zero777zero on 2009-07-23
ok, i was reading something different. btw, i consider a deb-file to be the easiest method.

---

### Post by gradinaruvasile on 2009-07-23
It is a deb file... U can download it separately by clicking on the lower item on the list and there u will open a list with links. The i386.deb is the one (that has no dbg in its name) u need (or amd64 if u have 64 bit ubuntu). Click on it, d/l it install it. But this way u wont get the subsequent updates.

Here is the exact link :
The standard version:

[https://launchpad.net/~ubuntu-webtech/+archive/o3d-daily/+files/o3d-plugin_0.1.40.0~svn20090723r21378-0ubuntu1~o3d1~jaunty_i386.deb]("https://launchpad.net/~ubuntu-webtech/+archive/o3d-daily/+files/o3d-plugin_0.1.40.0~svn20090723r21378-0ubuntu1~o3d1~jaunty_i386.deb")

And the 64-bit version (for 64 bit ubuntu):

[https://launchpad.net/~ubuntu-webtech/+archive/o3d-daily/+files/o3d-plugin_0.1.40.0~svn20090723r21378-0ubuntu1~o3d1~jaunty_amd64.deb]("https://launchpad.net/~ubuntu-webtech/+archive/o3d-daily/+files/o3d-plugin_0.1.40.0~svn20090723r21378-0ubuntu1~o3d1~jaunty_amd64.deb")

---

### Post by MaxIBoy on 2009-07-23
Yeah, I've heard about it. Google and Khronos are working on the project, aren't they?   Looks like it's an API for javascript, which means NoScript will cover it, which is good.  EDIT: Why are blank lines being deleted?! This is really annoying.

---

### Post by Vadi on 2009-07-24
I'm starting to be irritated by Google's inability to program their V8 for 64bit. Not going to bother with a nspluginwrapper here unless they make it work on their 32bit chromium.

---

### Post by zero777zero on 2009-07-25
game refuses to finish loading :S

---

### Post by zero777zero on 2009-07-27
so i write the developer and i get this reply:

Thanks for getting in touch. Unfortunately, Ubuntu is not supported at this time.

---

### Post by solitaire on 2009-07-27
Hmm....

it's not working for me! the web page keeps asking for the plugin to be installed.

I've added the repo and installed the plugin yet it is *still* asking for the plugin to be installed.

Firefox 3.0.12

---

### Post by PiotrekS on 2009-07-28
I have installed this extension and everything works fine :) Demos on the webpage of o3d are working. But i compiled o3d from source. I didn't try to install deb package - maybe are problems with deb installation.

---

### Post by solitaire on 2009-07-28
Strange! took a reboot of my laptop to get the plugin to be seen....
It's now working ^_^

---

### Post by TheSpook on 2009-07-28
Launchpad is claiming there were build errors for the newest version :(.

Following the install directions found here: [http://code.google.com/p/o3d/wiki/HowToBuild](http://code.google.com/p/o3d/wiki/HowToBuild).  For those who just want the plugin, run 

```

./scons plugin MODE=opt-linux

```

after checking everything out.


Edit:  I've got the plugin running on 64-bit Jaunty, Firefox 3.0.12, 8400GT.  Occasional crashes, otherwise alright.

---

### Post by weaponx69 on 2010-01-28
Whew, 
   I just got it working and it was worth it!  A free 3D web browser API.  Nice.  It is very hard to install in linux.  I tried the repo but it doesn't work.  I had to follow the instructions for installing it on google's website.  If anyone is interested and needs help installing it, just send me a message.

---

### Post by Funnnny on 2010-01-28
The game looks very promising, got this working on Windows

---


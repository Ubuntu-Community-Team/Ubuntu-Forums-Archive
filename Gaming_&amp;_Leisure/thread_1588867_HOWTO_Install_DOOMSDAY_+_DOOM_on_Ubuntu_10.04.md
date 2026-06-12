---
title: "HOWTO: Install DOOMSDAY + DOOM on Ubuntu 10.04"
date: 2010-10-05
forum: Gaming &amp; Leisure
---

### Post by Niccola on 2010-10-05
Hey guys!
After a deeper search in internet I've solved my problem with DOOM + Ubuntu. So, I'll share it with everybody that interest...

Well, the first step is install Doomsday dependencies and DOOM shareware WAD (if you already have the WAD. dont install that):

```
sudo apt-get install doom-wad-shareware libsdl-sound1.2 libsdl-net1.2 libsdl-mixer1.2 timidity
```

Now, add the following lines in /etc/apt/sources.list:

deb [http://debian.keesmeijs.nl/](http://debian.keesmeijs.nl/) lucid-kees main
deb-src [http://debian.keesmeijs.nl/](http://debian.keesmeijs.nl/) lucid-kees main

[B]OBS: in [http://dengine.net/linux](http://dengine.net/linux) you can see the lines to add for other distros;
[/B]

Now Add the archive key to apt's trusted keyring, and update your source:

```
gpg --keyserver gpg.mit.edu --recv-keys 0x4B6E7209
gpg --export -a 0x4B6E7209 > Yagisan.asc
sudo apt-key add Yagisan.asc
sudo apt-get update
```

And Finally install DOOMSDAY engine:
```
sudo apt-get install deng
```

Now Open your favorite text editor and paste in this code (make a script to run DOOM):
```
#!/bin/sh
doomsday -g jdoom -file /usr/share/games/doom/doom1.wad
```
Save it as 'doom' and make it executable
```
chmod +x doom
```

AND, Finally finally, Start Doomsday by executing the script:
```
./doom
```

For the best Graphics to your game install this optional addons:

**Installing the Hi-Res Models (Optional)**

The following jDoom major jPacks are available
deng-jdoom-rp-core**************(core files)
deng-jdoom-rp-decorations*******(decorations)
deng-jdoom-rp-effects*special***(effects)
deng-jdoom-rp-hud***************(heads up display)
deng-jdoom-rp-items*************(items)
deng-jdoom-rp-monsters**********(monsters)
deng-jdoom-rp-projectiles*******(projectiles)
deng-jdoom-ep*******************(The jDoom Environment Pack)
deng-jdoom-ui*******************(The jDoom User Interface Pack)
deng-jdoom-tp*******************(The jDoom Texture Pack)
deng-jdoom-sycraftsdoommusic****(High Quality Doom Soundtracks)

Using apt-get, install any of the packs you desire.

Now, have a Great Game!!

P.S.: The same you do for Heretic and Herex games... You only need to modify this command line for the path where has you game:

doomsday -g jdoom -file /usr/share/games/doom/doom1.wad

AND in "jdoom" you change with jHeretic or jHerex

---

### Post by Convoycation on 2010-11-28
Tried to get gpg.mit.edu, got nothing.  Went to pgp.mit.edu and appeared to have gotten one key.

At "sudo apt-get update" however, I got this:

> W GPG error: [http://debian.keesmeijs.nl](http://debian.keesmeijs.nl) lucid-kees Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 055D2AD2157AA138


Suggestions?

EDIT: DISREGARD THE ABOVE

Got Doom working fine.

Heretic however, is another story entirely.

> --- No IWAD has been specified! Important data might be missing. Are you sure you want to continue?
**ERROR** W_AddFile: /usr/share/deng/data/jheretic/auto/.basedata/fontb62.lmp
W_AddFile: /usr/share/deng/data/jheretic/auto/.basedata/fontb63.lmp
W_AddFile: /usr/share/deng/data/jheretic/auto/.basedata/mapmask.lmp
W_AddFile: /usr/share/deng/data/jheretic/auto/.basedata/menufog.lmp

W_CheckIWAD: Init aborted.


EDIT AGAIN: The above instructions for getting Doom only get me "Knee Deep in the Dead".  "The Shores of Hell" and "Inferno" can't be accessed and "Thy Flesh Consumed" is missing entirely.

---

### Post by fodorgyuri666 on 2011-01-28
> fodorgyuri666@fodorgyuri666:~$ gpg --keyserver gpg.mit.edu --recv-keys 0x4B6E7209
gpg: requesting key 4B6E7209 from hkp server gpg.mit.edu
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'gpg.mit.edu'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
fodorgyuri666@fodorgyuri666:~$ gpg --export -a 0x4B6E7209 > Yagisan.asc
gpg: WARNING: nothing exported
fodorgyuri666@fodorgyuri666:~$ sudo apt-key add Yagisan.asc
gpg: no valid OpenPGP data found.
fodorgyuri666@fodorgyuri666:~$ 


it seems dont work out for me. whats the matter whit it?
Can I fix it?

---

### Post by DoktorSeven on 2011-01-28
> **Convoycation said:**
> 

EDIT AGAIN: The above instructions for getting Doom only get me "Knee Deep in the Dead".  "The Shores of Hell" and "Inferno" can't be accessed and "Thy Flesh Consumed" is missing entirely.
The above links only to the Shareware version of Doom, which exists when you download Doomsday or another Doom variant.  You need to change the path shown to your existing doom.wad file, for example mine is in /share/Games/doom/iwads/doom.wad:

**doomsday -g jdoom -file /share/Games/doom/iwads/doom.wad**

Same with Heretic:

**doomsday -g jheretic -file /share/Games/doom/iwads/heretic.wad**

Again, change the path to where YOU have these WADs stored.

Of course, if you don't have these WADs, you will need to get a copy of them from an existing legally purchased version of Doom/Heretic/etc. :)

---

### Post by kn0w-b1nary on 2011-03-05
Thx a lot!

---

### Post by Niccola on 2012-06-06
Now it becomes easier to install,

new version Doomsday 1.9.8+ becomes with a ready .deb install file.

visit [dengine website]("http://dengine.net/ubuntu") to see the files

---

### Post by el_oscuro on 2013-01-27
> **fodorgyuri666 said:**
> it seems dont work out for me. whats the matter whit it?
Can I fix it?

After editing sources.lst, try:

sudo apt-get install kees-archive-keyring

Then continue with the  sudo apt-get update and the rest of the steps.

---


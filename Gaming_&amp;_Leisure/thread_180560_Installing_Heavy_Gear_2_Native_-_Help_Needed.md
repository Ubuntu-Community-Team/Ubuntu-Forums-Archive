---
title: "Installing Heavy Gear 2 Native - Help Needed"
date: 2006-05-22
forum: Gaming &amp; Leisure
---

### Post by Footissimo on 2006-05-22
Just got me copy of Heavy Gear 2 - kinda chuffed, though having some problems installing.

Its got the usual loki installer and so I install to /usr/local/games as I do with all the other games with the following command ```
sudo sh setup.sh
```

This gives me the following:

```
matt@Lumpi:/media/cdrom$ hg2
dirname: too few arguments
Try `dirname --help' for more information.
Creating preferences directory...
Creating directory /home/matt/.loki/hg2/
Creating directory /home/matt/.loki/hg2/shell
Creating directory /home/matt/.loki/hg2/shell/texts
Installing default /home/matt/.loki/hg2/bindings.def
cp: cannot stat `/bindings.def': No such file or directory
Installing default /home/matt/.loki/hg2/shell/texts/options.cfg
cp: cannot stat `/shell/texts/options.cfg': No such file or directory
Couldn't run Heavy Gear 2 (hg2stub). Is HEAVY_GEAR_2_HOME set?
```

Not sure what all this means, so I try the patch from the loki site:

```
sudo sh hg2-1.0b-unified-x86.run --keep
```

and it updates the program (yay!)..but when I run it I get this:

```
Try `dirname --help' for more information.
Creating preferences directory...
Creating directory /home/matt/.loki/hg2/
Creating directory /home/matt/.loki/hg2/shell
Creating directory /home/matt/.loki/hg2/shell/texts
Installing default /home/matt/.loki/hg2/bindings.def
cp: cannot stat `/bindings.def': No such file or directory
Installing default /home/matt/.loki/hg2/shell/texts/options.cfg
cp: cannot stat `/shell/texts/options.cfg': No such file or directory
Couldn't run Heavy Gear 2 (hg2stub). Is HG2_DATA_PATH set?
```

(boo!)

:(

'elp!

---

### Post by simplyw00x on 2006-05-22
Well it looks like you need to type 'export HG2_DATA_PATH=/path/to/hg2/data' and press enter, _then_ run hg2. Try the README file :p

---

### Post by Footissimo on 2006-05-22
Didn't help :(

..but installing it as user did :) :)  Kinda annoying, but better than not working at all :)

Edit, for anyone else wanting to install, I did it this way:

```
cd /whereever/CD/is/mounted
sh setup.sh
```

...loads up loki installer, install in user home directory

```
sudo apt-get install freetype2
```

...font package needed for game

```
cd ~/whereever/you/want/to/temporarily/put/the/patch
wget ftp://sunsite.dk/mirrors/lokigames/updates/hg2/hg2-1.0b-unified-x86.run
```

...get the patch

```
sh hg2-1.0b-unified-x86.run --keep
```

..run the patch...go through instructions..and its done :)

---

### Post by wishyjr on 2006-05-23
hiya, is there a native port of this game yousay? wow, could you point the way? i loved heavy gear years ago an i'd love to play it again. thanks.

---

### Post by Perfect Storm on 2006-05-23
[http://tuxgames.com/](http://tuxgames.com/)

---

### Post by nukedog on 2006-06-06
I'm horribly new to Ubuntu and linux, but I am learning, slowly.
I just updated to 6.06 and bought Heavy Gear 2 Linux.
I managed to install it thanks to the sage advice here, but I can't get it to run, even after trying everything suggested, except installing as user. Don't know how to do that.
I keep getting this error in terminal:

Try `dirname --help' for more information.
Installing default /home/nukedog/.loki/hg2/bindings.def
cp: cannot stat `/bindings.def': No such file or directory
Installing default /home/nukedog/.loki/hg2/shell/texts/options.cfg
cp: cannot stat `/shell/texts/options.cfg': No such file or directory
Couldn't run Heavy Gear 2 (hg2stub). Is HEAVY_GEAR_2_HOME set?

I am a newb, and welcome any suggestions.

Thanks!

---

### Post by Footissimo on 2006-06-06
Hiya

I'm going to have another go at it tomorrow and try and get it to run systemwide..so I can add it to [this](http://ubuntuforums.org/showthread.php?t=189360) thread.  To be honest, the errors that you're getting sound like the errors that I was getting  - as you have said, I got over that by just installing as user rather than root i.e. when it asks you where to put the files, you put it in your home directory i.e. /home/[enter username]/hg2 rather than the default usr/local/games.  If you want to try that then you can uninstall the old version:

```
cd /usr/local/games/hg2
```
```
sudo sh uninstall
```

---

### Post by nukedog on 2006-06-06
](*,) Thanks!
I'll try that.

---

### Post by nukedog on 2006-06-06
I tried it, and it said I did not have permission to write to /home/nukedog/hg2
To install as user, is there anything special I do? I just opened terminal, and just went at it.
](*,)

---

### Post by Footissimo on 2006-06-07
Got it to work systemwide - see [this](http://ubuntuforums.org/showthread.php?p=1106525#post1106525)  thread.  Worth removing the old files before doing so (including the hg2 directory under the hidden loki home directory (i.e. /home/[username]/.loki)

---

### Post by vpalexander on 2006-11-12
Has anyone successfully installed under Edgy? I get an error from setup: 

sudo sh setup.sh

setup.sh: 9: function: not found
x86

---

### Post by leech on 2006-11-12
I've already had one game (Postal 2 Apocalypse Weekend) that had issues with Edgy, simply because they switched to Dash instead of Bash for their shell.

Try running ```
sudo dpkg-reconfigure dash
``` and tell it not to use dash.  Then run the installer again.  To go back to dash, run the same command again.  

I'm really wondering how many things switching to Dash has broken.

Leech

---

### Post by Judicata on 2006-11-18
I had a similar problem. Telling it not to use Dash solved the problem (per leech's suggestion).

---


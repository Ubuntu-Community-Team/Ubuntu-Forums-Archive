---
title: "After updating to Ubuntu 8.10, xorg no longer works"
date: 2008-12-11
forum: General Help
---

### Post by Pharaoh Atem on 2008-12-11
I recently updated my Gateway M675 laptop to Ubuntu 8.10 from Ubuntu 8.04. Once I had updated, I was unable to use Xorg at all! It says when loading fglrx, (EE) No screens detected!

However, when I load any other driver, it somehow segfaults! I have no idea why! However, I do want to either use the Radeon or the fglrx driver because I use 3D functionality regularly on my laptop. And I use fglrx because performance under Wine with 3D is better than under the FOSS driver for some reason....

Please, is there a way to fix this? I already did the fix xorg options in recovery mode and in normal mode. aticonfig segfaults, so I can't do anything with that. I don't know which Catalyst revision this corresponds to, so meh.

---

### Post by phidia on 2008-12-11
Have you tried running/entering > sudo dpkg-reconfigure -phigh xserver-xorg?

BTW the command in recovery mode is "xfix".

---

### Post by Pharaoh Atem on 2008-12-12
> **phidia said:**
> Have you tried running/entering ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` ?

BTW the command in recovery mode is "xfix".

I used both of those! They don't help, since both of those commands reset it to the FOSS driver which just segfaults.

---

### Post by Bear Knuckle on 2008-12-12
What does the log say?

/var/log/Xorg.log*

---

### Post by Pharaoh Atem on 2008-12-12
> **Bear Knuckle said:**
> What does the log say?

/var/log/Xorg.log*
I cannot post a whole thing because i am operating from links2, but the error was the drm could not open /dev/dri/card0 as it didnt exist or something like that, then the backtrace occurred. That was with the opensource driver.

The fglrx driver had a different log. Apparently the error was that no devices were detected, then it said no screens were detected. Is there a way to fix this? Maybe make it force to know where the card is or something?

---

### Post by Poyntz on 2008-12-12
> **Pharaoh Atem said:**
> I cannot post a whole thing because i am operating from links2
Don't post the whole thing. Download pastebinit
ie, ```
sudo apt-get install pastebinit
```

Then pipe the output from xorg.log to pastebinit
ie, ```
cat xorg.log | pastebinit
```

Put the link it outputs here and someone will check over your log.


> **Pharaoh Atem said:**
> but the error was the drm could not open /dev/dri/card0 as it didnt exist or something like that, then the backtrace occurred. That was with the opensource driver.
If you're good with scripting modify xorg.conf to your appropriate graphic driver. Otherwise open a console and type:
```
apropos <brandname of your card>
```
- see what comes up and try to
```
sudo apt-get install <the most relevant config file you can find for your driver>
```

---

### Post by phidia on 2008-12-12
> **Poyntz said:**
> 

If you're good with scripting modify xorg.conf to your appropriate graphic driver. Otherwise open a console and type:
```
apropos <brandname of your card>
```
- see what comes up and try to
```
sudo apt-get install <the most relevant config file you can find for your driver>
```

Since 8.10's xorg 7.4 doesn't contain the configuration data for gpus & monitors it will be interesting to see how that works.

---

### Post by Pharaoh Atem on 2008-12-12
> **Poyntz said:**
> Don't post the whole thing. Download pastebinit
ie, ```
sudo apt-get install pastebinit
```

Then pipe the output from xorg.log to pastebinit
ie, ```
cat xorg.log | pastebinit
```

Put the link it outputs here and someone will check over your log.



If you're good with scripting modify xorg.conf to your appropriate graphic driver. Otherwise open a console and type:
```
apropos <brandname of your card>
```
- see what comes up and try to
```
sudo apt-get install <the most relevant config file you can find for your driver>
```

Here is the pastebin for the Xorg log for fglrx:
[http://pastebin.com/m1a0a5528](http://pastebin.com/m1a0a5528)

Here is the pastebin for the Xorg log for radeon:
[http://pastebin.com/m19d267b8](http://pastebin.com/m19d267b8)

I also have no idea what I am supposed to do with the apropos information...

---

### Post by Poyntz on 2008-12-13
> **phidia said:**
> Since 8.10's xorg 7.4 doesn't contain the configuration data for gpus & monitors it will be interesting to see how that works.

Well I managed to get my card working correctly through what I listed above. I found a config file for NVidia or ATI which on installation managed to install a driver/make visible a driver for my card. I then went to hardware drivers to find the outdated driver that was installed. I then upgraded to the latest driver to optimise the card's function. 
- that was on Ibex by the way ;)

> **Pharaoh Atem said:**
> I also have no idea what I am supposed to do with the apropos information...
Sorry, I forgot to mention.
```
apt-cache search <what you found under apropos search>
``` - to see if it's installable
then if it's listed,
**sudo apt-get install** <the application>

---


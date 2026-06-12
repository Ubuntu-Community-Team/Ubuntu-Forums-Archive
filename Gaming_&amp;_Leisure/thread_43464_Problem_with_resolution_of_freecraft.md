---
title: "Problem with resolution of freecraft"
date: 2005-06-22
forum: Gaming &amp; Leisure
---

### Post by frank_y on 2005-06-22
I just installed freecraft 1.18 and played it for a while, and decided to go fullscreen but accidently clicked on the 1600x1200 resolution. My monitor only goes up till 1024x768 so every time I started freecraft nothing would happen. I tried using the terminal, and it said could not create a window with that resolution so I know that's the problem. I tried using command line option -v 1 for 640x480 but it keeps loading a config file that I can't find and keeps trying to set it to the 1600 resolution. I did a "complete" uninstall with synaptic and reinstalled but still it wouldn't work.

Can anyone tell me how to change this config file, delete it, or temporarily force a resolution change so I can fix the option?

Thanks,

Frank

---

### Post by nybble on 2005-06-22
ya, i just did the same thing.. woops..
any one have a fix? :-#

---

### Post by nybble on 2005-06-22
oki, i suggest install [Stratagus](http://stratagus.sourceforge.net/). Its the same game almost, same engine etc..
```
sudo apt-get install stratagus
``` 

Enjoy!

---

### Post by frank_y on 2005-06-22
:) I did that too, but I was wondering if there is a fix for freecraft because I kind of like its ... simplicity. And I already know how to play warcraft. Heh.

---

### Post by nybble on 2005-06-28
I've figured it out.

```
gedit ~/.freecraft/preferences1.ccl
``` 

Find: 
```
(set-video-resolution! X X )
```

and change the X X to a resolution that your system supports. Ex. 1024 768
so that line should read:
```
 (set-video-resolution! 1024 768 ) 
```

You can do that, or just delete the .freecraft directory, and it will create a new one. but then you will loose any saved information...

Hope this helps

**nybble**

---

### Post by `GooZ´ on 2005-11-25
Thx ALOT! :-)

---


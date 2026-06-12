---
title: "Problem loading pages in the web"
date: 2009-05-02
forum: General Help
---

### Post by Macacoveio on 2009-05-02
Hi,
i tryed to search a little bit, but i didn't find anything like this.

since when i updated all the programs of my 9.04  neither Firefox or Epyphany are surfing well in the net...
[IMG]http://images.macacoveio.multiply.com/image/1/photos/17/600x600/1/Captura-de-tela.png?et=pMgx3nnyrF6eyBHZJlGqXw&nmid=238409045[/IMG]
the texts fonts appear in white and i can't see what's in the site, only the layout and the images...
can someone help me?
someone with the same problem?

i instaled 9.04 in a laptop and got the same problem...

I have already tryed changing the Theme of ubuntu,
i have already deleted and re-instaled firefox from the PC and the problem persist...
it occurs in all sites: gmail, google, etc, etc.


THXKS a lot!

---

### Post by Happy_Man on 2009-05-02
Try deleting the folder ~/.mozilla and see if that helps.

---

### Post by neu2buntu on 2009-05-02
in firefox goto >edit>preferences>content>colours.......see if your txt colour is white or not ,if so click on the colourbox and change

or tick "allow pages to choose their own colour"

---

### Post by Macacoveio on 2009-05-03
I had already tryed to change color, but it didn't worked...

now i tryed seamonkey and its the same thing that firefox....
white text...

i tryed to delete again
the firefox and reinstall it but the problem persist...
anyone has another clue?:confused:


thx

---

### Post by neu2buntu on 2009-05-03
try uninstalling with ```
sudo apt-get --purge remove firefox
``` this should take the config files out with it,then just reinstall it

---

### Post by Macacoveio on 2009-05-03
I tryed uninstalling like that too, but when i re-install firefox and open Gmail... it stays the same way...


but wow! now i could enter this site and post from the firefox! so some site open well, and other stay shited :-(

what might it be?

---

### Post by Macacoveio on 2009-05-03
i opened the firefox from the console and after a while with the same probkem i saw this:
"
[..]
(firefox:4267): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 10.5'

(firefox:4267): Pango-WARNING **: font_font status is: <unknown error status>

(firefox:4267): Pango-WARNING **: scaled_font status is: out of memory

(firefox:4267): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 10.5'

(firefox:4267): Pango-WARNING **: font_font status is: <unknown error status>

(firefox:4267): Pango-WARNING **: scaled_font status is: out of memory

(firefox:4267): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial Bold 10.5', text='The quick brown fox jumps over the lazy dog.'
"


maybe it have something with my problem, no?

---

### Post by neu2buntu on 2009-05-03
it maybe is that the sites you cant see your text in are using arial bold fonts..... try this ```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by Macacoveio on 2009-05-03
no...
i already got this package

---

### Post by neu2buntu on 2009-05-03
this font is also in package ttf-liberation,so same as before ```
sudo apt-get install ttf-liberation
```

---

### Post by Macacoveio on 2009-05-03
Nope... i tryed but they were already installed too....

very weird this problem...
i tryed to desactivate 2 plugins, and it didnt work also...

i'm sad!
the problem seem to be somewhere else...

---

### Post by neu2buntu on 2009-05-03
look here >firefox>edit>preferences>content>advanced>and tick "allow pages to choose their own fonts "

---

### Post by Macacoveio on 2009-05-03
It was already ticked! :(

---

### Post by cariboo on 2009-05-03
It looks like you done everything but replace the .mozilla directory like Happy_Man suggested. That looks like the only step left. Open an Applications-->Accessories-->Terminal and type:

```
mv .mozilla .mozilla.bak
```

If you've got Firefox running, restart it and you should be OK. If Firefox works the way it should you can copy your bookmarks file from .mozilla.bak/firefox/xxxxxx.default to .mozilla/firefox/xxxxxx.default. the xxxxxx will be a string of random numbers and letters.

---

### Post by Macacoveio on 2009-05-03
That's it!

i had only to renew these configuration files!

thanks a lot Cariboo, Happy_man, Neu2buntu and others

you helped me  a lot , and learned me lot of things too...

thanks
M

---

### Post by Macacoveio on 2009-05-04
NOOOOOOOO!


i started then firefox today, and then.............................................................


the problem was back!

i tryed to do the same step again, but didn't worked!

:confused::confused::confused::confused::confused::confused::confused::confused:

---


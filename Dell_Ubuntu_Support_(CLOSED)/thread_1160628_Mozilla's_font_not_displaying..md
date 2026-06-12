---
title: "Mozilla's font not displaying."
date: 2009-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sirebral on 2009-05-15
This problem has arisen after I installed some new TTF fonts on my Dell Mini.  After the new fonts where copied, everything but the Mozilla browser would work.  It just does not display any words.  Anyone know the fix to this?

---

### Post by coffeeaddict22 on 2009-05-16
Hi,
Have a look in the Firefox menu system: Edit/Preferences; the Content tab, and choose a default font.  I'd guess you deleted the font it's supposed to be using, which will make things look a bit empty.

---

### Post by sirebral on 2009-05-16
I tried that.  I can try it again.  in the meantime I have been using Arora as an internet browser.

---

### Post by sirebral on 2009-05-17
it would seem the problem is with Pango.  from my terminal

> (firefox:6846): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 8.25'

(firefox:6846): Pango-WARNING **: font_font status is: <unknown error status>

(firefox:6846): Pango-WARNING **: scaled_font status is: out of memory

(firefox:6846): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial Bold 8.25', text='The quick brown fox jumps over the lazy dog.'


If I have Firefox not allow pages to select their own font I can browse, but that is sucky.

---

### Post by coffeeaddict22 on 2009-05-17
Pango is the C programming language text rendering interface: ie it draws text.  Firefox can't find your fonts, by the looks.  I suspect you're missing a needed package; looking in Synaptic package manager (System/Administration/Synaptic) you probably need to reinstall the ttf-mscorefonts-installer package.  Search for it using the bar up the top, then either install it or reinstall it depending on the option, and that should fix it.

---

### Post by sirebral on 2009-05-17
nope. i also reinstalled anything with pango. not working.

---

### Post by coffeeaddict22 on 2009-05-18
Pango probably isn't the problem.  Pango is called by Firefox to draw the "pictures" that correspond to text.  Pango renders text; converts it from the minimum information (used by the system to figure out what letter you want on the screen) to the pixel colourings needed.  Have you looked in var/log/messages?  or run ```
dmesg
``` just after you've opened Firefox?  and what happens if you try to use Arial in an Openoffice doc?  If they render fine, try reinstalling firefox.

---

### Post by sirebral on 2009-05-20
i think you may have fixed my problem.  i seem to be missing arial.  gotta d/l it to check.

---

### Post by sirebral on 2009-05-21
Thanks a lot coffeeaddict.  I went into my fonts directory and discovered a number of folders that did had permission restrictions on them.  All is working now. :D

---

### Post by Trent T on 2009-10-17
Thanks coffeeaddict and sirebral!

I had a similar experience adding fonts to Ubuntu;
I opened a terminal, and started nautilus as root with the command;

sudo nautilus

then went to 

/usr/share/fonts

I right-clicked ttf font subdirectories  and went to 
properties ... permissions
to give read write access to all groups, 
applied these changes to all files within, and exited.
Now firefox fonts display again in my web browser!

Thanks again!!
Trent T

Problem Documentation:

After new font installation Firefox did not display fonts.
Alternative web browser epiphany also did not display fonts.

Starting firefox from terminal revealed error messages like this;

(firefox:5178): Pango-WARNING **:failed to create cairo scaled font, expect ugly output, the offending font is 'Arial 7.296875'

(firefox:5178): Pango-WARNING **:font_font status is: <unknown error status>

(firefox:5178): Pango-WARNING **:scaled_font status is: out of memory.

I installed an alternative web browser 'Epiphany' using Synaptics Package Manager.

It displayed the same error messages, and also displayed underlines instead of fonts.  Therefore the problem was in the system fonts.

---


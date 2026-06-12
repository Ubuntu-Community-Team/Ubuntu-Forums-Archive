---
title: "Berly not loading settings"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by UK-Wobbie on 2007-06-23
I got berly installed on my ubuntu 7.04 
And i made all the shortcuts how i liked it!
I saved the out saved file on my pendrive and when i had a go on loading it back up in a new ubuntu restall it did not open or load :(

Do any one no why?
thanks

---

### Post by Alex&amp;Linux on 2007-06-23
Hey.

I havent actually tried using a pre config with beryl more than once, and it didnt work either.
I have a very simple setup for beryl, so its not a big deal to start over for me.
However, its possible to copy your settings into a text file and gedit them into your existing config.

If youre not sure about how to do that:
To copy your settings, in terminal:

 $ cd .beryl

you should see "libberylsettings.ini" and "settings"

 .beryl$ cat settings

And you will see your config in text here.
To edit it
 
 .beryl$ gedit settings

You can copy this and save it to a text file, it functions as sort of an "image" of your config.
To set this to any other install of it, just do the same, except paste in your text when you gedit settings.
I havent had need to do it, but I cant see any reason why it shouldnt work.

Do you know how to fix the Nvidia black screen bug? Its pissing me off.

---


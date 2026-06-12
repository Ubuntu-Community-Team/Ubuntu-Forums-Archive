---
title: "problem with international characters"
date: 2006-07-04
forum: Desktop Environments
---

### Post by stdragon on 2006-07-04
Hi,

I'm trying to type vowels with macrons (the straight bar over the vowel) like &#299;, &#363;, etc. I've set my capslock key to be the Compose key (in Keyboard -> Layout options), and it's working with &#275;, &#299;, and &#363;.  However, "a" and "o" produce squiggles over the vowel instead of a straight line.

I've searched through the forums here and this problem is mentioned several times but never addressed. There's also some possibly incorrect information. For instance, one person suggested looking in /usr/X11R6/lib/X11/locale but that directory is totally empty for me. On the other hand, /usr/share/keymaps/include/ contains several files, none of which mention utf-8, and all of which seem to contradict each other for the key compositions. I have no idea which one is being used, or if any are at all.

So my question: Where is the real list of key compositions that are in use, and how can they be edited?

---

### Post by stdragon on 2006-07-09
Hey I figured it out!

Gnome/GTK doesn't use ANY of those files. There is a built-in list of compose sequences that you cannot change.

To force Gnome to use the standard way of doing it, you have to set the input method to "xim". Do this by editing /etc/environment and adding

    export GTK_IM_MODULE=xim

at the end. Now copy /usr/share/X11/locale/en_US.UTF-8/Compose to ~/.XCompose (e.g. in your home directory as .XCompose). Now logout and restart the X server and next time you log in everything will work as expected.

It might be a good idea to edit the file a bit too. I don't have a "macron" key on my keyboard so I replaced <macron> with <minus> everywhere. I also deleted all the Cyrillic, Arabic, and Greek stuff since I only wanted latin characters with accents.

---

### Post by bogen on 2006-07-14
Best. Hint. Ever. Seriously! It should be added to ubuntuguide.org! Thank you!!! :)

---

### Post by kolesarm on 2007-02-21
thanks a lot, stdragon - I often need to type german umlauts, and it was a pain to be switching the keyboard layout all the time!

---

### Post by Yeti can't ski on 2008-02-29
People should build a statue to you! This suggestion is now part of the Ubuntu guide on ComposeKey, but I think it is astonishing that there is not graphic ("dumb") way to do this. I have an Italian keyboard (without a tilde!) and needed German and Portuguese special characters. I couldn't find any help in the web because everyone is concerned with US keyboards. This post literally saved my Ubuntu's usability. Thank you!!!:)

---


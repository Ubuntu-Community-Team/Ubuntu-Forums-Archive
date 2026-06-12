---
title: "How do I create a custom keyboard layout?"
date: 2011-02-23
forum: Desktop Environments
---

### Post by sambhogi on 2011-02-23
I need to create a custom keyboard layout for Canadian Aboriginal syllabics. How do I do this? Keyboards exist for Windows and Mac. 

I can't find any current documentation for this.

---

### Post by robitabu on 2011-04-03
I have the same need right now. I use a Logitech with this layout: [http://www.vbshop.nl/products/LOGITECH/LOG9676701510.jpg](http://www.vbshop.nl/products/LOGITECH/LOG9676701510.jpg)
But it's not supported and not listed in any Gnome Keyboard Configuration tool.

I'd really like to add the Logitech LX710 keyboard layout to my Ubuntu 10.10 (and provided it to the community as well). But I don't find any (really nothing!) documentation about how to do that.

I'm pretty shure I'm searching it the wrong way, but I have problems even knowing what's the Keyboard Layout program name; hitting the Help button on it I get redirected to a Gnome Help window that alerts me with the following error only:  <<ghelp:gswitchit?layout-view>> URI not valid!

---

### Post by sambhogi on 2011-04-04
My research suggests that GNOME has made it very difficult to customize keyboard layouts. 

However, I did find this:

[http://code.google.com/p/keyboardlayouteditor/](http://code.google.com/p/keyboardlayouteditor/)

Bear in mind that Ubuntu is switching to Unity as its default desktop in the next release. Whether this will make such customizations easier or more difficult, I do not know.

---

### Post by Spirit of Yggdrasill on 2011-05-18
It is quite easy. You just need to create a copy of your almost working layout and do a few modifications.
Files to edit are in:
/usr/share/X11/xkb/symbols

Here is a tutorial to get you started:
[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

Be sure to backup existing layout before you do anything :)

I used this technique to move curly braces, brackets and less than and greater than symbols to a,s,d,f,z and x keys; because I use them constantly in coding and in my default layout (rs) they are hard to get :D

Enjoy the possibilities :popcorn:

---

### Post by grahammechanical on 2011-05-18
Ubuntu already has keyboard layouts for Inuktitut, Ktunaxa, Secwepemctsin. Are these not sufficient? Are the characters that you want present in Unicode fonts? A layout remaps the keyboard to characters already present in a Unicode font. A layout cannot give you what is not there.

Regards.

---


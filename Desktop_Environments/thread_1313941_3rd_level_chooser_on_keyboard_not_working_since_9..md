---
title: "3rd level chooser on keyboard not working since 9.10"
date: 2009-11-04
forum: Desktop Environments
---

### Post by dvandok on 2009-11-04
I recently switched to Karmic and discovered that the right-Alt behaviour stopped working.

I'm using an international keyboard layout with some extra options; I sometimes need accented characters and I could always type these with rightAlt+a for an à, for instance.

Oddly, this doesn't work anymore in almost any text input field, but it still works in gnome-terminal! The xev program shows that the right keysyms are getting through, so I suspect there's something amiss in relation to gnome.

Can anybody confirm this?

---

### Post by mathieud on 2009-11-05
Hello,

I have the same problem!

I can confirm that 3rd level chooser doesn't work under firefox, thunderbird, gedit and the keyboard preferences window while it works under gnome-terminal.

For me this include accents (especially upper-case), arobase (what a pain for thunderbird) and sharp.

I use latin-9 layout on a french AZERTY keyboard (and usually AltGr as the 3rd level chooser).

I remember that I had the same problem some time ago (I thonk it was at the beginning of 9.04).

Mathieu

---

### Post by dvandok on 2009-11-05
I dug a bit deeper, and I found out that somehow the 'Super' modifier is also attached to the key. That means that applications do not receive, e.g., 'agrave' (à) but 'Super-agrave' which is the composition of two modifiers. I found this by trying to edit keyboard shortcuts.

I'm going to open a bug for this.

---

### Post by mathieud on 2009-11-09
Hi dvandok,

Thanks for the bug report.

Hopefully someone will fix it!

Mathieu

---

### Post by lordcris on 2009-11-19
Any news on this one?

---

### Post by viranaso on 2009-11-23
I have what sounds like the same problem. I am using keyboard layout USA, with option for Adding Esperanto circumflexes to the qwerty keyboard, and key to choose 3rd level: Left Win and Right Alt. 

This problem did not occur in Jaunty (9.04), but does occur in Karmic (9.10).
This problem occurs in Gnome and in KDE.
I can confirm that the third level keys work with the terminal, and add that they still work with OpenOffice.org, Kate, Konqueror, and Lokalize,
but they do not work in gedit, Firefox or Thunderbird, Bluefish, gFTP, Gnucash, or Search for Files. When I press a 3rd level key combination no glyph appears on the screen and the cursor does not advance.

---

### Post by mathieud on 2009-11-25
Hello,

I don't know if that helps but I have just solved my problem.

Here are the steps I followed:
1) Open "Keyboard preferences" (System -> Keyboard preferences).
2) In the "Layout" tab, click on "Layout options". You will see a list of options. 
3) Unfold "Key to choose the 3rd level".
4) For me the "Any Win key" option was selected. I simply switched to "Right Alt".

Et voilà!

So basically for me the problem was just a wrong option... I have no idea why this, let's say, unsual option was selected...

Hope that helps,
Mathieu

---

### Post by RodGer GR on 2009-11-25
I don't really know what a 3d level chooser is but I have a problem that looks similar. I use two different keyboard layouts English and Greek. With Hardy Heron I had changed the keyboard preferences so that I could switch between the two layouts just by pressing the right alt  (Alt Gr) button. 
I tried to do the same in Karmic but it seems like there is a bug. Pressing the right alt changes only from English to Greek but doesn't work for the opposite.Using alt+shift works fine but that's not what I want...

Is there any way I can fix this. If it's a bug, for which packet I should file the bug. Is it the same bug referred from dvandvok? (If you filed the bug please tell us the number or give a link)
Thanks.

---

### Post by mathieud on 2009-11-25
Hello,

3rd level chooser is simply the key which allows you to type the third symbol on a key.

Similarly the 2nd level chooser allows you to type the 2nd symbol. The 2nd level chooser is usually the 'shift'  key (because the second symbol is usually the upper-case letter).
The 3rd level chooser is usually the "Alt Gr" key (right alt key).

For instance on my keyboard:
 - if I press the upper-left key it types "œ"
 - if I press Shift and the upper-left key I got "Œ" (the same character but upper-case)
 -if I press AltGr and the upper-left key I got "“"

In you case maybe the 3rd level key of the Grec layout is not binded to AltGr (see my previous post).

Mathieu

---


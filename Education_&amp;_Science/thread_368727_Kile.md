---
title: "Kile"
date: 2007-02-23
forum: Education &amp; Science
---

### Post by ali780 on 2007-02-23
Hello
Could you say me how can I install kile for using latex?
Thanks

---

### Post by slaanco on 2007-02-24
type in console 
```
sudo apt-get install kile 
```it should work

or u can run synaptic the find kile and install it thru it 

:)

---

### Post by lariosa42 on 2008-10-16
I use LaTeX a lot in Hardy, and recently started using Kile 2.0.0 as my editor.  It's a great program, but I can't seem to find a way to 'comment out' a block of text.  Of course, I can do it by manually inserting '%' symbols everywhere, but this is not practical when I need to comment/uncomment a few paragraphs.  Does anyone know if Kile has a 'comment out' feature, and if so, where it is located (or what hot-keys it uses)?  

If it is not a feature of Kile yet, it would be a very useful thing to add.  (While I'm on it 'red underlined' inline spell-check is probably the most important feature that should be added to Kile.)

Many thanks.

---

### Post by earlycj5 on 2008-10-16
> **lariosa42 said:**
> I use LaTeX a lot in Hardy, and recently started using Kile 2.0.0 as my editor.  It's a great program, but I can't seem to find a way to 'comment out' a block of text.  Of course, I can do it by manually inserting '%' symbols everywhere, but this is not practical when I need to comment/uncomment a few paragraphs.  Does anyone know if Kile has a 'comment out' feature, and if so, where it is located (or what hot-keys it uses)?  

If it is not a feature of Kile yet, it would be a very useful thing to add.  (While I'm on it 'red underlined' inline spell-check is probably the most important feature that should be added to Kile.)

Many thanks.

ctrl+d will comment out code.

---

### Post by Stefan_K on 2008-10-16
Further ctrl+shift+d could remove the comment signs.
Those commands can be found in the Tools menu.

Stefan

---

### Post by lariosa42 on 2008-10-17
Thanks for the replies, but it doesn't seem to work.  I tried both ctrl+d on regular text and ctrl+shift+d on test starting with %.  Neither had any effect.  Also, is it possible to "tab" a whole block of text, that is, move it all say, three spaces to the left or right?

---

### Post by lariosa42 on 2008-10-17
Actually, I figured this out.  The indent or "tabbing" feature is under the "Tools" menu.  However, the comment/uncomment menu items (also under "Tools") are grayed-out, even when I select text.  Hmmm...

---

### Post by stumbleUpon on 2008-10-18
> **lariosa42 said:**
> Actually, I figured this out.  The indent or "tabbing" feature is under the "Tools" menu.  However, the comment/uncomment menu items (also under "Tools") are grayed-out, even when I select text.  Hmmm...
Which version of Kile are you using....?

---

### Post by lariosa42 on 2008-10-18
I'm using Kile 2.0.0.  I just noticed there is a 2.0.2 version, but I haven't updated yet.  Running Kile (KDE based) on Ubuntu 8.04 (Gnome based) causes a few issues, so I'm not surprised that some things aren't running as smoothly as they could be.  I'm running it off of TeXLive 2007 (any word on whether the 2008 upgrade is worth it?).

Anyway, I figured out a partial fix to the above problem.  If go to Tools-->Highlighting-->Markup and select "LaTeX," then suddenly my document is properly highlighted, and I can use the Comment/Uncomment options as suggested in the above posts.  I have to do this every time I open the document, but at least it works.  I think this has something to do with the way LaTeX recognizes my documents (filetype: TeX document).  Anyway, hopefully that helps someone else with a similar problem.

---

### Post by d0.higgs on 2011-09-12
Thank you for this tip.
Now I have the opposite question, how to remove the comment sign from a block of commented-out block?

---

### Post by tommpogg on 2011-09-13
Hi, I'm using Kile in VI mode.
How can I comment a block of text?
It seems that the only way is to select the text with the mouse and then use the "Ctrl+d" shortcut. I would like to avoid using the mouse, keeping my hands on the keyboard, just like I do in VIM.

> **d0.higgs said:**
> Thank you for this tip.
Now I have the opposite question, how to remove the comment sign from a block of commented-out block?
Did you try Ctrl+Shift+d?

---

### Post by jacobsca on 2012-02-18
I have an issue with Kile. Not sure if this is the right forum or not.

Everything is fine and I can compile Latex and view it. What is happening is the the .toc file is not being written, moreover, it is being recognized as a Brasero file...clearly not what I want.

Is there an easy way to fix this so I can get the .toc file written correctly?

---


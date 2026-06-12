---
title: "Drag-n-drop text without tags"
date: 2011-09-03
forum: Desktop Environments
---

### Post by rainy-day on 2011-09-03
Hi,

I often need to copy and paste snippets of text from webpages into my editor. The easiest way to do this is to highlight and drag and drop text. Unfortunately, gnome (or browser?) "helpfully" adds all kinds of tags around the text (when using chrome, adds ^@ chars with Firefox).

How can I get plain text as with copy/paste?

I know that I can set up a mapping in my editor to strip tags, but I think it'd be easier and more robust to configure gnome or chrome, whichever one is at fault.

I googled for this issue with no luck.

Thanks!

---

### Post by sanderd17 on 2011-09-03
maybe you can use the Linux way of copy pasting:

Select text -> middle click on the place where you want to input text. 

The scroll wheel can be used as middle click, or if you're at a touchpad, click both buttons together.

---

### Post by rainy-day on 2011-09-03
I really don't like this method (and never use it) mainly for two reasons: first, you have to be precise where you point the mouse, and secondly that in all mice I've ever used (ms, logitech, wireless and wired, cheap and expensive) -- wheel is difficult to press, finger has to curl and press hard, and sometimes wheel will turn instead if you're not careful. And while you're messing around with the wheel, cursor moves a bit and you've pasted in the wrong spot.

I know there's a way to remap wheel to one of the additional buttons.. even so this is less than ideal because I'd have to still point precisely and I'd prefer to use vim commands to move cursor to the right spot and minimize use of mouse.

---

### Post by jfed on 2011-09-03
> **rainy-day said:**
> I really don't like this method (and never use it) mainly for two reasons: first, you have to be precise where you point the mouse, and secondly that in all mice I've ever used (ms, logitech, wireless and wired, cheap and expensive) -- wheel is difficult to press, finger has to curl and press hard, and sometimes wheel will turn instead if you're not careful. And while you're messing around with the wheel, cursor moves a bit and you've pasted in the wrong spot.

I know there's a way to remap wheel to one of the additional buttons.. even so this is less than ideal because I'd have to still point precisely and I'd prefer to use vim commands to move cursor to the right spot and minimize use of mouse.

I agree with you. While on a laptop with a touchpad I use this method 100% of the time, whilst using a traditional mouse I prefer the classic right-click copy&paste method. Unless it's for copy and pasting a URL. If that's the case, you can just triple-click on it to highlight it all, then easily mwheel press & goto in chrome :)

EDIT: Also, to comment on your actual problem; have you considered that the problem may be your editor? I did a quick check myself, using both Firefox and Chromium. I can drag and drop text just fine into gedit. Same with OpenOffice. It may be your editor. 

What version of GNOME are you using?

---

### Post by rainy-day on 2011-09-03
jfed: Using 2.30.2 gnome, you're absolutely right about gedit.. my editor is gvim, I have no idea why it's accepting html.. or how to stop it doing that..  

thanks for pointing out that gedit and I guess other editors don't do that.

---

### Post by rainy-day on 2011-09-03
I'm guessing that Gnome thinks Gvim is an html editor and pastes html tags together with text in it. When pasting into any text editor or terminal, it just pastes text. I need to tell Gnome that Gvim is just a text editor.

Hope someone knows how...

---

### Post by jfed on 2011-09-04
I'm not sure if you can. I mean I've never used it but that doesn't seem like the sort of thing that's in "preferences" I mean you could always edit the source code, or just give another editor a try. :P OpenOffice is quite nice.

And no problem, about the gedit pointer. ;)

EDIT: Also are you sure the issue is GNOME? I use XFCE, I could download and install the package and see if it still doesn't work if you give me the package name.

---

### Post by rainy-day on 2011-09-04
I'm pretty sure it's Gnome because that's what I run and I've heard that Gnome is the only(?) env that has text-drop feature.

I can't use any other editor because I've spent last 10 years learning the commands in Vim, tweaking settings and writing functions / plugins / etc. If it turned out Vim gives you cancer, I would at least seriously consider trying something else!

EDIT: wait, so text drop works for you in xfce too? Hmm, I'm kind of used to gnome though.. I'm asking on vim mail list just to be sure.

---

### Post by sanderd17 on 2011-09-04
> **rainy-day said:**
> I'm pretty sure it's Gnome because that's what I run and I've heard that Gnome is the only(?) env that has text-drop feature.

I can't use any other editor because I've spent last 10 years learning the commands in Vim, tweaking settings and writing functions / plugins / etc. If it turned out Vim gives you cancer, I would at least seriously consider trying something else!

EDIT: wait, so text drop works for you in xfce too? Hmm, I'm kind of used to gnome though.. I'm asking on vim mail list just to be sure.

I believe text drop (and almost all drag and drop things) are GTK features. XFCE ans LXDE also use GTK.

I can be wrong though.

---

### Post by rainy-day on 2011-09-04
So it is.. I think the issue is then that Gvim sets itself up as accepting marked up text on drops. I think I'll need to fix it in Gvim and recompile.

---


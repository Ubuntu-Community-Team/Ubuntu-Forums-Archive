---
title: "Mouse help?"
date: 2005-11-13
forum: Desktop Environments
---

### Post by ferentix on 2005-11-13
Erm... I just finished (re)installing Ubuntu Breezy, but now I have found my mouse to not work. Worse, I have no idea what kind of mouse it is (except that it isn't USB). Also, I can't properly understand that section of the "Linux hardware compatibility Howto".

So basically, rather than a vague description of the connector, I took a (crap) photo with the webcam on my WinXP machine! Can anyone help me identify what kind of mouse this is, and how to set it up under Ubuntu?

The logo on the back says "Genius", I've looked at a website for a company called "Genius" but their logo is different and they don't list this product (so it may be no longer supported, or they may be a different company...)

Any help/suggestions, please?

Here is picture
[IMG]http://i13.photobucket.com/albums/a255/Ferentix/Picture75.jpg[/IMG]

Oh, and I know you're meant to have 3 buttons on your mouse really... but I won't be able to get a new mouse for a while. In any case I need to know what type it is so I know what to look for when getting a new one.

---

### Post by Jemm on 2005-11-13
Looks like a Genius Easy Mouse Pro Serial 

[http://cgi.ebay.com/BNIB-NEW-Genius-Serial-Mouse-FREE-P-P-IN-uk_W0QQitemZ5829793142QQcategoryZ96886QQssPageNameZWDVWQQrdZ1QQcmdZViewItem#ebayphotohosting](http://cgi.ebay.com/BNIB-NEW-Genius-Serial-Mouse-FREE-P-P-IN-uk_W0QQitemZ5829793142QQcategoryZ96886QQssPageNameZWDVWQQrdZ1QQcmdZViewItem#ebayphotohosting)

but then again it could be something else :)

---

### Post by ferentix on 2005-11-13
You know what? I think you're right, because it looks almost identical to mine (except a different logo on the back of it) and the actual logo I find on my mouse is on that box (the one with the head of a mouse on the "G".

So... it's (probably) a serial mouse...

The thing is, now I know, how to actually get it to work?

EDIT: Well, found this guide [http://www.linux.com/howtos/3-Button-Mouse.shtml](http://www.linux.com/howtos/3-Button-Mouse.shtml)

Trying it now...


EDIT: ...Where is XConfig please? According to this guide I have to modify a portion of it? I've been trawling my computer this last hour to try find it..

EDIT: OK, solved it- found out it was actually xorg.conf I needed to edit. Changed the relevant options to set it's port as /dev/ttyS0, and the protocol to "Microsoft". Works fine now, and I learnt more about using the command line in the process :) Ideal. Thanks anyway :D

---


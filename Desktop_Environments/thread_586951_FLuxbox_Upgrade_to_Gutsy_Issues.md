---
title: "FLuxbox Upgrade to Gutsy Issues?"
date: 2007-10-22
forum: Desktop Environments
---

### Post by random_user on 2007-10-22
Wondering if I'm alone on this...

I don't think there are conflicting files, but I was wondering if anyone else using fluxbox is having issues after upgrading to Gutsy.  Mainly these couple things:

- It's not detecting the fluxbox system styles (yes the directory with styles exists)
- .roundCorners does not seem to be working (same goes for the .shaped attribute)


If anyone has any suggestions as to what could be causing these issues, I'd be glad to hear them!

---

### Post by seth0x2b on 2007-10-23
I got the same issue. Fresh Gutsy install, and no round corners in Fluxbox (I tested with pixmap based styles and normal ones).

---

### Post by random_user on 2007-10-23
Well at least I'm not alone on this :) If you so happen to find a fix to this please let me know! :)  (and likewise on my part)

---

### Post by RedSquirrel on 2007-10-23
The fluxbox package on gutsy has a few issues. For starters, it doesn't have XShape extension support and the menu is incomplete (missing Firefox, for example).

You can create your own menu and as for the XShape extension, you could compile your own Fluxbox. See the Howto in my sig for information on both of these topics.


EDIT: the menu problem has to do with the Debian menu and is not a Fluxbox-specific issue. I don't recall the styles not being recognized, but I'm currently on feisty with a compiled version of Fluxbox. In any event, setting up your own Fluxbox menu will help. ;)

---

### Post by seth0x2b on 2007-10-24
I don't understand this: they disbled Xshape even though they fixed bugs(like the one with the border missing where round corners were used..)? But anyways:
I compiled it with --enable-shape and round corners work now :)
@random_user:
1. Get the source tarball for Fluxbox 1.0
2. Extract it then enter the directory
3. ./configure --enable-shape --enable-xft --enable-kde --enable-gnome --enable--imlib2 --disable-slit
(you can use whatever flags you want, I disabled the slit because I don't use it)
4. make
5. sudo make install
6. Exit session and log back in
7. Done! :)

Also, RedSquirrel, thanks for your menu tutorial. I was used to the Debian style menu and was curious how to get it back :)

---

### Post by dnns123 on 2007-10-24
this is kinda rude, but get Fluxbuntu:popcorn:

---

### Post by random_user on 2007-10-24
Great, thanks a lot for the instructions! it works now :)

---

### Post by seth0x2b on 2007-10-24
> **dnns123 said:**
> this is kinda rude, but get Fluxbuntu:popcorn:
It's not rude. But as far as I know fluxbuntu is not a official Ubuntu, just some hack put together. Also..I think the iso is still under work(the Gutsy one).
@random_user: Don't mention it, glad to be of help.

---

### Post by RedSquirrel on 2007-10-24
> **seth0x2b said:**
> I don't understand this: they disbled Xshape even though they fixed bugs(like the one with the border missing where round corners were used..)? 

It is disappointing, but we can make our own fluxbox. :grin:

> **seth0x2b said:**
> But anyways:
I compiled it with --enable-shape and round corners work now :)
@random_user:
1. Get the source tarball for Fluxbox 1.0
2. Extract it then enter the directory
3. ./configure --enable-shape --enable-xft --enable-kde --enable-kde --enable--imlib2 --disable-slit
(you can use whatever flags you want, I disabled the slit because I don't use it)
4. make
5. sudo make install
6. Exit session and log back in
7. Done! :)


Just a few comments about these instructions:

3. The default configure options already include all of that. Disabling the slit isn't a bad idea if you don't use it, but the binary is so small it's not a big deal in my opinion. The only options left out if you just run './configure' are DEBUG (which you don't need) and NLS which you might want to try (I don't use it myself). You can run:

```
./configure -h
```to see what the options are.

5. I prefer to use checkinstall to make a deb package and install that. See the link in my signature for details.

6. Depending on how things are setup on your system, you might need to make a few more adjustments, such as configuring GDM to find your new Fluxbox. Again, see the link in my signature for details.


> **seth0x2b said:**
>  Also, RedSquirrel, thanks for your menu tutorial. I was used to the Debian style menu and was curious how to get it back :)


You're welcome. Glad it helped. :)

---

### Post by seth0x2b on 2007-10-24
I know about ./configure -h lol. I compile most everything from source. But the output of that shows that --enable-shape is defaulted but it didn't work for me without me asking so.
The reason for me skipping slit is that I didn't want that nagging "empty space" on the right of my screen even though there's nothing slitted. I don't really know how to get rid of that space, but not compiling it seems to do the trick. Who knows..
btw..one offtopic question. I got artwiz installed, but artwiz themes still don't work. I get a default big font. I know I installed the fonts correctly because I run xterm with -fn and I get artwiz fonts in the terminal.
Thanks again

---

### Post by RedSquirrel on 2007-10-24
> **seth0x2b said:**
> The reason for me skipping slit is that I didn't want that nagging "empty space" on the right of my screen even though there's nothing slitted. I don't really know how to get rid of that space, but not compiling it seems to do the trick. Who knows..

**Fluxbox Menu -> Configure -> Slit -> Maximize Over**


> **seth0x2b said:**
> btw..one offtopic question. I got artwiz installed, but artwiz themes still don't work. I get a default big font. I know I installed the fonts correctly because I run xterm with -fn and I get artwiz fonts in the terminal.
Thanks again

Not sure. I don't use artwiz. Sorry.

---

### Post by random_user on 2007-10-24
Yeah, sorry I don't use Artwiz fonts either :S

---

### Post by random_user on 2007-10-24
Actually...kind of a dumb suggestion, but have you tried editing whatever theme you're using to use a font that you *know* should work?  And if that stills show up large...not really sure what to say.  I did have another when upgrading to gutsy where my entire menu and fonts went huge..but I just changed my theme and it seemed to work.  The theme I was previously using was not mine, I didn't really feel like editing it (plus I got bored of it and realized it was ugly :P )

---


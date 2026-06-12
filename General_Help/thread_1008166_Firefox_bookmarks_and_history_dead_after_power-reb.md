---
title: "Firefox bookmarks and history dead after power-reboot"
date: 2008-12-11
forum: General Help
---

### Post by Jasper84 on 2008-12-11
I had a crash (probably caused by springlobby) and i was rather annoyed by other stuff so i didn't have the patience to try to kill the program, and slammed the power button of the powerextension to my computer stuff.

After that firefox lost its bookmarks and history, i can not make new bookmarks and history, nor can i access the backups. /home/jasper/.mozilla/firefox/j23qtvn7.default/bookmarks.html seems to be empty (just the default.)those .json backup file seem to have a lot of stuff in them, though. The adress bar seems to be buggered too, it doesnt update to the link i am at, unless i click on the symbol left to it, nor does backward or forward work.
Also, pidgin suddenly whines about not having seen the SSL certificate before. (This didn't happen immediately after, though.)

I already tried re-installing firefox, of course. How do i get this stuff to work again?

(I am using 8.04)

---

### Post by philinux on 2008-12-11
For future reference whenever you get a hard lock up caused by some bleeding edge software use this. 
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)
I find it easy if use use your little fingers to hold the alt and sysrq keys down,

Now I doubt if a power reset would mangle firefox's bookmarks. Anyway use this command to see what you've got.

locate bookmarks.html

You could also try starting firefox in safe mode.

firefox -safe-mode

Last resort, close FF, rename your .mozilla folder to .mozilla.bak and fire up firefox. This will create a new profile.

---

### Post by Jasper84 on 2008-12-11
I did the ~/.mozilla name-changing thing, and that worked :). I had already located the bookmarks file, but it was back to its default. Was however able to recover bookmarks with the .json backup file. As for the history, i don't care so much.

Thanks :)

---

### Post by lowtolerance on 2008-12-11
I highly recommend backing up your bookmarks offline, using an extension like foxmarks, so you don't run into this kind of issue in the future.

---

### Post by Bladeforger on 2008-12-11
Besides doing a backup, which is always a good idea... or an export to html through Firefox, there's another interesting way.  I've gravitated to this in pure self-defense against the "interesting" things that browsers do. 

Create a favorites file: f.html or fav.html.  Manually enter the links.  A friend of mine puts his up online so that when he travels from  office to office his links are always available to him.

I keep a few of these scattered around in the file:

```
<!--
<a href=""target="_blank">Blank</a><br />
<a href=""target="_blank">Blank</a><br />
<a href=""target="_blank">Blank</a><br />
-->
```(The markers are commented-out stuff.  This keeps my blank lines ready to paste a description into and then cut to outside the commented-out areas.)  

<a href=""target="_blank">Blank</a><br />
 becomes
<a href="http://ubuntuforums.org"target="_blank">Ubuntu Forums Main Page</a><br />

The file (mine) is about 700 lines long, by the way, with lots of older stuff commented out "temporarily".   I could probably take an hour or two and cull it down by half, but it's no big deal.

You can get a little fancy like this:

```
<DT><b>Email</b><br />
<DT><a href="http://mail.yahoo.com"target="_blank">Yahoo email</a><br />
<DD>YayHoo.</DD>
```Use this: <td>
stuff here in one column
</td>
<td>
makes the next column

Yes, it's more work, but I occasionally email my bookmarks to myself so they are preserved from  computer crash, Firefox crash, OS crash, fire, or hurricane.  Works for me.

Keith

---


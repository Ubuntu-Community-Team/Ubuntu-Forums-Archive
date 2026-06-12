---
title: "My Firefox &quot;Begs&quot; me to restart it"
date: 2009-05-05
forum: General Help
---

### Post by Gharchkhor on 2009-05-05
Hi

I was happy with my new installation of Jaunty Jackalope (:lolflag:) until suddenly the PC power went OFF. the sudden shutdown caused my Firefox to keep saying this message "Your browser has been updated and needs to be restarted." as a yellow bar below the tabs and a "Restart" button at its right side. But when I restart it that asks to be restarted again and again (as you've already guessed).

OK what's the solution?

---

### Post by toutanc on 2009-05-05
I guess you can try using safe mode to reset the settings or see where the problem comes from:

[http://www.universefirefox.com/how-to/firefox-safe-mode-how-to-use-it]("http://www.universefirefox.com/how-to/firefox-safe-mode-how-to-use-it")

```
firefox -safe-mode
```

I hope it does the trick :P

---

### Post by kanikilu on 2009-05-05
There's a workaround in this bug report that supposedly works (haven't needed to try it myself...):

[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303](https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303)

More information (and another possible solution):

[http://ubuntuforums.org/showthread.php?t=969921](http://ubuntuforums.org/showthread.php?t=969921)

---

### Post by Gharchkhor on 2009-05-05
> **toutanc said:**
> I guess you can try using safe mode to reset the settings or see where the problem comes from:

[http://www.universefirefox.com/how-to/firefox-safe-mode-how-to-use-it](http://www.universefirefox.com/how-to/firefox-safe-mode-how-to-use-it)

```
firefox -safe-mode
```I hope it does the trick :P
I can get the Firefox run in safe mode but the starting window won't show itself to me :)
This window I mean:
[IMG]http://www.universefirefox.com/images/2008/06/sm-interface.gif[/IMG]


Can't I just remove firefox and reinstall it?:confused: I remember a "dpkg" terminal code what is that? and what it does? and can it be helpful here? :)

---

### Post by Ugluk on 2009-05-05
I've marked firefox package to be reinstalled, and removed some flag file from $HOME and the message was gone.

---

### Post by Tipped OuT on 2009-05-05
Dude I had this happend before. I just needed to restart my computer. :lolflag:

---

### Post by Gharchkhor on 2009-05-05
**Nothing worked but this**: [http://ubuntuforums.org/showpost.php?p=6102512&postcount=2](http://ubuntuforums.org/showpost.php?p=6102512&postcount=2)

[B][COLOR=SeaGreen]SOLVED[/COLOR]
Thank you all for your time[/B]

---


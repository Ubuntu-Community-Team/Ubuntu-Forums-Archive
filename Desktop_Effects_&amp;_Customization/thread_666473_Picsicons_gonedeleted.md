---
title: "Pics/icons gone/deleted"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by Smultronsaft on 2008-01-13
Hi, I was deleting some compiz and emerald -folders before because i wanted to get rid of it, but some pictures or icons used in normal programs probably got deleted too.

Amarok: the play/stop buttons isn't visible but I can still click there

Kopete: that little butterfly-icon for msn in kopete is gone, I see some random colour instead

Ktorrent: All pics/buttons/icons gone

Cursor:the little pic that bounces next to the cursor when loading something is just a random colour too.

Does anyone know where those pictures are located, or how to get them back? It looks kinda ugly now... 
And Im using kde if that makes any difference.

---

### Post by .nedberg on 2008-01-13
Not sure if it would help, but it won't hurt:
```

sudo apt-get --reinstall install kubuntu-desktop

```

---

### Post by Smultronsaft on 2008-01-13
Nope that didnt help, tried reinstall kopete etc too, but nothing helps :/

---

### Post by glennric on 2008-01-13
> **.nedberg said:**
> Not sure if it would help, but it won't hurt:
```

sudo apt-get --reinstall install kubuntu-desktop

```

Reinstalling kubuntu-desktop won't help.  This is a meta package that depends on lots of other packages.  If you reinstall it, those other packages will not be reinstalled.  You will have to reinstall those other packages individually.  

As to getting the icons for kopete back, you may need to not only reinstall kopete, any other kopete packages that you have installed as well.  If this still doesn't help it may be because of something in your configuration and not because of missing files.  I am not sure what depends on kopete, but you could try 
```
apt-get remove --purge kopete
```
Then reinstall everything it uninstalls.  If that still doesn't work, it is probably a setting in your home directory that is causing the problem.

---

### Post by Smultronsaft on 2008-01-14
Nothing helps. Not even installing kde4 helped. I probably have to reinstall the whole system to get things back to normal, found several more apps that were missing stuff. Its all fun n games until linux goes foobar

---

### Post by .nedberg on 2008-01-14
Have you tried installing a new icon-theme? It might be that you deleted your icons. Istall a new one and use that one. It might help...

---

### Post by spdf on 2008-01-14
> **Smultronsaft said:**
> ... Its all fun n games until linux goes foobar

Where exactly were you deleting files from? If you were blindly deleting things in /usr, then I can understand why things went foobar.

---


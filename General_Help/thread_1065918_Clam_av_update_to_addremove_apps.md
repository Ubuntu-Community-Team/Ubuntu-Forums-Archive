---
title: "Clam av update to add/remove apps"
date: 2009-02-10
forum: General Help
---

### Post by dubhear on 2009-02-10
so...

i recently downloaded virus scanner, the one you can find from add/remove apps if you're ubuntu user, and i figured since updates are 365 days old (or even older)

how about if now on you could download it updated to this day, since some may not want to update it regulary or don't understand how?

how could this be done

btw: i update it thru terminal:
```
sudo clamtk
```
then it should start and you can click on update and see it's running with really old updates.

so what do you think? is it an empty cause for the trouble?

---

### Post by donkyhotay on 2009-02-10
What are you using the virus scanner for? If you're using it to help protect a windows box then just update your definitions when you need to scan a specific file. On the other hand if you're wanting automatic updates to protect our linux system then you should probably read the following link:
[http://catb.org/esr/writings/unix-koans/nervous.html](http://catb.org/esr/writings/unix-koans/nervous.html)

---

### Post by cariboo on 2009-02-10
If you really need a virus scanner, there are no Linux viruses in the wild, and you want to keep it up to date, open an Applications-->Accessories-->Terminal and type:

```
sudo freshclam
```

The above command will update clamav and create a cronjob that will check for updates daily.

For more on linux viruses have a look at this [article]("http://librenix.com/?inode=21").

Jim

---

### Post by dubhear on 2009-04-16
> **cariboo907 said:**
> If you really need a virus scanner, there are no Linux viruses in the wild,

yeah i know there are practically no linux viruses at all, but this is just a theory.

and thanks for a great tip for automatic updates!

i see now that there is no real reason to make clam-scanner to get updates by default when you apt get it.

case closed ;)

---


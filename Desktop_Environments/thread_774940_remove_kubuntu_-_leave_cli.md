---
title: "remove kubuntu - leave cli"
date: 2008-04-29
forum: Desktop Environments
---

### Post by talikarng on 2008-04-29
How can i remove kubuntu (8.04) and leave only a cli?

---

### Post by warp99 on 2008-04-30
> **talikarng said:**
> How can i remove kubuntu (8.04) and leave only a cli?
First issue the following:
```
sudo aptitude install kubuntu-desktop
```
Yes that is install, but we need to install any missing components so you can remove the entire desktop, then:
```
sudo aptitude purge kubuntu-desktop
```
and that will remove **all** of the KDE components associated with the kubuntu-desktop. This is the quickest way otherwise you'll have to delete each individual component. Remember to use 'aptitude' and not 'apt-get'.

---

### Post by talikarng on 2008-05-01
I didn't realise that it was this easy. Thanks.
(Before now I thought that doing this would remove everything).

---

### Post by aysiu on 2008-05-01
I don't really think that'll work, unless you started with a CLI only and used *sudo aptitude update && sudo aptitude install kubuntu-desktop* to install Kubuntu in the first place.

I think you'll have better luck with ```
sudo apt-get remove kdelibs-data kdm
```

---

### Post by talikarng on 2008-05-04
Thankyou to both  of you.
For anyone else who has to do this:

```
sudo apt-get purge kio-umountwrapper
```

then:

```
sudo apt-get purge kdebase-data kdelibs-data kdm
```

I found that by trying to remove kdebase-data first I got error messages caused by the removal of dolphin and konqueror.
(Something about a diversion of /usr/share/apps/dolphin/media_safelyremove.desktop not being found)

---


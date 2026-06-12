---
title: "[SOLVED] Enabling direct rendering"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by LinuxIsInnovation on 2008-01-16
Hello all
I want to enable direct rendering for Intel 945GM graphics on my laptop.
Check this:
```
glade@Muzic-Jukebox:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
glade@Muzic-Jukebox:~$ 

```  Please help.

---

### Post by veloce on 2008-01-16
Did you upgrade from Fiesty? If so, you need to:

sudo apt-get remove xserver-xgl

Restarting your x server should then allow direct rendering. (Assuming you have DRI enabled in your xorg.conf)

---

### Post by sayakb on 2008-01-17
Same case for me.. 
I installed from Gutsy CD directly..
also, i donot have xserver-xgl installed.

---

### Post by cammin on 2008-01-17
Did you install the Xubuntu CD?
When I did, it was missing the **libgl1-mesa-dri** package.

---

### Post by zetetic on 2008-01-18
> **sayakb said:**
> Hello all
I want to enable direct rendering for Intel 945GM graphics on my laptop.
Check this:
```
glade@Muzic-Jukebox:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
glade@Muzic-Jukebox:~$ 

```  Please help.

Go ask for help on windoze forums, you retarded.

---

### Post by sayakb on 2008-01-20
> **zetetic said:**
> Go ask for help on windoze forums, you retarded.

What should I do about my direct rendering? Should I post a new thread?

---

### Post by LinuxIsInnovation on 2008-01-20
> **LinuxIsInnovation said:**
> What should I do about my direct rendering? Should I post a new thread?

You post your queries in some other thread else bro.. people here are narrow minded and pathetic.. Im am closing this thread and leaving this community.. My God save these people..

---

### Post by zetetic on 2008-01-20
> **sayakb said:**
> Hello all
I want to enable direct rendering for Intel 945GM graphics on my laptop.
Check this:
```
glade@Muzic-Jukebox:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
glade@Muzic-Jukebox:~$ 

```  Please help.

This guy doesn't want any answers. He is just a troll. In fact, he already has a couple clones of himself on these forums.

---


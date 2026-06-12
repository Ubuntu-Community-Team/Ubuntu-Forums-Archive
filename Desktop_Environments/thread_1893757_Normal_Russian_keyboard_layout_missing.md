---
title: "Normal Russian keyboard layout missing"
date: 2011-12-11
forum: Desktop Environments
---

### Post by r.osmanov on 2011-12-11
Hi.

In a standard XUbuntu installation I can't find normal Russian keyboard layout :(

System Settings - Keyboard etc. allows to add miscellaneous(Osetian, phonetic, phonetic winkeys etc.) versions of Russian layout, except the normal one.

I fixed it temporarily with the following command: 
```
$ setxkbmap -layout us,ru -variant ',winkeys' -option 'grp:alt_shift_toggle,grp_led:scroll'

```Of course, I can put it into a runlevel script. 

I've also managed to do the same with /etc/default/keyboard XDG_* settings. 

But such kind of setup looks ugly. Furthermore, sometimes it is somehow overriden by system... 
So I'm searching for a standard way to set up the keyboard via  standard - preferably GUI - tools, as in Ubuntu, or KUbuntu.

Regards.

---

### Post by ilikelinuxitisthebest on 2011-12-11
click on Russian instead of the drop down window.

---

### Post by r.osmanov on 2011-12-12
> **ilikelinuxitisthebest said:**
> click on Russian instead of the drop down window.
Oh, if it were so simple. Look at the stuff it provides there in System settings - Settings manager - Keyboard - Layout - Add: 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=208944&stc=1&d=1323666364[/IMG]

As you see, there is no Russian(Russia), or Russian(Winkeys). So this is the case.

---

### Post by tapemaster on 2011-12-13
Hi r.osmanov

It is twisted, but trivial.
Just select "Russian" - the group from the list, don't expand "Russian" drop-down menu. Just press on it, and select "OK".

Thanks, ilikelinuxitisthebest. It did the trick for me with EN language as well.

--
Regards,
Alexei

---

### Post by ilikelinuxitisthebest on 2011-12-13
dont click the dropdown window. just click the header like this.

---

### Post by r.osmanov on 2011-12-13
Huh, very unusual :)

Thank you!

---

### Post by ilikelinuxitisthebest on 2011-12-20
your welcome. Did you appreciate my skills in the GIMP?;)

---

### Post by alex.rayu on 2011-12-20
Gimp is cool as always!
(I somehow have never had a problem with Russian layout for years now!)

---


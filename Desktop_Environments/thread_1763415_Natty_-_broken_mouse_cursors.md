---
title: "Natty - broken mouse cursors"
date: 2011-05-20
forum: Desktop Environments
---

### Post by hashcode on 2011-05-20
Hi, I want to use another cursor for Natty. I have Shere_Khan_X cursor (including cursor.theme), I copied extracted it to /usr/share/icons. Now when I run [B]
sudo update-alternatives --config x-cursor-theme 
[/B]I get this message: 
update-alternatives: error: /var/lib/dpkg/alternatives/x-cursor-theme corrupt: unexpected end of file while trying to read master file.

What shall I do now? Is there some way to let system recreate this file? And how to add new theme with cursor.theme file?

---

### Post by hashcode on 2011-05-22
bump

---

### Post by Frogs Hair on 2011-05-22
In quick search I found there has been problems with this theme to the point of a report to [http://gnome-look.org/](http://gnome-look.org/). I was unable to follow the link because the web site appears to be down at the moment . Remove the corrupt package and look into it further before proceeding.

---

### Post by hashcode on 2011-05-23
bump

---

### Post by HellBoyz77 on 2011-05-26
Same problem here, using alternatives work with other mouse pointers theme, but not with downloaded one.

I've added Chameleon cursors in usr/share/icons and added an entry to x-cursor-theme. I select it but it does not work after logging out/in.

---

### Post by benju on 2011-06-08
Hello, I came across this post while looking for the same thing myself, the problem as far as I can tell is that there is an extra line break ( or is it two, I can't remember ) at the end of the file ( /var/lib/dpkg/alternatives/x-cursor-theme ). Once you add this extra line(s) break(s) the file is correctly read and you're allowed to select the added cursor theme.

---

### Post by jmatties on 2011-06-09
Thank you! Adding 1 line-break fixed this error for me.

---


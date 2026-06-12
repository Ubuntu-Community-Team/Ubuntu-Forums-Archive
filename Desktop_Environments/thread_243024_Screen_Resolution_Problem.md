---
title: "Screen Resolution Problem"
date: 2006-08-24
forum: Desktop Environments
---

### Post by vangheem on 2006-08-24
Hi, I installed ubuntu on one of my computers and can't seem to get the resolution up to the max level.

Right now the resolution is at 1028x768.  The monitor supports 1280x1028. I would like it to reach it's max resolution.

So far I've tried running dpkg-reconfigure xserver-xorg.  Also, I've tried manually  editing the xorg.conf file and entering in the 1280x1028 values in the Monitor section.  Nothing has worked though.  When I try and change the resolution in with the gnome gui tool is never adds the 1280x1028 option.

Anyone have any ideas?


Thanks

---

### Post by jimbob on 2006-08-24
I think you mean 1280X1024, not 1028.  See if that makes a difference.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by vangheem on 2006-08-24
Nah, I just miss typed in the post..  It is right is the xorg.conf file.

---

### Post by jimbob on 2006-08-24
Does 1280X1024 show up as an available resolution in your xorg.conf file?

I would send you a copy of mine but I have installed the Xgl/Compiz mods so it probably wouldn't work for you.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by vangheem on 2006-08-24
1280x1024 is not in the xorg.conf file by default but I manually put it in thinking I could force it.  

Still hasn't worked...  Kindof weird.

---

### Post by jimbob on 2006-08-24
See if you can get someone who has an unmodified xorg.conf file and uses 1280X1024 resolution to send you theirs.

Hello out there ..............
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by vangheem on 2006-08-24
I have another computer with a working 1280x1024 xorg.conf file.  So I know the way it should look...

Was just hoping there was some other trick to getting it t work...

---


---
title: "trouble with wine"
date: 2006-02-27
forum: Gaming &amp; Leisure
---

### Post by illfilles on 2006-02-27
All right, I had wine working fine yesterday and today when i tried to load jagged alliance using the wine command.... nothing. I've tried to go into winecfg but I get the following message at the terminal:

ALSA lib seq_hw.C:455: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/ill/.kde/socket-illportal.
can't create mcp directory

What's going on here?

---

### Post by basse1989 on 2006-03-01
I get the same error when I click the "Audio" tab in winecfg...

EDIT: I did a
```
sudo modprobe snd-seq
```
and that got rid off the alsa error. winecfg still crashes when I click the "Audio" tab though, and I get
```

Creating link /home/basse/.kde/socket-kakburk.
can't create mcop directory

```
:(

---

### Post by basse1989 on 2006-03-01
I found the solution :D
```
mkdir -p ~/.kde/socket-<hostname>
```
worked for me :)

(google is your friend...;-)

---

### Post by illfilles on 2006-03-01
thanks man, that seemed to work brilliantly.

---


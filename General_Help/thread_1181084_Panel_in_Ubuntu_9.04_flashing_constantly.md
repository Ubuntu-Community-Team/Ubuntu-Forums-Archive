---
title: "Panel in Ubuntu 9.04 flashing constantly"
date: 2009-06-07
forum: General Help
---

### Post by wilkinlp01 on 2009-06-07
I was installing the mac4lin theme onto ubuntu 9.01 following a installation guide and i got to a stage where i had to restart,so i restarted and logged on and the top panel started to randomly flash and when you left click it the pop up menu pops up but instantly closes. i have turned the theme off by left clicking the desktop but it still doesnt do anything.:(
HELP!

---

### Post by pharohandy on 2009-08-15
same problem happened to me. is there anyone that knows how to correct it?

thanks in advance

---

### Post by ST3ALTHPSYCH0 on 2009-10-10
Alright, this is the 3rd and 4th instance I've seen of this with a quick search, all with no posted resolution, and all involving either the mac4lin theme or AWN. I'm now experiencing the same thing, and would really like to keep the mac 4 lin theme. Any answers?

---

### Post by alien47568 on 2009-11-22
hit ctrl+alt F2 and then log in and then type sudo apt-get install -f hit enter then type your sudo password (same as your normal password)then hit enter let it work and then hit ctrl+alt F7

---

### Post by ghostcoil on 2010-02-16
When i hit ctrl-alt F2 i ended up in a screen with a blinking cursor - if the same thing happens to you, you might try this in the command line
```

sudo debconf gnome-panel

```

As far as i can tell, it resets the panel to its default configuration... seems to have worked for me!

i found this on this website:
[http://www.saifur-rahman.com/2008/12/restoring-default-ubuntu-panel/](http://www.saifur-rahman.com/2008/12/restoring-default-ubuntu-panel/)

---


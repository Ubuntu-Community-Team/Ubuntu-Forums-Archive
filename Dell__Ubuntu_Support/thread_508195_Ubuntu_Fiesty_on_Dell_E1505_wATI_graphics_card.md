---
title: "Ubuntu Fiesty on Dell E1505 w/ATI graphics card"
date: 2007-07-23
forum: Dell  Ubuntu Support
---

### Post by michael37 on 2007-07-23
[SIZE="+2"]**Positives**[/SIZE]

Pretty much everything works with 64-bit Fiesty installed.

Among working features:
[LIST]
[*]Hibernate
[*]fglrx video driver
[**]OpenGL graphics is wicked fast
[*]Xgl nested
[*]CompizFusion WM
[**]wobbly windows and desktop cube
[*]Dell 1390 wireless card 
[**]using native driver, only at b speed
[*]Sound (no problems whatsoever)
[*]Thunderbird 2 with Lightning (in 32-bit mode)
[/LIST]
[SIZE="+2"]
**Negatives:**
[/SIZE]
The installation and configuration took me about 5 days.  Much longer than I expected, and much longer than most non-enthusiast users would care to spend :(

What doesn't work:
[LIST]
[*]Dual Monitors via VGA output
[/LIST]

---

### Post by strabes on 2007-07-24
I have used the aticonfig command in the past to set up my xorg.conf automatically. [Here's](http://gentoo-wiki.com/HOWTO_Dual_Monitors#With_the_proprietary_binary_driver) something from the gentoo wiki. You'll need to append "sudo" to both commands and you'll also need to change "/etc/init.d/xdm restart" to "sudo /etc/init.d/gdm restart" .

So, the two commands you should run are: ```
sudo aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right --iagp=off -v
sudo /etc/init.d/gdm restart
```

For more information see the "Screen-Related Options" section of ```
sudo aticonfig --help
```

[Here's](http://www.viajes-abaco.com/m400a/xorg_conf_fglrx_dual.htm) a (really complicated) example of a xorg.conf set up for dual monitors.

---

### Post by michael37 on 2007-07-24
Does that preserve the GL support so that Xgl will still work?   According to the attached xorg.conf, it should, but the whole example is so complicated it would be impossible to troubleshoot it.

---


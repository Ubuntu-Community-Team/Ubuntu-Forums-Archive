---
title: "Monitor Resolution Out of Range!"
date: 2009-01-04
forum: General Help
---

### Post by alexisfire on 2009-01-04
I got a beginning Ubuntu book for Christmas and installed 8.04LTS on my old computer.  I got it installed and working alright, but one of the first things the book showed me was to go to System>Administration>Hardware Drivers and Enable my graphics card device driver.  Then ubuntu told me to reboot my computer, which I did and my monitor comes back out of resolution now.  

From reading other forums I learned I could hit alt-ctrl-F1 and get to a prompt, but I haven't been able to figure anything out from the forums to fix my resolution.  I've been messing with the xorg.conf file, but I haven't gotten anything in there to work yet.
(and that file is possibly screwed up now from me tinkering with it...)

Please help!  I think I was liking linux so far, but now I'm stuck!

---

### Post by exploder on 2009-01-04
Did you get the "out of range" before you installed the graphics card drivers? What graphics card do you have?

---

### Post by linux_tech on 2009-01-04
In the terminal
Applications>Accessories>Terminal; type
```
xrandr
```
 what are the available resolutions that show up?

what video do you have?
what is the output of
```
lspci
```

what is your system type? make, model, memory

---

### Post by alexisfire on 2009-01-04
Thank you both for the responses!  I got up this morning and my computer won't boot anymore, it doesn't even post.  Its an old clunker and I'm just going to replace it, so... I guess this problem is solved.  

Thanks again for the help though!  Its really exciting to me that someone actually responded :)

---


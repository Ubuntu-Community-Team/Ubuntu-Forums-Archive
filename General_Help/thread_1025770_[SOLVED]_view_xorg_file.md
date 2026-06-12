---
title: "[SOLVED] view xorg file"
date: 2008-12-30
forum: General Help
---

### Post by jesse c on 2008-12-30
Whats the command to see what my xorg file reads.I have screwed around so much trying to fix nvidia x driver that i just did clean install from live cd and going to start over and at some point in the past i got forum help that had me add the word "nvidia" to my xconf(?) file under the 'driver' heading but ive done so many misc. attempts that i dont know where to look anymore

---

### Post by Elfy on 2008-12-30
xorg.conf is in /etc/X11

To view in a terminal 

```
cat /etc/X11/xorg.conf
```

To view in a GUI text editor on ubuntu
```
gedit /etc/X11/xorg.conf
```

To edit in a terminal
```
sudo nano /etc/X11/xorg.conf
```


To edit in GUI editor on ubuntu
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by jesse c on 2008-12-30
thanks forestpixie.Question- whats the difference between viewing and editing? the gui looked like the same page to me on both inputs

---

### Post by Elfy on 2008-12-30
Hi - gksudo was the difference :)

without root rights, given by sudo or gksudo in this case, you couldn't actually make any changes

The first example I gave could just have easily been

```
nano /etc/X11/xorg.conf
```

and you would have found the same thing.

---


---
title: "Ubuntu GUI doesn't load up?"
date: 2009-02-16
forum: General Help
---

### Post by aceplayer97 on 2009-02-16
Hi, I recently was using my computer and I was in a rush so I just used the power off button to shut it off. I turned it back on but when it loads only a terminal screen loads up. Does anyone know how I can get back to GUI?

---

### Post by sumguy231 on 2009-02-16
Go ahead and log in to the terminal and type
```
sudo /etc/init.d/gdm start
```
and see if you get any obvious errors.

Afterwards, you can try running
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions as best as you can, leave things blank if you're not sure. Honestly this may not still work in Hardy and above, it has been a while since I have had to do something like this.

---

### Post by aceplayer97 on 2009-02-16
I tried the second thing you said and it said that xserver-xorg is broken or not fully installed.:(

---

### Post by sumguy231 on 2009-02-16
Hmm, that would definitely be the problem. Try
```
sudo apt-get -f install
```

---

### Post by aceplayer97 on 2009-02-16
Well I did that but what do I do now? (I tried the dpkg reconfgure thing again but it said it was broken still)

---

### Post by sumguy231 on 2009-02-17
Do you know what any of the error output for apt-get -f install was?

---


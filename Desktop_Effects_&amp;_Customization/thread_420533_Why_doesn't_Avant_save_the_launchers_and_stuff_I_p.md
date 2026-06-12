---
title: "Why doesn't Avant save the launchers and stuff I put in it?"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-04-23
I finally got Avant installed and working yesterday, but when I turned on my computer today and started it, none of the launchers I had put in it yesterday were there. Is that normal? Will I have to repeatedly configure Avant every time I log on?

Also, how do I uninstall affinity?

---

### Post by user1397 on 2007-04-23
> **rainwalker said:**
> I finally got Avant installed and working yesterday, but when I turned on my computer today and started it, none of the launchers I had put in it yesterday were there. Is that normal? Will I have to repeatedly configure Avant every time I log on?

Also, how do I uninstall affinity?are you sure you're not talking about avast? because the only avant I know is the web browser for windows only.

also, how did you install affinity? methods of removal differ according to how you installed a package.

check this site out for a cool installation guide for ubuntu with lots of graphics.

---

### Post by rainwalker on 2007-04-23
Avant, it's a window navigator. See [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
That's what I did, but if I do the apt-get remove thing it talks about, Affinity still doesn't uninstall

---

### Post by user1397 on 2007-04-23
> **rainwalker said:**
> Avant, it's a window navigator. See [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
That's what I did, but if I do the apt-get remove thing it talks about, Affinity still doesn't uninstall
wait, you say you have edgy, so you must have installed from source.

go to the original source folder in a terminal
```
cd /path_to the directory/affinity-search
```

and then type ```
sudo make uninstall
```

---

### Post by rainwalker on 2007-04-23
That didn't work! 

Auugghhh!

---

### Post by user1397 on 2007-04-23
> **rainwalker said:**
> That didn't work! 

Auugghhh!well what was the exact error message/problem?

---

### Post by rainwalker on 2007-04-23
There wasn't an error or anything, it just didn't uninstall

I got it, though. I don't remember what I did, but I got it off.

---


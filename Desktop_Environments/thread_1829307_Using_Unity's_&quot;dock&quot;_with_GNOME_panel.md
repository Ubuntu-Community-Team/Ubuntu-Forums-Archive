---
title: "Using Unity's &quot;dock&quot; with GNOME panel?"
date: 2011-08-20
forum: Desktop Environments
---

### Post by travisHAZE on 2011-08-20
So Unity's version of the GNOME panel drives me nuts (and I HATE the menu Unity uses.) So I use GNOME, but I enjoy having a dock where I can see and manage my favorite applications and use it like a window manager at the same time. I've tried AWN, Cario, Docky, etc. but they either just don't function right (Docky, Cario), or in the case of AWN just wear on my nerves because it works so slow on my computer.

However, on the same computer Unity's "dock" doesn't function as badly as AWN does, in fact, if I tell it to close a program in the GUI, it does so quickly, cleanly, and if the application is misbehaving, it still handles it quickly. With AWN, if I tell it to close a program in GUI, and said program is misbehaving, it has a hissy fit, worse than my little sister did at 5 years old.

So, in my genius (:lolflag:) I've decided I would like to use Unity's "dock" with GNOME panel. Where would I begin? Is this possible?


Also, in the interest of not making another post (I hate watching my post count go up, sorry :p), in the terminal, if I wish to make multiple commands in one line, whats the functionality difference between using && and ;? (Aside from using less characters)
ie: ```
sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get upgrade
```vs.
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get upgrade
```

---

### Post by IanW on 2011-08-20
Have you tried [DockbarX](http://www.webupd8.org/2011/08/dockbarx-046-released-with-new-autohide.html)?

---

### Post by travisHAZE on 2011-08-20
It's being added to the same category as Cario and Docky, though it works better than they do.

Windows wont close from DockX, and if I close the window via (x), it keeps it open in the dock (but can't open the window cause it doesn't exist)

Aside from this kink, I love it :(

---

### Post by Larkspur on 2011-08-20
To try out the old panel with Unity, simply run: ```
gnome-panel
```

---

### Post by ssam on 2011-08-21
> **travisHAZE said:**
> 
Also, in the interest of not making another post (I hate watching my post count go up, sorry :p), in the terminal, if I wish to make multiple commands in one line, whats the functionality difference between using && and ;? (Aside from using less characters)
ie: ```
sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get upgrade
```vs.
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get upgrade
```


with '&&' then if one of the commands fails the following ones will not be run.

see [https://secure.wikimedia.org/wikipedia/en/wiki/Short-circuit_evaluation](https://secure.wikimedia.org/wikipedia/en/wiki/Short-circuit_evaluation) for more technical details.

---

### Post by travisHAZE on 2011-08-21
> **Larkspur said:**
> To try out the old panel with Unity, simply run: ```
gnome-panel
```
Doesn't work like you think it would, Unity's panel and gnome panel are  fighting over the same territory on my screen, regardless of settings,  both become nonfunctioning (buttons on either do not work; image wise,  they flicker back and forth between the two)

[quote=ssam]with '&&' then if one of the commands fails the following ones will not be run.

see [https://secure.wikimedia.org/wikiped...uit_evaluation]("https://secure.wikimedia.org/wikipedia/en/wiki/Short-circuit_evaluation") for more technical details.[/quote] Ahh excellent, thank you for that

---

### Post by Frogs Hair on 2011-08-21
If you really need or want another menu see the link .[http://www.ubuntuvibes.com/2011/06/how-to-get-classic-gnome-menu-in-unity.html](http://www.ubuntuvibes.com/2011/06/how-to-get-classic-gnome-menu-in-unity.html)

---

### Post by travisHAZE on 2011-08-22
> **Frogs Hair said:**
> If you really need or want another menu see the link .[http://www.ubuntuvibes.com/2011/06/how-to-get-classic-gnome-menu-in-unity.html](http://www.ubuntuvibes.com/2011/06/how-to-get-classic-gnome-menu-in-unity.html)
Thats all fine and dandy, if you can show me how to replace the unity launcher with that entirely, allow GNOME like customization of the unity panel, and still maintain the unity dock, then we're on the right track.

---

### Post by Frogs Hair on 2011-08-22
> **travisHAZE said:**
> Thats all fine and dandy, if you can show me how to replace the unity launcher with that entirely, allow GNOME like customization of the unity panel, and still maintain the unity dock, then we're on the right track.

That can't be done , the Gnome Panel and Unity Panel are completely different pieces of software so adding Gnome applets to won't work .

Adding a dock to Classic Gnome could be your best option. You could search for PPA that meets your needs . I could not find any or I would have posted a link . The Gnome Panel as we know it will be history on the next release unless "Mate" (a Gnome 2.32 fork) is ready for use on Ubuntu. That would most likely be a PPA.

---


---
title: "Gnome 3 in Ubuntu 11.10?"
date: 2011-10-15
forum: Desktop Environments
---

### Post by jtmcc on 2011-10-15
Hi. I have never liked Unity, i always used the Ubuntu classic theme. When i upgraded from 11.04 to 11.10, i realized that was a big mistake, cause I can't see how to switch back to classic. And now Unity is laggy. Is there any way i can get rid of unity and install Gnome 3?

---

### Post by beew on 2011-10-15
Unity sits on top of gnome 3.  You mean gnome shell, just type```
 sudo apt-get install gnome-shell
``` Next time when you log in you can choose "gnome" instead of "Ubuntu" by clicking the white button on the upper right corner of the login box. ("gnome" is for the gnome shell, to get something like "classic" you have to choose gnome fallback or something like that, can't remember the exact word, I don't use it)

---

### Post by luk1don on 2011-10-15
> **jtmcc said:**
> Hi. I have never liked Unity, i always used the Ubuntu classic theme. When i upgraded from 11.04 to 11.10, i realized that was a big mistake, cause I can't see how to switch back to classic. And now Unity is laggy. Is there any way i can get rid of unity and install Gnome 3?

Gnome 3 (gnome-shell) isn't much better than Unity... Are You mean Gnome 2?

---

### Post by beew on 2011-10-15
> **luk1don said:**
> Gnome 3 (gnome-shell) isn't much better than Unity... Are You mean Gnome 2?

There is no more gnome2, Gnome kills it and gnome3 is not the same as gnome shell. Gnome shell is a shell sitting on top of gnome3, so is Unity.

---

### Post by Kodeine on 2011-10-15
I too dislike Unity. When I went to 11.04 I immediately uninstalled it. Now on the move to 11.10 I gave it a bit more of a chance but in the end still my opinion hasn't differed. My computer is getting somewhat old now and Unity was a tad laggy for me to. Unity2D was a much better in that department.

But in the end I got Gnome 3. It's obviously different from what I was used to (Gnome classic) but I'm preferring it now over Unity. Probably going to take a while to get fully used to but in time I will. So give Gnome 3 ago and if all else failes classic is always there for you :)

---

### Post by Spr0k3t on 2011-10-15
If you are wanting "Classic", you will need to also install fallback.

```
sudo apt-get install gnome-session-fallback
```

Just remember, to make changes to any of the panels you have to press the ALT key.  Also, the System menu (for some bizarre reason) is now gone and most of the functionality is now hidden through the use of obscure commands or buried inside of some preferences dialog.

---

### Post by luk1don on 2011-10-15
> **Spr0k3t said:**
> If you are wanting "Classic", you will need to also install fallback.

```
sudo apt-get install gnome-session-fallback
```

Just remember, to make changes to any of the panels you have to press the ALT key.  Also, the System menu (for some bizarre reason) is now gone and most of the functionality is now hidden through the use of obscure commands or buried inside of some preferences dialog.

Have You got any tutorial how to configure this "classic" and its hidden functionalities?

---

### Post by luk1don on 2011-10-15
> **beew said:**
> There is no more gnome2, Gnome kills it and gnome3 is not the same as gnome shell. Gnome shell is a shell sitting on top of gnome3, so is Unity.

I know, I know:)

---

### Post by Spr0k3t on 2011-10-15
I don't have any tutorials, but this bit of information should help you find quite a bit.

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by jerrrys on 2011-10-15
there is also gnome.org

[http://library.gnome.org/users/](http://library.gnome.org/users/)

---

### Post by jtmcc on 2011-10-15
> **beew said:**
> Unity sits on top of gnome 3.  You mean gnome shell, just type```
 sudo apt-get install gnome-shell
``` Next time when you log in you can choose "gnome" instead of "Ubuntu" by clicking the white button on the upper right corner of the login box. ("gnome" is for the gnome shell, to get something like "classic" you have to choose gnome fallback or something like that, can't remember the exact word, I don't use it)
Is this somewhat like the pics on Gnome.org?

---


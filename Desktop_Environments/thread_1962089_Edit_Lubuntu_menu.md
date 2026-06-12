---
title: "Edit Lubuntu menu"
date: 2012-04-20
forum: Desktop Environments
---

### Post by geovino on 2012-04-20
How do you edit the Lubuntu menu? I've used alacarte for Mint but thats for the Gnome menu. What does Lubuntu (LXDE)use?

running Lubuntu 11.10 64bit

---

### Post by Perfect Storm on 2012-04-20
See this: [http://ubuntuforums.org/showpost.php?p=11420721&postcount=13](http://ubuntuforums.org/showpost.php?p=11420721&postcount=13)

---

### Post by geovino on 2012-04-20
> **Artificial Intelligence said:**
> See this: [http://ubuntuforums.org/showpost.php?p=11420721&postcount=13](http://ubuntuforums.org/showpost.php?p=11420721&postcount=13)

thanks, but this doesn't show me whats listed in the menus. And to install alacarte wants 50 programs to be installed along with it. Why? is it because its a gnome programs and if you run LXDE you needs all those programs just to run alacarte?

All I want to do is delete some of the games that I don't play. that should be simple. the old gnome would let you right click > edit menu and you could easily edit what you needed, now it seems to be complicated. 

there must be a better way, eh?

---

### Post by Perfect Storm on 2012-04-20
I don't there's a menu editor. Never heard of one. 

Can't you find the games you want to edit out of the menu in /usr/share/applications and rename with a _bak?

---

### Post by geovino on 2012-04-20
> **Artificial Intelligence said:**
> I don't there's a menu editor. Never heard of one. 

Can't you find the games you want to edit out of the menu in /usr/share/applications and rename with a _bak?

I'll try that out. thanks

Gnome 2: you would right click applications and you had an edit menu option. that is something was is very helpful and shouldn't have been removed.

---

### Post by Perfect Storm on 2012-04-20
LXDE is not Gnome2.
I think the reason why LXDE doesn't have a menu editor is to keep it light.

---

### Post by geovino on 2012-04-20
> **Artificial Intelligence said:**
> LXDE is not Gnome2.
I think the reason why LXDE doesn't have a menu editor is to keep it light.

That's OK. I solved the problem by going into synaptic and deleting ace-the-penguins. that deleted all the card games and the games heading on the menu. :)

---

### Post by jefsview on 2012-04-20
Have you tried this:

[http://lxmed.sourceforge.net/](http://lxmed.sourceforge.net/)

It's more text-based than Alacarte, but does with work Xfce's menu (I tried it when I was running Debian).

Of course it was created for LXDE and works far better than LXappearance or whatever that small menu-editor app is they use.

-- Jeff

---

### Post by Herpythebrony on 2012-04-20
[LIST]
[*]To install lxmed, first [download]("http://lxmed.sourceforge.net/download.html") a .tar.gz file.
[*]Unpack archive in your home or desktop folder.
[*]In terminal, enter the lxmed folder and type```
 chmod +x install.sh
``` to make install script executable.
[*]Install lxmed by typing ```
sudo ./install.sh
```
[*]Go to main menu -> Preferences -> Main Menu Editor
[/LIST]

---

### Post by Treeant34 on 2012-08-11
Awesome Cubed...

Thanks for throwing that one out there...

Been looking for a replacement for the missing Gnome Menu Editor for a while...

Why doesn't Lubuntu port Gnomes' Menu Editor over (very handy)?

I like the Gnome Desktop but LXDE is faster

Where can I put this comment so that the developers can see this?

Thx

---


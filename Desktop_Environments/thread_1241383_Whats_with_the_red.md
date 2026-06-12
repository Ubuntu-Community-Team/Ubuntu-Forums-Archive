---
title: "Whats with the red?"
date: 2009-08-15
forum: Desktop Environments
---

### Post by isee on 2009-08-15
OK  I hate red.  Just switched to Edubuntu, for reasons of my own, and think I can't run it if red is the theme.

Also, I thought I would be able to pick my desktop environment at login, between Jaunty or Ed.

Please help because I would like to keep Ed. on my laptop, but red is not an option, and Jaunty seems to be lost.

How can I pick Jaunty now?

---

### Post by hansdown on 2009-08-15
Hi isee.

Not sure what you mean. Hey, don't get me wrong, I hate red too,(maybe).

If you want to go back to jaunty, just boot from the jaunty disk, and re-install.

Erm... If you want to change your wallpaper, you can add anything you like.

---

### Post by isee on 2009-08-15
Thanks handsdown

My firefox bar is red, I do want edubuntu, but obviously need a new theme for it.  And I want to be able to get back to just Jaunty.  I would like to inform the Edubuntu people that red is not a good colour considering the intent of the software.

I thought I could choose at the login screen as to which desktop environmnet I wanted, but  it is not so on my laptop.

Thanks again!

---

### Post by kerry_s on 2009-08-15
> I thought I could choose at the login screen as to which desktop environmnet I wanted, but it is not so on my laptop.

jaunty is not a desktop.
you can select your other os install at the grub boot menu.

---

### Post by hansdown on 2009-08-15
I should say thankyou isee, as I didn't know that edubuntu did that.

For more themes, you can check here.

[http://www.google.ca/search?q=edubuntu+themes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=edubuntu+themes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Also, firefox has some too.

[http://www.google.ca/search?q=firefox+themes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=firefox+themes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by isee on 2009-08-15
OK Kerry_s   I see what you mean.  I was informed differently, but am learning at every post.  I'm a Noob.

If i were to have all Edubuntu and Kubuntu and UbuntuStudio as well as Jaunty installed, how can I navigate between the four?

---

### Post by XubuRoxMySox on 2009-08-16
You just have a red theme. Under Preferences>Appearance you can choose your theme from among several options.

The *theme* is what determines the color of window borders, fonts, and stuff like that. 

The *desktop environment* is whole 'nother animal. That's the desktop and the way it behaves. Ubuntu offers Gnome (Ubuntu), KDE (Kubuntu), Xfce (Xubuntu), and there are others you can download and install (Lubuntu is coming soon - watch for it!). They are quite different from each other and worth exploring just for fun!

If your computer has room on the hard drive, they're easy to install and remove 'til you settle on one you really like.

Try Kubuntu without a whole new install by opening a terminal and typing

```
sudo apt-get install kubuntu-desktop
``` Then log out. At the login screen, there's a li'l Options bar on the lower left. KDE desktop has now been added to the choices for your Session. Choose "just for this session," log in, and explore!

Don't like it? No problem. Remove it:

```
sudo apt-get purge kubuntu-desktop
```

Wanna explore Xubuntu?

```
sudo apt-get install xubuntu-desktop
``` Xfce now appears among your choices under the Options menu at Login. Not for you? Don't like it, don't care to use it again and don't want it taking up storage space? Remove it:

```
sudo apt-get purge xubuntu-desktop
```

My personal favorite? LXDE because it's super-simple and works on older hardware like mine:

```
sudo apt-get install lxde
```

Now LXDE appears in the list of Sessions to choose from. I love it, I'm a fanboy, so I make it my default. And then,

```
sudo apt-get-purge ubuntu-desktop
```

A desktop environment is not the same as a *theme*! You may choose any of the desktop environments and *still* have those awful red window borders and fonts no matter which d.e. you choose, so choose a different theme from your *Preferences>Appearance* menu.

-Robin

---

### Post by gjoellee on 2009-08-16
I think both Edubuntu and Ubuntu runs in GNOME. That means that if you install the Edubuntu-desktop you will just get all the edubuntu software in GNOME + all the programs that exist with Ubuntu.

---

### Post by isee on 2009-08-17
Thanks for the info on the purge command.

If I purge edubuntu from my laptop, will it revert back to the regular GNOME Ubuntu?

I do see the difference between KDE and Xfce and the others that don't use GNOME, so it seems to me that Ubuntu Studio and Edubuntu are more like desktop packages rather than different environments.

I have Studio on my desktop right now.  If I install Edubuntu on it also, I'm just wondering how the different desktop options would be presented in the Options menu on the login screen.  If it were Kubuntu I realize I would select KDE, but the difference between Studio and Edubuntu are not so clear to me.

Thanks again!

---


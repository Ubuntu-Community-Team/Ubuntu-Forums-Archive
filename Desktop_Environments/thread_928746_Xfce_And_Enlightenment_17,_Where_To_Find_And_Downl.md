---
title: "Xfce And Enlightenment 17, Where To Find And Download From?"
date: 2008-09-24
forum: Desktop Environments
---

### Post by Breandean on 2008-09-24
Where can I find the downloads for Xfce and Enlightenment 17? I should have the options at start up to choose between them right?

I'd like to use add/remove programs. But It did not clearly show, unless it is task manager, process manager.

---

### Post by Therion on 2008-09-24
> **Breandean said:**
> Where can I find the downloads for Xfce and Enlightenment 17? I should have the options at start up to choose between them right?
Ummmmm...  No.  Plain-vanilla Ubuntu comes with Gnome.  Period.  If you want Xfce or E. you have to download and install them yourself.  

> **Breandean said:**
> I'd like to use add/remove programs. But It did not clearly show, unless it is task manager, process manager.
The DE's you're looking for are not in the Repositories.  You'll need to google them and download them yourself.  

There are some distos, Ultimate for example (see my sig line), that come with extra DE's installed.  Ultimate has Gnome, KDE, Enlightenment and Xfce.

---

### Post by snowpine on 2008-09-24
```
sudo aptitude install xubuntu-desktop
```

That will give you a fully functional and themed Xubuntu Xfce desktop.  You can start it by choosing Xfce from the Options-->Sessions menu on the GDM login screen (or choose Gnome to get back to Ubuntu). 

If you don't like it, 'sudo aptitude remove xubuntu-desktop'.

You can also install a plain-jane Xfce by opening Synaptic and looking for xfce. I think the package you want is called 'xfce4-core' or something (memory a little fuzzy). You'll have to do a little bit of setup to get it looking nice, though.

Never used E17, sorry.

---

### Post by Piraja on 2008-09-24
I take it that you're using default Ubuntu Hardy (with the default Gnome desktop environment).

I'm not sure about e17, but you can download and install e16 by Synaptic Package Manager or command line: sudo apt-get install e16. And xfce4 too (sudo apt-get install xfce4). Another option for xfce is to download xubuntu-desktop (sudo apt-get install xubuntu-desktop), which is pretty much like Gnome DE but lighter. 

These are not in Add/Remove Programs. In order to use Synaptic, go to System > Administration > Synaptic Package Manager. The Search feature does not recognize Enlightenment, but all you need is type "e" and the first item will probably be e16.

Once you have installed xfce4 or e16, you should be able to choose them as startup options (choose Options or press F10 at the login window, and "Choose Session...").

EDIT: Oops, Therion and Snowpine were faster than me. But you do not have to do anything but "sudo apt-get install xfce4" or the same for "e16" (I haven't used Enlightenment) or for "xubuntu-desktop".

---

### Post by SeanHodges on 2008-09-24
Enlightenment 17 (bundled as "Elbuntu"):

[https://wiki.ubuntu.com/Elbuntu/](https://wiki.ubuntu.com/Elbuntu/)

Scroll down and follow the "Installing" instructions. You will need to change the references of "edgy" to "hardy" (assuming you are using Ubuntu 8.04).

Follow these and snowpine's instructions, and you should have both window managers available in your **Sessions** list at start-up.

---


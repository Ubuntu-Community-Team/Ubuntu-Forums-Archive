---
title: "Using sudo with fbpanel"
date: 2005-12-18
forum: General Help
---

### Post by simpat1zq on 2005-12-18
I did a clean base install of ubuntu, then I installed X, and gdm. I'm using fbpanel, and was wondering if it is possible to start apps that require sudo? 

When I add something to the menu, and use "sudo synaptic" for the command, it locks up the computer, and I have to hit the power button and reboot. It does the same thing for any app that I run using 'sudo'. 

I think it may have something to do with the password. Does anyone have any ideas?

thx

---

### Post by BathroomNinja on 2005-12-19
I looked up your other thread, so it looks like your runing Openbox.

What happens when you run the following from the **terminal**?

```
sudo apt-get install openbox-themes

```

I'm trying to see if this is a system wide problem or something that is only happening in fbpanel.  Also, you can get another terminal outside of X by using ALT-F2

Let me know what happens.

Also, did you follow this guide? [https://wiki.ubuntu.com/Openbox](https://wiki.ubuntu.com/Openbox)

---

### Post by simpat1zq on 2005-12-19
'sudo' works just fine when I'm at the command prompt, I was able to install the themes. I can even run synaptic from the command line. 

And it's not a problem just in fbpanel. When I run other panels, it does the same thing. 

thx

EDIT: Here's how I'm putting the entry into the fbpanel config, if that helps:

        item {
            name = Synaptic
            image = /usr/share/synaptic/pixmaps/synaptic_32x32.xpm
            action = sudo synaptic
        }

---

### Post by simpat1zq on 2005-12-19
Does anyone have any suggestions for a way to not have to power my comp off when it locks up like this? When I press the power button, it gracefully shuts down, so there has to be a way to get out of the lock.

thx.

---

### Post by ranf on 2005-12-20
[QUOTE=simpat1zq]
EDIT: Here's how I'm putting the entry into the fbpanel config, if that helps:

        item {
            name = Synaptic
            image = /usr/share/synaptic/pixmaps/synaptic_32x32.xpm
            action = sudo synaptic
        }[/QUOTE]
In Gnome I'd say use `gksudo synaptic'.
But I don't know if there is something similar available with Openbox.

---

### Post by simpat1zq on 2005-12-20
sweet. nice call on that gksudo thing. It worked. I'm not sure what it does different, but I'm able to put that in the menu, and it cranks right up.\

thx

---

### Post by duminas on 2005-12-20
gksudo is nothing more than a GTK (graphical) frontend to the command-line sudo--anything can use it.

Someone correct me if I'm wrong, but if you run "sudo program" from a menu like Openbox's or fbpanel's, it'll just sit, waiting for a password that never comes, and thus not run. gksudo allows you to enter one. 

**gksu -S** could do the same thing, but gksudo's a nice, handy alias. See *man gksudo* for more about it.

---

### Post by simpat1zq on 2005-12-20
ah, that makes sense.

---

### Post by BathroomNinja on 2005-12-20
very interesting.  I'm going to have to bookmark this answer.

---


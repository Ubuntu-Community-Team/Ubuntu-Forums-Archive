---
title: "MythTV, how do I change it to Ubuntu ?"
date: 2009-03-31
forum: General Help
---

### Post by shateredsoul on 2009-03-31
Hi,

I heard earlier that once you install Myth TV you can easily change it to the Ubuntu environment.... can someone explain this process to me?  I would really appreciate it.  I tried checking in the add/remove section for gnome.. but didn't find it.  That's what I was told to do.

---

### Post by skierkyles on 2009-04-01
Im not 100 percent sure, because I have never tried Mythbuntu, but I'd think it be...

In a terminal copy & paste.
```
sudo apt-get install ubuntu-desktop
```

Then at the login screen, click "Sessions" then Gnome.

---

### Post by shateredsoul on 2009-04-01
I think myth tv comes with xubuntu, is there anyway I can uninstall that so I don't have to click on "sessions" ?

---

### Post by skierkyles on 2009-04-01
Again I'm not 100% sure, but you would probably want to remove the **mythbuntu-desktop** package, (Which will probably wipe most of the mythTV applications), if you just want to remove XFCE (While leaving the mythTV apps) removing the **xfce4** package should do the trick.

You can use synaptic or a terminal do this.

But! I would definitely install **ubuntu-desktop** before you do any of this.

---

### Post by coffeecat on 2009-04-01
> **shateredsoul said:**
> I heard earlier that once you install Myth TV you can easily change it to the Ubuntu environment

> **shateredsoul said:**
> I think myth tv comes with xubuntu

I think we need to clarify a few things. First, Myth TV is an application which you can install in any version of Ubuntu, and in most other non-Ubuntu distros. Xubuntu is an Ubuntu variant which comes with the Xfce desktop. Mythbuntu is a special distro based on the Ubuntu codebase and which incorporates Myth TV, which is designed as a home media system, and which just happens to use the Xfce desktop. No doubt it shares some elements with Xubuntu, but it lacks a lot of the software (such as OpenOffice) that comes with Ubuntu or Xubuntu.

Lastly, you have tagged your thread with 'kubuntu', which is the KDE variant of Ubuntu. :? This is very confusing. You need to describe exactly what you are running.

Anyway, if this is mythbuntu, skierkyles is right in saying that installing the 'ubuntu-desktop' package would give you the standard Ubuntu gnome environment, but you'll still need to install the software you need.

> **shateredsoul said:**
> I think myth tv comes with xubuntu, is there anyway I can uninstall that so I don't have to click on "sessions" ?

All you have to do is, the first time you log in after installing 'ubuntu-desktop', to change to Gnome under sessions and choose 'keep as default desktop' where prompted. Then you'll always boot into Gnome without having to use the sessions chooser.

It would probably be best to leave Xfce alone, because Xfce uses a lot of Gnome libraries anyway, so you won't free up much disk space. And, besides, uninstalling Xfce might just take out some gnome stuff that you need.

---


---
title: "How to force Open Office to use the gnome/gtk theme?"
date: 2009-02-10
forum: Desktop Environments
---

### Post by deletarus on 2009-02-10
So I just uninstalled my .deb package OOo3 and added Open Office 3 to the repos using this tutorial [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
But now, my open office doesn't use my theme. It just uses the boring default theme. (I'm using Darkroom btw).

Does anyone know how to fix this?
I tried placing "OOO_FORCE_DESKTOP=gnome" in my ~/.bashrc file but it didn't seem to do anything. It's possible I put in the wrong spot, I have no idea...

Please, if anyone knows, HELP. It's sooooo ugly.

---

### Post by GeorgeMurango on 2009-02-24
I have the exact same problem. I couldn't get the theme to work, but under Tools -> Customize there are some color options that could at least make it stand out a bit less

---

### Post by kyouens on 2009-02-24
Under Tools->Options->Openoffice.org->Views you can also select an icon set.  After I installed Openoffice 3 using the tutorial linked above I had the option to select the Human icon set, and my Openoffice.org visual style looks pretty good with Gnome.  Take a look and see if you've got something else selected perhaps.

---

### Post by zurcherart on 2009-05-04
Did you figure this out in the meantime?  Was having the same problem until found this.

The openoffice.org-gnome package has to be installed for gnome integration.  It wasn't installed with the base when I reinstalled open office after the initial install.

Find that package in Synaptic, install the dependency it suggests as well (openoffice.org-gtk I think). 

I had to log out and log back in before open office used the new package.

Then it worked for me.

---

### Post by Buce on 2009-08-01
For people using something like fluxbox, who don't need the GNOME integration, you can also add

```
export OOO_FORCE_DESKTOP=gnome
```

to your ~/.fluxbox/startup in order to get the gtk theme to be applied.

---

### Post by Dullstar on 2009-08-01
That's odd.  It works fine for me.  What version are you using, along with what variant?

Ubuntu, Kubuntu, Xubuntu, etc.
Any of these can have GNOME installed as an extra.

---

### Post by LoloftheRings on 2009-11-11
If anyone is wondering how to do this for gnome:

System -> preferences -> startup applications/session

press the add button and enter the following:

Name: OOo theme
Command: export OOO_FORCE_DESKTOP=gnome
Description: Sets the OOo theme to the gnome theme

Log out, log in and see the results!

I haven't tested this, but I think it will work.

---


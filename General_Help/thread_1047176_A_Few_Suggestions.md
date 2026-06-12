---
title: "A Few Suggestions"
date: 2009-01-22
forum: General Help
---

### Post by butsam on 2009-01-22
To make Ubuntu more user-friendly, I would like to suggest the following:

1) Make firestarter a default application to install on desktops. A lot of my friends didn't even know they had a firewall and how to mess with it when they were new to Ubuntu, one less thing for them to have to set up.

2) Make it so when browsing the folders, it is possible to right-click on an executable and instruct it to "Run as Administrator", "Run as Root", or whatever you want to call it, as a menu option. A lot of programs, when downloaded, must be installed as root (or are more desirable to install as root). Of course, one should be prompted for their password before continuing, but this would really help with convenience for people who abhor the command line.

3) Make the gnome color chooser a default application to install (if someone chooses the gnome desktop environment). C'mon, do you really want users to have to install a different package to change the font color because they have a white desktop instead of a darker color? (I personally don't mind, but I can see this turning some people off to Ubuntu).

Just my few cents worth; nothing major here, Ubuntu is wonderful! I just think these three things would make Ubuntu even more usable than it already is to the lay person.

Sam

---

### Post by ajcham on 2009-01-22
> **butsam said:**
> 2) Make it so when browsing the folders, it is possible to right-click on an executable and instruct it to "Run as Administrator", "Run as Root", or whatever you want to call it, as a menu option. A lot of programs, when downloaded, must be installed as root (or are more desirable to install as root). Of course, one should be prompted for their password before continuing, but this would really help with convenience for people who abhor the command line.


Although it is not installed by default, **nautilus-gksu** gives you this capability.  I agree that it is very useful, although I suspect there is good cause for not having it by default.

---

### Post by hyper_ch on 2009-01-22
> **butsam said:**
> 1) Make firestarter a default application to install on desktops. A lot of my friends didn't even know they had a firewall and how to mess with it when they were new to Ubuntu, one less thing for them to have to set up.
Firestarter is outdated and not recommended anymore by Ubuntu. Furthermore there is hardy a need to alter the default configuration of iptables.

> **butsam said:**
> 2) Make it so when browsing the folders, it is possible to right-click on an executable and instruct it to "Run as Administrator", "Run as Root", or whatever you want to call it, as a menu option.
That depends on what you browser the folders with...


> **butsam said:**
> A lot of programs, when downloaded, must be installed as root (or are more desirable to install as root). Of course, one should be prompted for their password before continuing, but this would really help with convenience for people who abhor the command line.
You should restrain yourself from download "programs" in the windows way. Use the package mangager (Add/Remove, Synaptic, Adept, apt-get, aptitude, ...).

> **butsam said:**
> 3) Make the gnome color chooser a default application to install (if someone chooses the gnome desktop environment). C'mon, do you really want users to have to install a different package to change the font color because they have a white desktop instead of a darker color? (I personally don't mind, but I can see this turning some people off to Ubuntu).
I don't think most people ever change their desktop beyond setting a background image.

---

### Post by ajcham on 2009-01-22
> **hyper_ch said:**
> You should restrain yourself from download "programs" in the windows way. Use the package mangager (Add/Remove, Synaptic, Adept, apt-get, aptitude, ...).

Good point - I should add that I think the greater benefit of using nautilus-gksu is in performing file operations and editing files, rather than running programs.  This is probably an example of good cause for not having it installed by default - we shouldn't really encourage bad practice in running/installing applications.

---

### Post by butsam on 2009-01-31
> **hyper_ch said:**
> I don't think most people ever change their desktop beyond setting a background image.

But what if they choose a background image that has a lot of white? Then it is quite difficult to read any of the text on your desktop.

Sam

---

### Post by hyper_ch on 2009-01-31
> **butsam said:**
> But what if they choose a background image that has a lot of white? Then it is quite difficult to read any of the text on your desktop.

so?

---


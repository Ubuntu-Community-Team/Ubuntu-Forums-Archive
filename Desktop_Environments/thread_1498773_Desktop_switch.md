---
title: "Desktop switch"
date: 2010-06-01
forum: Desktop Environments
---

### Post by ahso4271 on 2010-06-01
Hi
i want to keep Gnome as my main desktop but then and when use the KDE interactive earth and all the rest of KDE. How can I switch easily between Gnome and KDE and what do i need to install?
Thanks

---

### Post by blchinezu on 2010-06-01
> **ahso4271 said:**
> Hi
i want to keep Gnome as my main desktop but then and when use the KDE interactive earth and all the rest of KDE. How can I switch easily between Gnome and KDE and what do i need to install?
Thanks

this should do it:
```
sudo apt-get install kubuntu-desktop kubuntu-restricted-extras
```
then at login you choose the session gnome or kde as you like.. so if you're in gnome just logout and login again using kde

personally i don't use kde interface but i install it and use it's applications from gnome

---

### Post by ahso4271 on 2010-06-01
Thanks, but would that break my current autologin in Gnome?

---

### Post by gator2802 on 2010-06-01
> **ahso4271 said:**
> Thanks, but would that break my current autologin in Gnome?
 
 
you can use the standard Gnome desktop and KDE applications.  The downside is to use the KDE packages you will have a boat load of dependancies that need to load (about 40) so it will work but it is not the most efficient option

---

### Post by SoFl W on 2010-06-01
***If** I remember* correctly when you install the kde option it asks you if you want gnome or kde as default.  Choose gnome.  Can someone else verify?

---

### Post by blchinezu on 2010-06-01
> **ahso4271 said:**
> Thanks, but would that break my current autologin in Gnome?
as *gator2802* and i already said... you install that and than just use the kde applications from gnome.. you don't necessarily have to login with a kde session... and no it shouldn't break anything.. i never breaked ubuntu by installing kde. just install the packages **and choose *gdm* during installation** as it will ask which login manager you want to use: *gdm* or *kdm*.. 

and after installation remove the kde boot splash screen so that it doesn't get automaticaly switched (or if you like the blue splash just let it be)
so if you want to remove it:
```
sudo apt-get remove plymouth-theme-kubuntu-logo
```this is how it's done in lucid (at least the easiest way i know of)... older versions don't use plymouth and so you can change it with startup-manager if i remember correctly

---

### Post by ahso4271 on 2010-06-02
> **gator2802 said:**
> you can use the standard Gnome desktop and KDE applications.  The downside is to use the KDE packages you will have a boat load of dependancies that need to load (about 40) so it will work but it is not the most efficient option


But only when selecting KDE? Not for my default Gnome (nice OSX alike) desktop? That would be to annoying...

sudo apt-get remove plymouth-theme-kubuntu-logo
This would log me into gnome per default? So I could logout and gdm->kde
That would be what I'm looking for.

By the way could I have complete different desktops sets to switch alike: OSX, default gnome, red, blue whatever. (complete windows, bar, fonts etc)

Thanks

---

### Post by blchinezu on 2010-06-02
> **ahso4271 said:**
> But only when selecting KDE? Not for my default Gnome (nice OSX alike) desktop? That would be to annoying...
i don't get it.. what don't you understand...
it's simple:
- you log in with gnome session, you can use the kde applications from within gnome
- you log in with kde session, you can use the gnome applications from within kde
the only thing is that the apps that are runned and don't belong to the session type consume a bit more ressources... let's say you use gnome and run amarok (like i always do). well, amarok will use more resources from within gnome than from within kde as it will have to start some kde processes to make amarok work. that happens for all the apps.
but still you can just logout and choose the kde session and login and you use a kde session and amarok will consume less resources... it's not such a big performance difference for a decent computer these days..
i repeat, this was just an example so that you (i hope) will better understand what i said untill now.

> **ahso4271 said:**
> 
sudo apt-get remove plymouth-theme-kubuntu-logo
This would log me into gnome per default? So I could logout and gdm->kde
That would be what I'm looking for.
That command will remove the boot splash screen installed by the kde packages previously installed, so that when your computer starts you won't see the blue kubuntu loading screen instead of the normal ubuntu

> **ahso4271 said:**
> 
By the way could I have complete different desktops sets to switch alike: OSX, default gnome, red, blue whatever. (complete windows, bar, fonts etc)
This would be made with multiple user accounts not only with different sessions

---

### Post by ahso4271 on 2010-06-03
Thanks I'll try that as I don't want to login at every reboot.

[http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html](http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html)

---


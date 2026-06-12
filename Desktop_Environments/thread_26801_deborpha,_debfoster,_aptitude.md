---
title: "deborpha, debfoster, aptitude"
date: 2005-04-14
forum: Desktop Environments
---

### Post by jorgepeixoto on 2005-04-14
Whenever I try do do anything in aptitude (e.g. sudo aptitude upgrade) I get something like this. 

The following packages are unused and will be REMOVED:
  gdk-imlib1 gnome-bin gnome-libs-data imlib-base libart2 libgdk-pixbuf2 
  libglade-gnome0 libglade0 libgnome32 libgnomeprint-bin libgnomeprint-data 
  libgnomeprint15 libgnomesupport0 libgnomeui32 libgnorba27 libgnorbagtk0 
  liborbit0 libpng10-0 libungif4g libxml1 

Is it really safe to remove those packages? If they are unused, why do they come installled in ubuntu?
Also, is it safe to perform a apt-get remove --purge `deborphan`? And how about debfoster? If I answer the debfoster questions correctly, is it safe to let it delete the unused packages?

thanks
[]'s

---

### Post by ubuntu_demon on 2005-04-14
[QUOTE=jorgepeixoto]Whenever I try do do anything in aptitude (e.g. sudo aptitude upgrade) I get something like this. 

The following packages are unused and will be REMOVED:
  gdk-imlib1 gnome-bin gnome-libs-data imlib-base libart2 libgdk-pixbuf2 
  libglade-gnome0 libglade0 libgnome32 libgnomeprint-bin libgnomeprint-data 
  libgnomeprint15 libgnomesupport0 libgnomeui32 libgnorba27 libgnorbagtk0 
  liborbit0 libpng10-0 libungif4g libxml1 

Is it really safe to remove those packages? If they are unused, why do they come installled in ubuntu?
Also, is it safe to perform a apt-get remove --purge `deborphan`? And how about debfoster? If I answer the debfoster questions correctly, is it safe to let it delete the unused packages?

thanks
[]'s[/QUOTE]
 If there are no applications removed that you like it's not a big deal. 

Never remove packages from ubuntu-base (you would know because it would want to remove the meta package ubuntu-base also)

It's nice (but not necessary) to conform to ubuntu-desktop or kubuntu-desktop if you are using either gnome or kde. Do this by :

sudo apt-get install ubuntu-desktop
or
sudo apt-get install kubuntu-desktop

for more about debfoster look here :
[http://www.ubuntuforums.org/showthread.php?t=24403](http://www.ubuntuforums.org/showthread.php?t=24403)

regarding deborphan sure you can remove it. But you can also use it to find residual configurationfiles (synaptic can use deborphan too)

---

### Post by jorgepeixoto on 2005-04-14
Maybe you haven't understood me, I don't want to remove deborphan, I want to remove the packages that deborphan lists as orphaned. That's what the command sudo apt-get remove --purge `deborphan` does, as opposed to the command sudo apt-get remove --purge "deborphan". 
So let me ask clearly: is it safe to remove orphaned libs? 
Is it safe to use debfoster as long as I answer its questions correctly? ( I had already read the article you mentioned , but I'm stiil worried about how safe debfoster is) 

thanks

[]'s

---

### Post by ubuntu_demon on 2005-04-14
[QUOTE=jorgepeixoto]Maybe you haven't understood me, I don't want to remove deborphan, I want to remove the packages that deborphan lists as orphaned. That's what the command sudo apt-get remove --purge `deborphan` does, as opposed to the command sudo apt-get remove --purge "deborphan". 
So let me ask clearly: is it safe to remove orphaned libs? 
Is it safe to use debfoster as long as I answer its questions correctly? ( I had already read the article you mentioned , but I'm stiil worried about how safe debfoster is) 

thanks

[]'s[/QUOTE]
 It's safe if you understand what you are doing.

If you keep at least ubuntu-base,grub(if you have grub installed), the kernel you use (for example linux-386 or linux-686) you can't do real harm. If you also keep ubuntu-desktop (or kubuntu-desktop) you won't remove any packages that are installed by default.
I only use deborphan to remove leftover configuration files. debfoster does a better/easier job in getting your orphans removed.

---

### Post by jorgepeixoto on 2005-04-16
The "understand what you are doing" is the hard part. :)
But from what you said, I think that I can use debfoster (not deborphan,as you mentioned), and, as long as I don´t let him remove ubuntu-desktop,ubuntu-base,  the kernel and grub, nothing bad will happen. I think this answers my question.

thanks
[]'s

---


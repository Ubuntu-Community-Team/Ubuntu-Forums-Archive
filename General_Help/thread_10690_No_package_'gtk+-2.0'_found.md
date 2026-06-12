---
title: "No package 'gtk+-2.0' found"
date: 2005-01-10
forum: General Help
---

### Post by tibz on 2005-01-10
Hi,

I'm trying to install a new theme engine from gnome-look.org (clearlooks 0.1). At one point in the process I get the following error in terminal:

checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
configure: error: GTK+-2.0 is required to compile redhat-artwork


Please help a new Ununtu addict!

---

### Post by randy on 2005-01-10
You'll need to install gtk2's development package to get the pc file (and header files)

---

### Post by tibz on 2005-01-10
Thanks Randy,

That's through synaptic I guess? 
I did try to select in synaptic what looked to me like the developpement packages for gtk. Synaptic gave me some stop error about interdependencies not being kosher with some library or other.
Can you advise what I have to do exacltly?

Much appreciated.

---

### Post by dude2425 on 2005-01-10
I'm also having a bunch of synaptic dependancy problems. Is there a hidden repo for ubuntu on the net somewhere that I'm missing? I can't even get  xmms.

I tryed downloading the source for GTK+ (2.6.1) with all the other stuff I need for it, compiled glib, and then went to compile the others and it tells me something about "PKG_CONFIG_PATH" or something like that, but I have no idea what to do from there. I need GTK+ 2 in order to install a lot of nice apps I saw in synaptic, and even gtk-smooth-engine-0.6 to have one of my favorite themes to work correctly.

---

### Post by luotinen on 2007-05-02
I had this problem when I was compiling Kipina 0.2.2.

It was helpful to mel to find out that 
gtk+-2.0 = libgtk2.0-dev

:)

---

### Post by hasimir44 on 2007-12-18
thank you! this is also needed for compiling gtkpod..

---

### Post by itismike on 2008-05-31
> **luotinen said:**
> It was helpful to mel to find out that gtk+-2.0 = libgtk2.0-dev

:)
Thank you luotinen!

---


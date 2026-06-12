---
title: "ColorZilla not working in FireFox 2.0.0.3"
date: 2007-05-22
forum: Desktop Environments
---

### Post by loboes41 on 2007-05-22
I'm running Feisty Fawn. I tried to install ColorZilla 1.0  on FireFox 2.0.0.3, but when i click the dropper tool, i get a message saying that it is incompatible with my platform.

Any ideas?

---

### Post by thayerw on 2007-05-24
I don't believe there is a Linux compatible version of Colorzilla yet.  If you are running Kubuntu, there is a great color picker kicker applet available in the [FONT="Courier New"]kicker-applets[/FONT] package.  GNOME doesn't have a color picker applet available from the repos, but you can easily compile the Color Applet found here:

[http://www.undiscoverable.com/2007/02/11/color-picker-applet/](http://www.undiscoverable.com/2007/02/11/color-picker-applet/)

It's the best (and only) GTK color applet I've found for GNOME.

---

### Post by explemonk on 2007-05-25
There is a Linux version of ColorZilla, and it does work on, for example, openSUSE 10.2.   However, from the the [ColorZilla web site]("http://www.iosart.com/firefox/colorzilla/"):

> ColorZilla on Ubuntu/FC5 Linux

    * Get the official Firefox from Mozilla.com
    * Install libstdc++5: "sudo apt-get install libstdc++5" 

---

### Post by vintagedaddyo on 2007-05-25
1.) Uninstall Colorzilla in Firefox if you have it already there.
     
   2.) Download the officially compiled binary tarball fo Firefox from: [http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)

   3.) Close Firefox

   4.) Unpack the tarball to a temp place, e.g.
```

      tar xzvf firefox-2.0.0.3.tar.gz -C /tmp/

```

   5.) In the terminal window type the following command(and input your password afterwards):

```

      sudo cp /tmp/firefox/libxpcom* /usr/lib/firefox/

```

   6.) Run firefox and install Colorzilla again.

---

### Post by loboes41 on 2007-05-26
That did it.  Thanks!

---

### Post by ray007 on 2007-05-29
Does that mean the official ubuntu firefox packages have a problem?

Otherwise the copying of libxpcom-files shouldn't make a difference, right?

---

### Post by Elijah on 2007-05-29
sudo apt-get install gcolor2 

or agave

---

### Post by ray007 on 2007-05-30
Yes, there are alternative ways to find the color.
And no, that's not an excuse for ubuntu's firefox-build to not work with colorzilla, since the official mozilla-builds apparently do work.

---

### Post by MilosBGood on 2008-01-22
> **vintagedaddyo said:**
> 1.) Uninstall Colorzilla in Firefox if you have it already there.
     
   2.) Download the officially compiled binary tarball fo Firefox from: [http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)

   3.) Close Firefox

   4.) Unpack the tarball to a temp place, e.g.
```

      tar xzvf firefox-2.0.0.3.tar.gz -C /tmp/

```

   5.) In the terminal window type the following command(and input your password afterwards):

```

      sudo cp /tmp/firefox/libxpcom* /usr/lib/firefox/

```

   6.) Run firefox and install Colorzilla again.

Thanks!!! :KS

---


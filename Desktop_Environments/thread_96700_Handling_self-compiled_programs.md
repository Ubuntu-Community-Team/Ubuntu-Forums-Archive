---
title: "Handling self-compiled programs"
date: 2005-11-29
forum: Desktop Environments
---

### Post by blueturtl on 2005-11-29
I've learnt that since some programs can be out of date in the repositories, or they might not be available at all it is often the easiest solution to install an application by compiling it from it's source.

There's just one thing though, where on earth do compiled programs go? :p 

Can they be easily removed? In case there's a new version out I'd like to remove an older program and compile and install the new one in it's place.

Someone mentioned the command *checkinstall* which supposedly converts the unpackaged files into debs but in my system the command just returns at "command not found" in the terminal. :confused: 

Of course that wouldn't help with programs I have already installed by compiling.
Yes I am well aware of **make uninstall** but that sometimes gives errors and then I'm not sure wether there might be remnants of the once installed app left behind. :(

---

### Post by 23meg on 2005-11-29
The best way to handle them is to install them with checkinstall. Install checkinstall first, it's in the repositories. Afterwards, every time you compile something, instead of ```
sudo make install
``` use ```
sudo checkinstall
```. This way the compiled app will be entered into the apt database and you'll be able to treat it as any other package.

---

### Post by blueturtl on 2005-11-29
Can I use the checkinstall program for apps I've already installed?

By this I mean going into the source directory, running checkinstall and installing the made packages "on top" of already installed compiled programs?

---

### Post by Emerzen on 2005-11-29
blueturtl, I don't know if you've gotten this yet or not, but "checkinstall" has to be installed (via synaptic) before it can be used.  I also recommend installing the package "build-essential" if you haven't already yet.

As 23meg pointed out, once you've installed checkinstall itself, those are the commands you use.  It will create a .deb package and install it...once it's finished, open Synaptic and search for the program you just installed-> highlight and look under properties for "installed files" for locations.  If you want to remove it, use Synaptic.  Programs that you've previously installed-> I would recompile and reinstall as above, this should overwrite any of the original files, then uninstall them w/ Synaptic or keep them if you choose.

---

### Post by blueturtl on 2005-11-29
Thank you guys. Getting checkinstall from the repository was the solution.

I will be sure to use it whenever I compile software by myself!

---

### Post by jasontan6 on 2007-06-25
I tried to use checkinstall with Pidgin 2.0.2 earlier on, the deb package was built but failed to install. Is there any other way to remove a self-compiled program which did not pass checkinstall?

---


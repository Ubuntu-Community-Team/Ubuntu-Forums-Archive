---
title: "Installing applications from source."
date: 2005-02-12
forum: Desktop Environments
---

### Post by sard on 2005-02-12
Is there any way to install from source like the Porthole system in Gentoo so you get the right version for your hardware?

The reason I switched from Vidalinux was because it took hours to install software, but there are some occasions where I would want to install from source.  Like Mplayer for example.

---

### Post by tim1 on 2005-02-12
I don't know about the porthole system but usually you install software from source like this:

tar xzf program-0.1.tar
cd program-0.1/
./configure (sometimes ./autogen.sh)
make
sudo make install

greets, tim

---

### Post by rosslaird on 2005-02-12
You can install from source in apt (using build-dep, for example, see [here](http://www.sdn.or.id/share/Debian-Doc/manuals/apt-howto/ch-sourcehandling.en.html)), or you can use apt-build (see [here](http://www.debtoo.org/apt-build.html)). There are now several tools for doing this, to get that extra 15% that compiling from source offers. From the apt-build howto:

> Debian is a binary-based distribution with an extremely stable performance record.&#8237; &#8236;All packages are distributed in an i386&#8237; &#8236;format&#8237; – &#8236;what this means,&#8237; &#8236;in a nutshell,&#8237; &#8236;is no optimizations have taken place.&#8237; &#8236;All packages are compiled with the&#8237; “&#8236;lowest common denominator&#8237;” &#8236;architecture as the target.&#8237; &#8236;As such,&#8237; &#8236;if you are running a newer system with mmx, sse or 3d-now instructions, you are not getting the most out of your processor.

This newest version of apt-build seeks to change this.&#8237; &#8236;With support for compile-time optimizations and architecture specific targets,&#8237; &#8236;apt-build can make most of your packages run much faster.&#8237; &#8236;Be warned,&#8237; &#8236;with optimizations you will add size to your executables.&#8237; &#8236;For most users,&#8237; &#8236;this is a welcome trade-off to have increased performance and decreased execution time. 

But I remember seeing a post somewhere about the challenge presented by this strategy: if you compile from source, I beleive, the application cannot be updated properly by the apt system (there was a discussion somewhere comparing apt and portage).

And, of course, you can use:

./configure
make
su
make install

(Doing it this way does not give you the "right version for your hardware" unless you specify the correct compilation flags. This is what portage does so well. It helps if you know what you are doing for the above.)

But such packages are definitely outside of the apt updating system.

Ross

---

### Post by sard on 2005-02-12
I don’t suppose there’s a nice GUI front-end for apt-build anywhere?

---

### Post by rosslaird on 2005-02-12
Nope, not yet. Maybe in a while... (it's very new).

---


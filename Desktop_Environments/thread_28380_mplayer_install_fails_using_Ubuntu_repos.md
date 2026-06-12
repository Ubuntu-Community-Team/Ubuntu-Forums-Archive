---
title: "mplayer install fails using Ubuntu repos"
date: 2005-04-19
forum: Desktop Environments
---

### Post by sb73542 on 2005-04-19
Hello, I followed the instructions on ubuntuguide for mplayer, but there is a mess of failed dependencies.  Here is my sources.list:

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

And here's the result after updating and trying to install mplayer-386:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libdirectfb-0.9-20 but it is not installable
               Depends: libggi2 (>= 1:2.0.5) but it is not installable
               Depends: libmad0 (>= 0.15.1b) but it is not installable
               Depends: libungif4g (>= 4.1.3) but it is not installable
               Depends: xmms but it is not installable
E: Broken packages


I went into synaptic and did a "Fix broken packages" but this made no difference.  There are currently 0 broken packages, according to Synaptic.  Any ideas?  Thanks for the help!

---

### Post by Jesus Franco on 2005-04-20
I get the same thing!

:(

---

### Post by drspin on 2005-04-20
Perhaps go into synaptic preferneces (can't remember how to get there ATM and I'm not on my box) choose the advanced tab (as it was called in Warty) and select the "prefer versions from..." and chose "Hoary" -- p[erhaps that will help... I did this earlier while installing mplayer and received similar error messages and it worked... I'll post more specific instructions when I get home if you need them.

Cole

---

### Post by jiyuu0 on 2005-04-20
try again
[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer) 

i've updated + tested it yesterday... should be ok

---

### Post by sb73542 on 2005-04-20
I just updated and installed per the instructions, but I get the same result.  No idea what's going on.  Thanks for the help!  Any more suggestions?

---

### Post by dejos on 2005-04-26
I have the same problem, although I have fewer error messages if I comment out non hoary. buy I still get this message

 mplayer-386: Depends: libsvga1 but it is not installable or
                        svgalib-dummyg1 but it is not installable

so I dont know what to do. all I know is that I'm completely confused why totem-gstreamer is packaged with the distro as the only thing it's good at is pissing me off.

---

### Post by mtron on 2005-04-27
Did it 30 sec. ago following the ubuntuguide (without backports) and everything was ok.

Anyway. In hoary and Backports is Version 1.0pre6. The latest Version is 1.0pre7, so compile and install it for yourself. Mplayer is very easy to install and remove from source and the preformance (at least for my machine) from the compiled mplayer is much better than the deb version

---


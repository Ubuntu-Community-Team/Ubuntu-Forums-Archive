---
title: "Control systems package for GNU Octave"
date: 2010-01-27
forum: Education &amp; Science
---

### Post by johnathanmcclure on 2010-01-27
I was using GNU Octave today to follow some MATLAB examples given in my university course on control systems.

One of the examples was to input a basic transfer function.  When I tried to type in:

```
num1=[10]; den1=[1 2 5]; sys1=tf(num1, den1)
```An error was returned:
```
error: 'tf' undefined near line # column #
```I was frustrated because the online manual for Octave seems to clearly describe the "tf" function.  Why was the tf function missing?

After searching for a while, [I found this mailing list posting]("https://www-old.cae.wisc.edu/pipermail/help-octave/2009-October/016389.html"), where I discovered the stock installation of Octave in the Ubuntu repositories does not include control system functions.

To get these functions, you have to download and install them from [Octave-Forge]("http://octave.sourceforge.net/").  There are a number of add-on packages available that are not in the default install.

In this case, I wanted the Controls packge, which is at [http://octave.sourceforge.net/control/index.html](http://octave.sourceforge.net/control/index.html).

Once I had the .tar.gz I went to the command line and did
```
$ sudo octave
octave:1> pkg install /foo/bar/downloadedpackage.tar.gz

```The results using Octave as a direct replacement for MATLAB aren't perfect, but it's going much better with the Control package!

---

### Post by not_a_phd on 2010-01-27
Did you try to get them through the Ubuntu repositories first?

I think that the octave-control package is what you were looking for.

---

### Post by johnathanmcclure on 2010-02-17
> **not_a_phd said:**
> Did you try to get them through the Ubuntu repositories first?

I think that the octave-control package is what you were looking for.

I think I tried to apt-get octave-control.  It didn't work on my 8.04 rig or my upgraded 9.10 64bit rig.

You seem to be right, it is in the repositories for 9.10, so I don't know what went on with my PC.  And it's also a package for 9.04, so those are theoretically covered too.   But it's not a package under 8.04 or 8.10, hmmm.

At least the workaround I describe seems to work on my rigs running 8.04 and 9.10.  I guess before trying it it'd be a good idea to attempt

```
sudo apt-get install octave-control
```

---

### Post by NibblerSA on 2012-11-05
Thanks for the help!

---


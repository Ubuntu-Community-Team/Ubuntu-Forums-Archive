---
title: "Installing Kwin themes!?"
date: 2007-04-10
forum: Desktop Environments
---

### Post by bg1256 on 2007-04-10
In running Kubuntu Edgy,

And I have not been able to successfully install any kwin themes.  

It seems that I am able to compile them successfully, but they do not appear in kcontrol.

The process I go through is:

1. download a tarball from kde-look.org
2. extract the tarball to home directory.
3. cd into extracted directory
4. ./configure, make, sudo make install

After doing that, what do I do?  There is obviously something I am missing, but I do not know what...

---

### Post by ComplexNumber on 2007-04-10
i think when you cmpile tem, they may have to be placed in the /usr directory. in other words, when you did "./configure", you may have had to write "./configure --prefix=/usr" instead. 

i haven't got kde installed at the moment, so i can't check for definite. then again, i can't remember for definite that i had to do that.


whcih theme are you referring to? or are you referring to all of the ones that you've installed?

---

### Post by bg1256 on 2007-04-10
As to the specific theme, it is the human window decoration for kwin.


I have not tried ./configure --prefix=/usr

I will try that when I get back to the computer in question.

Thank you!

---

### Post by bg1256 on 2007-04-11
It works!

Thanks for the tip!

---


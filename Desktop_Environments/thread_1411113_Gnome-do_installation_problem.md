---
title: "Gnome-do installation problem"
date: 2010-02-19
forum: Desktop Environments
---

### Post by kentpend on 2010-02-19
I have been trying to install gnome-do on 9.10 alternate (x64), but the installation breaks on missing dependencies, specifically libgconf2.24-cil and libgnome-vfs2.24-cil.  The exact output is
```

suscott@scott-lappy:~$ sudo apt-get install gnome-do
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-do: Depends: libgconf2.24-cil (>= 2.24.0) but it is not installable
            Depends: libgnome-vfs2.24-cil (>= 2.24.0) but it is not installable
E: Broken packages


```

I tried locating and installing those packages, but I couldn't figure out what sources that version would be in.  I downloaded and installed both manually, and still get the same error.  The interesting part is that there are no sources enabled on my desktop that aren't on my laptop, and I had no issues installing it on my desktop.  Even more interesting is that neither of those two dependencies are installed on my desktop.

Any ideas on how to fix this?  I'm stumped.

---

### Post by nothingspecial on 2010-02-19
I`m sure you already have, but the first thing to try in this situation is a good ol` ```
sudo apt-get install -f
```

---

### Post by kentpend on 2010-02-20
Yup, I had tried that already.  Same error.

---

### Post by kentpend on 2010-02-22
Problem solved.  The version in the ubuntu repositories does not have the same dependencies as the version in the gnome-do repositories, and did not have an issue being installed.

That being said, I'm still curious why the version in the gnome-do repository would not install when the packages it required were installed.

---


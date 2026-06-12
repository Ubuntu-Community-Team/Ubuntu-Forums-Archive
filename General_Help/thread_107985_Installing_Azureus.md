---
title: "Installing Azureus"
date: 2005-12-24
forum: General Help
---

### Post by winter_mute on 2005-12-24
Alright, so I got the backports set up so I could install azureus.  I've done this before on someone else's computer, and have the exact same list (or so I think) of repo's.  But when I go to install azureus via:

sudo apt-get install azureus

it says that I can't install it because the dependencies of

 Depends: sun-j2sdk1.5  but it is not installable or
 	java2-runtime  but it is not installable

And I can't seem to figure out how to fix this.  Any help?

Edit:  Nevermind, I found the setup tutorial.

---

### Post by GTvulse on 2005-12-24
```

sudo apt-get install fakeroot java-package

```

Go to java.com and grab the .bin Linux installer

```

fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

```

Follow the prompts, answer yes to all questions...

```

sudp dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb

```

And then...

```

sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.

```

That'll do it.

---

### Post by htinn on 2005-12-24
I could never get fakeroot method to work right. The way I installed java is here:

[http://ubuntuforums.org/showthread.php?t=76754](http://ubuntuforums.org/showthread.php?t=76754)

The filenames may be a little different, so just change the name where applicable.

---


---
title: "How do I install like 40 programs without using the commandline"
date: 2006-01-15
forum: General Help
---

### Post by donmayor on 2006-01-15
My Ubuntu linux system is not connected to the internet so I can't use apt get and I downloaded some programs to install. On installing through the commandline interface, it could not find some dependencies. I had to download all the dependencies and it added up to over 20 and they are on my flashdrive with long names. If I take them home to install on my system, I am wondering how i would do sudo dpkg -i libxi6_1.3.0-2_i386.deb and more for 20 programs. That would take me hours. Is there a shortcut where i can doubleclick a program like in windows XP and it installs? or I can use the application manager to search for these files to install?

---

### Post by GeneralZod on 2006-01-15
This is one of the "weak" points of Linux, in some ways; essentially, the answer is in general "No"; you can't find self-contained .deb files for the majority of applications you'd want to install.

If you already have all the .deb files (apps and dependencies) in one directory, you can just navigate to that directory in the terminal and do

```

sudo dpkg --i *.deb

```

About 100x quicker than using the GUI :) If this doesn't work, try copying all of the .deb files to /var/cache/apt/archives and try again.

It's certainly technically possible for someone to knock up a script that asks for a bunch of app names and spits out a bash script that will download all of the dependencies which you can bung on a thumbdrive along with cygwin and take to any internet-enabled Windows or Linux box, but I don't know if anyone has done anything like this.

---

### Post by bonzodog on 2006-01-15
hrm, not 100% sure about this, but:
open nautilus as root; [alt+F2, gksudo nautilus]. Then try double clicking the packages and see if that works.  I believe it IS possible to chain together the packages in a single command. try just doing the 'sudo dpkg -i' command then listing the packages one after the other with a space in between.

---

### Post by veloct on 2006-01-15
[http://www.ubuntuforums.org/showthread.php?t=91427&highlight=dpkg+nautilus+script](http://www.ubuntuforums.org/showthread.php?t=91427&highlight=dpkg+nautilus+script)

There's a nautilus script for doing dpkg, may not do multiple but it will make it a little easier.

---

### Post by donmayor on 2006-01-15
I don't really know how to install nautilius scripts cos i am a new linux user, i am finding out about that, but I got an easy answer on [http://www.ubuntuforums.org/showthread.php?t=114215](http://www.ubuntuforums.org/showthread.php?t=114215)....thanx

---

### Post by jnoreiko on 2006-01-15
[QUOTE=GeneralZod]
It's certainly technically possible for someone to knock up a script that asks for a bunch of app names and spits out a bash script that will download all of the dependencies which you can bung on a thumbdrive along with cygwin and take to any internet-enabled Windows or Linux box, but I don't know if anyone has done anything like this.[/QUOTE]

What would be cooler would be a script that asks for the names, then spits out a file, which you then take to an internet-enabled machine, and simply upload it to a repository server in a plain web form, and the server replies with a zip of all you need :)

---

### Post by slux on 2006-01-15
Check out [http://debian.pffa.de/ger/howto/apt-zip.html](http://debian.pffa.de/ger/howto/apt-zip.html)

Since Ubuntu is based on Debian, you get all the debian coolness ;)
apt-get install apt-zip.

---

### Post by learning curve on 2006-01-15
wget [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb)
sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb

Open Terminal and type the above command.  When it is done installing go to Applications/System Tools/Automatix.  Automatix will install many programs that are useful to you.
Learning Curve:cool:

---


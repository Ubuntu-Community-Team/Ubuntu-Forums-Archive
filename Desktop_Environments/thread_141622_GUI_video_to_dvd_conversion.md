---
title: "GUI video to dvd conversion?"
date: 2006-03-08
forum: Desktop Environments
---

### Post by DarkDancer on 2006-03-08
Is there a gui software package for Ubuntu that will convert video formats (.avi .mpg, etc) to a DVD format? I downloaded and installed a command line program that seemed very promising, but I can't get it to do anything (Ubuntu keeps telling me it's not there.) ANy help would be welcome... ;)

---

### Post by taurus on 2006-03-08
You can try DeVeDe, [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html).

---

### Post by DarkDancer on 2006-03-08
Thanks taking a look... ;)

---

### Post by DarkDancer on 2006-03-08
Looks cool, the instructions are sort of vague on how to instal it though.......

---

### Post by taurus on 2006-03-08
[QUOTE=DarkDancer]Looks cool, the instructions are sort of vague on how to instal it though.......[/QUOTE]
Okay, I guess I just have to type out the whole thing to show you how to install it then!!!  :rolleyes: 

```

tar xvjf devede13.tar.bz2
cd devede
sudo ./install.sh

```

---

### Post by DarkDancer on 2006-03-08
Thanks! ;) Seems to work, videos a little strange, I will have to tweak it I guess.

---

### Post by taurus on 2006-03-08
You can also try tovid, [http://tovid.berlios.de/en/index.html](http://tovid.berlios.de/en/index.html).  

Add these three lines to the bottom of your /etc/apt/sources.list as

```

sudo gedit /etc/apt/sources.list
(Now, cut and paste these three lines...)

# tovid:  Divx -> DVD...
deb http://packages.kirya.net unstable main contrib non-free
deb-src http://packages.kirya.net unstable main contrib non-free

(Save it and exit... Then run)
sudo apt-get update
sudo apt-get install tovid

```

---

### Post by DarkDancer on 2006-03-08
Getting an error when I try to install, it reads....


sudo install tovid
install: too few arguments
Try `install --help' for more information.

---

### Post by taurus on 2006-03-08
[QUOTE=DarkDancer]Getting an error when I try to install, it reads....


sudo install tovid
install: too few arguments
Try `install --help' for more information.[/QUOTE]
Oops.  That is a typo.  It should have read
```

sudo apt-get install tovid

```

---

### Post by DarkDancer on 2006-03-09
Hmmm, getting closer..... ;)

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
  tovid: Depends: python (< 2.4) but 2.4.2-0ubuntu2 is to be installed
E: Broken packages

---

### Post by syklitengutt on 2006-03-10
W: GPG error: [http://packages.kirya.net](http://packages.kirya.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EEFB43B2FBABB737

---

### Post by jtpratt on 2006-03-14
had the same problem.  Read my Ubuntu video conversion guide here:
[http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=810050](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=810050)

You'll find info for converting your files to DVD format using ffmpeg or mencoder, in addition to info about Tovid and dvdauthor.

Also - I had the same python dependency problem as you on tovid installation.  The 2 commands to run in terminal to fix it are on my web page as well.

---


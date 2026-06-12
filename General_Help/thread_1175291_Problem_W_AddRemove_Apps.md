---
title: "Problem W/ Add/Remove Apps"
date: 2009-06-01
forum: General Help
---

### Post by stat30fbliss on 2009-06-01
So, for no apparent reason my Add/Remove Programs has not been installing the applications.  Every time I try and install a program, no matter what it is, the Install fails.  I have attached a screen shot of the warning sign I get w/ details.  Its the same every time.

---

### Post by SunnyRabbiera on 2009-06-01
try this command:
sudo dpkg configure -a
In a terminal, seems like you need to refresh your sources though.
This is why using add/remove alone isnt such a good idea.

---

### Post by stat30fbliss on 2009-06-01
Hmm.  I ran your command and I will attach a pic of the response.

---

### Post by CatKiller on 2009-06-01
> **stat30fbliss said:**
> Hmm.  I ran your command and I will attach a pic of the response.

I think it should be ```
sudo dpkg --configure -a
```

---

### Post by stat30fbliss on 2009-06-02
hmmmmm, I ran that command as well and received a similar response.  I also ran update manager and received the same error message as the Add/Remove prompt.

---

### Post by plucky on 2009-06-02
Can you open Synaptic Package Manager? If so select **Edit > Fix Broken Packages** and then see if Add/Remove now works.

Or from a terminal ```
sudo apt-get install -f
```

Good Luck

---

### Post by stat30fbliss on 2009-06-09
> **plucky said:**
> Can you open Synaptic Package Manager? If so select **Edit > Fix Broken Packages** and then see if Add/Remove now works.

Or from a terminal ```
sudo apt-get install -f
```

Good Luck

Dang, I tried that as well, and still no improvement, and still getting the same error.

Im stuck!

---

### Post by plucky on 2009-06-09
You probably need to either edit the file and remove the broken package or use the "available.old" file instead.

```
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.broken
sudo mv /var/lib/dpkg/available.old /var/lib/dpkg/available
```

What this does is moves the file "available",which has the problem,into a file called "available.broken" and the moves a file called "available.old" and makes that the "available" file.

If that doesn't work,then you will have to reverse what you did above,and then edit the file and search for line number that is giving the problem and delete the package that is causing the error.

Use ```
gksudo gedit /var/lib/dpkg/available
``` and enable line numbering in gedit and search for the line number given in the error message and delete the package information.Save the file and try a "sudo apt-get update".


Good Luck

---

### Post by zvacet on 2009-06-09
@ **stat30fbliss**

Go to the system>admin>software sources and check all (except source) under Ubuntu software tab and first two under update tab.Reload.Now you should have all repos added.Try to install again.

---

### Post by stat30fbliss on 2009-06-11
> **zvacet said:**
> @ **stat30fbliss**

Go to the system>admin>software sources and check all (except source) under Ubuntu software tab and first two under update tab.Reload.Now you should have all repos added.Try to install again.

All of the boxes you specified were already checked

---

### Post by colau on 2009-06-11
> **SunnyRabbiera said:**
> try this command:
sudo dpkg configure -a
In a terminal, seems like you need to refresh your sources though.
This is why using add/remove alone isnt such a good idea.
```

sudo dpkg --configure -a

```

---

### Post by stat30fbliss on 2009-06-11
> **plucky said:**
> You probably need to either edit the file and remove the broken package or use the "available.old" file instead.

```
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.broken
sudo mv /var/lib/dpkg/available.old /var/lib/dpkg/available
```

What this does is moves the file "available",which has the problem,into a file called "available.broken" and the moves a file called "available.old" and makes that the "available" file.

If that doesn't work,then you will have to reverse what you did above,and then edit the file and search for line number that is giving the problem and delete the package that is causing the error.

Use ```
gksudo gedit /var/lib/dpkg/available
``` and enable line numbering in gedit and search for the line number given in the error message and delete the package information.Save the file and try a "sudo apt-get update".


Good Luck

I dont understand what you mean by 'the file or package' just because I was not aware of any one file I have used/downloaded that negated my PC's ability to update.  I was just searching through add/remove and noticed no matter what program I decided to add would download, but not install, with the error I posted above.  At a later date I followed my update prompt and received the same error message after the download but failed install. But it just kinda came out of nowhere.

With that said, your instructions specify a certain file or broken package I would need to focus on, and I wouldn't know which file or package to focus on...Somewhat of a newbie.  Ive troubleshooted Ubuntu somewhat, but this is a whole new problem I've never had.  And very frustrating!  Not one suggestion has worked yet... I enjoy exploring the options of linux programs available to me and finding good alternatives to my windows programs and with this bug holding me back I find Im using windows more and more...Help!

---

### Post by plucky on 2009-06-12
> All of the boxes you specified were already checked 
Un-check them and select close.It will ask you to reload.Do so.Then do the same again but this time select the boxes and again reload.

Then try to install something.

If that doesn't work (continue) 


> With that said, your instructions specify a certain file or broken package I would need to focus on, and I wouldn't know which file or package to focus on..

Have you tried to edit the "available" file using the gksudo gedit command.You will find it is just a text file of a list of packages that you have installed on your system.
In gedit you can turn on line numbering under the "preferences" tag.Do so.
Then search for the line number given in your error message.It will take you to the package that is broken.Delete the section that refers to the package,save the file and then try to install an application.


This is an example of what a package section looks like ```
Package: libexempi3
Priority: optional
Section: libs
Installed-Size: 748
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: exempi
Version: 2.0.2-2
Depends: libc6 (>= 2.4), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.2.1)
Size: 290566
Description: library to parse XMP metadata (Library)
 Exempi is a library to parse XMP metadata as defined by the
 specification.
 .
 XMP (Extensible Metadata Platform) facilitates embedding metadata in files
 using a subset of RDF. Most notably XMP supports embedding metadata in PDF
 and many image formats, though it is designed to support nearly any file type.
Original-Maintainer: Asheesh Laroia <asheesh@asheesh.org>
Homepage: http://libopenraw.freedesktop.org/wiki/Exempi
```



Good Luck

---


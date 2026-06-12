---
title: "Lexmark Z55 driver..."
date: 2006-02-14
forum: Desktop Environments
---

### Post by Postman on 2006-02-14
I'm trying to install the driver for my Lexmark Z55 driver and untarred it and tried doing the 'sh' function in the 'lexmarkz55-2.0-1.gz.sh' file and it only brought up this: 'Verifying archive integrity...OK
Uncompressing Lexmark Z55 Printer Drivertrap: usage: trap [-lp] [arg signal_spec ...]'
Is there a step I am missing here cuz the readme says that's all I need to do but I can't find the PPD driver for it.

Matt T.

---

### Post by bluevoodoo1 on 2006-02-14
Have you seen this post?
[http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark](http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark)

It says that it will work with the z55 in an [older]("http://ubuntuforums.org/showthread.php?t=49714") post.

---

### Post by Postman on 2006-02-14
[QUOTE=bluevoodoo1]Have you seen this post?
[http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark](http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark)

It says that it will work with the z55 in an [older]("http://ubuntuforums.org/showthread.php?t=49714") post.[/QUOTE]

I tried using the Alien command with and without the SUDO command and it says 
that the Alien command not found.  Is this Alien installable or did i miss it in the Ubuntu install?

---

### Post by bluevoodoo1 on 2006-02-14
[QUOTE=Postman]I tried using the Alien command with and without the SUDO command and it says 
that the Alien command not found.  Is this Alien installable or did i miss it in the Ubuntu install?[/QUOTE]

yup!

```

sudo apt-get install alien

```

---

### Post by Postman on 2006-02-14
OK, thanks for the alien install.  Now I am to the part of the 'sudo gunzip' where I unzip the PPD but I can't seem to find the Lexmark Z55 PPD.GZ  Is it labelled differently or does it not show the extension of the file?

---

### Post by bluevoodoo1 on 2006-02-14
the z55 might be labelled differently. Some in the above thread said they got their z55 working with that tutorial but some file names were different...

---

### Post by Postman on 2006-02-14
Would it be under a .ppd file or is it binary?  There are two files that are binary that look like they might contain the drivers: 'lexmarkz55' and 'z55driver'  How can I be able to access these files?  Thanks for your help, btw.

---

### Post by bluevoodoo1 on 2006-02-14
It should be under a .ppd file. I have a lexmark z605 so I didn't have to change much and my ppd file looks exactly like the how-to... Lexmark-Z600-lxz600cj-cups.ppd 

it will probably end in a .gz like Lexmark-Z600-lxz600cj-cups.ppd.gz  since with that line of code they are to be gunzipped. Are either of the two you mentioned have that suffix? have you already gunzipped them? If do do the last line of code, the go to in GNOME: System->Administration->Printing to select your z55.

---

### Post by Postman on 2006-02-14
Well my problem is that I am going to the folders of where the 'sudo tar -x -v -z -f lexmarkz55-2.0.tgz -C /' defaulted to and there is no kind of .gz nor .ppd.gz files anywhere.  Just two files that are executables labelled 'lexmarkz55' and 'z55drivers'  I have followed the instructions to the letter, and I know it was made for a different printer, I just don't know where the files are if at they were loaded at all.

---

### Post by bluevoodoo1 on 2006-02-14
Hmm... does anyone else have any ideas?

---

### Post by Postman on 2006-02-16
I apparantly downloaded the wrong driver (sorta) named "CJLZ55LE.tar.gz"  Instead I downloaded "CJLZ55LE-CUPS-1.0-1.TAR.GZ" and followed the Lexmark Z600 installation instruction provided by bluevoodoo's link and it worked to a 't.'  Just for anyone reading this, download the 'CUPS' version of the driver and not the one without 'CUPS' in the file name.  The driver without 'CUPS' only provides the straightforward driver and not the ppd's needed to work in Ubuntu.

---

### Post by bluevoodoo1 on 2006-02-16
I'm glad you got it to work!

---


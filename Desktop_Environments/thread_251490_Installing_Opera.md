---
title: "Installing Opera"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Unflux on 2006-09-05
Hey,

Downloaded the gar.tz Opera installation file but have no idea how to install the files correctly as I`m just starting out with Linux.

Can someone tell me what I am required to do please ?

Thanks.

---

### Post by kostkon on 2006-09-05
Hi,

I think you don't need to use a tar.gz file. Do it like this:

Edit your sources.list file like this. From command line do:

```
gksudo gedit /etc/apt/sources.list
```

and add the following line to the file and then save it:

```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

then do:

```
sudo apt-get update
```

and then just go to synaptic and search for Opera. Select the app from the list and click to install it. Like this if there is a new version it will be automatically updated.

Or just install it from command line like this:

```
sudo apt-get install opera
```

I hope I helped you

---

### Post by The Seeker on 2006-09-05
On the [Opera download page](http://www.opera.com/download/?platform=linux), select Ubuntu from the drop down menu.

Once you've downloaded the file, right-click on it and choose Open with "GDebi Package Installer". This will install version 9.01 as downloading using apt-get will get you version 9.0.

---

### Post by cotcot on 2006-09-05
Or install version 8.54. I tried a lot and finally quit with 9.0.

---

### Post by daiwai on 2006-09-05
Just extract the archive, change to the directory where opera was extracted and  run opera from there.

```

tar -gxvf opera-9.0-2006MMDD.6-shared-qt.i386-en.tar.gz
cd opera-9.0-2006MMDD.6-shared-qt.i386-en
./opera

```

---

### Post by Unflux on 2006-09-05
> **The Seeker said:**
> On the [Opera download page](http://www.opera.com/download/?platform=linux), select Ubuntu from the drop down menu.

Once you've downloaded the file, right-click on it and choose Open with "GDebi Package Installer". This will install version 9.01 as downloading using apt-get will get you version 9.0.

This is what I had been doing previously and I get receiving an error.  The same thing happened again when I tried redownloading.  Yet after receiving the error message, I closed the dialog box and retried and shazaam, it worked !

Odd that ...  ;) 

Thanks for all the help though.

---


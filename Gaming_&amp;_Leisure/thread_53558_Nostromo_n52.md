---
title: "Nostromo n52"
date: 2005-08-01
forum: Gaming &amp; Leisure
---

### Post by synap on 2005-08-01
When I have a little more time I will make this thread into a How To.  From a fresh install of ubuntu these are the steps I had to follow to compile and install the Nostromo n52 drivers.

Note that I still havent figure out how to set the permissions on the files listed in the 3rd post.


```

sudo apt-get install cvs
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/nostromodriver login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/nostromodriver co -P nostromo_driver
cd nostromo_driver
sudo apt-get install automake1.6
sudo apt-get install texinfo
sudo apt-get install libfltk1.1-dev
sudo apt-get install libgtk+2.0-directfb-udeb-dev
sudo apt-get install libxml2-dev
sudo apt-get install fluid
sudo apt-get install libxtst-dev
sudo ./configure
sudo make
sudo make install

```

---

### Post by synap on 2005-08-01
The reasoning behind trying to get this to register as a gamepad was that the n50 already dose, which allowed for qjoypad to register and configure it easily enough.

With some research I found that a driver has been in the works:
[http://sourceforge.net/projects/nostromodriver](http://sourceforge.net/projects/nostromodriver)

Downloading the CSV
```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/nostromodriver login
``` 
press enter at password prompt
```
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/nostromodriver co -P nostromo_driver
``` 

Change to the nostromo_driver directory.
```
cd nostromo_driver
```

Some things to note:
Apparently this can **only** be compiled with automake1.6
```
sudo apt-get automake1.6
```

Make sure that only automake1.6 is in use (I think 1.4 is default install because I don't recall installing it myself).
```
sudo apt-get remove automake1.4
```

You also need makeinfo which apparently is part of the texinfo package.
```
sudo apt-get install texinfo
```

```
sudo ./configure
```
```
sudo make 
```
```
sudo make install 
```

Hopefully everything comes back without any error messages.

The daemon will be ran as the normal user so you need to make sure you have write access to /dev/input/event*.
```
sudo chmod 666 /dev/input/event*
``` -dose this cause security concerns?
Run the daemon
```
nostromo_daemon
```
and the configure
```
nostromo_config
```

That should be it.  

There were some additional packages I needed to install when I ran the ./configure.  I didn't write them down but it was easy enough to synaptic them.  

Hope this helps anyone else looking to getting their nostromo n52 working (drivers also support n50)

---

### Post by synap on 2005-08-01
Is there a way to change the permissions permanently on these files?
/dev/input/event*

After each reboot it reset back to 600.

---


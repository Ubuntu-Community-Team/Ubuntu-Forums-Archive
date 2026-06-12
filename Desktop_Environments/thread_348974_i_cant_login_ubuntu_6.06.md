---
title: "i cant login ubuntu 6.06"
date: 2007-01-29
forum: Desktop Environments
---

### Post by nemanaldin on 2007-01-29
hi
i cant login to ubuntu 6.06 and show these errors plz help me
[http://i18.tinypic.com/2py9kjp.jpg](http://i18.tinypic.com/2py9kjp.jpg)

[http://i16.tinypic.com/2hd0dok.jpg](http://i16.tinypic.com/2hd0dok.jpg)

[http://i12.tinypic.com/2ij5579.jpg](http://i12.tinypic.com/2ij5579.jpg)

---

### Post by taurus on 2007-01-29
What does ~/.xsession-errors say anyway?  At the GUI login screen, press <Ctrl><Alt>F2 and log into the console with your name and password.  Then, examine .xsession-errors to see what does it say.

```
more .xsession-errors
```
(Hit the space bar for the next 24 lines.)

---

### Post by nemanaldin on 2007-01-29
hi
thanks for help
i write that command and it say this plz help me
[http://i7.tinypic.com/47v6t13.jpg](http://i7.tinypic.com/47v6t13.jpg)

---

### Post by taurus on 2007-01-29
While you are still log in into a console, run

```
sudo aptitude update
sudo aptitude install alsa-base alsa-utils
```
Now, press <Alt>F7 to get back to the GUI login screen and see if you can log into Gnome again.

---

### Post by nemanaldin on 2007-01-29
hi
thanks taurus but these commands not solve my problem
i tired plz help me

---

### Post by taurus on 2007-01-29
Or maybe

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by nemanaldin on 2007-01-30
hi
i tested that commands but my problem still not solve 
ask of this command sudo aptitude
[http://i5.tinypic.com/2h2jgif.jpg](http://i5.tinypic.com/2h2jgif.jpg)
and this sudo aptitude install ubuntu-desktop
[http://i7.tinypic.com/29da7t5.jpg](http://i7.tinypic.com/29da7t5.jpg)
thanks

---

### Post by nemanaldin on 2007-02-01
any one can help?????

---

### Post by JohnPhys on 2007-02-01
As far as I know, the "Could not get lock" error occurs when there is a process of apt/aptitudue/update-manager already running, or you're not typing in the root password correctly.  Does it give these errors after a reboot? If so, maybe try

```
ps -aux | grep apt
```

to see if there are any aptitude or apt-get processes running that you need to kill, with 

```
sudo kill ####
```

where "####" is the Process IDentification (PID) number, which should be the second column from the left in the output from the first line of code I suggested.

Once you have killed off any errant apt processes, you should be able to run the apt-get commands successfully.

Did you get the "could not get lock" errors from apt while trying to install the alsa packages?

Hope this helps!

---


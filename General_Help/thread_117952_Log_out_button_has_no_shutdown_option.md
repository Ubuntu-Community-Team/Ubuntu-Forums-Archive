---
title: "Log out button has no shutdown option"
date: 2006-01-15
forum: General Help
---

### Post by schermozzel on 2006-01-15
I recently changed from gnome to kde and now I don't have a shutdown option im my log off button in the k menu. All I get is "End current session"

I am running kdm so it should be able to do it. Why isn't there a shutdown option?

---

### Post by nrwilk on 2006-01-15
from the command-line type this:
```

sudo kcontrol

```

then expand the "System Administration" section.

Select "Login Manager".

The fourth tab over should be labeled "Shutdown".  Click it.

Under the "Allow Shutdown" section, there is a drop-down menu labeled "local."  Click it and select "everybody".

Now, all users should be able to shutdown the computer locally.  If it doesn't work after you do this, then I'm not sure what else you can do, but I'm sure a more experienced person can think of something.


If nothing else, you can select the "end current session" option and then once at the login screen you can choose "shutdown" from the "actions" menu.

---

### Post by schermozzel on 2006-01-16
Ok I've done that but there's still no shutdown option

---

### Post by purdy hate machine on 2006-01-17
You need to make kdm your default desktop environment. To do this run the following commands in Konsole or Terminal.

to download and install the kdm package for kde:

 ```
sudo apt-get install kdm
```

to configure and set kde as your default desktop environment:

```
sudo dpkg-reconfigure kdm
```

---

### Post by schermozzel on 2006-01-17
I have kdm and it's already the default login manager so that's not the problem either

---

### Post by purdy hate machine on 2006-01-18
Do you get any error messages when you run:

```
sudo dpkg-reconfigure kdm
```

---

### Post by famouscoco on 2007-11-27
i have the same problem but in gnome.what should i do??

---

### Post by enchance on 2007-11-28
Shutting down your computer using the terminal is quite simple. I actually use it everyday instead of clicking shutdown.

Shuts down your computer and turns off the power
```
sudo shutdown -P now
```
Restarts the system
```
sudo shutdown -r now
```
You can replace "now" with a duration such as this example where the computer will power off after 5 mins
```
sudo shutdown -P +5
```
or this where it shuts off once it hits a certain time
```
sudo shutdown -P 13:30
```

---

### Post by tesseract_rider on 2008-04-08
I have the same issues. 
have run dpkg-reconfigure kdm
have checked that in system settings poweroff should be allowed.
i can happily use the command line, but what's the GUI for?

any ideas much appreciated.

---

### Post by photopath on 2008-04-19
I think it's an NVIDEA driver bug - mine was fine until I added support for my graphics card from the Nvidea site (to sort out a refresh rate problem)

I've not seen it since!

I just use the command line shutdown - but it's a bit of a pain.

---


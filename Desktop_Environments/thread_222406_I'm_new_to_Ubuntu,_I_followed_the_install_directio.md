---
title: "I'm new to Ubuntu, I followed the install direction at FireFox's website"
date: 2006-07-24
forum: Desktop Environments
---

### Post by aten on 2006-07-24
this is what is says:

Extract the tarball in the directory where you want to install Firefox:

```
tar -xzvf firefox-1.5.0.4.tar.gz
```

This will create a firefox subdirectory of that directory.


------

But now do I run the file firefox which is in the directory, if I click on it it says "**Do you want to run "firefox", or display its contents?** 

"firefox" is an executable text file"
------


Then I can click on "run in Terminal", "Display", "cancel", "run"

if i click run nothing happens.

What do I do?

Thanks for all of the help in advance.

---

### Post by dtfinch on 2006-07-25
Nautilus isn't the best for running programs. It'll start them with the wrong  current directory and such.
You can create a launcher for it.
You can run it from the terminal. Something like: cd firefox && ./firefox, depending on where you put it.
You can set it as your default browser in System->Preferences->Preferred Applications. Mine, for example, has web browser set to "custom" with the command "/home/david/firefox/firefox %s".

---

### Post by aten on 2006-07-25
Thanks for the help but one question what is Nautilus?

---

### Post by dtfinch on 2006-07-25
"File Browser". I could swear the title bar used to say Nautilus, the name of the gnome file browser.

---

### Post by easyease on 2006-07-27
hi mate, as your new to ubuntu this might be of interest....
 [http://klik.atekon.de/](http://klik.atekon.de/)
It's a great place to get lots of big name software on your pc quickly and very easily. its even got blooming google earth on it now....

---

### Post by xmastree on 2006-07-27
> **aten said:**
> 
Extract the tarball in the directory where you want to install Firefox:

Why are you trying to download and install from a tarball? :confused: 
Just use synaptic, that's what it's for after all.

Menu>System>Administration>Synaptic Package Manager

Much easier than messing around, unless you really want to learn the hard way.

---


---
title: "Problem installing Gimmie"
date: 2009-05-26
forum: General Help
---

### Post by rrajath on 2009-05-26
I tried installing Gimmie. I reached the step where I had to give the command 'make', which apparently didn't work since I got this error.

```
make: *** No targets specified and no makefile found.  Stop.
```

What is the problem? And how do I solve this issue?

---

### Post by rrajath on 2009-05-27
bump!

---

### Post by Soul-Sing on 2009-05-27
There is no Makefile in this directory.

is there a directory with a readme/howto file?

---

### Post by rrajath on 2009-05-27
Yes. There is no make file in the directory. There's a file called BUILDING:

```

Gimmie Build Instructions

----

1) Install devel headers for GTK+2, PyGTK, libgnome-menu and GConf.  
   To do this on Ubuntu, run:
	$ sudo apt-get install libgtk2.0-dev python-gtk2-dev \
	  libgnome-menu-dev libgconf2-dev

2) Optionally install libgnomecups devel headers to display printer status.

3) Build Gimmie:
	$ ./autogen.sh --prefix=/usr
	$ make
	$ sudo make install

   If you have problems with Python packages, try installing python-gnome2,
   python-gnome2-desktop and python-gnome2-extras packages for your 
   distribution if they are not installed already.

4) To add Gimmie to your Gnome panel, right click the panel and select 
   "Add to Panel...".  Gimmie should be located in the Utilities section.

   To start the standalone version just run `gimmie`.  
```

I followed all the instructions, installed the required packages. But, I'm not able to find the autogen.sh nor the make file.

---

### Post by Soul-Sing on 2009-05-27
Maybe this will be helpful:

[http://ubuntuportal.blogspot.com/2007/03/how-to-install-gimmie-new-gnome-panel.html](http://ubuntuportal.blogspot.com/2007/03/how-to-install-gimmie-new-gnome-panel.html)

succes!

---

### Post by rrajath on 2009-05-27
Well, I'm not able to get past that 'make' command. I don't have the make file. This is probably the 6th time I'm trying. I downloaded gimmie from various sources. I'm just not able to install from any of those. :(

---

### Post by Soul-Sing on 2009-05-27
You have installed: build-essential?

---

### Post by rrajath on 2009-05-27
Yes. build-essential is already installed.

---


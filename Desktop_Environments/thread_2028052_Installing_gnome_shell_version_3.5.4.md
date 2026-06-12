---
title: "Installing gnome shell version 3.5.4"
date: 2012-07-17
forum: Desktop Environments
---

### Post by orange2k on 2012-07-17
Today I recieved in my mailbox a message that Gnome-shell 3.5.4 is ready with a download link: gnome-shell-3.5.4.tar.xz

How do I install that thing?

---

### Post by orange2k on 2012-07-17
I figured it out, well, in part: I unzippid the file, went into the new directory and
I ran ./configure, but it gave me this error:
```

configure: error: Package requirements (gio-unix-2.0 >= 2.31.6
			       libxml-2.0
                               gtk+-3.0 >= 3.3.9
                               atk-bridge-2.0
                               libmutter >= 3.5.4
                               gjs-internals-1.0 >= 1.33.2
			       libgnome-menu-3.0 >= 3.5.3
                               
                               gdk-x11-3.0 libsoup-2.4
                               gl
			       clutter-x11-1.0 >= 1.9.16
			       clutter-glx-1.0 >= 1.9.16
                               libstartup-notification-1.0 >= 0.11
                               gobject-introspection-1.0 >= 0.10.1
			       libcanberra
                               telepathy-glib >= 0.17.5
                               telepathy-logger-0.2 >= 0.2.4
                               polkit-agent-1 >= 0.100 xfixes
                               libnm-glib libnm-util gnome-keyring-1
                               gcr-3 >= 3.3.90
                               gnome-desktop-3.0 >= 3.5.1) were not met:

No package 'atk-bridge-2.0' found
No package 'libmutter' found
No package 'gjs-internals-1.0' found
No package 'libgnome-menu-3.0' found
No package 'clutter-x11-1.0' found
No package 'clutter-glx-1.0' found
No package 'gobject-introspection-1.0' found
No package 'telepathy-glib' found
No package 'telepathy-logger-0.2' found
No package 'polkit-agent-1' found
No package 'libnm-glib' found
No package 'libnm-util' found
No package 'gnome-keyring-1' found
No package 'gcr-3' found
No package 'gnome-desktop-3.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_SHELL_CFLAGS
and GNOME_SHELL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by markbl on 2012-07-17
Buddy you are going to drive over a cliff if you go that way ...

If you really want an experimental system with gnome-shell 3.5.4 on ubuntu 12.04 then by far your best (and easiest) approach is is to add the ricotz ppa. Read the warnings at [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing) then if you are still keen:
```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get install gnome-shell

```

But this is not really advisable unless you are an experienced linux user who can recover from system problems.

---

### Post by orange2k on 2012-07-18
> **markbl said:**
> Buddy you are going to drive over a cliff if you go that way ...

If you really want an experimental system with gnome-shell 3.5.4 on ubuntu 12.04 then by far your best (and easiest) approach is is to add the ricotz ppa. Read the warnings at [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing) then if you are still keen:
```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get install gnome-shell

```

But this is not really advisable unless you are an experienced linux user who can recover from system problems.

Well, I tried Ricotz PPA and it IS unstable, so I had to recover with purge-ppa...

---

### Post by vasa1 on 2012-07-18
> **markbl said:**
> ...
But this is not really advisable unless you are an **experienced linux user** who can recover from system problems.
+1. 
Otherwise, just wait till your Update Manager offers it to you. From what I understand, the odd ones (like 3.5) are "experimental" and the even ones (like 3.4 and the future 3.6) are "stable".

---

### Post by orange2k on 2012-07-18
> **vasa1 said:**
> +1. 
Otherwise, just wait till your Update Manager offers it to you. From what I understand, the odd ones (like 3.5) are "experimental" and the even ones (like 3.4 and the future 3.6) are "stable".

Thank you for that information!
I was curious so I had to try...
When I installed gnome-shell 3.5.4 via Ricotz's PPA all my extensions were gone and I had no option to get them back, and none of the other extensions would even show up on the page ([https://extensions.gnome.org/](https://extensions.gnome.org/))...
I guess its not an easy path to configure Gnome-shell from scratch...

---

### Post by kurt18947 on 2012-07-18
> **orange2k said:**
> Thank you for that information!
I was curious so I had to try...
When I installed gnome-shell 3.5.4 via Ricotz's PPA all my extensions were gone and I had no option to get them back, and none of the other extensions would even show up on the page ([https://extensions.gnome.org/](https://extensions.gnome.org/))...
I guess its not an easy path to configure Gnome-shell from scratch...

The same thing happened with gnome-shell 3.2 to 3.4, all the extensions failed.  It's possible to edit the metadata.json file, replacing 3.4 with 3.5.4 but my experience was that editing worked with some, did not work with others.

---

### Post by Cheesemill on 2012-07-18
> **orange2k said:**
> Thank you for that information!
I was curious so I had to try...
When I installed gnome-shell 3.5.4 via Ricotz's PPA all my extensions were gone and I had no option to get them back, and none of the other extensions would even show up on the page ([https://extensions.gnome.org/](https://extensions.gnome.org/))...
I guess its not an easy path to configure Gnome-shell from scratch...
That's because extensions are written for a specific version of Gnome Shell.
As 3.5 has only just been released no-one has written or updated their extensions for it yet.
Even if you succeed in compiling it yourself you will still have the same problem.

For now if you want to use any extensions you have to stick to 3.4.

---


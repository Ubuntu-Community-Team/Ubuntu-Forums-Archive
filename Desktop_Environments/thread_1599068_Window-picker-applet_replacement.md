---
title: "Window-picker-applet replacement?"
date: 2010-10-17
forum: Desktop Environments
---

### Post by Marceau on 2010-10-17
If you remember, window-picker-applet was included in UNE 10.04, and placed the title bar of a maximized application window in the gnome panel, thus saving quite a few vertical pixels. This is very useful on tiny netbook screens.

I used the applet on a regular gnome session as I don't use the UNE interface as such.

Now that I've upgraded to 10.10 and find myself still preferring the regular gnome desktop (not UNE), I tried reinstalling the window-picker-applet, but I find it no longer works well with Ubuntu.

Does anyone know of a different applet/project that has the same/similar function?

I'd basically like something that will take the title bar of a maximized application and place in the top gnome-panel.

---

### Post by nilarimogard on 2010-10-17
For the buttons and window title on the top panel, use [Window Applets]("http://www.webupd8.org/2010/10/window-applets-028-released-with-6-new.html"). For the icons only application list, use [DockBarX]("http://www.webupd8.org/2010/10/dockbarx-gets-closer-to-version-040.html").

---

### Post by LanoxxthShaddow on 2012-03-26
Hi Marceau,  there is now a port for the Gnome 3 Fallback Mode available at:  [https://github.com/lanoxx/window-picker-applet](https://github.com/lanoxx/window-picker-applet)  You can download and compile it if you want. Unfortunately I have not had time to create a PPA yet.  Best Regards Lanoxx

---

### Post by robytrevi on 2012-04-06
> **LanoxxthShaddow said:**
> Hi Marceau,  there is now a port for the Gnome 3 Fallback Mode available at:  [https://github.com/lanoxx/window-picker-applet](https://github.com/lanoxx/window-picker-applet)  You can download and compile it if you want. Unfortunately I have not had time to create a PPA yet.  Best Regards Lanoxx
I'm trying to create a deb package of window-picker-applet with your port but I have some errors.
First thing you didn't write it but I had to make manually the folder /usr/share/window-picker-applet
than the package won't be created and here the error:

dpkg-deb: errore: analisi del file "/var/tmp/tmp.rdCBnuZ02M/package/DEBIAN/control" vicino alla riga 7 pacchetto "lanoxx-window-picker-applet":
 errore nella stringa Version "d9ebcd2-1": il numero di versione non inizia con una cifra

It told that the version (d9ebcd2-1) number must start with a number.
But I don't know where to find that and how to modify it (the folder in the error is a temp folder and it disappear during the package construction).

Can you help me?
I'm talking about Ubuntu 12.04 (classic).

---


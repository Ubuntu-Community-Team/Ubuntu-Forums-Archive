---
title: "Azureus broke on me!"
date: 2006-02-24
forum: Desktop Environments
---

### Post by skinnyfat on 2006-02-24
Hey guys, any help on this would be appreciated. I recently used Automatix to install Azureus 2.3.0.6-3. It was working fine with the Sun Java 1.5 installation. Azureus told me to upgrade to version 2.4 so I did so. It also told me that I needed to update an SWT library file. After I did so when i tried to run it, I got nothing. I then tried running it a terminal to see the error and got this:

[SIZE="1"]skinnyfat@ubuntuBOX:~$ azureus
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3139 in java.library.path
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:109)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:158)[/SIZE]

Any ideas? Thanks in advance.

---

### Post by Trab on 2006-02-25
there would be a reason automatix uses an outdated version of automatix...
try removing it via synaptic, then reinstalling it via automatix...

---

### Post by skinnyfat on 2006-02-25
I removed azureus and reinstalled it via automatix and still get the same error when I try to run it. :cry:

---

### Post by Perfect Storm on 2006-02-25
Try this way:
Uninstall Azureus.

download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.

```

cd /to/the/folder/where/you/saved/azureus
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/
sudo chown -R root:root /opt/azureus/
smeg

```

Pick **Internet** and click **New Entry**

Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png

press ok.

---

### Post by skinnyfat on 2006-02-25
You are the man, it worked. I appreciate your input.:D

---

### Post by tidy_boy on 2006-02-25
I have the same problem I am very new to linux.

How do I unistall azurues please

---

### Post by tidy_boy on 2006-02-25
anyone I am really new to this and would appreciate the help

---

### Post by Trab on 2006-02-25
you need to open a terminal...
```

sudo apt-get remove azureus

```
it should ask u a question, you say yes...
it will then remove it...
good luck!
(this only works if u installed it via a deb, apt-get, synaptic, or automatix...)

---

### Post by tidy_boy on 2006-02-25
cheers Trab that worked :D

---

### Post by Dingo_aus on 2006-02-27
Worked for me too - you're the best :)

---

### Post by munralamun on 2006-03-06
Very useful. Thanks for posting. Stuff like this is invaluable for those who get lost (me!).

:)



[QUOTE=Artificial Intelligence]Try this way:
Uninstall Azureus.

download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.

```

cd /to/the/folder/where/you/saved/azureus
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/
sudo chown -R root:root /opt/azureus/
smeg

```

Pick **Internet** and click **New Entry**

Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png

press ok.[/QUOTE]

---

### Post by spartan777 on 2006-03-12
somebody should make this a sticky, or artificial intelligence should post this in the how-to's. this is the answer to about 3 hours of my own troubleshooting and forum-crawling. THANK YOU A.I.!!

---

### Post by jonas.p on 2006-03-14
you can also edit your azureus start script /usr/bin/azureus

change
```
-Djava.library.path=/usr/lib/jni:/usr/lib
```
to
```
-Djava.library.path=/usr/lib/jni:/usr/lib:.
```
since the needed library is in $HOME/.azureus/

worked fine for me

---

### Post by el1 on 2006-09-24
> **Artificial Intelligence said:**
> Try this way:
Uninstall Azureus.

download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.

```

cd /to/the/folder/where/you/saved/azureus
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/
sudo chown -R root:root /opt/azureus/
smeg

```

Pick **Internet** and click **New Entry**

Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png

press ok.



Thanks dude :D now I got azureus back :D

---


---
title: "Installing the most stable version of Compiz"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by Bohlio on 2007-05-19
Heres my setup, Im using ubuntu 7.04, with an ATI x300 running on fglrx drivers. To get the basic desktop effects to work, I had to create an XGL session to get around the "The composite manager is not available" message. Now i want to take it a step further and install the latest STABLE version of Compiz on my computer. My question is, how do i do it. All the guides I've found talked about installing Compiz under Gnome... What i dont quite know is, since I'm running under the XGL session, is that different from Gnome? Im new to the ubuntu world and dont quite understand all these 3D desktop and X, XGL, Gnome, things :neutral:
Any help would be greatly appreciated. I haven't set XGL to my default yet, In order to run it, I have to go to options, session, then select XGL. I dont know if this makes things easier for installing Compiz, or just complicates things.
Any help would be greatly appreciated. :)

---

### Post by Bohlio on 2007-05-19
Ok well nobody seems to want to answer this, and i think I kinda figured a little out. I installed the Compiz extras and Compiz manager through the packet manager, and I got the whole cube and wobbly effects working brilliantly! I love it. But i dont think its the newest version, In the packet manager it says its version 0.3.6 ( or really similar) but the compiz website says that a stable version 0.4 is available. But it is not in the packet manager and that is pretty much the only way i know how to install things. When i update the packet manager, it still doesnt reveal the newer version. Does anyone know how?

---

### Post by Matthaeus on 2007-05-19
[http://xorg.freedesktop.org/archive/individual/app/compiz-0.4.0.tar.gz](http://xorg.freedesktop.org/archive/individual/app/compiz-0.4.0.tar.gz)

Link from the compiz site. Download it, extract it, and run the install file.

Hope it works, Matt.

---

### Post by Bohlio on 2007-05-19
The instal file is just a text document that says...
> compiz uses libstartup-notification which is available at
[ftp://ftp.gnome.org/pub/GNOME/sources/startup-notification/](ftp://ftp.gnome.org/pub/GNOME/sources/startup-notification/)

compiz uses automake, in order to generate the Makefiles for compiz use:

	$ autogen.sh

After that, standard build procedures apply:

	$ make
	# make install

I dont really know what that means :-(

---

### Post by Matthaeus on 2007-05-19
Im a linux noob, but i guess this is what you should do:

Open a terminal, change directory to the extracted files. eg cd "paste the folder location"
then type
sh autogen.sh
sudo make install

Matt.

---

### Post by Bohlio on 2007-05-20
all i have to do is change the directory to the files and type in those two commands? Huh... I thought it would be harder than that :-P

---

### Post by Bohlio on 2007-05-20
well... that doesnt work, 
```
chad@chad-desktop:~$ cd /home/chad/Desktop/compiz-0.4.0
chad@chad-desktop:~/Desktop/compiz-0.4.0$ sh autogen.sh
sh: Can't open autogen.sh

```
Is there a way to install this using the Packetmanager??

Any help would be appreciated :-)

---

### Post by tenmoi on 2007-05-20
> **Bohlio said:**
> well... that doesnt work, 
```
chad@chad-desktop:~$ cd /home/chad/Desktop/compiz-0.4.0
chad@chad-desktop:~/Desktop/compiz-0.4.0$ sh autogen.sh
sh: Can't open autogen.sh

```
Is there a way to install this using the Packetmanager??

Any help would be appreciated :-)

you must be root to run it

Code:

sudo sh autogen.sh;)

---

### Post by Bohlio on 2007-05-21
Didnt work... :-(

```
chad@chad-desktop:~/Desktop/compiz-0.4.0$ sudo sh autogen.sh
sh: Can't open autogen.sh

```

Should there be a file in that directory called autogen.sh??? because there isn't :-( 
There is a Makefile.im and a makefile.am though, which I'm guessing is part of the next step... :-(

---

### Post by kpolice on 2007-05-21
```
./autogen.sh --prefix=/usr --enable-gnome --enable-metacity --enable-gconf --enable librsvg --disable-kde
```

If everything goes without problems "make" and finally "sudo make install" but first you will have to remove the compiz packages from synaptic.

Anyway if you don't know how to deal with software compiled from source you'll better stay with compiz 0.3.6 .

---

### Post by Bohlio on 2007-05-21
That tricky huh? Well I guess untill i get more aquainted with Ubuntu or till it is available through the packet manager ill just have to stay with 0.3.6.

Oh well, thanks for your help :-)

---

### Post by Kuoi on 2007-06-03
> **Bohlio said:**
> The instal file is just a text document that says...


I dont really know what that means :-(

I've a file on my computer , to know what to do if I want to install a source file the easy way , but in this case ...
They make it very difficult installing Compiz from source.
I wanted to send you my way , but I'll test everything before I reply ( mostly ) , and in this case , I can't figure out too how to install Compiz.

It's made for** experts only** I suppose , so I just leave it to them to install it on their computer.
Nice from Compiz we noobs can't try it out , and don't tell me it's easy ... all my installs from sources I did using my"explanation" file are working.
It is sometimes a bit searching , but with the file I know where and what to search.
In the case of Compiz , I've found nothing !!!!

Good luck , Kuoi

---

### Post by matteospqr on 2007-06-07
People I am trying desperately to install compiz but with no success.  I have installed all the packages with synaptic, what else should I do???

---

### Post by matteospqr on 2007-06-07
When I try to install the Compiz-Settings I get this message:


checking for PACKAGE... configure: error: Package requirements (dbus-1 compiz >= 0.3.3 dbus-glib-1 gconf-2.0 gtk+-2.0 >= 2.0.0) were not met:

No package 'dbus-1' found
No package 'compiz' found
No package 'dbus-glib-1' found
No package 'gconf-2.0' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---


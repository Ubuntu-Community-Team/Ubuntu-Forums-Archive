---
title: "pSX having trouble with 32 bit libs on amd64 system"
date: 2009-01-18
forum: Gaming &amp; Leisure
---

### Post by Miles_Prower on 2009-01-18
The core of it all is that pSX runs fine until I try to bind my disc drive to it. Selecting "insert cd drive" gives errors in the terminal. These errors lead me to believe that the system is looking for 32 bit libraries, but only finding 32 bit ones. I don't know how to isolate these libraries, find 32 bit versions, and ensure that pSX knows where to find them... That is where I need help, please.


Here's what the terminal gives when I click 'add disc drive':
```
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

```

here are the results of running
ldd pSX

```

	linux-gate.so.1 =>  (0xf7f92000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7ed5000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7ebf000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7df6000)
	libgtkglext-x11-1.0.so.0 => /usr/lib32/libgtkglext-x11-1.0.so.0 (0xf7df3000)
	libgdkglext-x11-1.0.so.0 => /usr/lib32/libgdkglext-x11-1.0.so.0 (0xf7da6000)
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7d35000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7d1f000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7cce000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7cc4000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7cac000)
	libpangox-1.0.so.0 => /usr/lib32/libpangox-1.0.so.0 (0xf7c9f000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf7c99000)
	libglade-2.0.so.0 => /usr/lib32/libglade-2.0.so.0 (0xf7c82000)
	libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf78e4000)
	libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf77a7000)
	libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf771b000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf76ff000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf76e5000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf76da000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf7696000)
	libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf7623000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf75e5000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf75e0000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf75dc000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf7525000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7436000)
	libm.so.6 => /lib32/libm.so.6 (0xf7410000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7401000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf73e8000)
	libc.so.6 => /lib32/libc.so.6 (0xf728a000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf654a000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6547000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6538000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6449000)
	librt.so.1 => /lib32/librt.so.1 (0xf6440000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6413000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6408000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf6405000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf63fb000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf63f4000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf63eb000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf63e6000)
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf63bd000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf6355000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf62df000)
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf62db000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf62d7000)
	libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf6295000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf626f000)
	libxcb-render-util.so.0 => /usr/lib32/libxcb-render-util.so.0 (0xf626a000)
	libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf6261000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6248000)
	/lib/ld-linux.so.2 (0xf7f93000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf621e000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf621b000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf6218000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf61f1000)
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf61d6000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf61d1000)


```


I thought this was interesting during install, but after reading warning after warning about rivers running red with blood and plagues and something about donuts, I decided I didn't want to force apt-get to install the desired packages.

```
taels@tornado:~/workspace/pSX$ sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk
[sudo] password for taels: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
Note, selecting ia32-libs instead of ia32-libs-sdl
ia32-libs is already the newest version.
Note, selecting ia32-libs instead of ia32-libs-gtk
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I couldn't find the desired packages in synaptic. Would forcing them be relatively safe? Could it solve the issue? Seems likely, but again, I keep seeing warnings about how forcing apt-get will give george bush a third term, and I don't want to mess up my good computer.


Just to clear this up, I know you're supposed to killall pulseaudio before running pSX; I do.

Thanks for reading, and I appreciate any help you'd be willing to offer.
~Tails

---

### Post by dfreer on 2009-01-18
Hmmmm, I've been using cd images to play games on pSX for quite a while now, didn't realize using a physical CD would cause different problems.

The ia32-libs-sdl and ia32-libs-gtk packages haven't been real packages since the Gutsy release of ubuntu. They are now virtual packages pointing towards ia32-libs, which explains your second error.

As for the first one, you could use [http://packages.ubuntu.com](http://packages.ubuntu.com) to find out whether there are any 32-bit versions of the libraries you need in a 64-bit package. 

For example, searching for the first library libgioremote-volume-monitor.so shows that it belongs to the GVFS package, and that there is no 64-bit package that contain this in a 32-bit library:

[http://packages.ubuntu.com/search?searchon=contents&keywords=libgioremote-volume-monitor.so&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libgioremote-volume-monitor.so&mode=exactfilename&suite=intrepid&arch=any)

If there were a 32-bit library available for 64-bit systems, it would look like this:

[http://packages.ubuntu.com/search?searchon=contents&keywords=libgdk_pixbuf-2.0.so.0&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libgdk_pixbuf-2.0.so.0&mode=exactfilename&suite=intrepid&arch=any)

Now, all 3 libraries that it is complaining about are provided by the package GVFS (gnome virtual file system). Whether or not you can simply drop in the 32-bit libs or not is a tricky question, and unfortunately I currently do not have debian/ubuntu installed (new PC haven't gotten around to it yet) to help you out there.

I'd try downloading the 32-bit package of GVFS from the above site, and extract all of the files inside. The files in the control.tar.gz are mostly useless; ignore them for now. 

In the data.tar.gz file, you should find a usr folder. This directly corresponds with your file system; anything in this usr folder would be placed in your /usr folder in the same spots if this was a normal 32-bit installation.

Since you are running 64-bit, I'd place everything in usr/lib in your /usr/lib32/ folder, keeping track of what you place in there in case you decide to uninstall this (it's only two folders to keep track of, /usr/lib32/gio and /usr/lib32/gvfs). Ignore the files in usr/share for now.

Run ldconfig to have ld update it's database on currently installed libraries, then try running pSX again. If it works great, if it doesn't I'd try two more things:

Install the file in usr/share/dbus-1/services/ in /usr/share/dbus-1/services/, but change the name to gvfs-ia32-daemon.service, and change the following line:
```
[D-BUS Service]
Name=org.gtk.vfs.Daemon
**Exec=/usr/lib/gvfs/gvfsd**

[D-BUS Service]
Name=org.gtk.vfs.Daemon
**Exec=/usr/lib32/gvfs/gvfsd**

```

I don't know how to start DBUS services manually, so if you do either do that, or simply restart your computer I'm sure something will start it up automatically. Then try pSX again.

If it still doesn't work, you can try manually installing all of the 32-bit libraries that GVFS depends on that aren't provided by ia32-libs, but I really don't know if that would help at all, someone with more experience with Gnome's Virtual File System would be needed.

Dropping the 32-bit libraries in the GVFS package won't FUBAR your system at all; as long as you don't overwrite existing files and remove them if they don't work for pSX. Hopefully you'll be able to get pSX working simply by dropping in the 32-bit libraries, if you have to add the DBUS service and/or have to install more 32-bit libraries to get the 32-bit version of GVFS working, it could possibly mess up your system, I really don't know.

---

### Post by Miles_Prower on 2009-01-18
grr.. the three files that it's complaining about are now in /usr/lib32/gio/modules/ , but pSX is still looking in the usr/lib directory instead of usr/lib32 where it should...
```

sound: underrun
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
sound: underrun
```

Could I modify the source code to point to the correct directory, or is that handled by ubuntu itself?


edit:
I got 'getlibs' and ran this command:
```
taels@tornado:~/workspace/pSX$ getlibs -l libgioremote-volume-monitor.so
```
, which solved the library problems. pSX still hangs when I try to bind my disc drive to it, though. I'll make some isos and see if that works, then post the results here.

---

### Post by Miles_Prower on 2009-01-18
Yeah, that did it. I just played, like, the first five minutes of breath of fire 4. Looks good. I can't add the disc drive without having the program crash, but disc images work. I need to make backups of my games anyways. 

So, if anyone's reading this because they had the same or a similar problem, install getlibs and grab the correct libraries like so:
heres the error:
```
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
```
heres the getlibs command:
[HTML]getlibs -l libgioremote-volume-monitor.so
[/HTML]


By the way, your name was in every forum thread I could find about pSX, and you solved, like, 90% of em. Way to keep up, dude.
Also, that makes me think you're like a pSX developer or something. Are you?

---

### Post by dfreer on 2009-01-18
Negative on being a pSX developer, what little programming skills I learned in my first year of college I've since long forgotten. I did however create the first .deb packages of pSX for ubuntu back when pSX first released a linux version. 

As my how-to thread became quite popular and I saw various problems and solutions posted, I have seen quite a bit so I guess you could say I know more about running pSX in linux than most people.

As for getlibs, I **really** do need to play with that program, to answer some questions of my own about it. I've heard it works for quite a lot of people so I'm glad it worked for you. It doesn't do much that's different from what I posted above, did you perhaps forget to run the **ldconfig as root** after you manually installed the libs? That would be why it Ubuntu didn't know about them.

Thanks for posting the above information for future readers btw!

---

### Post by Miles_Prower on 2009-01-18
I did run sudo ldconfig, and no errors came from it. (is root>super user?)I dunno. Huh. Have you ever heard of gvfs breaking nautilus? Every time I try to get to open places>>network, or open places>>computer, or open the trash can I get an error like 

Could not display "X"
Nautilus cannot handle "X" locations

Where X is network, computer, or trash, respectively.
I hear that this is a bug in gvfs, have you heard anything about that? If so, is there an apt-get option to downgrade a package to an earlier version?

I don't mean to dump all my problems on you or anything, so if it's not something you've seen before, don't worry about it.

Thanks for all the help,
"Tails"

---

### Post by dfreer on 2009-01-19
super user = root, they are the same thing (User ID of 0).

Did this new error occur before or after you installed the 32-bit libs?If it came before, then I don't think I can help you as I've never seen the error, and haven't run ubuntu for quite a while. 

If it came afterwards I suspect it has something to do with installing the 32-bit GFVS libs.

---


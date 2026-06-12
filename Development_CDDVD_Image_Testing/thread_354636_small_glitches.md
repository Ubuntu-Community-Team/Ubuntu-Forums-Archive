---
title: "small glitches"
date: 2007-02-06
forum: Development CD/DVD Image Testing
---

### Post by ronacc on 2007-02-06
I installed the edgy(i386) version of opera from the opera website using dpgk --force-architecture , (opera does not appear in synaptic for x86_64 arch)
the --force had worked for me in edgy before a 64bit .deb came out.I tried both 9.02 and 9.10 versions of opera , both yeild the same error.

/usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

the line from dpkg available is
Depends: libc6 (>= 2.1.3), xlib6g (>= 3.3.6) | xlibs | libxmu6, libqt3-mt (>= 3.3.4), libstdc++6

the installed version of libqt-mt.so is 3.3.7 with links from earlier versions ( but not 3.3.4)
no dmesg or syslog messages are generated when trying to start opera , it just fails to start with the above message.

any ideas ? 



I installed gdesklets and gdeklets-data with synaptic , trying to start gdesklets gives this error.


Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

the .gdesklets dir in /home/~ has this message , no other log messages are generated.

Log messages of /home/ron/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[02/06/07-07:42:13]===
Could not import tiling module!


I dont think the opera problem is a bug but the gdesklets I'm sot sure about.
again any ideas ?

---

### Post by pochu on 2007-02-07
Hi ronacc.

About the gdesklets problem, I think it's a bug in the python code. So I ask you to report a bug in Launchpad.

And about the opera problem... I think this is not a bug. I think the problem is that you've installed an x86 app in an x86_64 system, so it can't open the shared libraries, which are compiled for this architecture.

Also, this is not the right forum to ask these questions. This is for iso testing, not for problems with apps and architectures.

If any mod can move this to the right forum, maybe ronacc would have better answers than mine :D

Regards
Pochu

---

### Post by ronacc on 2007-02-07
Ok I'll post the gkdesklets as a bug I just wasn't sure it was and don't want to waste the devs time with spurious stuff. and Ill post my questions elsewhere.

---

### Post by pochu on 2007-02-07
That would be fine.

Also I'm not really sure if that about gdesklets is really a bug, but I think it is, and if it isn't, there is no problem. We will reject it ;)

---

### Post by reets on 2007-05-07
Got the same err:

Log messages of /home/dave/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[05/07/07-12:10:24]===
Could not import tiling module!

---

### Post by madman91 on 2007-05-11
Same issue!!

---

### Post by joshuachad on 2007-08-05
i know this was posted awhile ago but here is how i fixed it on Gutsy

Go to :
[https://demo.launchpad.net/ubuntu/gutsy/+source/gdesklets/](https://demo.launchpad.net/ubuntu/gutsy/+source/gdesklets/)

and make sure you have all the dependencies installed un 'Package Relationships'

Ill paste here to make it easy:
Package relationships
Build dependencies

    * cdbs
    * debhelper (>= 5.0.37ubuntu1)
    * gnome-pkg-tools
    * libglib2.0-dev (>= 2.4.1-2)
    * libgnomeui-dev (>= 2.6.1.1-2)
    * libgnomevfs2-dev (>= 2.8.4)
    * libgtk2.0-dev (>= 2.4.1-3)
    * libgtop2-dev (>= 2.6.0-4)
    * librsvg2-dev
    * libxml-parser-perl
    * pkg-config
    * python-dev
    * python-gnome2-dev
    * python-gtk2-dev
    * python-pyorbit-dev
    * swig

---


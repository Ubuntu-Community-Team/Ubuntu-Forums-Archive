---
title: "nVidia Driver Intallation Problems"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Yeldarb on 2005-06-22
I'm having problems installing the nVidia drivers using *sudo apt-get install nvidia-glx*.  I've been searching and it seems the problem is unique to my system... well as far as I can tell at least.

The problem is that rather than downloading and installing the package, it asks for me to insert my Kubuntu installation CD.
> 
Media change: please insert the disc labeled
 'Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

Now this in itself wouldn't be a problem... I just found it odd as none of the other packages I have installed asked me to do this.

So I put in the CD and it starts unpacking and installing, but it gives me an error.
> 
Unpacking nvidia-glx (from .../nvidia-glx_1.0.7174-0ubuntul_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /cdrom//pool/restricted/l/linux-restricted-modules-2.6.10/nvidia-glx_1.0.7174-0ubuntul_i386.deb (--unpack):
 short read in buffer_copyu (backend dpkg-deb during './usr/lib/libGLcore.so.1.0.7174')
Errors were encountered while processing:
 /cdrom//pool/restricted/l/linux-restricted-modules-2.6.10/nvidia-glx_1.0.7174.0ubuntul_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help would be much appreciated.  Thanks.

---

### Post by Zeddicus on 2005-06-22
Did you mount the cd before hitting enter?

Also, try commenting out the cdrom portion of /etc/apt/sources.list, apt-get update, then try again?

---

### Post by Yeldarb on 2005-06-22
[QUOTE=Zeddicus]Did you mount the cd before hitting enter?

Also, try commenting out the cdrom portion of /etc/apt/sources.list, apt-get update, then try again?[/QUOTE]
 Thanks Zeddicus.  Commenting the first line of */etc/apt/sources.list* did the trick.  Is there a reason I would need that in the future, or should I leave it commented out?

---

### Post by Zeddicus on 2005-06-22
[QUOTE=Yeldarb]Is there a reason I would need that in the future, or should I leave it commented out?[/QUOTE]

Doesn't do any harm to leave it commented out.  Without it commented out, apt-get will want the CD for files it knows are on the CD.  Commenting it out just tells it to get it from the server.

---


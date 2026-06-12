---
title: "ATi XGl - shell script issues?"
date: 2006-09-21
forum: Desktop Environments
---

### Post by kaisa on 2006-09-21
Just installed ubuntu for the first time, and im working on getting some desktop improvements...namely XGL. I've been working with:

[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)


my drivers are installed correctly, as games like warsow run perfectly, also fglrx identifies my card correctly.

The walkthrough that im using has me making a shell script in order to start the instance of XGL at login. Currently what is happening is that i'll select XGL for the session, and then wait for about 15 seconds and an error message will pop up. At the bottom of the error I see:
```
Unrecognized option: -fullscreen
```

So i think to myself, there must be something wrong with the command the shell script is passing to it... so I checked the script:
```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec gnome-session

```

I just cant figure out whats wrong with it. It's written exactly as the guide says. If anyone has some insight as to whats going on, that would be great.

Thanks.

---

### Post by kaisa on 2006-09-21
Posting the xsession-errors file that was generated when i tried to open the xgl session:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "zach"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/zach:/tmp/.ICE-unix/8055

(gnome-panel:8128): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:8128): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:8128): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
gnome-window-decorator: no process killed

** (update-notifier:8156): WARNING **: no cdrom: disk

xvinfo:  Unable to open display :1
compiz: Couldn't open display :1
XGL Absent, assuming AIGLX
```

funny thing, this error file doesnt show the -fullscreen unrecognized command bit.

---

### Post by kaisa on 2006-09-21
I've done a bit more digging, and it seems like the heart of the problem has to do with the ati drivers and the libgl.so.1.2 file. I tried reinstalling libgl1-mesa...

Well the part of the how-to that i just cant seem to figure out is this part:

>     *  And here comes the big part: the mesa libraries. I see many people having the well-known "compiz.real: GLX_EXT_texture from pixmap is missing" error, and they can't seem to find out why this happens. Well, the reason as simple and as complicated the message suggests: this certain extension is NOT supported by ATI's driver (nVidia doesn't support it either, so no need to go OMGATILOOSE etc ). So, in order to run compiz, you're going to have to resort to standard mesa libraries. But, I hear you ask, where should I find these? The answer is simple: package libgl1-mesa has them. Now read carefully: when you install this particular package via apt-get, it'll place a libGL.so.1.2 inside your /usr/lib, and a symlink file called libGL.so.1 which points to the libGL.so.1.2 file. Now, if you install the ATI drivers by using the installer, these files will be replaced by symlinks to ATI's libGL.so.1.2 which resides inside /usr/lib/fglrx. So what do you do? After installing libgl-mesa and before installing ATI's drivers, create a directory called /opt/mesa and copy the file there, like this: 

```
sudo mkdir /opt/mesa
```
```
sudo cp /usr/lib/libGL.so.1.2 /opt/mesa/libGL.so.1.2
```


he then goes on to talk about symlinks (doesnt explain what they are :( ) and how to copy the correct files, but the files i need arent there.. gah I dont know, im just confused as hell

---

### Post by kaisa on 2006-09-21
I've lost the login screen now...god damn. Looks like its a fresh install and a trip back to the drawing board for me

---

### Post by blitzer on 2006-09-21
> **kaisa said:**
> I've lost the login screen now...god damn. Looks like its a fresh install and a trip back to the drawing board for me

Hi Kaisa,  I am going to give you a  :KS  for effort on your project.  I have giving up on ATI drivers and installing Dapper it is to time consuming  :( 

I'm sticking with Breezy untill Edgy comes out with fixes I hope :cool: 

Don't give up the answer is in the forums somewhere.;)

---


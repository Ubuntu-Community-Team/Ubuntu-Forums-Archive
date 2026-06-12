---
title: "Aevum Obscurum setup"
date: 2009-01-08
forum: Gaming &amp; Leisure
---

### Post by xtremesupremacy3 on 2009-01-08
Hey everyone,

Well I'm kinda stuck.
Having downloaded Aevum Obscurum a while back and played it, I needed to do some changes to my machine and decided to reinstall Ubuntu and download AO again. so now I got java and I try and run the install file, but this is the output I get from the terminal:

```
Unpacking JRE ...
Starting Installer ...
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2a397c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb2a39891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xa84f2494]
#3 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/xawt/libmawt.so [0xa85fda76]
#4 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/xawt/libmawt.so [0xa85e380a]
#5 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/xawt/libmawt.so [0xa85e3a51]
#6 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa85e3c5c]
#7 [0xb2ac7b8b]
#8 [0xb2ac1a7b]
#9 [0xb2ac1a7b]
#10 [0xb2abf157]
#11 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so [0xb77cffec]
#12 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so [0xb78dd1f8]
#13 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so [0xb77cfe1f]
#14 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb782d4bd]
#15 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75d92cd]
#16 [0xb2ac742b]
#17 [0xb2ac19a4]
#18 [0xb2abf157]
#19 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so [0xb77cffec]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb2a397c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb2a3996e]
#2 /usr/lib/libX11.so.6 [0xa84f1619]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xa84e7666]
#4 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/xawt/libmawt.so [0xa85e26df]
#5 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/xawt/libmawt.so [0xa85e2970]
#6 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/xawt/libmawt.so [0xa85e3b98]
#7 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa85e3c5c]
#8 [0xb2ac7b8b]
#9 [0xb2ac1a7b]
#10 [0xb2ac1a7b]
#11 [0xb2abf157]
#12 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so [0xb77cffec]
#13 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so [0xb78dd1f8]
#14 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so [0xb77cfe1f]
#15 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb782d4bd]
#16 /home/arfee/Desktop/AevumObscurum_Main_unix_V1.sh.31313.dir/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75d92cd]
#17 [0xb2ac742b]
#18 [0xb2ac19a4]
#19 [0xb2abf157]

```

And the installer comes up. Now the problem is that the installer is just a white box, no release notes, no next box to click on, totally nothing.
I did it via sudo, I chmod-ded it, nothing.

And theres nothing out there on Google to help, can you guys help me discover whats going on? 

Thanks
Arthur

---

### Post by 0bso on 2009-01-08
Not sure what the solution is, but you're not alone.

[https://bugs.launchpad.net/xorg-server/+bug/185311](https://bugs.launchpad.net/xorg-server/+bug/185311)

---

### Post by donkyhotay on 2009-01-08
If you follow the link posted by 0bso there are some solutions listed about 11th post down that look useful. They recommend doing
```
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /opt/java/jre/lib/amd64/xawt/libmawt.so
```
or
```
sed -i 's/XINERAMA/FAKEEXTN/g' /opt/java/jre/lib/i386/xawt/libmawt.so
```
depending on what kind of system you have. I don't know if it works or not (haven't encountered this error myself) but there are more posts and suggestions and looks like a good place to start.

---

### Post by donkyhotay on 2009-01-08
If you follow the link posted by 0bso there are some solutions listed about 11th post down that look useful. They recommend doing
```
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /opt/java/jre/lib/amd64/xawt/libmawt.so
```
or
```
sed -i 's/XINERAMA/FAKEEXTN/g' /opt/java/jre/lib/i386/xawt/libmawt.so
```
depending on what kind of system you have. I don't know if it works or not (haven't encountered this error myself) but there are more posts and suggestions and looks like a good place to start.

---


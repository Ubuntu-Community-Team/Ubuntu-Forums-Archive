---
title: "[SOLVED] Blank startup screen in maple 12"
date: 2008-09-12
forum: Education &amp; Science
---

### Post by Line on 2008-09-12
Hi
I had this problem getting my Maple 12 to work. Now the problem is solved, and here is the thing that had to be done.

1) Use a text-editor to open the "maple" file in (your maple dir)/bin
2) Add ```
export AWT_TOOLKIT=MToolkit && xmaple
``` to the top section of the file
3) Save and restart Maple

Found some other solutions out the too that may be smarter than this
[http://ubuntuforums.org/showthread.php?t=881692&highlight=maple+blank]("http://ubuntuforums.org/showthread.php?t=881692&highlight=maple+blank")
[http://ubuntuforums.org/showthread.php?t=450064&highlight=maple+blan]("http://ubuntuforums.org/showthread.php?t=450064&highlight=maple+blank")

Thanks

---

### Post by ginbuntu on 2008-11-12
it seems your solution does not work for Ubuntu amd64. 
if I use export AWT_TOOLKIT=MToolkit, I'll get an error 

```

jin@jin-desktop:~$ export AWT_TOOLKIT=MToolkit
jin@jin-desktop:~$ /opt/maple12/bin/maple -x
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f8e79aee9fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7f8e79aeeab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7f8e7a56b698]
#3 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f8e7b163d66]
#4 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f8e7b11297b]
#5 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f8e7b112c4d]
#6 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f8e7b112ec2]
#7 [0x7f8e9a2a6563]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f8e79aee9fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f8e79aeeb77]
#2 /usr/lib/libX11.so.6 [0x7f8e7a56a8c0]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x2e) [0x7f8e7a56108e]
#4 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f8e7b111ca5]
#5 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f8e7b111ef9]
#6 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so [0x7f8e7b112cef]
#7 /opt/maple12/jre.X86_64_LINUX/lib/amd64/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x12) [0x7f8e7b112ec2]
#8 [0x7f8e9a2a6563]
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f8e9eccf5af, pid=7608, tid=1102383440
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x315af]  catgets+0x1f
#
# An error report file with more information is saved as hs_err_pid7608.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted
jin@jin-desktop:~$ 


```

---

### Post by robertyou on 2008-11-12
Hi,

I would also add this solution to your list..
[http://ubuntuforums.org/showthread.php?t=924232](http://ubuntuforums.org/showthread.php?t=924232)

It makes more sense to me how the problem could occur this way, seems that the path to system's java jre isn't correctly specified in the launching code of file maple.

Maybe you can give it a try, ginbuntu.

Cheers.

---

### Post by jac0117 on 2009-01-24
Thanks LINE, your solution worked perfect for me.
I'm using Ubuntu Intrepid 32bit

And just to add, once you add that line to the file and save it you end up with a simple .txt file instead of a shell/script.  Then you just create a launcher to the xmaple file, not the maple file. 

Cool, thanks again.

---

### Post by dox_drum on 2009-03-13
Thank you, it worked for me... and I'm using Maple 11 running Intrepid.

[CENTER]Enjoy![/CENTER]

---

### Post by chacham23 on 2009-05-14
Thanks worked for me too.. maple12 +ubuntu 9.04

---

### Post by visarute on 2009-11-19
Thanks so much!!!
This line work perfectly for me too with:

Ubuntu 9.10
Maple 11.02

---


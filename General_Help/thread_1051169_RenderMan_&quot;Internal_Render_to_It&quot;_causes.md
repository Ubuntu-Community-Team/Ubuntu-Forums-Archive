---
title: "RenderMan &quot;Internal Render to It&quot; causes Maya Lockup"
date: 2009-01-26
forum: General Help
---

### Post by phuziun on 2009-01-26
Hello,

My name is Dave Hale and I'm a Linux systems administrator for the [Savannah College of Art and Design]("http://scad.edu").  We run Ubuntu Hardy Heron 8.04.1 x86_64 here.  I realize this isn't a supported distribution for RenderMan, but I'm just hoping that someone can help us from the goodness of their hearts, so that our students can continue on with their work.

It's been reported to us by our RenderMan professor here that a majority of the time he invokes an "Internal Render to It" it locks up Maya.   We need this for a couple of reasons, primarily for our Secondary outputs.   I've seen this, I've reproduced this, however I haven't found a consistent way to reproduce the issue.  It almost seems to randomly work and randomly not work.

We've implemented the centos lib hack in order to get "it" to even run in the first place.  I've tried running maya with `strace maya` and `maya -d gdb` and adding the RATDEBUG=6 to my Maya.env file.  However, most of this hasn't returned any useful information.  My Backtrace from maya -d gdb usually gives me something like:

#0  0x00007ffb0d21fc86 in poll () from /lib/libc.so.6
#1  0x00007ffb0e485d7a in _XtWaitForSomething () from /usr/lib/libXt.so.6
#2  0x00007ffb0e486e73 in XtAppNextEvent () from /usr/lib/libXt.so.6
#3  0x00007ffb13fe21a2 in TeventHandler::processXEvent ()
   from /usr/autodesk/maya2008-x64/lib/libExtensionLayer.so
#4  0x00007ffb13fe2254 in TunixEventHandler::handleEvents ()
   from /usr/autodesk/maya2008-x64/lib/libExtensionLayer.so
#5  0x00007ffb13fd6f97 in Tapplication::start ()
   from /usr/autodesk/maya2008-x64/lib/libExtensionLayer.so
#6  0x0000000000410369 in appmain ()
#7  0x000000000041e2fb in main ()

Except when it's actually locked up, the libXt row will look more like:
**#1  0x00007ffb0e485d7a in ?? from /usr/lib/libXt.so.6**

With two or three questions marks where there is usually a function.  So to me, it would seem as if Maya is hanging on:
**#1  0x00007ffb0e485d7a in _XtWaitForSomething () from /usr/lib/libXt.so.6**

Because, there doesn't really seem to be much going on, Maya is just hanging... waiting for something to happen, exactly as it does when your waiting for "It" to finish receiving a render.

So, I went ahead and loaded the [CentOS version of libXt]("http://mirror.centos.org/centos/5.2/os/x86_64/CentOS/") into my custom lib folder for "It", this didn't appear to do anything, but it's hard to say since the lock-ups are inconsistent!

I've posted about this on the RenderMan Support forums and Autodesk's The Area.

[https://renderman.pixar.com/forum/editpost.php?s=&action=editpost&postid=57842](https://renderman.pixar.com/forum/editpost.php?s=&action=editpost&postid=57842)
[http://area.autodesk.com/index.php/forums/viewthread/21885/](http://area.autodesk.com/index.php/forums/viewthread/21885/)

Any ideas or suggestions would be extremely appreciated as our students are approaching mid-terms.]

---


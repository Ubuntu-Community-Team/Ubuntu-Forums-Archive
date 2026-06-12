---
title: "OpenOffice/Firefox doing copy&amp;paste"
date: 2006-11-14
forum: Desktop Environments
---

### Post by Hokky on 2006-11-14
Can any of you help me confirm a bug?

You need a Gmail account.

Start up Open Office in Edgy and write a small paragraph. Copy the text with Ctrl-C and then paste the text into the body of a new message you are composing with Gmail.

On my computer Open Office crashes completely and has to be restarted.

Any ideas?

---

### Post by Rothchild on 2006-11-14
Yeah I just tried this and can confirm that pasting in to Gmail from Open Office causes OO to crash. Here's the meat of the backtrace for anyone who understands this stuff ;-)

0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6eaa01e in __lll_mutex_lock_wait ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6ea668b in _L_mutex_lock_238 () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb6ea6cd9 in pthread_mutex_unlock ()
   from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7205ec3 in osl_acquireMutex ()
   from /usr/lib/openoffice/program/libuno_sal.so.3
#5  0xb74575d0 in vos::OMutex::acquire ()
   from /usr/lib/openoffice/program/libvos3gcc3.so
#6  0xb4e04eb2 in SalYieldMutex::acquire ()
   from /usr/lib/openoffice/program/libvclplug_gen680li.so
#7  0xb4e04b7d in X11SalInstance::AcquireYieldMutex ()
   from /usr/lib/openoffice/program/libvclplug_gen680li.so
#8  0xb4dfaa29 in SalXLib::Yield ()
   from /usr/lib/openoffice/program/libvclplug_gen680li.so
#9  0xb4e05037 in X11SalInstance::Yield ()
   from /usr/lib/openoffice/program/libvclplug_gen680li.so
#10 0xb7c7ef08 in Application::Yield ()
   from /usr/lib/openoffice/program/libvcl680li.so
#11 0xb7c7efdc in Application::Execute ()
   from /usr/lib/openoffice/program/libvcl680li.so
#12 0x0806d8c7 in desktop::Desktop::Main ()
#13 0xb7c84c2c in InitVCL () from /usr/lib/openoffice/program/libvcl680li.so
#14 0xb7c84d35 in SVMain () from /usr/lib/openoffice/program/libvcl680li.so
#15 0x0805fdc3 in sal_main ()
#16 0x0805fe46 in main ()


I just double checked and it doesn't do it in Konqueror (I'm using kubuntu)


Child

---

### Post by FyreBrand on 2006-11-14
You don't need a gmail account.  The same thing happens to me in Moodle.  I try and copy something from OO.writer to the Moodle post window in firefox and OO crashes.

Have you looked on Launchpad to see if there is a bug filed for it?  I do think I remember reading this before but I'm not sure now.  I'll try and look later if you don't get to it before me.

---

### Post by ShadowVlican on 2006-11-14
maybe OO doesn't support html in clipboard

try pasting in a plain text editor, then copy again to paste in OO

---

### Post by Hokky on 2006-11-15
I'm tied up at work and don't have time to look into this for another 24 hours. Feel free to file a bug. I'll have a look at it later anyway. 

I know that pasting the text into Gedit works fine.
Since I mess my system up with different repositories I needed someone "pure" to confirm the bug. Don't know how pure you all are, but the problems seems to occur on other systems too.

Thanks for replying everyone.

---

### Post by Tim Prosser on 2006-11-15
This is a known bug - see 

[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62432](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62432)

You might find the updated package available fixes the problem, although I haven't used them long enough to confirm completely:

add these lines to your /etc/apt/sources.list file:

   deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) edgy/$(ARCH)/
   deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) edgy/all/

and it should make OOo 2.0.4-2 available


I'm surprised this hasn't been released yet, it really is a big nono having openoffice so unstable.  Its the main application for me - and I get in big trouble when it crashes on the other half...

---

### Post by Hokky on 2006-11-15
Thanks! You saved me the trouble of looking up this later.

I'll wait until they release a bug fix and use the GEdit method for now.

To bad this hasn't been fixed yet. It's quite serious.

---

### Post by FyreBrand on 2006-11-15
Thanks Tim.

---


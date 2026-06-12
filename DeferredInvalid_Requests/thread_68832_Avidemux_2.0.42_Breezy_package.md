---
title: "Avidemux 2.0.42 Breezy package"
date: 2005-09-24
forum: Deferred/Invalid Requests
---

### Post by Blue1k on 2005-09-24
I made a Breezy package for avidemux from source.

Hope you will consider it.

[email]Blue1k@shaw.ca[/email] :)

---

### Post by bored2k on 2005-09-29
Is there anyone we could try it ?

By the way, the old one works.

---

### Post by Blue1k on 2005-09-30
Sure..I uploaded it to a link I will you give you through PM.

Cheers!

---

### Post by Blue1k on 2005-10-19
If anyone wants to try it (instead of adding debian repo), you can dld it from:

[http://rapidshare.de/files/6485564/avidemux-2.0.42_2.0.42-1_i386.deb.html]("http://rapidshare.de/files/6485564/avidemux-2.0.42_2.0.42-1_i386.deb.html")

---

### Post by jeremy on 2005-10-19
Seems fine to me, thanks.

BTW the command to run it is 'avidemux2'.

---

### Post by JuanC on 2005-10-19
Any Amd64 package?

---

### Post by newOldUser on 2005-10-22
I'm new to this (linux, ubuntu and debian packages) but would like to try your avidemux package. I've heard good things about the program and would like to create some video clips from DVD's. 

I've downloaded the file to my home directory and ran 

sudo dpkg -i *package.deb*

It looks like it installed but when I open a terminal and enter "avidemux2" this is what I get:

```
avidemux2: error while loading shared libraries: libmad.so.0: cannot open shared object file: No such file or directory
```

Did I miss a step? Any idea on how to fix the problem?

---

### Post by Blue1k on 2005-10-22
You need the mad library. 

Try 

sudo apt-get install libmad0****  :)

---

### Post by bored2k on 2005-10-22
I have made an avidemux 2.1_branch1 package using SVN. The avidemux creator is urging everyone to use the SVN instead of the old unstable package. I compiled this one for support with pretty much everything. It's a **LOT** better than the stable avidemux 2.0.42.

[http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html](http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html)

---

### Post by Blue1k on 2005-10-22
Oh sweet!

Thanks!!

---

### Post by bored2k on 2005-11-01
[http://rapidshare.de/files/7068397/avidemux_2.1_svn-2_i386.deb.html](http://rapidshare.de/files/7068397/avidemux_2.1_svn-2_i386.deb.html)

New Avidemux 2.1.00 build from SVN .

---

### Post by jdong on 2005-11-11
DEFERRED : Will consider for Extras later

---

### Post by -DarkMind- on 2005-12-03
thanks for the package :)

---

### Post by binks on 2005-12-04
very very nice would be good to see this in repos 
ps this version is far better than the previous ones

---

### Post by bored2k on 2005-12-10
Avidemux 2.1 **Final** package (might depend on a few things).
It only lacks x264 support and Xvid 0.9 (though it has Xvid 1.0+ enabled).

[http://rapidshare.de/files/8944662/avidemux-2.1.0-1_i386.deb.html](http://rapidshare.de/files/8944662/avidemux-2.1.0-1_i386.deb.html)

---

### Post by 23meg on 2005-12-10
[QUOTE=bored2k]Avidemux 2.1 **Final** package (might depend on a few things).
It only lacks x264 support and Xvid 0.9 (though it has Xvid 1.0+ enabled).

[http://rapidshare.de/files/8944662/avidemux-2.1.0-1_i386.deb.html](http://rapidshare.de/files/8944662/avidemux-2.1.0-1_i386.deb.html)[/QUOTE]
This build rocks. I've had to install libfaac0 and liba52-0.7.4 from the repositories to get it to work.

---

### Post by GeneralZod on 2005-12-11
[QUOTE=23meg]This build rocks. I've had to install libfaac0 and liba52-0.7.4 from the repositories to get it to work.[/QUOTE]

I also had to install libsmjs1.

---

### Post by bored2k on 2005-12-11
[QUOTE=GeneralZod]I also had to install libsmjs1.[/QUOTE]
[QUOTE=23meg]This build rocks. I've had to install libfaac0 and liba52-0.7.4 from the repositories to get it to work.[/QUOTE]Ok so I'm no good at building good debian packages, y'all blew my cover as a shaman l33t meister :( .

---

### Post by GeneralZod on 2005-12-11
Mirror'd, as rapidshare is annoying ;)

[http://---------------](http://---------------)

Edit:

Holy crap - you people are burning up gigabytes per day(!).  I'm going to have to remove this mirror, I'm afraid - I don't have the bandwidth to deal with this. :/

---

### Post by ElijahLofgren on 2005-12-15
[QUOTE=bored2k]Ok so I'm no good at building good debian packages, y'all blew my cover as a shaman l33t meister :( .[/QUOTE]
I had to also install liblame0, libfaad2-0 and libxvidcore4 . ;)

---

### Post by tommi-fi on 2006-01-05
Can't get Avidemux to work.

I have Ubuntu 4.10 installed and updated to Hoary
Downloaded: [http://rapidshare.de/files/8944662/avidemux-2.1.0-1_i386.deb.html]("http://rapidshare.de/files/8944662/avidemux-2.1.0-1_i386.deb.html")

and installed:
liblame0
libfaad2-0 
libxvidcore4
libsmjs1
libfaac0
liba52-0.7.4

Installing Avidemux :
```

xxxxxxa@Ubuntu:~ $ sudo dpkg -i avidemux-2.1.0-1_i386.deb
(Reading database ... 97982 files and directories currently installed.)
Unpacking avidemux-2.1.0 (from avidemux-2.1.0-1_i386.deb) ...
dpkg: error processing avidemux-2.1.0-1_i386.deb (--install):
 trying to overwrite `/usr/local/bin/avidemux2', which is also in package avidemux-2.0.42
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 avidemux-2.1.0-1_i386.deb
```

---

### Post by cutOff on 2006-01-08
> **GeneralZod]Mirror'd, as rapidshare is annoying  said:**
> http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb[/url]
Great! worked like a charm.

Thanks

---

### Post by sven-tek on 2006-01-08
wow avidemux is good stuff, should be in official repo
... and should be in a dapper standard package imho

---

### Post by GeneralZod on 2006-01-08
[QUOTE=cutOff]Great! worked like a charm.

Thanks[/QUOTE]

It's not actually mine - you should be thanking bored2k :)

---

### Post by kxs on 2006-01-15
[QUOTE=sven-tek]wow avidemux is good stuff, should be in official repo
... and should be in a dapper standard package imho[/QUOTE]

I agree. it should be a standard package in dapper

---

### Post by Jeffery Mewtamer on 2006-01-30
This topic is a God send. Yay I'm closer then ever to being 100% Linux.

---

### Post by Robban59 on 2006-02-11
Hi there everybody,

I'm still running Hoary, tought I'd give Avidemux a run , so I installed the package "avidemux-2.1.0-1_i386.deb"; when I try to run it I get this : 

robban@dalkey:~/downloads$ avidemux2
avidemux2: error while loading shared libraries: libslang.so.2: cannot open shared object file: No such file or directory

I tried to find/get the lib "libslang.so.2" but didn't succeed : so where do I find it ? I hope it is not running Hoary the problem...


Thanx in advance/

---

### Post by gingermark on 2006-02-18
[QUOTE=bored2k]Avidemux 2.1 **Final** package (might depend on a few things).
It only lacks x264 support and Xvid 0.9 (though it has Xvid 1.0+ enabled).

[http://rapidshare.de/files/8944662/avidemux-2.1.0-1_i386.deb.html](http://rapidshare.de/files/8944662/avidemux-2.1.0-1_i386.deb.html)[/QUOTE]
Thankyou so much for this. Is most appreciated.

---

### Post by quini on 2006-03-03
Buenas.

Gracias por los paquetes... y si teneis algo de tiempo libre y quereis debianizar la última versión, adelante  ;)

Un saludo  :D

---

### Post by quini on 2006-03-03
[QUOTE=Robban59]I'm still running Hoary, tought I'd give Avidemux a run , so I installed the package "avidemux-2.1.0-1_i386.deb"; when I try to run it I get this : 

robban@dalkey:~/downloads$ avidemux2
avidemux2: error while loading shared libraries: libslang.so.2: cannot open shared object file: No such file or directory

I tried to find/get the lib "libslang.so.2" but didn't succeed : so where do I find it ? I hope it is not running Hoary the problem...
[/QUOTE]

You should use apt-file:

1. sudo aptitude install apt-file -y
2. sudo apt-file update
3. apt-file search libslang.so.2
4. sudo aptitude install xxxx (where xxxx is the package found in 3.)

Hope that helps  ;)

---

### Post by jerob on 2006-03-05
i have had 2.0.42 working perfectly and decided to try out 2.1 and i
after i start it up if i go to "open" a file i automatically get the following in terminal.
is there somethign that i didn't do correctly or failed to download?

```
jeremy@ubuntuserver:/$ avidemux2

 LARGE FILE AVAILABLE : 1 offset
Locales for avidemux appear to be in

I18N : _File

*******************
  Avidemux 2, v  2.1.0
*******************
 http://fixounet.free.fr/avidemux
 Code      : Mean & JSC
 GFX       : Nestor Di , nestordi@augcyl.org
 Testing   : Jakub Misak
 FreeBSD   : Anish Mistry, amistry@am-productions.biz
Arcc X86 X86_64 activated.

 Registering Encoders
*********************
Mjpeg encoder registred
Xvid-4  encoder registred
FFMPEG  encoder registred

 3 encoder registered
Initializing global xvid 4
        xvid build:xvid-1.0.3
        xvid thread:0
        xvid SIMD supported:(f7)
                MMX
                MMXEXT
                SSE
                3DNOW
                3DNOWEXT
Checking cpu capabilities
        Cpu has MMX
        Cpu has 3DNOW
        Cpu has MMXEXT
        Cpu has SSE
End of cpu capabilities check
Using /home/jeremy/.avidemux as base directory for prefs/jobs/...
Found 14 video encoder
Found 9 audio encoder
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Registering Filters
*********************

Using dummy audio device
Global SDL init...
Spidermonkey initialized.

 Canonizing null string ??? (//)
Images stat:___________Max memory consumed (MB)     : 0
Current memory consumed (MB) : 0
Max image used               : 0
Cur image used               : 0
#0  0xffffe410 in ?? ()
#1  0xbf843830 in ?? ()
#2  0x00000000 in ?? ()
#3  0x00000000 in ?? ()
#4  0xb6ebde16 in fork () from /lib/tls/i686/cmov/libc.so.6
#5  0xb71b65b4 in fork () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb775ddaf in g_on_error_stack_trace () from /usr/lib/libglib-2.0.so.0
#7  0x0805a0a8 in ?? ()
#8  <signal handler called>
#9  0x0837a235 in operator delete[] ()
#10 0x0837a317 in operator delete[] ()
#11 0x0837a879 in operator delete[] ()
#12 0x08057cd1 in ?? ()
#13 0x0829c311 in operator delete[] ()
#14 0xb785dab3 in g_cclosure_marshal_VOID__VOID ()
#15 0xb78523a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#16 0xb7860b13 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#17 0xb7862150 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#18 0xb78654f0 in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#19 0xb7c0aece in gtk_tool_button_get_type () from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb785dab3 in g_cclosure_marshal_VOID__VOID ()
#21 0xb78523a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#22 0xb7860b13 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#23 0xb7862150 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#24 0xb78624c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#25 0xb7aa822c in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
#26 0xb7aa9a4c in _gtk_button_set_depressed ()
#27 0xb785dab3 in g_cclosure_marshal_VOID__VOID ()
#28 0xb7851d75 in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
#29 0xb78523a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#30 0xb7860769 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#31 0xb7862150 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#32 0xb78624c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#33 0xb7aa81a6 in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
#34 0xb7aa9115 in _gtk_button_paint () from /usr/lib/libgtk-x11-2.0.so.0
#35 0xb7b6902c in _gtk_marshal_BOOLEAN__BOXED ()
#36 0xb7851d75 in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
#37 0xb78523a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#38 0xb7860c9f in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#39 0xb7861ec3 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#40 0xb78624c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#41 0xb7c4b16f in gtk_widget_activate () from /usr/lib/libgtk-x11-2.0.so.0
#42 0xb7b67767 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#43 0xb7b67ba0 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#44 0xb7a0bb2d in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#45 0xb77744ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#46 0xb77774f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#47 0xb77777e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#48 0xb7b66e65 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#49 0x0805a025 in ?? ()
#50 0xb6e46ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#51 0x08054381 in ?? ()
Memory stat:
Images stat:___________Max memory consumed (MB)     : 0
Current memory consumed (MB) : 0
Max image used               : 0
Cur image used               : 0
Global mem stat
        Memory consumed :0 (MB)

 Goodbye...

jeremy@ubuntuserver:/$
```

---

### Post by bean1336 on 2006-03-29
[QUOTE=bored2k]I have made an avidemux 2.1_branch1 package using SVN. The avidemux creator is urging everyone to use the SVN instead of the old unstable package. I compiled this one for support with pretty much everything. It's a **LOT** better than the stable avidemux 2.0.42.

[http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html](http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html)[/QUOTE]


I successfully download the file to my desktop, but when I try to install it usiing konsole it tells me it cannot find the file...
Ive tried dpkg and apt-get install and both won't work, can I not save to my desktop?

---

### Post by pickarooney on 2007-01-21
Anyone know if this package works for Edgy or if there's an updated one which will?

---

### Post by SadaraX on 2007-01-21
Here is a link to a working DEB file for the latest version of Avidemux (2.3):

[http://ubuntuforums.org/showpost.php?p=1941290&postcount=9](http://ubuntuforums.org/showpost.php?p=1941290&postcount=9)

---

### Post by pickarooney on 2007-01-22
Quality! Thanks :)

---


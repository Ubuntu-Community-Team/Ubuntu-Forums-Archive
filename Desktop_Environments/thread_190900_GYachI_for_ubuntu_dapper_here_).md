---
title: "GYachI for ubuntu dapper here :)"
date: 2006-06-06
forum: Desktop Environments
---

### Post by loell on 2006-06-06
UPDATE: [GYachI-Sidetrack for fiesty]("http://ubuntuforums.org/showthread.php?t=431290")



[GYcachI for edgy]("http://www.ubuntuforums.org/showthread.php?t=289509")

recommended official download

[COLOR="Red"]**[COLOR="Red"][gyachi.sourceforge.net/download.shtml]("gyachi.sourceforge.net/download.shtml")[/COLOR]**[/COLOR] 

this package can now resolve dependencies...

------------------------------------------------------



previous deb package:

[**_[COLOR="Red"]Here[/COLOR]_**]("http://www.yourfilelink.com/get.php?fid=161405")
:)
or you can download the rpm package from gyachi homepage and convert it to deb package :)


Updated deb package built from CVS August 4, 2006
:)
Improvements: Tabbed Chat window ala Gaim, logs, and some bug fixes


download and install
_**[GYachI]("http://www.yourfilelink.com/get.php?fid=147714")**_
note: **Xubuntu ** users should install libgtkhtml2 before running GYachI
note: **Kubuntu** users should install libgtkhtml2 and ltdl3 before running GYachI




[http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")
About GYachE Improved (a.k.a. GYachI)

Welcome to the home of GyachE Improved (GyachI) program. This is a fork from Gyach Enhanced Yahoo! client for Linux operating systems. It was born purely out of impatience. Since there was no progress on Gyach Enhanced for about a year, a couple of impatient GYach Enhanced users decided to continue development of that client, fearing that original author Erica Andrews lost interest or abandoned project altogether. Therefore, in the true spirit of Open Source we, the developers, thought of simply "carrying on the torch".

This Yahoo! client for Linux operating system supports almost all of the features you would expect to find on the official Windows Yahoo! client: Voice chat, webcams, faders, 'nicknames', audibles, avatars, display images, and more. Yet, it remains very light-weight and memory-friendly. GyachE Improved uses Gtk-2 for its user interfaces (Gtk-2 2.0.6 or better required).

---

### Post by mumushi on 2006-06-06
i installed the deb package and it was successful no dependency problems but when i run it nothing happens.

---

### Post by loell on 2006-06-07
for those that have the same problem satarting gyachi, try rebooting

---

### Post by deega on 2006-06-07
You didn't happen to create a src or ppc deb, did ya?

---

### Post by Lizzy on 2006-06-07
Nothing happends, not after rebooting eighter :rolleyes:

The weird thing is that both the previous version and this version doesn't run on Dapper. The previous version run under Breezy.

---

### Post by jvictor on 2006-06-07
Its too complex an app for yahoo chat ! It looks more like an IDE to me ;)

---

### Post by pratzabrat on 2006-06-07
Is there an amd64 version somewhere?

---

### Post by copey02 on 2006-06-07
i am having trouble with the webcam feature. i have my webcam running fine. and starting to view my webcam through gyachi works fine, but once i hit broadcast it freezes up or tells me that i am instantly disconnected from the yahoo webcam server. any idea why this would happen?

---

### Post by Lizzy on 2006-06-07
i figured out why it didn't work. I had to remove the .yahoorc directory from my .home catalog :-D

---

### Post by loell on 2006-06-07
@copey02

do you still have webcam broadcasting problem?
what's the error message? this is a cvs version which is supposedly to solve the new
yahoo protocol for handling webcam broadcasting. the current 1.0.4 had some problems with that.

---

### Post by stanz on 2006-06-16
[quote=jvictor]Its too complex an app for yahoo chat ! It looks more like an IDE to me ;)[/quote] [LEFT][FONT=Comic Sans MS][SIZE=2]I second that...tho~ i'll give it a try.[/SIZE][/FONT] There's allot of options - I never dealt with...
[/LEFT]
   [FONT=Comic Sans MS][SIZE=2]like choosing which server, or ip addy's ? [/SIZE][/FONT] :-&
[FONT=Comic Sans MS][SIZE=2]My Thanks to the developers...  I didn't even need to reboot !
Quick Question tho.. I'm trying to add launcher to panal... where's the bin file?
I looked in */bin, usr/share *... did i miss it?
============ Newbie moment... i guess...
O~K...found it in "[I]/usr/local/share/applications/**GYachEImproved**", "dhaaaa".
[/I]and got a kewl icon in *"/pixmaps" *folder.... Now on to see if i can work the toys! [/SIZE][/FONT]

---

### Post by loell on 2006-06-16
i also admit that its more like a beatiful IDE than an IM app..
well, its a work in progress according to the developers :)

---

### Post by loell on 2006-06-16
:) its in

/usr/local/bin/gyachi

---

### Post by stanz on 2006-06-19
[quote=loell]:) its in /usr/local/bin/gyachi[/quote] 
Ha...geez, your right - but, what was i using that started it up?  chuckles...
Hey- I think its a kewl start &  i compliment the developers, for their efforts!!
where would we be without them?!!  =D>

---

### Post by shane2peru on 2006-07-08
I stumbled upon this thread, and gave it a whirl, wow!  It is nice.  I'm looking at all the options.  Do webcams work with this with yahoo?  and voice .  Thanks for the info, installed easy.

Shane

---

### Post by loell on 2006-07-08
yes, GyachI is  a yahoo messenger for linux that has the capability to use webcams, you can view, send, recieve webcam images :)

you can also use the voice chat room feature :)



however, pc to pc call which is in the new "yahoo mesenger with voice" in windows is sip base..

This feature is not yet included in the current version of GYachI.
but this might be included in the next version Gyachi-NG (next generation) :)

---

### Post by shane2peru on 2006-07-08
I did notice that it had all those features.  Great!!!  Does anyone know how to shut off the chat rooms.  I don't like them, and don't like them signing on as soon as I open the window.  I disconnect right away, but just don't like that feature at all.  Can it be disabled, or removed?  (Maybe this isn't the right place for this, sorry if it isn't.)

Shane

---

### Post by JoeG on 2006-07-08
You don't have to go to a chat room.  On the Yahoo! Login window, on the lower right, you'll find a checkbox for "no chat room".  Check it and there ya go.

---

### Post by fabertawe on 2006-07-09
> **pratzabrat said:**
> Is there an amd64 version somewhere?

I tried a --force-architecture install (bare in mind I'm a relative newbie ;) ). On running with Linux32 it grumbled about missing modules which I started manually installing from the Debian packages website. This worked for about three or four but I'm now stuck at this -

```
(gyachi:6231): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libubuntulooks.so:  cannot open shared object file: No such file or directory

(gyachi:6231): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to l oad image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so:  /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared objec t file: No such file or directory

(gyachi:6231): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gyachi:6231): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to l oad image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so:  /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared objec t file: No such file or directory

(gyachi:6231): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gyachi:6231): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to l oad image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so:  /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared objec t file: No such file or directory

(gyachi:6231): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gyachi:6231): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to l oad image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so:  /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared objec t file: No such file or directory

(gyachi:6231): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to l oad image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so:  /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared objec t file: No such file or directory

(gyachi:6231): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to l oad image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so:  /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared objec t file: No such file or directory

(gyachi:6231): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to l oad image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so:  /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared objec t file: No such file or directory

(gyachi:6231): Pango-WARNING **: No builtin or dynamically
loaded modules were found. Pango will not work correctly.
This probably means there was an error in the creation of:
  '/etc/pango/pango.modules'
You should create this file by running pango-querymodules.

(gyachi:6231): Pango-WARNING **: pango_shape called with bad font, expect ugly o utput

(gyachi:6231): Pango-WARNING **: pango_font_get_glyph_extents called with bad fo nt, expect ugly output

(gyachi:6231): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to l oad image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so:  /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared objec t file: No such file or directory
Segmentation fault

```

I'm running Ubuntu 6.06, AMD64-K8 kernel.

Anyone have any ideas as to what I can do to get this running or even if it's possible at all? I'll post to the 64bit users forum if it's inappropriate here.

Thanks ... Paul

---

### Post by loell on 2006-07-09
sorry i don't have amd64 computer,

i'm running a pretty old computer ;) 

you could compile gyachi from cvs, since all dependencies are in the repo :)

---

### Post by shane2peru on 2006-07-09
>  JoeG  	You don't have to go to a chat room. On the Yahoo! Login window, on the lower right, you'll find a checkbox for "no chat room". Check it and there ya go.

Thanks JoeG for the info.  Got it and that is better. I also deleted the chatroom from that line, so it couldn't connect.  

Shane

---

### Post by fabertawe on 2006-07-10
> **loell said:**
> sorry i don't have amd64 computer,

i'm running a pretty old computer ;) 

you could compile gyachi from cvs, since all dependencies are in the repo :)

Hi loell,

Amazingly I managed to compile version 1.04 :shock: 

Trouble is I have no voice or video :confused: I have the correct video device set and I know it works with other apps but nothing happens with this when I try to activate it. I have also been unable to hear voice in chat rooms but have not tried talking with it myself. I will keep fiddling but I think this is beyond my capabilities! It's a shame as I've still yet to find a messenger I can use my webcam with :-(

Paul

---

### Post by loell on 2006-07-10
i would suggest posting it to

[http://gyachi.sourceforge.net/forums.shtml]("http://gyachi.sourceforge.net/forums.shtml")

in the help section

maybe the developers can help you, and in turn help the project too with amd64 specifics :)

please don't give up just yet, i personally believe you can contribute feedback on gyachi with this problem [-o<

---

### Post by fabertawe on 2006-07-11
> **loell said:**
> i would suggest posting it to

[http://gyachi.sourceforge.net/forums.shtml]("http://gyachi.sourceforge.net/forums.shtml")

in the help section

maybe the developers can help you, and in turn help the project too with amd64 specifics :)

please don't give up just yet, i personally believe you can contribute feedback on gyachi with this problem [-o<

More good news... I got the webcam working!! \\:D/ 

Audio still doesn't work but I'm working on it ;-)

Paul

---

### Post by loell on 2006-07-11
yes, that good news, thanks for the feedback :)

---

### Post by fabertawe on 2006-07-11
Would you believe it, my desktop's knackered and it looks like I'll have to reinstall from an image. Trouble is I'll lose all the Gyachi stuff and have to start from scratch!

I'll start a new thread and see if anyone can help me restore my current setup first.

Paul

---

### Post by fabertawe on 2006-07-13
> **fabertawe said:**
> Would you believe it, my desktop's knackered and it looks like I'll have to reinstall from an image. Trouble is I'll lose all the Gyachi stuff and have to start from scratch!

I'll start a new thread and see if anyone can help me restore my current setup first.

Well I got no help with my desktop problem and had to reinstall ](*,) 

Anyway... now I can't compile Gyachi... I've no idea how I managed it last time! I've spent 4 hours on this today and I'm beaten. I'll have to keep using Windows for this, which saddens me no end.

Paul

---

### Post by loell on 2006-07-13
i don't know if you've tried this, 
but anyway :)

to automatically download dependencies use

   
    auto-apt run ./configure

---

### Post by fabertawe on 2006-07-14
> **loell said:**
> i don't know if you've tried this, 
but anyway :)

to automatically download dependencies use

   
    auto-apt run ./configure

I wish I'd known about this before now! I'd actually resolved all dependencies by installing one by one as I went along #-o 

Anyway... './configure' completes but I'm failing at 'make' with this output
```
paul@ubuntu:~/temp/gyachi/gyachi-1.0.4$ make
make  all-recursive
make[1]: Entering directory `/home/paul/temp/gyachi/gyachi-1.0.4'
Making all in intl
make[2]: Entering directory `/home/paul/temp/gyachi/gyachi-1.0.4/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/paul/temp/gyachi/gyachi-1.0.4/intl'
Making all in po
make[2]: Entering directory `/home/paul/temp/gyachi/gyachi-1.0.4/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/paul/temp/gyachi/gyachi-1.0.4/po'
Making all in gyvoice
make[2]: Entering directory `/home/paul/temp/gyachi/gyachi-1.0.4/gyvoice'
if gcc -DHAVE_CONFIG_H -I. -I/home/paul/temp/gyachi/gyachi-1.0.4/gyvoice -I.. -DLOCALEDIR=\"/usr/local/share/locale\"  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/alsa      -g -O2  -Wall -Wno-pointer-sign -funsigned-char -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.c: In function ‘main’:
main.c:61: warning: passing argument 2 of ‘gtk_tree_view_set_model’ from incompatible pointer type
main.c:72: warning: passing argument 2 of ‘g_timeout_add’ from incompatible pointer type
if gcc -DHAVE_CONFIG_H -I. -I/home/paul/temp/gyachi/gyachi-1.0.4/gyvoice -I.. -DLOCALEDIR=\"/usr/local/share/locale\"  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/alsa      -g -O2  -Wall -Wno-pointer-sign -funsigned-char -MT support.o -MD -MP -MF ".deps/support.Tpo" -c -o support.o support.c; \
        then mv -f ".deps/support.Tpo" ".deps/support.Po"; else rm -f ".deps/support.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I/home/paul/temp/gyachi/gyachi-1.0.4/gyvoice -I.. -DLOCALEDIR=\"/usr/local/share/locale\"  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/alsa      -g -O2  -Wall -Wno-pointer-sign -funsigned-char -MT interface.o -MD -MP -MF ".deps/interface.Tpo" -c -o interface.o interface.c; \
        then mv -f ".deps/interface.Tpo" ".deps/interface.Po"; else rm -f ".deps/interface.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I/home/paul/temp/gyachi/gyachi-1.0.4/gyvoice -I.. -DLOCALEDIR=\"/usr/local/share/locale\"  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/alsa      -g -O2  -Wall -Wno-pointer-sign -funsigned-char -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
        then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
callbacks.c: In function ‘on_about1_activate’:
callbacks.c:113: warning: passing argument 1 of ‘gtk_message_dialog_new_with_markup’ from incompatible pointer type
callbacks.c: In function ‘on_gyv_button_on_clicked’:
callbacks.c:132: warning: passing argument 1 of ‘gtk_widget_set_sensitive’ from incompatible pointer type
callbacks.c: In function ‘on_gyv_button_off_clicked’:
callbacks.c:142: warning: passing argument 1 of ‘gtk_widget_set_sensitive’ from incompatible pointer type
if gcc -DHAVE_CONFIG_H -I. -I/home/paul/temp/gyachi/gyachi-1.0.4/gyvoice -I.. -DLOCALEDIR=\"/usr/local/share/locale\"  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/alsa      -g -O2  -Wall -Wno-pointer-sign -funsigned-char -MT afl.o -MD -MP -MF ".deps/afl.Tpo" -c -o afl.o afl.c; \
        then mv -f ".deps/afl.Tpo" ".deps/afl.Po"; else rm -f ".deps/afl.Tpo"; exit 1; fi
In file included from wine/winbase.h:5,
                 from afl.c:24:
wine/winnt.h:625:2: error: #error You need to define a CONTEXT for your CPU
In file included from wine/winbase.h:5,
                 from afl.c:24:
wine/winnt.h:628: error: syntax error before ‘*’ token
wine/winnt.h:628: warning: type defaults to ‘int’ in declaration of ‘PCONTEXT’
wine/winnt.h:628: warning: data definition has no type or storage class
wine/winnt.h:754:2: error: #error You need to define DEFINE_REGS_ENTRYPOINT macros for your CPU
wine/winnt.h:765:3: error: #error You must define GET_IP for this CPU
wine/winnt.h:1021: error: syntax error before ‘PCONTEXT’
wine/winnt.h:1021: warning: no semicolon at end of struct or union
wine/winnt.h:1022: warning: type defaults to ‘int’ in declaration of ‘EXCEPTION_POINTERS’
wine/winnt.h:1022: warning: type defaults to ‘int’ in declaration of ‘PEXCEPTION_POINTERS’
wine/winnt.h:1022: warning: data definition has no type or storage class
wine/winnt.h:1034: error: syntax error before ‘PCONTEXT’
In file included from wine/winbase.h:5,
                 from afl.c:24:
wine/winnt.h:1048: error: syntax error before ‘ExceptionInfo’
wine/winnt.h:1051: error: syntax error before ‘epointers’
In file included from afl.c:24:
wine/winbase.h:1342: error: syntax error before ‘CONTEXT’
wine/winbase.h:1481: warning: type defaults to ‘int’ in declaration of ‘CONTEXT’wine/winbase.h:1481: error: syntax error before ‘*’ token
afl.c: In function ‘ACM_GetStream’:
afl.c:46: warning: cast to pointer from integer of different size
afl.c: In function ‘acmDriverAddA’:
afl.c:73: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverEnum’:
afl.c:134: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverID’:
afl.c:157: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverOpen’:
afl.c:232: warning: cast from pointer to integer of different size
afl.c: In function ‘MSACM_UnregisterDriver’:
afl.c:303: warning: cast from pointer to integer of different size
afl.c: In function ‘MSACM_GetDriverID’:
afl.c:342: warning: cast to pointer from integer of different size
afl.c: In function ‘MSACM_GetDriver’:
afl.c:350: warning: cast to pointer from integer of different size
afl.c: In function ‘MSACM_GetObj’:
afl.c:358: warning: cast to pointer from integer of different size
afl.c: In function ‘acmStreamOpen’:
afl.c:414: warning: cast from pointer to integer of different size
afl.c:426: warning: cast from pointer to integer of different size
afl.c:464: warning: cast from pointer to integer of different size
afl.c:471: warning: cast from pointer to integer of different size
afl.c:493: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamClose’:
afl.c:517: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamConvert’:
afl.c:564: warning: cast from pointer to integer of different size
afl.c:564: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamPrepareHeader’:
afl.c:612: warning: cast from pointer to integer of different size
afl.c:612: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamReset’:
afl.c:650: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamSize’:
afl.c:693: warning: cast from pointer to integer of different size
afl.c:693: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamUnprepareHeader’:
afl.c:744: warning: cast from pointer to integer of different size
afl.c:744: warning: cast from pointer to integer of different size
make[2]: *** [afl.o] Error 1
make[2]: Leaving directory `/home/paul/temp/gyachi/gyachi-1.0.4/gyvoice'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/temp/gyachi/gyachi-1.0.4'
make: *** [all] Error 2
```

You obviously know what you're doing, perhaps you can suggest something from looking at the output above? Don't suggest I switch to the 386 kernel ;-) although that would solve all my problems!

Thanks loell for all your help. 

Paul

---

### Post by loell on 2006-07-14
:-k i'm also puzzled, 
you've had successfuly compiled it before, 
but now you can't pass trhough in MAKE , i'm not good in analyzing "MAKE".
but i've already posted this in gyachi forum, :) 
hope someone can help us there.. we'll just have to wait for any response..
just hang in there :mrgreen:

---

### Post by fabertawe on 2006-07-14
> **loell said:**
> :-k i'm also puzzled, 
you've had successfuly compiled it before, 
but now you can't pass trhough in MAKE , i'm not good in analyzing "MAKE".
but i've already posted this in gyachi forum, :) 
hope someone can help us there.. we'll just have to wait for any response..
just hang in there :mrgreen:

Thanks for doing that, I should have done it myself :oops: but I've been very busy lately 8-[ 

Could it have been because I had some necessary 32bit libs already installed? Also, I didn't get the web cam working (64bit) until **after** I'd installed chroot and played with running your 32bit Gyachi.

I will check out the Gyachi forums, thanks loell :)

---

### Post by sacksank on 2006-07-16
If anyone can give me the how-to to install gyachI on Dapper AMD64 would be much appriciated.. as I'm on my way to a full convert to UBUNTU on my new lappy.. thanks again.

---

### Post by fabertawe on 2006-07-16
> **sacksank said:**
> If anyone can give me the how-to to install gyachI on Dapper AMD64 would be much appriciated.. as I'm on my way to a full convert to UBUNTU on my new lappy.. thanks again.

I'm still working on it and haven't given up all hope (just yet!)... it won't be 64bit though as one of the developers has told me the audio part is pure 32bit and that's what my attempt to make is failing on. If I can compile a static 32bit version then it can be run with the linux32 wrapper but I'm a novice at this so don't hold your breath ;-)

Loell's version available from the first page does work under chroot. There's a how-to somewhere for it, just do a forum search. I had no problem installing chroot and loell's Gyachi worked under that. Personally, I don't want to jump through all those hoops and install a load of stuff just to run the odd bit of software so I haven't installed chroot this time.

Paul

---

### Post by loell on 2006-07-16
I do hope that 64bit compilation issues of gyachi will be resolved soon..

---

### Post by fabertawe on 2006-07-17
> **loell said:**
> I do hope that 64bit compilation issues of gyachi will be resolved soon..

Loell, would it be at all possible for you to compile a static version of your 32bit .deb? Seeing as **you** know what you're doing :D 

Cheers ... Paul

---

### Post by loell on 2006-07-17
unfortunately static compilation may not seem as easy as i percieve it to be
i did inquire about this, and they say you will have to touch the makefiles and configure scripts

i thought it was just a simple command like

./configure --enable-static



but i'll try to inquire further on this :)

---

### Post by fabertawe on 2006-07-17
> **loell said:**
> unfortunately static compilation may not seem as easy as i percieve it to be
i did inquire about this, and they say you will have to touch the makefiles and configure scripts

i thought it was just a simple command like

./configure --enable-static

but i'll try to inquire further on this :)

That's very much appreciated, thanks :-D

---

### Post by mumushi on 2006-07-21
I installed gyachi on my Xubuntu and got this error message > gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory


Where could i dl this dependency? Your help is greatly appreciated. Thanks!

---

### Post by loell on 2006-07-21
in synaptic just search for libgtkhtml2-0 and install it :)

---

### Post by jis on 2006-07-26
> **loell said:**
> hi, this a deb package made the latest cvs as of June 7,  2006
enjoy, :D 

[http://www.420megs.com/users/gyachi/gyachi_1.0.4-1_i386.deb]("http://www.420megs.com/users/gyachi/gyachi_1.0.4-1_i386.deb")


I installed it, but when I run it I get following: "gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open sha red object file: No such file or directory." (Note: I am using Xubuntu, which uses Xfce instead of Gnome.) I have no libgtkhtml package installed. Should I install libgtkhtml2 or the newer one?

---

### Post by loell on 2006-07-26
yes you should install libgtkhtml2..

---

### Post by jis on 2006-07-27
> **loell said:**
> yes you should install libgtkhtml2..

I installed that and something else, and I can now run the program, but now I get this in the Chat tab in the beginning:
"Plugin Loaded:  'Blowfish-Internal' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better".

What is this plugin for? I do not find GpgMe and GPG in repositories so I do not know hot to install them.

---

### Post by sabitha on 2006-07-27
just install libgpgme6
code :
$ sudo apt-get install libgpgme6

and then create a simbolik link because gyach need libgpgme.11.so

$ sudo ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so.11
$ sudo ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so

hope this help

---

### Post by jis on 2006-07-27
> **sabitha said:**
> just install libgpgme6
code :
$ sudo apt-get install libgpgme6

and then create a simbolik link because gyach need libgpgme.11.so

$ sudo ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so.11
$ sudo ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so

hope this help

I have already installed libgpgme11 and have /usr/lib/libgpgme.so.11 but not /usr/lib/libgpgme.so. Command "ls -al /usr/lib/libgpg*" gives:
"lrwxrwxrwx 1 root root     21 2006-06-09 18:37 /usr/lib/libgpg-error.so.0 -> libgpg-error.so.0.1.4
-rw-r--r-- 1 root root  10292 2005-10-25 06:25 /usr/lib/libgpg-error.so.0.1.4
lrwxrwxrwx 1 root root     26 2006-07-27 18:49 /usr/lib/libgpgme-pthread.so.11 -> libgpgme-pthread.so.11.5.0
-rw-r--r-- 1 root root 128484 2005-10-25 07:35 /usr/lib/libgpgme-pthread.so.11.5.0
lrwxrwxrwx 1 root root     18 2006-07-27 18:49 /usr/lib/libgpgme.so.11 -> libgpgme.so.11.5.0
-rw-r--r-- 1 root root 125828 2005-10-25 07:35 /usr/lib/libgpgme.so.11.5.0
"

Should I uninstall libgpgme11?

---

### Post by sabitha on 2006-07-27
i dont know but i think u can remove first and then install libgpgme6 like i say.:smile:

---

### Post by jis on 2006-07-27
Thanks, sabitha. Now it loads the plugins without errors.

---

### Post by PokerFacePenguin on 2006-07-28
I just came across the GYachi program and downloaded 1.0.4 (i am running dapper/kubuntu).

I sudo ./configure and get the following:

```


*** Edited for brevity ***
.
.
.

checking for LC_MESSAGES... yes
checking for bison... no
checking for CFPreferencesCopyAppValue... (cached) no
checking for CFLocaleCopyCurrent... (cached) no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for sed... /bin/sed
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for X... no
configure: error: X development libraries not found

```

the config.log says: 
```


*** Edited for Brevity ***
.
.
.

#define HAVE_WCHAR_T 1
#define HAVE_WCSLEN 1
#define HAVE_WINT_T 1
#define HAVE___ARGZ_COUNT 1
#define HAVE___ARGZ_NEXT 1
#define HAVE___ARGZ_STRINGIFY 1
#define HAVE___FSETLOCKING 1
#define ICONV_CONST 
#define INTDIV0_RAISES_SIGFPE 1
#define PACKAGE "gyachi"
#define PACKAGE_BUGREPORT "gyachi-help@lists.sourceforge.net"
#define PACKAGE_NAME "gyachi"
#define PACKAGE_STRING "gyachi 1.0.4"
#define PACKAGE_TARNAME "gyachi"
#define PACKAGE_VERSION "1.0.4"
#define STDC_HEADERS 1
#define VERSION "1.0.4"
#define X_DISPLAY_MISSING 1
#endif
#ifdef __cplusplus
extern "C" void std::exit (int) throw (); using std::exit;

configure: exit 1

```

It won't compile for me so far...i'm stumped...anyone have any ideas?

---

### Post by loell on 2006-07-28
can you check if you  have libglib1.2-dev?
also make sure that you downloaded the source via cvs, because i  think it has noticeable bugs if you downloaded in the normal downloadable source

do you have problems in installing the deb package from the first post?

[http://www.420megs.com/users/gyachi/gyachi_1.0.4-1_i386.deb]("http://www.420megs.com/users/gyachi/gyachi_1.0.4-1_i386.deb")

---

### Post by PokerFacePenguin on 2006-07-28
It sure would be easier to dpkg that .deb, but 420 says no external linking to that site....i even signed up but do not see user gyachi...

In answer to your question about glib1.2-dev....no i found it to be not installed.....i have to wonder what else i will be missing and how far I will get after I install this glib1.2-dev.........

---

### Post by loell on 2006-07-28
sorry for the trouble i'll try to fix the link..
the free account was deleted..

---

### Post by PokerFacePenguin on 2006-07-28
I appreciate it.  It will probably make things go alot smoother for me.
Are you going to use the same username/link when you recreate?

---

### Post by loell on 2006-07-28
no i probably won't, anyway here is one link

[GYachI]("http://www.yourfilelink.com/get.php?fid=144411")
:KS

---

### Post by PokerFacePenguin on 2006-07-28
Thanks, that link is downloading.. now if dpkg will do it's thing hopefully I will be set.

---

### Post by PokerFacePenguin on 2006-07-28
Hmmm....I installed the .deb and it won't run...so I sudo gyachi and I get:

> 
sudo gyachi

gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

so I install libgtkhtml-2

then 

sudo gyachi
gyachi: error while loading shared libraries: libltdl.so.3: cannot open shared object file: No such file or directory


is this app targeted at GNOME?  (I run Kubuntu instead of Ubuntu)
I am wondering if there are going to be a million more dependencies...giving this install of libltdl a try to see what happens...



Same thing happened to me as mumushi...I installed it, and rebooted per suggestion..gyachi still wont run...


**** Edit  ***

Ok, i installed ltdl3 and ltdl3-dev and it runs now....good deal...thanks for the deb

---

### Post by loell on 2006-07-28
no problem, glad that i could help :)
yes, unfortunately this is targeted to ubuntu
i'm still trying and learning to make the package resolve their dependencies regardless of the desktop environment.

---

### Post by PokerFacePenguin on 2006-07-29
Ok, the program starts...I ended up having to change ownership and permissions of ~/.yahoorc and subordinate directories to my username to get it to run....no problem there....but here is the rub...

when I run gyachi, it complains in the terminal window but starts the program.  Here is what it says:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gyachi:8303): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

(gyachi:8303): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(gyachi:8303): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(gyachi:8303): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gyachi:8303): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gyachi:8303): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(gyachi:8303): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setBrush: Will be reset by begin()
QPainter::setBrush: Will be reset by begin()
QPainter::setPen: Will be reset by begin()
QPainter::setWorldMatrix: Will be reset by begin()

(gyachi:8303): Gdk-CRITICAL **: gdk_pixmap_foreign_new_for_display: assertion `(anid != 0)' failed

(gyachi:8303): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

(gyachi:8303): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

Now after I login to my yahoo account nothing else pops up in that terminal window.

But if I start my webcam (and I can see it myself..it finds /dev/video0)
the terminal window complains with :

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I can see the webcam, but nobody else can (even after I broadcast and allow anyone with permissions)

What dependencies/libs do you think I am missing?

---

### Post by loell on 2006-07-29
i think all dependencies were already satisfied, the permission with .yahoorc that you mention maybe cause by executing it as "sudo gyachi" base in your previous post.
now that directory permission is ok :)

there might be a problem accessing the webcam device,
i'm not sure as to what is the cause of the problem, but before clicking the broadcasting button try unchecking the "Automaticaly deny anonymous user" check box and check "Automatically allow All users to view" check box then click broadcasting button, if it says broadcasting above the close button then see if other users can view your webcam.

---

### Post by PokerFacePenguin on 2006-07-29
Got it going.  Thanks all.

---

### Post by wthww on 2006-07-30
GREAT JOB
works wonderfull. im completely linux now :P

---

### Post by fireedo on 2006-08-03
Ok I succesfully installed gyachi but why I cant login.....I can login using GAIM but I cant login with gyachi
any idea?
thanx

---

### Post by loell on 2006-08-03
you need to choose the server from the list in the login dailog box.

---

### Post by fireedo on 2006-08-03
ah...yes u right....sorry for this :)

---

### Post by loell on 2006-08-03
:p

---

### Post by fireedo on 2006-08-03
the new cvs build has a lot of bug fixed ....can u make the new one?

---

### Post by loell on 2006-08-03
i'm still testing it, when the "send instant message window" is fixed then i'll make an update :) yes, it has lot of improvements :)

---

### Post by loell on 2006-08-03
Updated deb package built from CVS August 4, 2006
:)
Improvements: Tabbed Chat window ala Gaim, logs, and some bug fixes

**_[GYachI]("http://www.yourfilelink.com/get.php?fid=147714")_**

---

### Post by sabitha on 2006-08-04
what u mean u cant login
did u place your username, password and server with right
like this :

---

### Post by sabitha on 2006-08-04
> Improvements: Tabbed Chat window ala Gaim, logs, and some bug fixes :-k i didnt see that

---

### Post by sabitha on 2006-08-04
my fault ...... #-o 
that because gyahi-plugins-xmms after i remove that first and then install again the curent cvs from you i see that now.
nice job :D

---

### Post by sabitha on 2006-08-05
all i want to know now is the voice chat work or not because i just hear people talking on room but i can't talk on that room same like voice on private massage.

---

### Post by loell on 2006-08-05
yes, in fact i was just talking on Linux, FreeBSD, Solaris:1 room just awhile ago.

---

### Post by toallpointswest on 2006-08-08
Can anyone help me with GyachI? Everytime I go to Profile a user, GyachI crashes. Doesn't matter which browser setting I use, it's all the same. Help!!

---

### Post by loell on 2006-08-08
have you tried using, the option "use builtin profile (window)"?
i think you woul have a running or open browser for the profile to be shown in the browser. ie, if you set the profile to be shown on mozilla browser, then there should be a running browser for the profile to be shown.

if the crashing continues.
can you also execute this in the console? and post the output here.

---

### Post by toallpointswest on 2006-08-09
Here is the console output:

```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
Error opening PCM device default
*** glibc detected *** free(): invalid pointer: 0x0875d430 ***
Aborted (core dumped)

```

---

### Post by loell on 2006-08-09
this might be a bug in gyachi yahoo profile function.

---

### Post by cptnapalm on 2006-08-09
auto-apt run ./configure

Holy Debian, Batman!  ...and I thought installing stuff couldn't get any easier...  Whoever came up with apt and its siblings really and truly deserves a life of eternal bliss...

---

### Post by loell on 2006-08-09
lol :D

---

### Post by toallpointswest on 2006-08-09
> **cptnapalm said:**
> auto-apt run ./configure

Holy Debian, Batman!  ...and I thought installing stuff couldn't get any easier...  Whoever came up with apt and its siblings really and truly deserves a life of eternal bliss...

What does that command do?

---

### Post by loell on 2006-08-10
> **toallpointswest said:**
> What does that command do?
basically, when you build from source, it installs all the necessary dependencies

---

### Post by elbowgeek on 2006-08-10
Hi all...

Just stumble on this thread and installed it.  It runs fine, and I filled in my username and password.  However I'm confused by the server and port options.  Which do I use?  It looks great, and may be the answer to my dream of a fully functioning Yahoo chat client on Linux.

Many thanks :-)

---

### Post by elbowgeek on 2006-08-10
Just to give an idea of what happens when I try to log on, it appears as though it connects, but then immediately kicks me out.  This appears in the chat window that comes up:

```
[10/08/06 03:02:06]      CONNECTED: type /help for help

Current Buddy List: antiquesetc18, callieaunt1965, snugradio, strawberry_pocky_shu   (friends online in RED)


  ** You have been disconnected from Yahoo! [ Error receiving from socket: 0
 ] **

```

Any ideas on what this could be?

Cheers :-)

---

### Post by elbowgeek on 2006-08-10
Never mind, it just occurred to me that I'm logged on using Trillian at work, which doesn't relinquish the Yahoo connection, so it's probably merely that.  But if anyone has any other suggestions or tips for better use of this great-looking program, I'd appreciate it.

Cheers

---

### Post by loell on 2006-08-10
to autoreconnect try on the setup dailog --> options tab --> check "autoreconnect if disconnected"
:)

and a tip, for better navigation in the pm window or tab, their is a little arrow between the save button and the ignore button, that little arrow is actually a menu, for webcam invitation, or view webcam and more :)

---

### Post by pneaveill on 2006-08-10
> **loell said:**
> no i probably won't, anyway here is one link

[GYachI]("http://www.yourfilelink.com/get.php?fid=144411")
:KS
Loell, wanted to say thanks for the link. First time I was able to run gyachi.

Two thumbs up

---

### Post by loell on 2006-08-10
your welcome, though all credits will go to the developers :)
namely Stefan Sikora, Zoltan csala, Greg hosler :)

you might want to also try the recently updated deb package from the first post..

---

### Post by pneaveill on 2006-08-10
Dumb question, but which post number? Ihave 1.0.4 from yours. Is there a better *.deb?

---

### Post by loell on 2006-08-10
still both would be 1.0.4, i'm following closely the developments of thier cvs.

the very first post, at page 1

---

### Post by pneaveill on 2006-08-10
Am I missing something or is the file the exact same for #1 and #84? I tried download #1 as suggested and it told me it was already installed.

---

### Post by loell on 2006-08-10
thats because both have the same name, you must uninstall gyachi that you downloaded from the link in #84 post, before installing gyachi from the #1 post.

---

### Post by pneaveill on 2006-08-10
Check

---

### Post by bonjun on 2006-08-12
i install the package and reboot,,then at terminal i run gyachi and it says 

> ~$ gyachi
gyachi: error while loading shared libraries: libltdl.so.3: cannot open shared object file: No such file or directory


what's wrong... i was able to install this properly on breezy, i'm on dapper now

---

### Post by loell on 2006-08-12
you need to install,   libltdl3 
are you in kubuntu?

---

### Post by bonjun on 2006-08-12
> **loell said:**
> you need to install,   libltdl3 
are you in kubuntu?

nope, ubuntu only

---

### Post by loell on 2006-08-12
ok.. that's odd though :-k  you're the first to require libltdl3 in ubuntu with gyachi. do update me on your install :)

---

### Post by bonjun on 2006-08-12
it works now,,, with automatix, selected java installation, i saw libltdl3 was being installed,, and when i launched gyachi at terminal it works,,,,
thanks.......

---

### Post by bonjun on 2006-08-12
i don't know why my ubuntu needs libltdl3, as you have said on the your first post only, kubuntu needs it.... 
anyway why bother.. :) my gyachi works now... and thanks a lot...

---

### Post by loell on 2006-08-12
lol.. well np.. :)

---

### Post by toallpointswest on 2006-08-12
> **cptnapalm said:**
> auto-apt run ./configure

Holy Debian, Batman!  ...and I thought installing stuff couldn't get any easier...  Whoever came up with apt and its siblings really and truly deserves a life of eternal bliss...

Drat that didn't work.
```
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
/usr/bin/auto-apt: line 115: type: ./configure: not found
E: Exec ./configure failed, auto-apt failed

```

---

### Post by loell on 2006-08-12
are you sure you have ./configure in the current source directory?

---

### Post by dayz on 2006-08-15
I have installed gyachi on my kubuntu dapper
when I start, its splash but disappear and
I get this error on terminal

```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gyachi:4745): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(gyachi:4745): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(gyachi:4745): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(gyachi:4745): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(gyachi:4745): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(gyachi:4745): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(gyachi:4745): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(gyachi:4745): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap
```

anyone can help me! please....[-o<

---

### Post by loell on 2006-08-16
oh my, i haven't seen this kind of error before
but have you installed ltdl3? in Kubuntu?

---

### Post by sabitha on 2006-08-24
can u make new version 1.0.5
i see the new version on site [http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)

---

### Post by loell on 2006-08-24
sure, :)

[http://www.yourfilelink.com/get.php?fid=160707]("http://www.yourfilelink.com/get.php?fid=160707")

pls inform me if it runs fine or not , seems like starting a new howto thread is nice idea for the new version.

---

### Post by GStubbs43 on 2006-08-24
1.0.5 Works fine here, after I had installed 1.0.4 from the first post, which also went fine, then uninstalled it, and finally installed 1.0.5. :D Basically, all I'm saying is: "No problems here!"

---

### Post by loell on 2006-08-24
thanks, there's very little differnce between 1.0.4 cvs from the first post and version 1.0.5 , the most obvious improvement between them is the enhanced caplet support, clicking the exit button will not terminate gyachi, instead it just remains in the system tray, its a feature implemented by many IMs , if you would like to really terminate the program, there is a quit item in the connection menu.

---

### Post by vasimakhtar on 2006-08-24
Hello,
Can you help me to install Gyachi? on dapper
thanks

---

### Post by loell on 2006-08-24
> **vasimakhtar said:**
> Hello,
Can you help me to install Gyachi? on dapper
thanks

what's seems to be the problem of your installation?

---

### Post by fabertawe on 2006-08-25
> **loell said:**
> sure, :)

[http://www.yourfilelink.com/get.php?fid=160707]("http://www.yourfilelink.com/get.php?fid=160707")

pls inform me if it runs fine or not , seems like starting a new howto thread is nice idea for the new version.

Hi Loell my friend :) ....well guess what, I finally have it working on amd-64 :shock: 

It was quite a struggle, so much so in fact there is no way I can even write a mini how-to! I first installed all the various bits (including plugins) of 1.0.5 from the Gyachi downloads (before you posted yours!), this wouldn't work "as is" of course :roll: .. I then compiled 1.0.5 **as 32bit** but had to omit the webcam (the only thing I really need!) and plugins as I couldn't figure out how to compile them #-o ...anyway, after installing a few 32bit libs and making a ton of links I now have working Gyachi with webcam :biggrin: 

I'm going to keep at it and hopefully one day (far in the future no doubt!) I will be able to just compile the whole thing with little fuss.

Cheers ... Paul

---

### Post by fabertawe on 2006-08-25
> **loell said:**
> seems like starting a new howto thread is nice idea for the new version.

Is it possible to just change the title of the thread to "GYachI for ubuntu dapper here"? You may end up answering the same questions all over again ;)

Paul

---

### Post by loell on 2006-08-25
I'm very happy for you Paul :KS 

so there is hope then for 64 bit users, i hope you can sort it out on how you did it, and maybe you can compose a "How to" for this in the near future :) 

your right about the thread title , i'll try to ask a forum staff if its possible to make a slight change of the title..

---

### Post by sabitha on 2006-08-25
v1.0.5 fine but why xmms status missing can u add the plugins again like previous version:D

---

### Post by loell on 2006-08-26
ok, pls try [This]("http://www.yourfilelink.com/get.php?fid=161405")
perhaps i missed something before..

---

### Post by Lizzy on 2006-08-26
Hi, i just installed the latest version and it works just fine. Great job :-D! There's only one thing i can't get to work. My avatar/picture. I don't know what i'm doing wrong, but i can't add a picture or an avatar at all. When i try to add my picture it tells me that it can't resize it to a 96/96 .png, even if this pic has the correct size and file-format :rolleyes: :confused: ??? What am i doing wrong, or is there a "trick" to get this work??


Thx Lizzy

---

### Post by sabitha on 2006-08-26
> Hi, i just installed the latest version and it works just fine. Great job ! There's only one thing i can't get to work. My avatar/picture. I don't know what i'm doing wrong, but i can't add a picture or an avatar at all. When i try to add my picture it tells me that it can't resize it to a 96/96 .png, even if this pic has the correct size and file-format   ??? What am i doing wrong, or is there a "trick" to get this work??

install imagemagick to use that
$ sudo apt-get install imagemagick

---

### Post by sabitha on 2006-08-26
great job loel for the last but thats mean downgrading the package
all fine

---

### Post by Lizzy on 2006-08-26
> **sabitha said:**
> install imagemagick to use that
$ sudo apt-get install imagemagick


Thank you ever so much for your help, that worked perfectly :D

---

### Post by loell on 2006-08-26
> **sabitha said:**
> great job loel for the last but thats mean downgrading the package
all fine

i forgot the convention part of packaging ;) 
i just hope that an ubuntu MOTU( Masters of The Universe) can build gyachi soon :)

---

### Post by fabertawe on 2006-08-27
> **loell said:**
> i just hope that an ubuntu MOTU( Masters of The Universe) can build gyachi soon :)

I hope the pressure of being MOGFU (Master of GYachi for Ubuntu) isn't proving too much ;) Keep up the good work :)

---

### Post by loell on 2006-08-27
> **fabertawe said:**
> I hope the pressure of being MOGFU (Master of GYachi for Ubuntu) isn't proving too much ;) Keep up the good work :)

LoL, :biggrin:

---

### Post by Psquared on 2006-08-30
I get this error when i run gyachi:

GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:
libgpgme.so.11: cannot open shared object file: No such file or directory
Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
**** Plugin '/usr/local/share/gyachi/plugins/gyachimcrypt.so' could not be loaded because of an error:
libmcrypt.so.4: cannot open shared object file: No such file or directory
Location: /usr/local/share/gyachi/plugins/gyachimcrypt.so
** Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'GyachI-XMMS' 
 Loaded 3 plugins from '/usr/local/share/gyachi/plugins'.


I'm using Dapper with lots of extras from automatix. AMD cpu 512 mb of memory. (its an older amd cpu)

---

### Post by loell on 2006-08-30
so, your system is 64 bit then?
please consult [Fabertawe]("http://ubuntuforums.org/member.php?u=130067")

as he is the only 64 bit user i know, who had succesfully run gyache-improved on a 64 bit computer.

unfortunately gyachi does not run on a 64 bit computer if it is not tweaked.

---

### Post by sabitha on 2006-08-30
> **Psquared said:**
> I get this error when i run gyachi:

GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:
libgpgme.so.11: cannot open shared object file: No such file or directory
Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
**** Plugin '/usr/local/share/gyachi/plugins/gyachimcrypt.so' could not be loaded because of an error:
libmcrypt.so.4: cannot open shared object file: No such file or directory
Location: /usr/local/share/gyachi/plugins/gyachimcrypt.so
** Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'GyachI-XMMS' 
 Loaded 3 plugins from '/usr/local/share/gyachi/plugins'.


I'm using Dapper with lots of extras from automatix. AMD cpu 512 mb of memory. (its an older amd cpu)

install libgpgme6 & libmcrypt4 with this :
$ sudo apt-get install libgpgme6 libmcrypt4

hope this can solves the problem
but without those plugins gyachi still can run fine

---

### Post by Psquared on 2006-08-30
Hey thanks for the help. Are those files in universe repos or do I need backports? Also, will GYachi do photo sharing? (like Yahoo Messenger?)

Thanks

---

### Post by loell on 2006-08-30
with regards to photo sharing, its currently being develop, the lead developer wants to implement a drad n drop function similar to windows YM.

---

### Post by Psquared on 2006-08-30
> **sabitha said:**
> install libgpgme6 & libmcrypt4 with this :
$ sudo apt-get install libgpgme6 libmcrypt4

hope this can solves the problem
but without those plugins gyachi still can run fine

that helped; now I get this:

GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:
libgpgme.so.11: cannot open shared object file: No such file or directory
Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Plugin Loaded:  'MCrypt' 
 Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'GyachI-XMMS' 
 Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.

So I've got 4 plugins now instead of 3. I found an rpm for Mandriva for gyachigpgme but no .deb. libgpgme6 is installed.

---

### Post by loell on 2006-08-30
My bad, photo sharing is already implemented, though not so polished

its in "Tools" menu --> Browse my photo albums.

---

### Post by sabitha on 2006-09-03
> **Psquared said:**
> that helped; now I get this:

GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:
libgpgme.so.11: cannot open shared object file: No such file or directory
Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Plugin Loaded:  'MCrypt' 
 Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'GyachI-XMMS' 
 Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.

So I've got 4 plugins now instead of 3. I found an rpm for Mandriva for gyachigpgme but no .deb. libgpgme6 is installed.

:-k maybe this help
you need make a link to /usr/lib/libgpgme.so.6.3.7
$ sudo ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so.6
$ sudo ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so

---

### Post by loell on 2006-09-04
Good news :)

official GYachI deb package for ubuntu dapper is now in gyachi homepage,

that way ubuntu users can now download from sourceforge

[http://gyachi.sourceforge.net/download.shtml]("http://gyachi.sourceforge.net/download.shtml")

this package can now resolve dependencies :)

---

### Post by Seryozha on 2006-09-04
i got the deb from the sourceforge site and i installed all dependencys but i get gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory
when i am trying to load the app.  i checked and i do have the libgtkhtml-2 installed

---

### Post by loell on 2006-09-04
hmm, strange.. have you uninstalled the previous deb before installing the new one?

---

### Post by Seryozha on 2006-09-04
i never had a previous one

---

### Post by loell on 2006-09-04
hi seryozha,

can you try this deb package instead, and see if this package work for you?

[http://www.yourfilelink.com/get.php?fid=161405]("http://www.yourfilelink.com/get.php?fid=161405")

---

### Post by pneaveill on 2006-09-05
> **loell said:**
> hi seryozha,

can you try this deb package instead, and see if this package work for you?

[http://www.yourfilelink.com/get.php?fid=161405](http://www.yourfilelink.com/get.php?fid=161405)
Looked a ways back on this thread, but not seeing it. Is gyachi supposed to have voice yet? Or am I missing something?

Please inform

====================
Update: did not play around enough with it and i found it. To all the people who worked so hard on this thing -- congrats!!

---

### Post by loell on 2006-09-05
it supports room voice chat

---

### Post by pneaveill on 2006-09-06
Loell,
Yes. It was one of those newbie error things. I tried all but one button. Yes, the ONE button and then got the sound. Thanks for trying to help.

---

### Post by Seryozha on 2006-09-06
> **loell said:**
> hi seryozha,

can you try this deb package instead, and see if this package work for you?

[http://www.yourfilelink.com/get.php?fid=161405]("http://www.yourfilelink.com/get.php?fid=161405")

I am still getting the same error:

gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

---

### Post by loell on 2006-09-06
> **Seryozha said:**
> I am still getting the same error:

gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

can you re-install libgtkhtml-2 via syanptic? 
normally,  libgtkhtml-2.so.0 comes with the package libgtkhtml-2.
and can you tell me your system specs?

---

### Post by Seryozha on 2006-09-07
> **loell said:**
> can you re-install libgtkhtml-2 via syanptic? 
normally,  libgtkhtml-2.so.0 comes with the package libgtkhtml-2.
and can you tell me your system specs?

That didnt help at all.

I'm runnin Dapper 6.06
MSI MOBO
Athalon 3500+
1 GB RAM
NVIDIA 6600 GT

---

### Post by loell on 2006-09-07
> **Seryozha said:**
> That didnt help at all.

I'm runnin Dapper 6.06
MSI MOBO
Athalon 3500+
1 GB RAM
NVIDIA 6600 GT

i see, your running a 64 bit line processor, gyachi does not work on a 64 bit system, due to some win32 wine component, there is however a 64 bit user who had success running it on his system, maybe you can ask [Paul]("http://ubuntuforums.org/member.php?u=130067") ,on how to do it. :)

---

### Post by bonjun on 2006-09-08
i made a launcher on my xubuntu, but everytime i click on the launcher, this error appear...

> Could not run "Gyach Enhance"

Failed to execute child process "gaychi" (No such file or directory)

but launching it from terminal gives me no problem...

---

### Post by loell on 2006-09-08
perhaps its a typo, or i think its definitely a typo
its "gyachi" not "gaychi" ;)

---

### Post by pneaveill on 2006-09-09
> **pneaveill said:**
> Loell,
Yes. It was one of those newbie error things. I tried all but one button. Yes, the ONE button and then got the sound. Thanks for trying to help.

 Next issue I am having: When I blacklisted an individual yesterday, trying to mute her, nothing would stop me from hearing her. Just what is the "mute" button supposed to do, if not mute the people we don't want to listen to? Or, perhaps this is another newbie error and I need a bit more explantion with this whole thing.  Appreciate the patience

---

### Post by loell on 2006-09-09
the mute button on gyachi voice chat does not work yet at the moment.

---

### Post by aie on 2006-09-09
well, I am not able to have a voice conversation !!!
It tells me Please start pY! voice chat so I do, but it wont achieve anything.

Am I mis-manipulating ?

---

### Post by loell on 2006-09-09
if you're talking about one to one conversation then it does not seem to work that way, but with room voice chat then its almost always ok.

---

### Post by bjorkiii on 2006-09-09
Well im a happy chap im glad i found this thread been tryin to get voice in chatroom for a few weeks ty all very much :D

---

### Post by fabertawe on 2006-09-10
> **loell said:**
> i see, your running a 64 bit line processor, gyachi does not work on a 64 bit system, due to some win32 wine component, there is however a 64 bit user who had success running it on his system, maybe you can ask [Paul]("http://ubuntuforums.org/member.php?u=130067") ,on how to do it. :)

Hi MOGFU :biggrin: 

I have responded to Seryozha via private message. I hope I haven't confused him/her too much ;) I have asked Seryozha to let me know if it works so I can post some sort of guide (I didn't write it all down at the time unfortunately and am working from memory).

Paul

---

### Post by shogun1234 on 2006-09-10
Hi,

I came across to see this thread and encounter a problem when using gyachi. After launching the gyachi, it always issues errors like " Invalid UTF-8 string passed to  pango_layout_set_text()". 

I guess that should be the problem of encoding. So I modify the source code (callbacks.c send_pm_session_text function) by g_convert_with_fallback() to test weather it is so. Then, I can see the text typed in pm window are correctly displayed. Unfortunately, meanwhile another problem occurred. After pressing the enter key in the pm window, the typed words sent out are still displayed incorrectly (but those words are correctly displayed in the console after source code modified).

Would anyone be able to tell me how gyachi handle/ process the encoding or character set? 

I sincerely any suggestion.

Thank you very much.

The code snippet to modify callbacks.c is as follow:

========== pm_session_text BEG ========== 
#include <glib.h> 
... 
char * encode_str;  
const char *to_codeset = "Big5"; 
... 
encode_str = g_convert_with_fallback( 
textbuf, 
strlen(textbuf), 
to_codeset, 
"UTF-8", 
"?", 
NULL, 
NULL, 
NULL 
); 
printf("\n\n\nafter encoded textbuf -> %s\n\n\n", encode_str); 
 
========== pm_session_text END ==========

---

### Post by loell on 2006-09-10
Heheh :mrgreen: , That would be very nice paul, looking forward to see it , i bet it will the first howto of gyachi in 64 across all linuxes :-D 


hi shogun1234 :)

geez, i only do  installation troubleshooting, gyachi usage and packaging, 
i'm not even good at those ;) , however its good to know, that you have already been tinkering to fix encoding, sorry i wish i could help you on encoding problems, you seem to know more. hope the developers and you can fix it :KS

---

### Post by rics on 2006-09-11
Hi there! iv installed gyachi on my ubuntu but it cannot load one plugins. Ive already installed libgpgme 0.3.16 but everytime i connect it appears the error. Hope u can help me. 

Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

Location: /usr/local/share/gyachi/plugins/gyachigpgme.so

---

### Post by loell on 2006-09-11
some users suggested symbolic linking by doing,

sudo ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so.11

then, hopefully the plugin will load sucessfully, though gyachi can run just fine without the gpgme plugin.

---

### Post by rics on 2006-09-11
I've already tried linking it to /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so.11 but same errors appeared. Anyway, i can use the gyachi even thought it cannot load that plugin.Anyway tnx for the ideas :) More Power and Mabuhay!

---

### Post by bonjun on 2006-09-12
> **loell said:**
> perhaps its a typo, or i think its definitely a typo
its "gyachi" not "gaychi" ;)

oh sorry, my fault, (tanga ko talaga:))


btw,,, i've tried the new version, and it gives me this error...
> ~$ gyachi

(process:4418): Gdk-WARNING **: locale not supported by Xlib

(process:4418): Gdk-WARNING **: cannot set locale modifiers
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 74 overflow
Unhandled property: 53 list-style
Unhandled property: 41 font
Unhandled property: 53 list-style
Unhandled property: 41 font
Unhandled property: 53 list-style
Unhandled property: 41 font
Unhandled property: 53 list-style
Unhandled property: 41 font
*** glibc detected *** free(): invalid next size (normal): 0x086d4b70 ***
Aborted


---

### Post by loell on 2006-09-12
> **bonjun said:**
> oh sorry, my fault, (tanga ko talaga:))


btw,,, i've tried the new version, and it gives me this error...

hmm, this might be a buffer overflow, i'm not sure though, can you do strace?

strace gyachi

and perhaps copy/paste and pm me the long output.

---

### Post by pneaveill on 2006-09-14
Probably just newbie thought here, but any thoughts on removing some of the booting ability. Each time I use it, I get booted. NOt meaning to be critical here.

Is there something I can do differently or tweak something or whatever?

Otherwise it is cool.

---

### Post by loell on 2006-09-15
you can disable the boot prevention capability in "setup" --> "protections" tab then uncheck one or both basic and advance boot prevetion :)

---

### Post by pneaveill on 2006-09-15
> **loell said:**
> you can disable the boot prevention capability in "setup" --> "protections" tab then uncheck one or both basic and advance boot prevetion :)

That was cool how that worked. Next issue: for the people getting ignored, is there a way I can change the ignoring message:

[ B!tch-Be-Gone 1.0.7 - IGNORING: 'person' ( person) ] *    *CLICK*     Acceptable levels of ignorance have been exceeded:    . You are #51 in my iggy bin.     See ya!    
 *** ignoring  perosn  ( person )  ***

anything to adjust this?

---

### Post by loell on 2006-09-15
:(  its in the source code, it can be adjusted but then it needs recompiling ;)

---

### Post by pneaveill on 2006-09-15
> **loell said:**
> :(  its in the source code, it can be adjusted but then it needs recompiling ;)
how do I do that or is there something that can be fixed?

I like almost all of it, except for the language part of it.

---

### Post by loell on 2006-09-15
> **pneaveill said:**
> how do I do that or is there something that can be fixed?

I like almost all of it, except for the language part of it.

i would assume, that you already know the basics of compiling :)

quoted from gyachi forum :KS , address to a user who also ask that same question.

> 
Scott, 
 
If you compile from source and know a little bit about c, specifically the printf family of formatted output, the message can be modified by appropriate editing of the source file client/ignore.c in line 428 (This is the March 20 version of this file) 
 
-Matt


---

### Post by pneaveill on 2006-09-16
> **loell said:**
> i would assume, that you already know the basics of compiling :)

quoted from gyachi forum :KS , address to a user who also ask that same question.

Think I got the file edited and recompiled per your instructions. They were suprisingly simple for a non-programmer such as myself. I rebooted the machine and looked for it in the applications menu and it was not there. DId I miss something?  Also, where do I find the gyache forum?  Been a big help

---

### Post by loell on 2006-09-16
because its recompiled it won't be in the menu, but you could exeute in the command line with "gyachi" , eventually you can just create a launcher for that.

gyachi forum is at 

[http://gyachi.sourceforge.net/forums.shtml](http://gyachi.sourceforge.net/forums.shtml)

---

### Post by pneaveill on 2006-09-16
> **loell said:**
> because its recompiled it won't be in the menu, but you could exeute in the command line with "gyachi" , eventually you can just create a launcher for that.

gyachi forum is at 

[http://gyachi.sourceforge.net/forums.shtml](http://gyachi.sourceforge.net/forums.shtml)

To be honest, I am not really a programmer and still a bit of a newb. Couple questions: (1) how do I run it from command line; (2) how do I build a launcher for it; (3) where do I find it in the filesystem?

---

### Post by loell on 2006-09-16
> **pneaveill said:**
> To be honest, I am not really a programmer and still a bit of a newb. Couple questions: (1) how do I run it from command line; (2) how do I build a launcher for it; (3) where do I find it in the filesystem?

ok, base on your questions have you really compiled it?  have you manage to satisfy all dependencies in compiling? i just find it a little bit odd, anyways, 

1. you can run it by typing gyachi in the command line console
2. creating launchers will  differ from desktop environments your using, i'm not gnome right now, but it think you can just right click the desktop in the menu there is something like "create launcher" and just fill the necessary settings. in xfce though where i am currently at, you can right click any of the two panel, then add item --> launcher.
3. its in /usr/local/bin/gyachi

---

### Post by pneaveill on 2006-09-16
> **loell said:**
> ok, base on your questions have you really compiled it?  have you manage to satisfy all dependencies in compiling? i just find it a little bit odd, anyways, 

1. you can run it by typing gyachi in the command line console
2. creating launchers will  differ from desktop environments your using, i'm not gnome right now, but it think you can just right click the desktop in the menu there is something like "create launcher" and just fill the necessary settings. in xfce though where i am currently at, you can right click any of the two panel, then add item --> launcher.
3. its in /usr/local/bin/gyachi

I thought it was installed properly, it went through all the steps and I did not see any errors. So now what can I do?

---

### Post by loell on 2006-09-16
if you did 

./configure
make
make install

with no errors then it is properly installed.

---

### Post by pneaveill on 2006-09-16
> **loell said:**
> if you did 

./configure
make
make install

with no errors then it is properly installed.

 Newbie question: I tried it the more automatic way, with no reported errors. I downloaded the source and editied it as you suggested, then converted it over to a deb, then installed the deb.  Yet will not work. Should I uninstall and start over with it or what do you advise?  Side note: I am loading this on two computers and wondering how best, once completed, to upload the deb to the other computer.  THanks for the patience with a non-programmer

---

### Post by loell on 2006-09-17
i'm not sure how you're doing that, downloading the source and then converting to deb? if you really need to edit the message "B!tch be-gone" and you want it badly :wink: , i could do it for you and i'll send it to you in a simple deb package, it may take a while though. so what message would like to  substitute?

note: i'm not a programmer too :rolleyes:

---

### Post by pneaveill on 2006-09-17
> **loell said:**
> i'm not sure how you're doing that, downloading the source and then converting to deb? if you really need to edit the message &quot;B!tch be-gone&quot; and you want it badly :wink: , i could do it for you and i'll send it to you in a simple deb package, it may take a while though. so what message would like to  substitute?

note: i'm not a programmer too :rolleyes:

 That would be great!! As for the wording, something like: Grumbler-be-gone would be acceptible. 
FYI: [ubuntu hacks]("http://www.oreilly.com/catalog/ubuntuhks/") is the only place I could find any info on how to do this that a non-programmer like me could understand. If there is a better site or whatever, might be helpful to some here.

---

### Post by pneaveill on 2006-09-19
> **pneaveill said:**
> That would be great!! As for the wording, something like: Grumbler-be-gone would be acceptible. 
FYI: [ubuntu hacks]("http://www.oreilly.com/catalog/ubuntuhks/") is the only place I could find any info on how to do this that a non-programmer like me could understand. If there is a better site or whatever, might be helpful to some here.

Downloaded and installed perfectly. Was incredible watching them trying to attack me while online. Finally, they got me and spammed almost everyone on my yahoo list.  Any ideas on hardening this thing even further?

Thanks in advance,

Paul

---

### Post by loell on 2006-09-19
try playing on the offered options in, setup --> "protection" tab , basically just check them as you see fit. but on the source code as i grasp as small part of it, it is supposed to fight back by sending back those things that spammers/booters send. but probably its an old bug of the gyach program series. but to fully minimize those bots and possibly erradicating them, the initiative should come from yahoo itself.

---

### Post by pneaveill on 2006-09-19
> **loell said:**
> try playing on the offered options in, setup --> "protection" tab , basically just check them as you see fit. but on the source code as i grasp as small part of it, it is supposed to fight back by sending back those things that spammers/booters send. but probably its an old bug of the gyach program series. but to fully minimize those bots and possibly erradicating them, the initiative should come from yahoo itself.

Yapoo knows of the longstanding problem, yet refuses to do anything about it

---

### Post by GoneWithTheWind on 2006-09-24
How well is gyachi working for those of you using it, compared to gaim or yahoo messenger?

---

### Post by GoneWithTheWind on 2006-09-24
> **loell said:**
> **[COLOR="Blue"]GYachI 1.0.5[/COLOR]** is already out 
you can download the official ubuntu deb package from

[COLOR="Red"]**[COLOR="Red"][gyachi.sourceforge.net/download.shtml]("gyachi.sourceforge.net/download.shtml")[/COLOR]**[/COLOR] 

I've installed this, but it's not showing up under applications > internet.

---

### Post by loell on 2006-09-24
> **John Rupp said:**
> I've installed this, but it's not showing up under applications > internet.

according to your system spec from your signature, you are in 64 bit , 
due to a wine component gyachi won't run a 64 bit system, but you can ask [Paul]("http://ubuntuforums.org/member.php?u=130067"), he seems to be the first user to run it on a 64 bit system :). , 


basic usability is more or equal to gaim, not unless you wan't to use the follwing features:

webcam , room voice chat, email preview , auto ignore and ignore list, etc.

---

### Post by GoneWithTheWind on 2006-09-24
Think it is 32 bit.  Where do you see 64 bit.

---

### Post by loell on 2006-09-24
oh, i thought AMD Athlon is 64 bit, in any case, can you type 

gyachi

in the command line console? and see if there is any output.

---

### Post by GoneWithTheWind on 2006-09-24
Wow, yes.  

$ gyachi

(gyachi:4891): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed
GyachE Improved 1.0.5
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal'
 Plugin Loaded:  'GyachI-XMMS'
 Plugin Loaded:  'GyachI-Photos'
 Plugin Loaded:  'MCrypt'
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.

- - - - -

And a chat room screen opened with this:

GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
 Plugin Loaded:  'GyachI-XMMS' 
 Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'MCrypt' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.

- - - - - - -

Plus a yahoo login screen.  
And it's now listed under applications > internet.

Looks like that got it going, so I will try it out.  Thanks!  :D

---

### Post by fabertawe on 2006-09-25
> **loell said:**
> according to your system spec from your signature, you are in 64 bit , 
due to a wine component gyachi won't run a 64 bit system, but you can ask [Paul]("http://ubuntuforums.org/member.php?u=130067"), he seems to be the first user to run it on a 64 bit system :).

Hi Loell, FYI... I have been working through installing it with Seryozha (with a view to making a How-To in the process) but we have hit a wall right now so I am looking into making a .deb but need to learn the process first! If you have any helpful advice or links regarding deb making it would be very much appreciated :) 

Cheers ... Paul

---

### Post by loell on 2006-09-25
Sure Paul :) , i'll pm you an intro ;)
another easy way is through checkinstall,  unfortunately ubuntu's current version does not manage dependencies, but checkinstall 1.6 does,  the newer version, by editing the control file, you might have no idea what i'm talking about, but it will be clear to you :) as you will read the intro..

i've mailed you instead, seems like the pm had a limit..

---

### Post by GoneWithTheWind on 2006-09-27
I tested Gyachi last night and the webcam doesn't open.

"Enable webcam device" under "general" is checked, and "webcam device" shows **/dev/video0** (not sure if this is right).

Gyachi (webcam broadcaster) says "**An error occured at 'ioct| VIDIOCSPICT'.  Could not set camera properties.**"

Also was not able to view.

---

### Post by GoneWithTheWind on 2006-09-27
> **John Rupp said:**
> **(gyachi:4891): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed**
GyachE Improved 1.0.5
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal'
 Plugin Loaded:  'GyachI-XMMS'
 Plugin Loaded:  'GyachI-Photos'
 Plugin Loaded:  'MCrypt'
**** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:**

**An error occurred initiating the plugin.**
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.

How do I load the plugin/s that failed?

---

### Post by sabitha on 2006-09-27
> Gyachi (webcam broadcaster) says "An error occured at 'ioct| VIDIOCSPICT'. Could not set camera properties."
is your system know your webcam??? check the usb with 
$ lsusb

> An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

install with :
$ sudo apt-get install libgpgme6

---

### Post by GoneWithTheWind on 2006-09-27
> **sabitha said:**
> check the usb with $ lsusb

$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 04fc:504b Sunplus Technology Co., Ltd Aiptek, 1.3 mega PockerCam
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

> install with :
$ sudo apt-get install libgpgme6

$ sudo apt-get install libgpgme6
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libgpgme6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 68.5kB of archives.
After unpacking 176kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libgpgme6 0.3.16-2 [68.5kB]
Fetched 68.5kB in 1s (37.9kB/s)
Selecting previously deselected package libgpgme6.
(Reading database ... 88110 files and directories currently installed.)
Unpacking libgpgme6 (from .../libgpgme6_0.3.16-2_i386.deb) ...
Setting up libgpgme6 (0.3.16-2) ...

- - - - -

Will try it again.  Thanks!

---

### Post by GoneWithTheWind on 2006-09-27
I will try the webcam later.  I'm still getting this:

"** plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

an error occurred initiating the plugin.
system requirements: gpgme (gpgme 0.3.16 or better), gpg 1.0.7 or better

---

### Post by GoneWithTheWind on 2006-09-27
When I go in a chat room, and click a nickname for profile, gyachl disconnects.

---

### Post by lamego on 2006-09-27
Give it a try here:
[http://www.getdeb.net/search.php?keywords=GYachI](http://www.getdeb.net/search.php?keywords=GYachI)

---

### Post by loell on 2006-09-27
> **John Rupp said:**
> I tested Gyachi last night and the webcam doesn't open.

"Enable webcam device" under "general" is checked, and "webcam device" shows **/dev/video0** (not sure if this is right).

Gyachi (webcam broadcaster) says "**An error occured at 'ioct| VIDIOCSPICT'.  Could not set camera properties.**"

Also was not able to view.

does your webcam works with other applications? try ekiga if you can see any images from your webcam.

---

### Post by GoneWithTheWind on 2006-09-27
It works on w/xp.

Will see about ekiga.

---

### Post by GoneWithTheWind on 2006-09-27
Ekika wants to configure my router.

I am very happy with SunRocket Voip and would rather not change the settings for the router.

---

### Post by loell on 2006-09-27
ok, try installing 

camorama

its a webcam grabber application.

launch it and see if you can see any images , if it does not show any, then your webcam might not be compatible with linux.

---

### Post by GoneWithTheWind on 2006-09-28
I'm having a hard time getting camorama to work.

I download camorama but it didn't show up on my on my computer.  When I clicked "open" under downloads, a screen popped up with choices for "add" or "extract" but nothing happened when I cliced them.  Likewise nothing happened typing camorama or camorama-0.17 in the terminal.  However camorama showed up at system > administrative > synaptic package manager, so I went to "applications" and clicked "add", checked and added the program.

Now camorama is still not showing up on any list that I see and still not working on terminal.  How do I get it to run?

---

### Post by GoneWithTheWind on 2006-09-28
Currently a folder of camorama is showing up on my desktop.

Clicking "camorama webcam viewer" opens a screen that tries to open the cam.  It asks me if I want to import the pictures that are on the webcam (there aren't any on it).  I click yes.

**Camorama is showing that I have an "aiptek 1.3 mega pocketcam".**

Clicking "import":  says "could not import photos, no images found".  I'm not trying to import photos, just to open the webcam.

Anyway, this shows that linux does detect the webcam?

---

### Post by GoneWithTheWind on 2006-09-28
Clicking the same thing again and this time an error message:

Error (camorama)

Could not connect to video device (/dev/video)).
Please check connection.

---

### Post by erie_pa_halloween_guy on 2006-09-30
Hello folks Im really frustrated here running Mepis 6.0 and after seveeral attemppts of trying to get gyachi running all i get is the following error

gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

Ccan anyone help??

---

### Post by loell on 2006-09-30
install libgtkhtml2 via apt-get or synaptic.
may i ask where did you get deb package? ubuntu deb package from gyachi download site is suppose to solve this dependency.

---

### Post by erie_pa_halloween_guy on 2006-09-30
Holy crap that worked LOL i swear i tried that already  now lets see if it stays stable thank y9ou ever soooo much

---

### Post by loell on 2006-10-01
ssshhhh!!! , this is just my update :) , an experimental edition , it just uses a different icon. check it out...

update to newer build

[http://www.yourfilelink.com/get.php?fid=183164](http://www.yourfilelink.com/get.php?fid=183164)

---

### Post by sabitha on 2006-10-01
> **loell said:**
> ssshhhh!!! , this is just my update :) , an experimental edition , it just uses a different icon. check it out...

[http://www.yourfilelink.com/get.php?fid=182874](http://www.yourfilelink.com/get.php?fid=182874)

dpkg: error processing gyachi_1.0.5-1_experimental_i386.deb (--install):
 trying to overwrite `/usr/lib/win32/tsd32.dll', which is also in package w32codecs
Errors were encountered while processing:
 gyachi_1.0.5-1_experimental_i386.deb

---

### Post by loell on 2006-10-01
sorry my bad, i did not configure it to install on default directory, anyway here is the newer build, hope you like it ;) 

[http://www.yourfilelink.com/get.php?fid=183164](http://www.yourfilelink.com/get.php?fid=183164)

these are some screenshots

[[IMG]http://img166.imageshack.us/img166/5006/gyachiexsf5.th.png[/IMG]](http://img166.imageshack.us/my.php?image=gyachiexsf5.png)

[[IMG]http://img106.imageshack.us/img106/4486/gyachiex2ns5.th.png[/IMG]](http://img106.imageshack.us/my.php?image=gyachiex2ns5.png)

---

### Post by GoneWithTheWind on 2006-10-01
Any response to what I asked previously.

---

### Post by loell on 2006-10-01
there are several aiptek webcams in [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
i'm not sure if your webcam is included. perhaps  wait on ubuntu edgy, maybe your webcam will be detected by then. in my case i already have ubuntu installed before buying a webcam , i just make sure the webcam that i buy is on that list.

---

### Post by pneaveill on 2006-10-02
I know that I am not a programmer, so please work with me with what I am asking. I found a site that shows some things on how to make yahoo pagers more secure. Below is a list of stuff for M$ stuff that I found and wondered if any of it could be hacked into gyachi:

> [http://www.bigblueball.com/forums/yahoo-messenger-support/13961-how-stop-others-booting-you-8.html](http://www.bigblueball.com/forums/yahoo-messenger-support/13961-how-stop-others-booting-you-8.html)


under Preferences and do the following, you will help yourself further to not be booted:
-Messeges: Min. the Msg's to the Taskbar
      -Show the msg's at the bottom right of the screen
  -Msg's are show in a single IM box.
  - Untick enable IM inv.

-File Transfer: Never Accept files from anyone and Never allow other to download from me

-Chat: Ignore Chat Invitations
  -**Fortunately, there is an antidote.** Open the **filter1.txt** file with Notepad. You'll find it in the Yahoo folder (usually C:\Program Files\Yahoo!\Messenger\).

Add these words to the filter1.txt file:
**&lt;snd,&lt;alt, &lt;url=, &lt;font, &lt;fade, &lt;a, &lt;html&gt;, &lt;body, &lt;iframe, &lt;frame, src=, &lt;img, &lt;url&gt;, url(, onLoad=, [http://,]("http://,/") www, &lt;embed**
-Privacy: Ignore anyone who is not on my Friends List (you wont get PM's from people whom you dont have added)


Is there a way to modify things to add these somehow? Or maybe it does and I missed it.

Hope I am not too far out of line

Paul

---

### Post by sabitha on 2006-10-02
> **loell said:**
> sorry my bad, i did not configure it to install on default directory, anyway here is the newer build, hope you like it ;) 

[http://www.yourfilelink.com/get.php?fid=183164](http://www.yourfilelink.com/get.php?fid=183164)

these are some screenshots

[[IMG]http://img166.imageshack.us/img166/5006/gyachiexsf5.th.png[/IMG]](http://img166.imageshack.us/my.php?image=gyachiexsf5.png)

[[IMG]http://img106.imageshack.us/img106/4486/gyachiex2ns5.th.png[/IMG]](http://img106.imageshack.us/my.php?image=gyachiex2ns5.png)

good work loel, i like the new icon specialy when my buddies status on SMS :)

---

### Post by loell on 2006-10-03
@sabitha i'm glad that you find it useful :)  , i'm still searching for icons that can somehow match the actions of the program. 

@pneaveill , that would be nice if it can be hacked in gyachi, but i guess only the developers can say if its possible.

---

### Post by pneaveill on 2006-10-03
> **loell said:**
> 
@pneaveill , that would be nice if it can be hacked in gyachi, but i guess only the developers can say if its possible.

Any ideas on how to get a hold of them and ask them about this?

---

### Post by GoneWithTheWind on 2006-10-03
Thanks for the list.  I have the Aiptek PenCam 1.3 SD.

The list has this one, but I'm not sure whether it's exactly the same version of cam, and where to find the product or vendor ID.  The S/NO is AEE20031249.

---

### Post by GoneWithTheWind on 2006-10-03
> **John Rupp said:**
> When I go in a chat room, and click a nickname for profile, gyachl disconnects.

Is there a fix for this yet.

---

### Post by loell on 2006-10-03
in "setup" at the "options" tab in miscellaneous options, you can set it to "window" or web browser as profile viewer , and then check auto-reconnect if disconnected.

your previous output
$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 04fc:504b Sunplus Technology Co., Ltd Aiptek, 1.3 mega PockerCam
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

this 04fc:504b , seems to be no match in the list, just be optismistic, maybe they can find a way to include it later ;)

---

### Post by loell on 2006-10-03
> **pneaveill said:**
> Any ideas on how to get a hold of them and ask them about this?

in gyachi.sourcforge.net

---

### Post by GoneWithTheWind on 2006-10-04
Web browser as profile viewer is working fine now.  Thanks.

> **loell said:**
> this 04fc:504b , seems to be no match in the list, just be optismistic, maybe they can find a way to include it later ;)

If I want to purchase another cam, where would I find this number on it?

---

### Post by GoneWithTheWind on 2006-10-04
As a note, when I right click a nickname, the menu doesn't stay open unless I keep holding the button down.  Otherwise it works okay though.

- - - - -

Uh oh... now when I try to sign on, Gyachi keeps disconnecting and reconnecting over and over.  The only things I had changed were to autoreconnect, and to use the browser for profiles.

Now I have unchecked auto reconnect and when I try to reconnect, Gyachi still keeps disconnecting me, and won't even let me sign on at all.  This is the message it keeps giving me:

You have been disconnected from Yahoo!
Error receiving from socket: 0

---

### Post by loell on 2006-10-04
maybe there are two copies of gyachi running.

---

### Post by pradish on 2006-10-15
Hi,

  I am a nebie to Linux and Ubuntu.. i have just installed Gyachi.. and i got eveything to work.. my voice chat is working cam is fine... the only issue i have is in my buddie list... my buddie list doesnot come o completely.. i have few of my frnds who are there in my buddie list but.. wont shoe up on Gyachi.. infact i get they have added me and if i wish to remove thm... 
  I have a huge buddie list.. is there any restriction in Gyachi.. on no of buddies tht it can display/except?

Thanks!!

---

### Post by loell on 2006-10-15
:-k  i haven't expirience this buddy list problem yet , perhaps this is a bug.

---

### Post by pradish on 2006-10-16
any one.. facing this issue.. i get the message that they have added me and they might be a stalker!!!!.. funny isnt it

---

### Post by loell on 2006-10-16
in menu "setup" --> "protection" tab , check the checkbox "Do not allow anyone to add in me in their buddy list" and then restart gyachi

---

### Post by sefmars on 2006-10-16
ok so i got it working 1 time but i hawe started it from commandline i loged in then i ctrl+c in console so it shut down i can not get iti working ever since this is what it says


mars@XANQK72QT35:/home$ gyachi

(gyachi:10863): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

(gyachi:10863): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(gyachi:10863): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(gyachi:10863): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gyachi:10863): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gyachi:10863): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(gyachi:10863): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setBrush: Will be reset by begin()
Segmentation fault



i have a xandros 4 home edition updated from ubuntu dapper mirors :D so it should be the same with kubuntu

---

### Post by loell on 2006-10-16
have you tried uninstalling it, and then install it again? see if it still works.

---

### Post by sefmars on 2006-10-17
tried theat tried to run as root
updated sistem

the thing is now theat after system update i can only login with as root//i updated with ubuntu dapper//tried creating a new usser and nada (login faild)if you have any sugestions !!??

---

### Post by ayoli on 2006-10-17
would be nice to have a deb for edgy :p then i think i'll give gyachi a try

---

### Post by BLTicklemonster on 2006-10-17
Bah, Gyachi is a cluttered mess. I like it and all, but man, what a miasma or whatever. I have yet to get a voice converation going with another yahoo user.

---

### Post by loell on 2006-10-17
> **ayoli said:**
> would be nice to have a deb for edgy :p then i think i'll give gyachi a try

have you tried the dapper deb? :-k  i would assumed it will work.

---

### Post by loell on 2006-10-17
> **BLTicklemonster said:**
> Bah, Gyachi is a cluttered mess. I like it and all, but man, what a miasma or whatever. I have yet to get a voice converation going with another yahoo user.

True, its in cluttery gui , i attempted to redo some icons in my experimental edition, see the first post , i don't know if i somehow lessen the clutter.

the voice thing , is just a room voice chat, its not sip voice call
you have to enter in a room, nad launch the voice chat, then press the on button, if someone is talking in the particular room, then you'll hear them.

---

### Post by sabitha on 2006-10-30
.deb for edgy????????

---

### Post by sabitha on 2006-10-30
> **loell said:**
> have you tried the dapper deb? :-k  i would assumed it will work.

for edgy please....:-? 
already download the dapper version and failed when install. there is something about lingail... when erorr i forget because i close the terminal :(

---

### Post by loell on 2006-10-31
yeah, i thought  dapper deb is compatible but then its not, 
so here it is in the new thread

[gyachi for edgy]("http://www.ubuntuforums.org/showthread.php?t=289509")

---

### Post by BLTicklemonster on 2006-10-31
So have they ever fixed gyachi to where yahoo voice chat works correctly? Yeah, you can chat with voice or something whatever, but try joining a conference someone in yahoo has initiated and joining in a conversation. I've yet to get that to work.

---

### Post by ragadanga63 on 2006-11-29
Yo! loell kabayan!  Got Gyachi running. I like it a lot.  Now i'm only two apps(Coreldraw and Photoshop CS) away from saying byebye to windows.  

Thank you, pre for your effort.  Makes me proud of being a pinoy.

---

### Post by loell on 2006-11-30
> **ragadanga63 said:**
> Yo! loell kabayan!  Got Gyachi running. I like it a lot.  Now i'm only two apps(Coreldraw and Photoshop CS) away from saying byebye to windows.  

Thank you, pre for your effort.  Makes me proud of being a pinoy.

salamat pre , welcome sa ubuntuforums :)

---

### Post by Joo on 2006-12-01
All,
downloading and installing GYACHE got no problem at all. Starting the application also got no problem. Trying to log in is BIG PROBLEM for me. :( 

On the login window, I enter my yahoo id (tried both with and without @yahoo.com suffix) and my password, but I could not log in. I've tried every server on the drop down list and still could not log in. ](*,) 

Can somebody help me to solve my problem? What server do you use for Yahoo Messenger? Btw, I also type the 'csa.yahoo.com' for the server as per Yahoo Messenger help site, but as you might guess, STILL NOT CONNECTED... Duuuh...

TIA,
Joo

---

### Post by loell on 2006-12-01
usually the first three server on the drop down list will connect you to yahoo, try running it on the terminal/console 

```
gyachi
```

and see the output when you attempt to log in.

you can also paste it here.

---

### Post by Joo on 2006-12-02
Hi Loell,

this is what I get on the console:

wiyani@Wiyani-desktop:~$ gyachi

(gyachi:6048): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

After entering userid and password, also selecting scs-dcna.msg.yahoo.com in the server, I get the response on the pop up window saying:

Could not connect to Yahoo!
Socket connection failed: 4

And from the Gyachi panel, I get this:

GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
 Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'MCrypt' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Plugin Loaded:  'GyachI-XMMS' 
 Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.


  ** Could not connect to Yahoo! [ Socket connection failed: 4 ] **

[12/02/2006 14:14:19]      Disconnected from Yahoo!    See Ya!  Online for  0 : 00 : 10

I do hope you could help me solve this problem. I don't mind using GAIM, but application capable of voice chatting is better. :mrgreen: 

Thanks in advance.
Joo

---

### Post by loell on 2006-12-02
strange :-k  , do you have any other issues with your internet?
are you behind a restrictive firewall? try re-installing the app

i only get this message

** Could not connect to Yahoo! [ Socket connection failed: 4 ] **

when my isp is down

---

### Post by Joo on 2006-12-02
I connect to internet via ADSL router. Allied Telesyn model AT-AR256E. Yes, it has firewall but as far as I know, it is only protecting the router from being accessed from WAN (Internet).

I don't know if this could be the culprit as I have no problem signing into my Yahoo Messenger from my Xp laptop.

Suppose if my router is the problem (stupid question), how do I configure or what things should I have to look for in the router setup?

In the mean time, I'll take your suggestion to reinstall GyachI...

Thanks in advance.
Joo

---

### Post by sabitha on 2006-12-02
** Could not connect to Yahoo! [ Socket connection failed: 4 ] **

i think this is a serious error because i got this too,but you can connect to yahoo if you use port: 80 rather then 5050 (default on gyachi) but if you use this port (80) you can´t see/view webcam from another. the ISP not down like loel say :D

---

### Post by loell on 2006-12-02
i haven't tried this, but you can specify a proxy on 

> setup ---> options tabs

---

### Post by fabertawe on 2006-12-03
Hi Loell :) 

Would you know where I could find Jasper source patched for the memory leak? I've been looking for a long time but can't find anything. It's not the biggest problem in the world but it would be nice if I didn't have to stop the webcam after an hour or two to reclaim a few hundred Mb!

Thanks ... Paul

---

### Post by loell on 2006-12-03
hi paul , i haven't found it either, after several searches, we'll ask hoshy , or zoltan , if they have a tar source.

---

### Post by fabertawe on 2006-12-04
> **loell said:**
> hi paul , i haven't found it either, after several searches, we'll ask hoshy , or zoltan , if they have a tar source.

Hi Loell... I was just about to post something in the help forum but checked the downloads again and saw a 64bit .rpm for Jasper. Must have missed it before or it's new. I've extracted the files and will give it a try today and let you know if it works (I'm guessing it's patched or it wouldn't be there).

Cheers ... Paul

---

### Post by loell on 2006-12-04
i thought those rpms are just binaries

---

### Post by fabertawe on 2006-12-04
> **loell said:**
> i thought those rpms are just binaries

They are, it'll save me compiling them ;) 

I won't get a chance to test the cam today after all but will post back when I do with the outcome.

Paul

---

### Post by sabitha on 2006-12-06
> ** Could not connect to Yahoo! [ Socket connection failed: 4 ] **

yeah your right loel. my fault like you say my ISP problem. there a problem between my ISP and Yahoo Messenger port. but now the problem is gone thank&#347; for the great sofware.

---

### Post by fabertawe on 2006-12-10
Can anyone using a web cam with GYachI let me know what kind of memory usage you're getting with 'gyachi-upload' and the other webcam component please?

Loell, I tried those .rpm versions of Jasper and the Jasper library and while it seems they might be using less memory it's still a huge amount (90Mb for gyachi-upload after about an hour as I recall). I haven't been able to test this properly yet but will get more accurate figures when I can.

Cheers ... Paul

---

### Post by loell on 2006-12-10
thanks for looking into this bug, paul.

i only use webcam occasionally , with my family , so i can't post some figures. 

hmm, libjasper's code is worth taking a look,  oh well, the question would be can an ordinary user like me, comprehend it? :-k 

i tried contacting zoltan, but he seem busy.

---

### Post by loell on 2006-12-10
this the homepage of libjasper

[http://www.ece.uvic.ca/~mdadams/jasper/]("http://www.ece.uvic.ca/~mdadams/jasper/"):KS

and there seems to be a new release. jasper 1.9 with all the patches to address the memorey leak

---

### Post by BLTicklemonster on 2006-12-10
Checking back again....

So does gayache let me TALK with people in yahoo conferences that I have been invited to? SPECIFICALLY YAHOO CONFERENCES I HAVE BEEN INVITED TO, NOT JUST SPEAK IN SOME OBSCURE WAY FORM OR FASHION.

I'd really like to see it do that.

---

### Post by ljpm on 2006-12-13
> **Joo said:**
> Hi Loell,

this is what I get on the console:

wiyani@Wiyani-desktop:~$ gyachi

(gyachi:6048): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

After entering userid and password, also selecting scs-dcna.msg.yahoo.com in the server, I get the response on the pop up window saying:

Could not connect to Yahoo!
Socket connection failed: 4

And from the Gyachi panel, I get this:

GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
 Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'MCrypt' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Plugin Loaded:  'GyachI-XMMS' 
 Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.


  ** Could not connect to Yahoo! [ Socket connection failed: 4 ] **

[12/02/2006 14:14:19]      Disconnected from Yahoo!    See Ya!  Online for  0 : 00 : 10

I do hope you could help me solve this problem. I don't mind using GAIM, but application capable of voice chatting is better. :mrgreen: 

Thanks in advance.
Joo

Hi,

I am having the same problem. Can't connect to yahoo.

GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
 Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'MCrypt' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Plugin Loaded:  'GyachI-XMMS' 
 Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.


  ** Could not connect to Yahoo! [ Socket connection failed: 4 ] **

[12/02/2006 14:14:19]      Disconnected from Yahoo!    See Ya!  Online for  0 : 00 : 10


It is a new install of Ubuntu Dapper. Gyachi is the only thing I have installed so far. (I haven't even run update after the initial install. Could this be the problem?)

---

### Post by loell on 2006-12-13
perhaps something is blocking you from using port 5050, ie (router/firewall).

---

### Post by calvmari on 2006-12-16
Hi Loell,

Thank you very much for the deb package! Do you know when the 1.0.7 version will be release?

I'm eagerly awaiting the time when photoshare will be available for gyachi :)

---

### Post by loell on 2006-12-16
1.0.6 will be the next release , there is a discussion in gyachi forum about the next release , so far no one could commit yet, sadly, the main developer is currently pre-occupied by his work on a proprietary project, but hopefully there might be a new release on or before january. i'm also planning to contribute  another tiny code patch myself.

 we'll just hope for the best.


:)

---

### Post by loell on 2006-12-18
i hate to bring this sad news up, currently the room voice chat does not work anymore, due to yahoo's recent change of the protocol.

hoshy the main developer promises to look on this, its a very painful task analysing packets.

don't you just love yahoo for doing this? they owe so much from the open source yet they do not support it, easily crippling third party messenger/client by changing the way their protocol works.

there is a lesson that must be learned here, while we recommend gaim/kopete/gyachi for yahoo protocol to the new users, let us not forget to tell them about those protocols  that really support the linux platform.

---

### Post by loell on 2006-12-18
and now it works..

---

### Post by pneaveill on 2006-12-19
Anything special we need to do to get this thing to work properly?

---

### Post by loell on 2006-12-19
none

---

### Post by BLTicklemonster on 2006-12-19
> **loell said:**
> and now it works..

What works?

---

### Post by loell on 2006-12-19
> **BLTicklemonster said:**
> What works?

room voice chat

---

### Post by sabitha on 2006-12-24
anybody got trouble with webcam broadcast???
this is a bug or what, because if my webcam broadcast just 1 people can view my webcam. if there is another people want to see again at least 2 or more people my webcam stop broadcast and there is an error message ...broken pipe ...(i forgot). this is happen with all my computer (13 comp)

---

### Post by BLTicklemonster on 2006-12-24
> **loell said:**
> room voice chat

... as in, if I have friends using yahoo, and they start a conference, and invite me, and they are all on windows yacking away, I will be able to carry on an intelligent conversa- no wait, I can yack with them, too?

---

### Post by loell on 2006-12-25
> **BLTicklemonster said:**
> ... as in, if I have friends using yahoo, and they start a conference, and invite me, and they are all on windows yacking away, I will be able to carry on an intelligent conversa- no wait, I can yack with them, too?

no, as in getting into a room and start voice chatting with people in that room.

---

### Post by BLTicklemonster on 2006-12-25
Dang! That's the only thing messing me up right now. Well, that, and it never snows here. :(

---

### Post by loell on 2006-12-25
same here ;) 

would you like a video demo on how room voice chat works? perhaps i can make one :mrgreen:

---

### Post by BLTicklemonster on 2006-12-25
No thanks, the only use I have for Yahoo is online gaming meetings with my clan. They all use yahoo on winders. Now if I could start a chat room that was private and invitation only blah blah blah, would it work that way? I mean they could come in and talk with me?

---

### Post by loell on 2006-12-25
i tried it before, but it doesn't seem to work, however there are public yahoo rooms that is much less populated by users, maybe you can meet with your clan in a specific room and talk there, yeah yeah i know, its a lame suggestion ;)  , but i think its the only option when you're using gyachi.

---

### Post by BLTicklemonster on 2006-12-25
OH well. Thanks anyway, loell.

---

### Post by hextor on 2006-12-27
Hello,

Glad to hear is working for all of you.. but doesnt work for me :(

I download the deb file, try to run and the package installer throws at me:

Error: Dependancy not satisfiable libpango1.0-0

any help? Thanks!

---

### Post by loell on 2006-12-27
what's your distro/version? is it dapper or edgy?

---

### Post by hextor on 2006-12-28
I am using dapper at the moment. Thanks for any help!

---

### Post by loell on 2006-12-28
i hope you did not install the gyachi's edgy deb package to dapper, in any case download gyachi's dapper deb package from [http://gyachi.sourceforge.net](http://gyachi.sourceforge.net)

---

### Post by justin_c18 on 2007-01-02
```
(gyach:12451): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(gyach:12451): Pango-WARNING **: Error loading GPOS table 4097
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIManager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.TreeView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints, longs, or tuples
```


Not sure what is going on here. Please help..... ](*,)
I'm running Ubuntu dapper, 6.06. 
HELP!

---

### Post by loell on 2007-01-02
lol :mrgreen:  , i'm sure this is not gyachi , its either gyach or gyach-enhanced , gyachi has move it voice from python to pure lightweight c. 
you can download the proper dapper deb package at

[http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")

---

### Post by justin_c18 on 2007-01-02
woo woo quick reply, thanks. Going to try it out now.
/me hopes for the best

---

### Post by justin_c18 on 2007-01-02
Well, after spending pretty much 6 hours trying to get this thing to work, the mic connects, Not sure about cam. But, now Windows will be out forever. Especially since my mother can go in yahoo chats now and chat when she wants to. Does this version work with person to person mic chatting, or still a no go? IF it is a still no go, what can I install to enable p2p chat in linux?

---

### Post by loell on 2007-01-02
i was told that person to person works in older versions of yahoo messenger, but now only the room voice chat works in gyachi. there are several options for voice calls like skype , gizmo , ekiga (voice and video) .

your wondering why the fast reply? that's because of gyachi's yahoo mail notifier, which is set to mail me when there's a new post, though sometimes ubuntuforums won't mail me, of the latest post. ;) 

and oh i can totally relate with you, i always talked to my mom with gizmo. through its voice call , and regular yahoo instant messaging and webcam with gyachi. :D

---

### Post by justin_c18 on 2007-01-02
WIll Skype work cross platform though?
will it work with Linux? and Linux to windows, windows to linux users?
hrm, didn't know Skype could be used in Linux to be truthful, if that's the case.

---

### Post by loell on 2007-01-02
yes, skype has a linux version , for voice calls, but no webcam capabilities yet.

your linux expirience would be more easier if you install automatix [http://www.getautomatix.com]("http://www.getautomatix.com")

its a gui script for installing skype , google earth, flash , codecs for playing  mp3 and videos , and a lot more

download and install the dapper 386 package [here]("http://www.getautomatix.com/wiki/index.php?title=Installation")

---

### Post by justin_c18 on 2007-01-02
> **loell said:**
> yes, skype has a linux version , for voice calls, but no webcam capabilities yet.

your linux expirience would be more easier if you install automatix [http://www.getautomatix.com]("http://www.getautomatix.com")

its a gui script for installing skype , google earth, flash , codecs for playing  mp3 and videos , and a lot more

download and install the dapper 386 package [here]("http://www.getautomatix.com/wiki/index.php?title=Installation")

Excellent dude. Just used it to install a bunch of packages. Made things a lot easier, and I got skype working. Almost gave myself a heart attack from thinking there was a cost. lol, but i'm good now.

thanks again, you rock!

---

### Post by loell on 2007-01-02
you're welcome, glad that i could help :KS

---

### Post by justin_c18 on 2007-01-03
IS there anything I need to install to get my webcam working with gyachi, it's a logitech webcam.

I just hope this works, or hope I can get the webcam working...

---

### Post by justin_c18 on 2007-01-03
hrm, yeah someone with the newest YIM cannot communicate with me with video. It doesn't work. is there anything that I need to install to get this webcam working?:confused:

```
(gyachi:20535): Gtk-CRITICAL **: gtk_widget_set_events: assertion `!GTK_WIDGET_REALIZED (widget)' failed

(gyachi:20535): Pango-WARNING **: Error loading GPOS table 4097
```

---

### Post by loell on 2007-01-03
what is your webcam's model? or do

```
lsusb
```

in the command line.

you can also launch ekiga and click the webcam icon,
see if your webcam is detected and working in ubuntu.

---

### Post by justin_c18 on 2007-01-04
Bus 001 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000

I've installed Easy Cam, it has installed the driver. It works with amsn. But not with gyachi and the newest YIM on windows. Not sure why, it keeps on saying that I don't have the right version of YIM or something like that in Windows, when the otherside tries to connect or something...

URl where I got the APT, and instruction on how to install Easy Cam.
[https://help.ubuntu.com/community/Webcam#head-f684dbd396e512a2911697e1a80bc5d00af4fbce](https://help.ubuntu.com/community/Webcam#head-f684dbd396e512a2911697e1a80bc5d00af4fbce)

---

### Post by loell on 2007-01-04
i see, its a v4l2 compliant webcam , gyachi is only v4l1 compliant, i think you need to recompile and pass a parrameter --enable-v4l2

---

### Post by justin_c18 on 2007-01-04
> **loell said:**
> i see, its a v4l2 compliant webcam , gyachi is only v4l1 compliant, i think you need to recompile and pass a parrameter --enable-v4l2

How can I do that? I can step around Linux, running is a challenge though.

I'm not sure where to get information about recompiling/passing the parameter/enabling-v412, Where can I find?

---

### Post by sabitha on 2007-01-06
i need your help loel
im personaly use ubuntu but my friends use vectorlinux. the problem is my friend use gyach for chat with me but his gyachi closed self (not long). he use the .rpm sources. here the message when he start the program :
> (gyachi:8974): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(gyachi:8974): Gtk-CRITICAL **: gtk_widget_set_events: assertion `!GTK_WIDGET_REALIZED (widget)' failed


(gyachi:8974): Gtk-CRITICAL **: gtk_widget_set_events: assertion `!GTK_WIDGET_REALIZED (widget)' failed

(gyachi:8974): Gtk-CRITICAL **: gtk_widget_set_events: assertion `!GTK_WIDGET_REALIZED (widget)' failed

and not for long the gyachi closed self. and hre´s the message :
> *** glibc detected *** free(): invalid next size (normal): 0x08686fd0 ***

i need your advise here about that

---

### Post by loell on 2007-01-06
> **sabitha said:**
> i need your help loel
im personaly use ubuntu but my friends use vectorlinux. the problem is my friend use gyach for chat with me but his gyachi closed self (not long). he use the .rpm sources. here the message when he start the program :


and not for long the gyachi closed self. and hre´s the message :


i need your advise here about that

hi sabitha :) , i'm not familiar with how vectorlinux works or how it installed the generic rpm for gyachi, as for the error, there could be many factors for the closing the program , different version of the libraries installed,  dependencies ,or a memory leak.

---

### Post by bren21 on 2007-01-08
hi, I am having trouble connecting to gyachi.  whenever I type in my sn and pw it either says incorrect password or invalid user.  I know the password and username are correct, but I am not sure if i am using the right server or not.  Which server should I log into, I have tried most of them with no luck.

---

### Post by loell on 2007-01-09
just try the first three servers in the list

---

### Post by bren21 on 2007-01-09
I tried those, it keeps on saying invalid user

---

### Post by loell on 2007-01-09
can you log in through gaim using those exact Username and password?

---

### Post by bren21 on 2007-01-10
yep, no problems logging into gaim

---

### Post by loell on 2007-01-10
i have no idea why it would say invalid user, try re-installing gyachi, see if you can log in.

---

### Post by PradeepSridharan on 2007-04-24
I am newbie to Ubuntu. I have installed Fiesty on my laptop and then later installed Gyachi meant for Edgy and it seems to work. However, whenever, I try to start a voice conversation I get stuck. The window says that Voice chat has been enabled and then says "Open PY voice chat" or something similar. However when the voice chat window opens, the name/alias list is empty and when I start the voice conference by clicking "RUN". Nothing happens.

Kindly guide me.
Pradeep.

---

### Post by loell on 2007-04-24
you must click the "ON" button to activate it.

---

### Post by PradeepSridharan on 2007-04-24
I did click on the ON button. Anyway, I shall give it a try again and let you know. Thanks again.
Pradeep.

---

### Post by justin_c18 on 2007-05-01
Where can I find a gyachi .deb for feisty?

---

### Post by loell on 2007-05-01
the edgy deb package is compatible with fiesty :)

---

### Post by justin_c18 on 2007-05-01
> **loell said:**
> the edgy deb package is compatible with fiesty :)

Awesome, thanks for the good news. Going to reformat my mother's computer and install it =)

---

### Post by thegreenman on 2007-05-02
can you force architecture on this for x64 amd? 

anyone tried it?

---

### Post by loell on 2007-05-02
you can chroot.

---

### Post by loell on 2007-05-03
just my update for fiesty :) , pls. refer to the first post.

or go directly to [Gyachi-sidetrack for fiesty]("http://ubuntuforums.org/showthread.php?t=431290")

---

### Post by Epperly on 2007-05-20
Can anyone show me gyachi for dapper drake please? :D Thank you!
nvm, lol... I'm dumb. Thanks!

---

### Post by CityofAsh on 2007-06-01
Running gyatchi on edgy 6.10.

Problems with sound drivers i think.
When i run pY!chat i get errors in the terminal

```
cityofash@CityofAsh-Debain:/etc/apt$ gyachi
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'V8235'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver return 
ed error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned er 
ror: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned err 
or: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
Error opening PCM device default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'V8235'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver return 
ed error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned er 
ror: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned err 
or: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA: Error opening PCM-playback device default


```

Any ideas on this one?

---

### Post by loell on 2007-06-01
perhaps your using oss, instead of alsa

---

### Post by CityofAsh on 2007-06-04
Well i did a little trouble shooting. V8235 is my onboard sound card. When i initially installed UBUNTU the card was enabled inthe bios. I had disabled it after the install. So to trouble shooting. I removed the PCI sound blaster and enabled the VIA onboard card. Amazing now i can hear all sounds just about. Gyachi i cannot hear people chatting in pY! Voice. I can now see screen names in the voice box now tho. Also my mic does not work. The only conclusion i can come to is remove and reinstall ALSA (if this is possible). Or format and reinstall Ubuntu all over again (not a very good option).  I would think enableing the onboard card would have fixed all of the errors. Anyway i do not wish to use the onboard card. When i get home from work i will see what i can figure out.  Any other suggestions would be appreciated.

Thanks for your quick responce.

~City

---

### Post by GoneWithTheWind on 2007-07-02
I'm using year old versions of gyachi and giam on ubuntu 6:06.

Is there a newer version of gyachi available that will work?

---

### Post by loell on 2007-07-02
i have a mod/hack version of gyachi , with newer icons , simpler spam controls in public chat, some interface cleanups, and an updated notifier.

but the problem is, i can't build a dapper deb , i only have fiesty deb.

 i posted the link since then, in the first post of this thread.

---

### Post by CityofAsh on 2007-07-02
I have 5.0 it works. Try changing  the servers to connect.

~City

---

### Post by loell on 2007-07-02
i think john is talking about newer version, not server connection plroblem ;)
and its not 5.0 its version is 1.0.5

---

### Post by CityofAsh on 2007-07-02
Yeah thats alright i forgot. I didn't feel like looking it up. I knew it had a 5 and a 0 in it.

---

### Post by VvWolverinevV on 2008-02-19
> **fabertawe said:**
> I have been working through installing it with Seryozha (with a view to making a How-To in the process)

Paul, were you ever able to make a how-to for installing GYachE on x86-64?

---

### Post by pburn on 2008-03-04
I am a linux newbie and i installed Gyachi ( on Gutsy) today. Although I can see the icon in my Applications --> Internet-->GyachE I, however when I click on the icon, nothing happens. I tried rebooting twice, but I am always met with the same fate. 
I was earlier trying to install Gyach (followed the instructions [http://ubuntuforums.org/showthread.php?t=69840](http://ubuntuforums.org/showthread.php?t=69840) ) but got an error "gyach: error while loading shared libraries: libgailutil.so.16: cannot open shared object file: No such file or directory".  Then I tried installing Gyachi, but it doesnt run either ...
Thanx

---

### Post by loell on 2008-03-04
what's the error when you, execute gyachi in the terminal/console?
and where did you download the deb package for your gutsy install?

---

### Post by pburn on 2008-03-04
Hi Loell,
 
when I type gyachi in console this is wht i get...

inder@inder-laptop:~$ gyachi &
[1] 6342
gyachi: error while loading shared libraries: libgailutil.so.16: cannot open shared object file: No such file or directory
inder@inder-laptop:~$ 

I downloaded it from the link you gave at  [http://ubuntuforums.org/showthread.php?t=431290&highlight=gyachi](http://ubuntuforums.org/showthread.php?t=431290&highlight=gyachi)

---

### Post by loell on 2008-03-04
strange, there shouldn't have this error.  anyways you could uninstall/install gyachi and also install **libgail-common**

---

### Post by pburn on 2008-03-04
reinstalled Gyachi 5 times ....nothing...still the same....do u think it might have to do something with GYACH installation...cause i was supposed to make a soft symbolic link in the instructions and then did something with ldconfig.... do u think tht might be causing a problem ? Plus i dont know how to remove tht symbolic link....

thank you Loell for your patience with a novice....thank you !

---

### Post by pburn on 2008-03-04
also when i try to update anything ...this is the message i get in my terminal, which i never saw before.. 

ldconfig deferred processing now taking place 

do u think this might have something to do ...

---

### Post by loell on 2008-03-04
hmm, i see.. your ldconfig might be messed up already :(
i don't know if theres a solution.

[https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/156041]("https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/156041")

---

### Post by pa28675 on 2008-03-19
Hi. When i tried to install Gyachi for Ubuntu 7.10 it gave me an error dependancy error for libasound2. But i have installed this using the synaptic package manager. Any clues to what i should do??? Thanks

---

### Post by loell on 2008-03-19
try to make sure that the gyachi package you install is for gutsy.

---

### Post by fabertawe on 2008-04-01
> **VvWolverinevV said:**
> Paul, were you ever able to make a how-to for installing GYachE on x86-64?

Apologies for the late reply, I've not been following the thread. I never got around to the x86_64 how-to unfortunately. When I moved from Gutsy to Hardy I was able to reuse my previous deb. As far as I recall compiling was a case of disabling the plugins and the voice component in the makefiles and installing a multitude of libs until it compiled. Video's always worked great.

Paul

---

### Post by loell on 2008-04-01
gyachi's ./configure had now an option, --disable-wine iirc to make 64bit compilation smoother :)

---

### Post by jhon_doe on 2008-05-25
hi, i am newbie here
i have install gyach enhanced v1.0.7
i am connect via proxy which require Authentication
when i tried to connect, there an error say 
"HTTP/1.0 407 Proxy Authentication Required"

where i must write user and password for my proxy ???
in Setup tab option there is no field which i can used to fill my uname n password..

please
:confused::confused::confused:

---

### Post by loell on 2008-05-26
please refer to the first post.

---


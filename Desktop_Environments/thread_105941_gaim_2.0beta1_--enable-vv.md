---
title: "gaim 2.0beta1 --enable-vv ??"
date: 2005-12-19
forum: Desktop Environments
---

### Post by _jB on 2005-12-19
Hey..
I'm trying to build gaim2.0 WITH video support, but keep running into problems :-k 

**./configure --enable-gnutls=yes --enable-vv=yes**
```
gaim 2.0.0cvs

Build Protocol Plugins........ : yes
Protocols to link statically.. :
Protocols to build dynamically : gg irc jabber msn novell oscar simple yahoo zephyr

UI Library.................... : GTK+ 2.x
SSL Library/Libraries......... : GNUTLS

Build with Plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : no
Build with Tk support......... : no
Build with Audio support...... : yes
Build with GtkSpell support... : no
Build with Voice/Video support : yes
Build with DBUS support....... : no
Build with Cyrus SASL support. : no
Has you....................... : yes


Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification.......: no

Print debugging messages...... : no

Gaim will be installed in /usr/local/bin.
Warning: You have an old copy of gaim at /usr/local/bin/gaim.

configure complete, now type 'make'
```

**make**
```
make[3]: Entering directory `/home/jb/Desktop/gaim/src/mediastreamer'
if /bin/sh ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../mediastreamer -I/usr/include -I/usr/include/speex  -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DG_LOG_DOMAIN=\"MediaStreamer\" -I/usr/include -I/usr/include/speex  -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -DHAVE_GLIB -Wall  -g -g -O2 -MT msrtprecv.lo -MD -MP -MF ".deps/msrtprecv.Tpo" -c -o msrtprecv.lo msrtprecv.c; \
then mv -f ".deps/msrtprecv.Tpo" ".deps/msrtprecv.Plo"; else rm -f ".deps/msrtprecv.Tpo"; exit 1; fi
msrtprecv.c: In function 'ms_rtp_recv_process':
msrtprecv.c:123: error: 'struct _RtpSession' has no member named 'payload_type'
make[3]: *** [msrtprecv.lo] Error 1
make[3]: Leaving directory `/home/jb/Desktop/gaim/src/mediastreamer'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jb/Desktop/gaim/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jb/Desktop/gaim'
make: *** [all] Error 2
```

Talked to a friend, and he thinks that it's **msrtprecv.lo** thats messing it up. So we thought, let's build **linphone**, but linphone complaines about missing the ffmpeg headers/libs :???: (could be us that's all wrong about this though :))
I tried googeling for ffmpeg header/libs but I can't find any. I have ffmpeg installed (via synaptic) but no headers there (if they are in the ffmpeg package I should have them installed ??)

Any ideas ?

---

### Post by canopus4320 on 2005-12-24
I was having the exact same problem here, I've even tried to compile oRTP from source with no luck. Finally, I got it working by removing all libortp0 and libortp0-dev packages and installing the ones that i've found here:
[Original Page in Google Groups]("http://groups.google.com/group/google-talk-open/browse_thread/thread/4dd012dfc38d830f/d029a032fbda528f")
Packages:
[ortp-dev_0.7.1-1_i386.deb]("http://lumumba.uhasselt.be/~takis/breezy/ortp-dev_0.7.1-1_i386.deb")
[ortp0_0.7.1-1_i386.deb]("http://lumumba.uhasselt.be/~takis/breezy/ortp0_0.7.1-1_i386.deb")

I hope this info help you solving that error.
Good luck!

---

### Post by GameGod on 2005-12-24
The -vv stuff is merged back into 2.0.0, but it's not integrated into any menues or anything (I'm pretty sure...)
So... you won't really get anything out of compiling it with -vv on ... :(

---


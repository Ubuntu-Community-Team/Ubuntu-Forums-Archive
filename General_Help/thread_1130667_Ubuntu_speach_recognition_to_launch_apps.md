---
title: "Ubuntu speach recognition to launch apps"
date: 2009-04-20
forum: General Help
---

### Post by ajhtiredwolf on 2009-04-20
There was a program I found tat could use speach recognition from sphynx2, in order to launch applications called perlbox-voice however it is extremely old and doesn't seem to function well aynmore. I was wondering if anyone knew of a something that had replaced it or something else I could use? I searched and was unable to find anything, thank you.

---

### Post by xRes on 2009-04-20
Opera comes with limited voice activated control. Of course that only works within the browser though so probably doesn't help your question...

---

### Post by hesjnet on 2009-04-20
Acording to [Wikipedia]("http://en.wikipedia.org/wiki/Linux_speech_recognition_software#Current_development_status") the [GnomeVoiceControl]("http://live.gnome.org/GnomeVoiceControl") should do the job.

> GnomeVoiceControl is a dialogue system to control the GNOME Desktop that was developed in the Google Summer of Code in 2007.

---

### Post by ajhtiredwolf on 2009-04-20
Thank you, but unfortuantely  after sudo apt-get install gnome-voice-control,then trying to run the program, I was unsuccessful. Pressing the "start voice" button does nothing, it SHOULD say idle, calibrating, then started. So I went ahead and tried to install it from source, trying to install version .03 gave me this error on make



/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/local/include/sphinxbase -I/usr/local/include/pocketsphinx      -g -O2 -MT gstsphinxsink.o -MD -MP -MF ".deps/gstsphinxsink.Tpo" -c -o gstsphinxsink.o gstsphinxsink.c; \
	then mv -f ".deps/gstsphinxsink.Tpo" ".deps/gstsphinxsink.Po"; else rm -f ".deps/gstsphinxsink.Tpo"; exit 1; fi
In file included from gstsphinxsink.c:33:
gstsphinxsink.h:32:17: error: fbs.h: No such file or directory
gstsphinxsink.c:321: error: expected declaration specifiers or ‘...’ before ‘s2_fsg_trans_t’
gstsphinxsink.c: In function ‘gst_sphinx_construct_trans_list’:
gstsphinxsink.c:325: error: ‘s2_fsg_trans_t’ undeclared (first use in this function)
gstsphinxsink.c:325: error: (Each undeclared identifier is reported only once
gstsphinxsink.c:325: error: for each function it appears in.)
gstsphinxsink.c:325: error: ‘transitions’ undeclared (first use in this function)
gstsphinxsink.c:337: error: expected expression before ‘)’ token
gstsphinxsink.c:360: error: ‘trans_list’ undeclared (first use in this function)
gstsphinxsink.c: In function ‘gst_sphinx_sink_set_fsg’:
gstsphinxsink.c:371: error: ‘s2_fsg_t’ undeclared (first use in this function)
gstsphinxsink.c:371: error: expected ‘;’ before ‘fsg’
gstsphinxsink.c:372: error: ‘s2_fsg_trans_t’ undeclared (first use in this function)
gstsphinxsink.c:372: error: ‘trans_list’ undeclared (first use in this function)
gstsphinxsink.c:374: error: ‘fsg’ undeclared (first use in this function)
gstsphinxsink.c:375: error: too many arguments to function ‘gst_sphinx_construct_trans_list’
make[2]: *** [gstsphinxsink.o] Error 1
make[2]: Leaving directory `/home/wolf/Documents/gnome-voice-control-0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/w















I also tried verison 0.2 unsuccesfully, the version that is apt-get is 0.2

---

### Post by frenchn00b on 2009-09-12
get those tar.gz:
```

pocketsphinx-0.4.1.tar.gz

sphinxbase-0.3.tar.gz
```


and tar xvf them
then ```
./autogen.sh
./configure
make 
make install
```

start first with sphinxbase-0.3

Enjoy !!

---

### Post by cabez0n on 2009-10-20
Has any of you has tried gnome-voice-control 0.4 on amd64 ?
In my case it builds and installs correctly but i can't find the applet to add to the panel.

---


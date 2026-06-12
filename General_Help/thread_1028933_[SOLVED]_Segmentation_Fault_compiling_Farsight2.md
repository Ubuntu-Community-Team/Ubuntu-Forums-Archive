---
title: "[SOLVED] Segmentation Fault compiling Farsight2"
date: 2009-01-02
forum: General Help
---

### Post by maddog46113 on 2009-01-02
Ive been having troubles compiling software lately...

most of the software i try to compile i get this

```

fs-rtp-stream.c: In function &#8216;_state_changed&#8217;:
fs-rtp-stream.c:718: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
make[4]: *** [libfsrtpconference_la-fs-rtp-stream.lo] Error 1
make[4]: Leaving directory `/home/aaron/farsight2/gst/fsrtpconference'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/aaron/farsight2/gst/fsrtpconference'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/aaron/farsight2/gst'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aaron/farsight2'
make: *** [all] Error 2

```

Now im trying to compile Farsight2 so i can compile amsn with webcam support for my particular webcam. I dont know what to do. Ive tried reinstalling automake but I havent got anywhere. I have build essential installed. maybe im missing something. :confused::confused::confused:

Sengmentation faults happen randomly heres another output after another try 

```

/usr/include/libxml2/libxml/parser.h:790: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;*&#8217; token
cc1: warnings being treated as errors
/usr/include/libxml2/libxml/parser.h:792: error: type defaults to &#8216;int&#8217; in declaration of &#8216;xmlParserInputPtr&#8217;
/usr/include/libxml2/libxml/parser.h:792: error: &#8216;xmlParserInputPtr&#8217; declared as function returning a function
In file included from /usr/include/libxml2/libxml/globals.h:20,
                 from /usr/include/libxml2/libxml/xmlIO.h:117,
                 from /usr/include/libxml2/libxml/parser.h:799,
                 from /usr/include/gstreamer-0.10/gst/gstconfig.h:171,
                 from /usr/include/gstreamer-0.10/gst/gstelement.h:51,
                 from /usr/include/gstreamer-0.10/gst/gstbin.h:27,
                 from /usr/include/gstreamer-0.10/gst/gst.h:34,
                 from ./pyfarsight.override:6:
/usr/include/libxml2/libxml/SAX.h:65: error: &#8216;resolveEntity&#8217; declared as function returning a function
In file included from /usr/include/libxml2/libxml/globals.h:21,
                 from /usr/include/libxml2/libxml/xmlIO.h:117,
                 from /usr/include/libxml2/libxml/parser.h:799,
                 from /usr/include/gstreamer-0.10/gst/gstconfig.h:171,
                 from /usr/include/gstreamer-0.10/gst/gstelement.h:51,
                 from /usr/include/gstreamer-0.10/gst/gstbin.h:27,
                 from /usr/include/gstreamer-0.10/gst/gst.h:34,
                 from ./pyfarsight.override:6:
/usr/include/libxml2/libxml/SAX2.h:63: error: &#8216;xmlSAX2ResolveEntity&#8217; declared as function returning a function
In file included from /usr/include/libxml2/libxml/parser.h:799,
                 from /usr/include/gstreamer-0.10/gst/gstconfig.h:171,
                 from /usr/include/gstreamer-0.10/gst/gstelement.h:51,
                 from /usr/include/gstreamer-0.10/gst/gstbin.h:27,
                 from /usr/include/gstreamer-0.10/gst/gst.h:34,
                 from ./pyfarsight.override:6:
/usr/include/libxml2/libxml/xmlIO.h:286: error: &#8216;xmlCheckHTTPInput&#8217; declared as function returning a function
/usr/include/libxml2/libxml/xmlIO.h:294: error: &#8216;xmlNoNetExternalEntityLoader&#8217; declared as function returning a function
In file included from /usr/include/gstreamer-0.10/gst/gstconfig.h:171,
                 from /usr/include/gstreamer-0.10/gst/gstelement.h:51,
                 from /usr/include/gstreamer-0.10/gst/gstbin.h:27,
                 from /usr/include/gstreamer-0.10/gst/gst.h:34,
                 from ./pyfarsight.override:6:
/usr/include/libxml2/libxml/parser.h:1030: error: &#8216;xmlNewIOInputStream&#8217; declared as function returning a function
/usr/include/libxml2/libxml/parser.h:1054: error: expected &#8216;)&#8217; before &#8216;f&#8217;
/usr/include/libxml2/libxml/parser.h:1056: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;xmlGetExternalEntityLoader&#8217;
/usr/include/libxml2/libxml/parser.h:1060: error: &#8216;xmlLoadExternalEntity&#8217; declared as function returning a function
make[3]: *** [pyfarsight.lo] Error 1
make[3]: Leaving directory `/home/aaron/farsight2/python'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/aaron/farsight2/python'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aaron/farsight2'
make: *** [all] Error 2


```

---

### Post by Rainstride on 2009-01-02
> **maddog46113 said:**
> Ive been having troubles compiling software lately...

most of the software i try to compile i get this

```

fs-rtp-stream.c: In function ‘_state_changed’:
fs-rtp-stream.c:718: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
make[4]: *** [libfsrtpconference_la-fs-rtp-stream.lo] Error 1
make[4]: Leaving directory `/home/aaron/farsight2/gst/fsrtpconference'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/aaron/farsight2/gst/fsrtpconference'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/aaron/farsight2/gst'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aaron/farsight2'
make: *** [all] Error 2

```

Now im trying to compile Farsight2 so i can compile amsn with webcam support for my particular webcam. I dont know what to do. Ive tried reinstalling automake but I havent got anywhere. I have build essential installed. maybe im missing something. :confused::confused::confused:

Sengmentation faults happen randomly heres another output after another try 

```

/usr/include/libxml2/libxml/parser.h:790: error: expected declaration specifiers or ‘...’ before ‘*’ token
cc1: warnings being treated as errors
/usr/include/libxml2/libxml/parser.h:792: error: type defaults to ‘int’ in declaration of ‘xmlParserInputPtr’
/usr/include/libxml2/libxml/parser.h:792: error: ‘xmlParserInputPtr’ declared as function returning a function
In file included from /usr/include/libxml2/libxml/globals.h:20,
                 from /usr/include/libxml2/libxml/xmlIO.h:117,
                 from /usr/include/libxml2/libxml/parser.h:799,
                 from /usr/include/gstreamer-0.10/gst/gstconfig.h:171,
                 from /usr/include/gstreamer-0.10/gst/gstelement.h:51,
                 from /usr/include/gstreamer-0.10/gst/gstbin.h:27,
                 from /usr/include/gstreamer-0.10/gst/gst.h:34,
                 from ./pyfarsight.override:6:
/usr/include/libxml2/libxml/SAX.h:65: error: ‘resolveEntity’ declared as function returning a function
In file included from /usr/include/libxml2/libxml/globals.h:21,
                 from /usr/include/libxml2/libxml/xmlIO.h:117,
                 from /usr/include/libxml2/libxml/parser.h:799,
                 from /usr/include/gstreamer-0.10/gst/gstconfig.h:171,
                 from /usr/include/gstreamer-0.10/gst/gstelement.h:51,
                 from /usr/include/gstreamer-0.10/gst/gstbin.h:27,
                 from /usr/include/gstreamer-0.10/gst/gst.h:34,
                 from ./pyfarsight.override:6:
/usr/include/libxml2/libxml/SAX2.h:63: error: ‘xmlSAX2ResolveEntity’ declared as function returning a function
In file included from /usr/include/libxml2/libxml/parser.h:799,
                 from /usr/include/gstreamer-0.10/gst/gstconfig.h:171,
                 from /usr/include/gstreamer-0.10/gst/gstelement.h:51,
                 from /usr/include/gstreamer-0.10/gst/gstbin.h:27,
                 from /usr/include/gstreamer-0.10/gst/gst.h:34,
                 from ./pyfarsight.override:6:
/usr/include/libxml2/libxml/xmlIO.h:286: error: ‘xmlCheckHTTPInput’ declared as function returning a function
/usr/include/libxml2/libxml/xmlIO.h:294: error: ‘xmlNoNetExternalEntityLoader’ declared as function returning a function
In file included from /usr/include/gstreamer-0.10/gst/gstconfig.h:171,
                 from /usr/include/gstreamer-0.10/gst/gstelement.h:51,
                 from /usr/include/gstreamer-0.10/gst/gstbin.h:27,
                 from /usr/include/gstreamer-0.10/gst/gst.h:34,
                 from ./pyfarsight.override:6:
/usr/include/libxml2/libxml/parser.h:1030: error: ‘xmlNewIOInputStream’ declared as function returning a function
/usr/include/libxml2/libxml/parser.h:1054: error: expected ‘)’ before ‘f’
/usr/include/libxml2/libxml/parser.h:1056: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘xmlGetExternalEntityLoader’
/usr/include/libxml2/libxml/parser.h:1060: error: ‘xmlLoadExternalEntity’ declared as function returning a function
make[3]: *** [pyfarsight.lo] Error 1
make[3]: Leaving directory `/home/aaron/farsight2/python'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/aaron/farsight2/python'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aaron/farsight2'
make: *** [all] Error 2


```

i keep getting the same thing when i was trying to compile zsnes, pcsx,pcsx2, and a few other programs. it always happens during "make", i think its a bug of some kind.

---

### Post by maddog46113 on 2009-01-02
Seems like it... However

I just got it to compile correctly....

I had to use make clean after ./configure...

```

sudo ./configure
sudo make clean
sudo make
sudo make install

```

Im pretty sure it is a bug tho

[https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/211255](https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/211255)

---

### Post by Rainstride on 2009-01-02
> **maddog46113 said:**
> Seems like it... However

I just got it to compile correctly....

I had to use make clean after ./configure...

```

sudo ./configure
sudo make clean
sudo make
sudo make install

```

Im pretty sure it is a bug tho

[https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/211255](https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/211255)

ill try that and see if it works for me.

---

### Post by Rainstride on 2009-01-02
no luck, still get error 1 during make (and make clean).

> g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=native -O3 -fomit-frame-pointer -s -fno-rtti -o tools/strutil.o -c tools/strutil.cpp
In file included from tools/strutil.cpp:22:
tools/strutil.h: In static member function &#8216;static int ci_char_traits::compare(const char*, const char*, size_t)&#8217;:
tools/strutil.h:34: error: &#8216;strncasecmp&#8217; was not declared in this scope
make: *** [tools/strutil.o] Error 1


---


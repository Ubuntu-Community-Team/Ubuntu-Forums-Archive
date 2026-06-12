---
title: "Fonomo - Video Conferencing in Pidgin"
date: 2009-05-18
forum: General Help
---

### Post by krnekhelesh on 2009-05-18
Hi,

I'm trying to install fonomo pluggin for pidgin 2.5.5. Unfortunately they only provide the source code and not a easy to install .deb file.

I read the instruction and it asked me to install it using the following command
**make all install-user**

I tried running the command in the terminal but I get the following error

```
ik@nik-laptop:~/Desktop/pidgin-fonomobutton-0.1.5$ make all install-nik
gcc `pkg-config pidgin --cflags --libs` --shared -Wall -O2 fonomobutton.c -o fonomobutton.so
fonomobutton.c: In function ‘send_button_cb’:
fonomobutton.c:65: warning: format not a string literal and no format arguments
fonomobutton.c:68: warning: format not a string literal and no format arguments
fonomobutton.c: In function ‘create_fonomo_button_pidgin’:
fonomobutton.c:112: warning: passing argument 2 of ‘gtk_icon_theme_choose_icon’ from incompatible pointer type
make: *** No rule to make target `install-nik'.  Stop.

```

Can anyone help me?

---

### Post by lilshelil on 2009-07-28
Im getting the same thing except i have:

No rule to make target "all". Stop.

Help?

---

### Post by ewindisch on 2009-07-29
I'm with Fonomo.com -- I've uploaded a fix as version 0.1.6.  Please try this and report back!

[ftp://ftp.grokthis.net/pub/fonomo/pidgin-fonomobutton-0.1.6.tar.bz2](ftp://ftp.grokthis.net/pub/fonomo/pidgin-fonomobutton-0.1.6.tar.bz2)

---

### Post by lilshelil on 2009-07-29
shelly@dell-desktop:~/Desktop/pidgin-fonomobutton-0.1.6$ make all install-shelly
gcc -fPIC `pkg-config pidgin --cflags --libs` --shared -Wall -O2 fonomobutton.c -o fonomobutton.so
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
fonomobutton.c:25:18: error: glib.h: No such file or directory
fonomobutton.c:36:20: error: notify.h: No such file or directory
fonomobutton.c:37:20: error: plugin.h: No such file or directory
fonomobutton.c:38:21: error: version.h: No such file or directory
fonomobutton.c:40:20: error: pidgin.h: No such file or directory
fonomobutton.c:42:21: error: gtkconv.h: No such file or directory
fonomobutton.c:43:23: error: gtkplugin.h: No such file or directory
fonomobutton.c:45:26: error: conversation.h: No such file or directory
fonomobutton.c:46:24: error: gtkconvwin.h: No such file or directory
fonomobutton.c:48:23: error: gtkimhtml.h: No such file or directory
fonomobutton.c:55: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
fonomobutton.c:87: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
fonomobutton.c:132: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
fonomobutton.c:152: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_load&#8217;
fonomobutton.c:175: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_unload&#8217;
fonomobutton.c:193: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;info&#8217;
fonomobutton.c:227: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
fonomobutton.c:231: warning: return type defaults to &#8216;int&#8217;
fonomobutton.c: In function &#8216;PURPLE_INIT_PLUGIN&#8217;:
fonomobutton.c:231: error: expected &#8216;{&#8217; at end of input
make: *** [all] Error 1
shelly@dell-desktop:~/Desktop/pidgin-fonomobutton-0.1.6$





That was what happened. Maybe i am doing something wrong? Im a noob at this. :(
Do i need the purple plugin in order to install this?

---

### Post by ewindisch on 2009-07-30
It is necessary to first install pidgin-dev (sudo apt-get install pidgin-dev), in order to compile Pidgin plugins.

---

### Post by lilshelil on 2009-08-01
shelly@dell-desktop:~/Desktop$
cd /home/shelly/Desktop/pidgin-fonomobutton-0.1.6shelly@dell-desktop:~/Desktop/pidgin-fonomobutton-0.1.6$ make all install-shelly
gcc -fPIC `pkg-config pidgin --cflags --libs` --shared -Wall -O2 fonomobutton.c -o fonomobutton.so
fonomobutton.c: In function ‘send_button_cb’:
fonomobutton.c:65: warning: format not a string literal and no format
arguments
fonomobutton.c:68: warning: format not a string literal and no format
arguments
fonomobutton.c: In function ‘create_fonomo_button_pidgin’:
fonomobutton.c:112: warning: passing argument 2 of
‘gtk_icon_theme_choose_icon’ from incompatible pointer type
make: *** No rule to make target `install-shelly'.  Stop.


shelly@dell-desktop:~/Desktop/pidgin-fonomobutton-0.1.6$ sudo su


root@dell-desktop:/home/shelly/Desktop/pidgin-fonomobutton-0.1.6# make
all install
gcc -fPIC `pkg-config pidgin --cflags --libs` --shared -Wall -O2
fonomobutton.c -o fonomobutton.so
fonomobutton.c: In function ‘send_button_cb’:
fonomobutton.c:65: warning: format not a string literal and no format
arguments
fonomobutton.c:68: warning: format not a string literal and no format
arguments
fonomobutton.c: In function ‘create_fonomo_button_pidgin’:
fonomobutton.c:112: warning: passing argument 2 of
‘gtk_icon_theme_choose_icon’ from incompatible pointer type
cp fonomobutton.so /usr/lib/pidgin
cp camera-fonomo.png /usr/share/icons/hicolor/22x22/devices/
root@dell-desktop:/home/shelly/Desktop/pidgin-fonomobutton-0.1.6# 



After i install pidgin-dev., i tried to 'make install-user' under the user but it didnt work.

Then, i did it under root.

The process went trough but i couldnt see the button in the pidgin window.

I went to the pidgin plug-in window and there it is, the option to activate it. Which i did. Surely enough the fonomo button on the right side showed up.

Havent tried to V-chat w. anyone yet, but if any problems occur i will report back.

Thanks a bunch!!! :KS

---

### Post by cmiller57 on 2009-11-04
I downloaded the 1.6 version and get the following error message when compiling. Any help?

gcc -fPIC `pkg-config pidgin --cflags --libs` --shared -Wall -O2 fonomobutton.c -o fonomobutton.so
fonomobutton.c: In function &#8216;send_button_cb&#8217;:
fonomobutton.c:65: warning: format not a string literal and no format arguments
fonomobutton.c:68: warning: format not a string literal and no format arguments
fonomobutton.c: In function &#8216;create_fonomo_button_pidgin&#8217;:
fonomobutton.c:112: warning: passing argument 2 of &#8216;gtk_icon_theme_choose_icon&#8217; from incompatible pointer type
/usr/bin/ld: cannot find -lpurple
collect2: ld returned 1 exit status
make: *** [all] Error 1

---

### Post by ewindisch on 2009-11-05
cmiller57:  It is necessary to first install pidgin-dev (sudo apt-get install pidgin-dev), in order to compile Pidgin plugins.  This should automatically include the libpurple-dev package as a dependancy.

---


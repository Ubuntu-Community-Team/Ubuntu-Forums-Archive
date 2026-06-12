---
title: "Easy_e17 is not working for me: bunch of stuff is missing"
date: 2008-10-24
forum: Desktop Environments
---

### Post by MaxIBoy on 2008-10-24
When I run the script with the "-i" command, my distro is detected as Debian. It seems to work, but after spitting out a bunch of the typical build process gibbrish, I get this:

```
gcc: /usr/lib/libltdl.so: No such file or directory
make[5]: *** [libesmart_container.la] Error 1
make[5]: Leaving directory `/home/maxtothemax/e17_src/esmart/src/lib/esmart_container'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/maxtothemax/e17_src/esmart/src/lib/esmart_container'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/maxtothemax/e17_src/esmart/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/maxtothemax/e17_src/esmart/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/maxtothemax/e17_src/esmart/src'
make: *** [all-recursive] Error 1
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/esmart.log'!

maxtothemax@maxtothemax-laptop:~$ 

```

When I run it with "--skip=esmart," and it doesn't crash until later:
```
-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation
- apps-compilation and installation
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- imlib2 ..................... previously installed
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... SKIPPED
- emotion .................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking whether to build static libraries... yes
configure: creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EVAS... yes
checking for EDJE... yes
checking for ECORE... yes
checking Ecore_X.h usability... yes
checking Ecore_X.h presence... yes
checking for Ecore_X.h... yes
checking Ecore_Fb.h usability... no
checking Ecore_Fb.h presence... no
checking for Ecore_Fb.h... no
checking for VLC... no
checking for XINE... configure: error: Package requirements (libxine >= 1.1.1) were not met:

No package 'libxine' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XINE_CFLAGS
and XINE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/emotion.log'!

maxtothemax@maxtothemax-laptop:~$ 

```
I can't for the life of me find libxine anywhere, on the Internet or otherwise (except in rpm format, but I don't want to resort to Alien if I can help it.)

All right, so I'll skip emotion as well:
```
------------------------------ Installing packages -----------------------------
- imlib2 ..................... previously installed
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ ok          
- etk_extra .................. ok          
- ewl ........................ ok          
- exml ....................... ok          
- enhance .................... ok                  
- e_dbus ..................... ok          
- exalt ...................... ok          
- e .......................... ok          
- entrance ................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for X... /usr/bin/X
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EVAS... yes
checking for ECORE... yes
checking for EDJE... yes
checking for ESMART... configure: error: Package requirements (
  esmart_container >= 0.9.0
  esmart_text_entry >= 0.9.0
) were not met:

No package 'esmart_container' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ESMART_CFLAGS
and ESMART_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/entrance.log'!

maxtothemax@maxtothemax-laptop:~$ 


```


Fine, I'll skip entrance too, it's probably unimportant anyway:
```
------------------------------ Installing packages -----------------------------
- imlib2 ..................... previously installed
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ previously installed
- etk_extra .................. previously installed
- ewl ........................ previously installed
- exml ....................... previously installed
- enhance .................... previously installed
- e_dbus ..................... previously installed
- exalt ...................... previously installed
- e .......................... previously installed
- entrance ................... SKIPPED
- edje_editor ................ ok          
- edje_player ................ ok          
- elicit ..................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking if malloc debugging is wanted... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ELICIT... configure: error: Package requirements (
  imlib2
  evas
  eet
  esmart_draggies
  esmart_container
  ecore
  ecore-config
  ecore-evas
  ecore-file
  edje
) were not met:

No package 'esmart_container' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ELICIT_CFLAGS
and ELICIT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/elicit.log'!

maxtothemax@maxtothemax-laptop:~$ 


```


Okay, what the heck, I'll skip elicit too.
```
------------------------------ Installing packages -----------------------------
- imlib2 ..................... previously installed
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ previously installed
- etk_extra .................. previously installed
- ewl ........................ previously installed
- exml ....................... previously installed
- enhance .................... previously installed
- e_dbus ..................... previously installed
- exalt ...................... previously installed
- e .......................... previously installed
- entrance ................... SKIPPED
- edje_editor ................ previously installed
- edje_player ................ previously installed
- elicit ..................... SKIPPED
- elitaire ................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ELITAIRE... configure: error: Package requirements (
  eet
  evas
  ecore
  ecore-config
  ecore-evas
  ecore-file
  edje
  esmart_container
  esmart_draggies
  esmart_resize
  ewl
) were not met:

No package 'esmart_container' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ELITAIRE_CFLAGS
and ELITAIRE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/elitaire.log'!

maxtothemax@maxtothemax-laptop:~$ 

```


Fine, I'll try skipping elitaire:
```
------------------------------ Installing packages -----------------------------
- imlib2 ..................... previously installed
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ previously installed
- etk_extra .................. previously installed
- ewl ........................ previously installed
- exml ....................... previously installed
- enhance .................... previously installed
- e_dbus ..................... previously installed
- exalt ...................... previously installed
- e .......................... previously installed
- entrance ................... SKIPPED
- edje_editor ................ previously installed
- edje_player ................ previously installed
- elicit ..................... SKIPPED
- elitaire ................... SKIPPED
- enna ....................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
gcc -DHAVE_CONFIG_H -I. -I../.. -DPACKAGE_LIB_DIR=\"/opt/e17/lib\" -DPACKAGE_DATA_DIR=\""/opt/e17/share"\"  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina   -I/usr/include/libxml2    -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_REENTRANT -MT event_key.o -MD -MP -MF .deps/event_key.Tpo -c -o event_key.o event_key.c
mv -f .deps/mediaplayer.Tpo .deps/mediaplayer.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -DPACKAGE_LIB_DIR=\"/opt/e17/lib\" -DPACKAGE_DATA_DIR=\""/opt/e17/share"\"  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina   -I/usr/include/libxml2    -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_REENTRANT -MT list_item.o -MD -MP -MF .deps/list_item.Tpo -c -o list_item.o list_item.c
mv -f .deps/event_key.Tpo .deps/event_key.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -DPACKAGE_LIB_DIR=\"/opt/e17/lib\" -DPACKAGE_DATA_DIR=\""/opt/e17/share"\"  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina   -I/usr/include/libxml2    -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_REENTRANT -MT xml_utils.o -MD -MP -MF .deps/xml_utils.Tpo -c -o xml_utils.o xml_utils.c
mv -f .deps/list_item.Tpo .deps/list_item.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -DPACKAGE_LIB_DIR=\"/opt/e17/lib\" -DPACKAGE_DATA_DIR=\""/opt/e17/share"\"  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina   -I/usr/include/libxml2    -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_REENTRANT -MT url_utils.o -MD -MP -MF .deps/url_utils.Tpo -c -o url_utils.o url_utils.c
mv -f .deps/xml_utils.Tpo .deps/xml_utils.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -DPACKAGE_LIB_DIR=\"/opt/e17/lib\" -DPACKAGE_DATA_DIR=\""/opt/e17/share"\"  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina   -I/usr/include/libxml2    -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_REENTRANT -MT md5.o -MD -MP -MF .deps/md5.Tpo -c -o md5.o md5.c
In file included from url_utils.c:2:
url_utils.h:4:23: error: curl/curl.h: No such file or directory
url_utils.h:5:24: error: curl/types.h: No such file or directory
url_utils.h:6:23: error: curl/easy.h: No such file or directory
In file included from url_utils.c:2:
url_utils.h:15: error: expected ‘)’ before ‘*’ token
url_utils.c:20: error: expected ‘)’ before ‘*’ token
make[3]: *** [url_utils.o] Error 1
make[3]: *** Waiting for unfinished jobs....
mv -f .deps/md5.Tpo .deps/md5.Po
make[3]: Leaving directory `/home/maxtothemax/e17_src/MISC/enna/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/maxtothemax/e17_src/MISC/enna/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/maxtothemax/e17_src/MISC/enna'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/enna.log'!

maxtothemax@maxtothemax-laptop:~$ 
```

Have I made my point?

---

### Post by almahtar on 2008-11-29
```
gcc: /usr/lib/libltdl.so: No such file or directory

```
Install the libltdl3-dev package and anything that depends on it (sudo apt-get install libltdl3-dev)

```

checking for VLC... no
checking for XINE... configure: error: Package requirements (libxine >= 1.1.1) were not met:

No package 'libxine' found

```
Install vlc, vlc0-dev, libxine0-dev and their dependents (sudo apt-get install vlc vlc-dev libxine0-dev )


```

In file included from url_utils.c:2:
url_utils.h:4:23: error: curl/curl.h: No such file or directory
url_utils.h:5:24: error: curl/types.h: No such file or directory
url_utils.h:6:23: error: curl/easy.h: No such file or directory

```

Install libcurl4-gnutls-dev (sudo apt-get install libcurl4-gnutls-dev)

You'll probably also need libtheora-dev and a few others.  Whenever it errors out on something open up synaptic, click in the package list window, and type "libwhatever" (where whatever is xine, curl, etc) and look for the -dev version of it.

Note: If it complains about missing XKBRules.h, it's provided by libxkbfile-dev.

I just got it building perfectly but I had to install some -dev packages to get there, for sure. I'd keep a list of them but it would be incomplete anyway because I already had a lot of them installed.

---

### Post by jaguarcat311 on 2008-11-30
I have a similar problem, but mine is an error on e....

------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ previously installed
- etk_extra .................. previously installed
- ewl ........................ previously installed
- exml ....................... SKIPPED
- enhance .................... SKIPPED
- e_dbus ..................... previously installed
- exalt ...................... SKIPPED
- e .......................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
make[2]: Entering directory `/var/cache/e17_src/e/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/var/cache/e17_src/e/doc'
Making all in po
make[2]: Entering directory `/var/cache/e17_src/e/po'
test -z "bg.gmo ca.gmo cs.gmo de.gmo el.gmo eo.gmo es.gmo fi.gmo fr.gmo fr_CH.gmo hu.gmo it.gmo ja.gmo ko.gmo pt_BR.gmo ru.gmo sl.gmo zh_CN.gmo zh_TW.gmo" || make bg.gmo ca.gmo cs.gmo de.gmo el.gmo eo.gmo es.gmo fi.gmo fr.gmo fr_CH.gmo hu.gmo it.gmo ja.gmo ko.gmo pt_BR.gmo ru.gmo sl.gmo zh_CN.gmo zh_TW.gmo
make[3]: Entering directory `/var/cache/e17_src/e/po'
make[3]: `bg.gmo' is up to date.
make[3]: `ca.gmo' is up to date.
rm -f cs.gmo && /usr/bin/msgfmt -c --statistics -o cs.gmo cs.po
rm -f de.gmo && /usr/bin/msgfmt -c --statistics -o de.gmo de.po
cs.po:1180: number of format specifications in 'msgid' and 'msgstr' does not match
cs.po:4188: 'msgstr' is not a valid C format string, unlike 'msgid'. Reason: In the directive number 1, the character ' ' is not a valid conversion specifier.
cs.po:5639: format specifications in 'msgid' and 'msgstr' for argument 2 are not the same
/usr/bin/msgfmt: found 3 fatal errors
533 translated messages, 23 fuzzy translations, 832 untranslated messages.
make[3]: *** [cs.gmo] Error 1
make[3]: *** Waiting for unfinished jobs....
1096 translated messages, 223 fuzzy translations, 69 untranslated messages.
make[3]: Leaving directory `/var/cache/e17_src/e/po'
make[2]: *** [stamp-po] Error 2
make[2]: Leaving directory `/var/cache/e17_src/e/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/e'
make: *** [all] Error 2
--------------------------------------------------------------------------------

Not exactly sure what to do. seems that if I try installing e17-svn, everything goes fine, but my xclient script entries are outdated and I dont think its trying to start the correct e17. I still have entries for e16, matchbox and kde, though those have been removed from the system

---

### Post by MaxIBoy on 2008-12-27
> **almahtar said:**
> ```
gcc: /usr/lib/libltdl.so: No such file or directory

```
Install the libltdl3-dev package and anything that depends on it (sudo apt-get install libltdl3-dev)

```

checking for VLC... no
checking for XINE... configure: error: Package requirements (libxine >= 1.1.1) were not met:

No package 'libxine' found

```
Install vlc, vlc0-dev, libxine0-dev and their dependents (sudo apt-get install vlc vlc-dev libxine0-dev )


```

In file included from url_utils.c:2:
url_utils.h:4:23: error: curl/curl.h: No such file or directory
url_utils.h:5:24: error: curl/types.h: No such file or directory
url_utils.h:6:23: error: curl/easy.h: No such file or directory

```

Install libcurl4-gnutls-dev (sudo apt-get install libcurl4-gnutls-dev)

You'll probably also need libtheora-dev and a few others.  Whenever it errors out on something open up synaptic, click in the package list window, and type "libwhatever" (where whatever is xine, curl, etc) and look for the -dev version of it.

Note: If it complains about missing XKBRules.h, it's provided by libxkbfile-dev.

I just got it building perfectly but I had to install some -dev packages to get there, for sure. I'd keep a list of them but it would be incomplete anyway because I already had a lot of them installed.

Yeah, sorry it took so long for me to get back to you. I'll try that.

---


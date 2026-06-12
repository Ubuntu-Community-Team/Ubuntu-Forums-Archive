---
title: "What is locale??"
date: 2005-05-15
forum: Desktop Environments
---

### Post by makis on 2005-05-15
Hi all,

I try to run some apps and I receive an error I cannot understand and fix.
for example, when I try to run MinGWStudio (a C/C++ IDE) I have the following feedback:


[b] makis@ubuntu:~/temp/MinGWStudio$ sudo ./MinGWStudio
 Password:

 (process:22689): Gdk-WARNING **: locale not supported by Xlib
 (process:22689): Gdk-WARNING **: can not set locale modifiers

(MinGWStudio:22689): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(MinGWStudio:22689): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory

** (MinGWStudio:22689): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
 Failed to load Pango module for id: 'BasicScriptEngineFc'

 ** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
 aborting...
 Aborted[/b]     


Let me tell you that the paths/files:

/usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so
/usr/lib/pango/1.4.0/modules/pango-basic-fc.so

are there (not missing).

I have the same problem when I try to run Nvu, and other apps..](*,)

I think I have to change locale from UTF-8 to ISO-8859-1, but I do not know how!


Any help please?

Thx in advance

---

### Post by abhaysahai on 2005-05-16
type tha command 
"locale" to get the locale.
try 
"locale -a" to know all the installed locale on you system.
synaptic to install more locales.

Abhay

---

### Post by Sam on 2005-05-16
[QUOTE=abhaysahai]type tha command 
"locale" to get the locale.
try 
"locale -a" to know all the installed locale on you system.
synaptic to install more locales.

Abhay[/QUOTE]
To configure the locales:
```
$ sudo dpkg-reconfigure locales
```

---

### Post by makis on 2005-05-16
thx very much my friends!

I try

**root@ubuntu:/home/makis # sudo dpkg-reconfigure locales**

and I choose just en_GB.ISO-8859-1 and en_US.ISO-8859-1 (I deleted any UTF-8)

Then I see in the shell :

**Automatically selecting en_GB.UTF-8 locale in addition to en_GB.  **#comment:](*,)#

[b]Generating locales...
  en_GB.ISO-8859-1... done
  en_US.ISO-8859-1... done
Generation complete.

[/b]I type in the shell:

[b]root@ubuntu:/home/makis # locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
en_GB
en_GB.iso88591
en_US
en_US.iso88591

[/b]#why not en_GB.ISO-8859-1  and en_US.ISO-8859-1 ?? Didm't I change them??

And after
[b]
root@ubuntu:/home/makis # locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=[/b]


Why do I still have UTF-8??
Why cannot find LC_CTYPE and LC_MESSAGES while they exist?

How can I configure all these locale parameters????](*,)

Thx

---


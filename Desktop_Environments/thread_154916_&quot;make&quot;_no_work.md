---
title: "&quot;make&quot; no work"
date: 2006-04-04
forum: Desktop Environments
---

### Post by pwrstick on 2006-04-04
Hello,

I'm trying to install banshee. I don't want to apt-get it because that gives me version 10.4, and there's version 10.9 which I'm hoping is going to fix a few things for me.

Reading the INSTALL tells me to 
1. make
2. make check (optional))
3. make install

I've used make before (on my asterisk box) and it worked find.  Problem is now make does nothing:
bash: make: command not found

Also, ./make gives:
bash: ./make: No such file or directory

Super nub!
Thanks for help
-Phil

---

### Post by Sutekh on 2006-04-04
You need the basic compiler tools;

```
sudo apt-get install build-essential
```

---

### Post by frodon on 2006-04-04
Run a ./configure before, sometimes it's required, it will generate the makefile.

---

### Post by pwrstick on 2006-04-04
Thanks!  Looks like things are moving forward.  ./configure actually worked just fine, and now it seems 'make' actually does something, but this is what I get:

make: *** No targets specified and no makefile found.  Stop.

I would guess the ./configure would make the makefile.  I did notice this during ./configure:
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Hmm... well any more help is greatly appreciated.

-Phil

P.S. A file listing in the folder I'm trying to do this:
aclocal.m4     configure       INSTALL              Makefile.in
AUTHORS        configure.ac    install-sh           missing
banshee.pc.in  COPYING         intltool-extract.in  mkinstalldirs
burn-sharp     data            intltool-merge.in    NEWS
ChangeLog      depcomp         intltool-update.in   po
config.guess   docs            libbanshee           README
config.h.in    entagged-sharp  ltmain.sh            src
config.log     HACKING         MAINTAINERS
config.sub     hal-sharp       Makefile.am

---

### Post by frodon on 2006-04-04
If you didn't install the *build-essential* package do it, it's really needed, install it and try again (see the Sutekh's post)

---

### Post by pwrstick on 2006-04-04
sudo apt-get install build-essential was executed before that last post, so I guess I got to figure something else out...  In the meantime Rhythm box is keeping me going :D

---

### Post by Perfect Storm on 2006-04-04
> I would guess the ./configure would make the makefile. I did notice this during ./configure:
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Also you need to look at the output when running ./configure and make. It tells you alot what's wrong.

```
sudo apt-get install libxml-parser-perl
```
Should do it.

---

### Post by localzuk on 2006-04-04
try running ```
sudo cpan
```
Follow the instructions to set it up (defaults are fine, choose mirrors near to you).

Once it is set up, run (within cpan) install XML::Parser.

---

### Post by localzuk on 2006-04-04
What are the differences between using CPAN to do it and using the native package?

---

### Post by Sutekh on 2006-04-04
[QUOTE=pwrstick]

I would guess the ./configure would make the makefile.  I did notice this during ./configure:
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool[/QUOTE]
```
sudo apt-get install libxml-parser-perl
```

Ed: Woh, way too slow!

---

### Post by pwrstick on 2006-04-04
Holy shnikeys, I'm feeling the love.  Thanks for all your help!

So now that the parser is installed, ./configure went from about 8 lines of output to about 100 lines of output, so I think we're on track!  Now it stops at: 

checking for HELIX_REMOTE... configure: error: Package requirements (helix-dbus-server >= 0.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

I'm trying to be intuitive (sudo apt-get install helix-dbus-server and the like) but am coming up with nothing.

---

### Post by localzuk on 2006-04-04
I'm not to sure about this one, but have you tried installing the 'helix' package?

---

### Post by pwrstick on 2006-04-04
Yeah I looked into that... there was something I found in synaptic like a Helix Media Player -- but if I installed that it said that Realplayer had to be installed.  But, "RealPlayer 10 supports RealAudio, RealVideo 10, MP3, Ogg Vorbis and Theora, H263, AAC and more."

I wasn't sure if Realplayer was installed via one of the script installers I used (Automatix, or easy Ubuntu)?

---


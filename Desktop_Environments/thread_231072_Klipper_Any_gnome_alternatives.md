---
title: "Klipper: Any gnome alternatives?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by khughes on 2006-08-06
I am having this problem in gnome where every time I copy anything, whether it be from a webpage, console, program, etc, and I open a new window to paste it in, the only way the contents are there to be pasted is if the previous window that I copied the contents from is still open. I have a habit of closing windows alot and this is a major frustration for me because then I have to go back in to wherever I was and copy the contents again. If it is a webpage, I can only hope I remembered where it was.

Anyways, when I had made the switch over to KDE for a while I noticed that this wasnt happening to me anymore and I think it had something to do with a program running in my system tray called Klipper. My question is, does gnome have a program like this that will resolve my problem? If not, is there any resolution that anyone knows of? Thanks alot in advance.

---

### Post by 3rdalbum on 2006-08-06
I've heard that Glipper will do the trick. It's GTK, not Gnome, so that's also good if you plan to use a different desktop environment.

[http://sourceforge.net/projects/glipper/]("http://sourceforge.net/projects/glipper/")

---

### Post by khughes on 2006-08-06
I will give that a shot and see how it goes. 

So I am right in thinking that I do need one of these programs to resolve my copy/paste problem right? There isnt just some configuration that I can make to fix this? 

I couldnt seem to find a deb in the repos for glipper so I guess sourceforge is the only supplier.

---

### Post by byen on 2006-08-07
Yes,I would second the "Glipper" recommendation. I have been using it for over 2 months now and it seems to run just fine. To my best knowledge I think installing and running Glipper would be the way to go if you want the clipboard utility for Gnome. Try it and check it out... it might just do the job for you...
Goodluck!

---

### Post by john rose on 2006-08-07
Using Breezy. Just downloaded glipper from sourceforge and extracted its files. I'd already installed the build-essential package using Synaptic Manager. However, when executing ./configure (after coming out with a number of messages) it stopped with 'checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool'. make would then not operate.

Do I need to download & install something else (e.g. XML::Parser perl module)? If so, what is commonly called?

Below is shown the terminal log:
admin@jessica-laptop:~/Downloads/glipper-0.89$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  de fr sv
checking for intltool >= 0.23... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
admin@jessica-laptop:~/Downloads/glipper-0.89$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by john rose on 2006-08-07
Just call me Stupid. Googled to find out package name (of XML Parser thingy) is libxml-parser-perl. Installed it OK using Synaptic. Then got similar message about glib2.0 when trying ./configure again. So Googled and installed libglib2.0-dev. Similarly libgtk2.0-dev.So glipper now installed.

My excuse is that I've only been using Ubuntu Linux for a few days. Previously tried SUSE on a desktop but it wouldn't work on this old HP Pavilion N5412 due to graphics driver problems.

Anyway glipper still has same problem that I was trying to solve: xpdf no longer allows the X feature automatic copying into clipboard of highlighted text (e.g.in order to paste into an OO2 document) from a displayed pdf file. I think this feature went after I did a Ubuntu update (I'm using Breezy because Dapper refuses to display on the screen). However, glipper does pickup up copied text in gedit which didn't work before. I've tried installing gnome-clipboard-daemon (even though it's supposed to be built into Breezy) but that didn't work with xpdf or gedit.

Any ideas?

---

### Post by joelito on 2006-08-07
I created a Deb using checkinstall, hopefully it will work for you.

---

### Post by khughes on 2006-08-18
I just went to the website above ([http://sourceforge.net/projects/glipper/](http://sourceforge.net/projects/glipper/)) and they had a deb there. It was easy to install.

---


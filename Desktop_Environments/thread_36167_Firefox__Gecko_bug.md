---
title: "Firefox / Gecko bug"
date: 2005-05-22
forum: Desktop Environments
---

### Post by mtron on 2005-05-22
Could someone please test the Page from ynet? 
[http://www.ynetnews.com/](http://www.ynetnews.com/)

As soon as i try to open it, firefox and ephipany shut down.

The error is:

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.

[I]The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 31 error_code 169 request_code 148 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/I]

Program Info:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.8) Gecko/20050513 Firefox/1.0.4 (Ubuntu package)
Xserver-xorg 6.8.2-10 (hoary)

Can sb. confirm this bug?

---

### Post by crmanski on 2005-05-22
mton, what version of firefox are you using?
I am using the current Firefox 1.0.4 from the Backports project ( [http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47) ) and the page loads fine for me.

---

### Post by mtron on 2005-05-22
I am using the same version... strange, what might cause it?

---

### Post by angkor on 2005-05-22
Same here, loading fine with:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.7) Gecko/20050425 Firefox/1.0 (Ubuntu package 1.0.3)

---

### Post by mtron on 2005-05-22
I ran firefox with some debug options and fould the bug. The package
libflash-mozplugin 0.4.11-2 (hoary)

from the repositories causes the gecko engine to crash.

remove the package
sudo apt-get remove libflash-mozplugin

and install Flashplayer with the plugin-finder from firefox

---


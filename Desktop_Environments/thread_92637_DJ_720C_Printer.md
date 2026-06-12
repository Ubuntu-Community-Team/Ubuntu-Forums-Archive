---
title: "DJ 720C Printer"
date: 2005-11-20
forum: Desktop Environments
---

### Post by trufflesdad on 2005-11-20
I am trying to setup my HP printer...I use the kde printer setup and it loads
the printer driver yet when I try the print test page nothing happens...
I have tried stopping and restarting cupsysy but no joy..I booted from the b/b live cd and printing works perfectly....Any input appreciated...I have searched
the forums fro the problem and tried what is on offer but nothing seems to work...

---

### Post by Tschaeck on 2005-11-21
you could try setting up your hp-printer with cups using your webbrowser just like this tutorial explains: [http://hpinkjet.sourceforge.net/install.php#print_queue](http://hpinkjet.sourceforge.net/install.php#print_queue)

and when you install the package "hplip" with adept you will get a qt-gui showing some info about your printer e.g. ink levels.

---

### Post by trufflesdad on 2005-11-23
[QUOTE=Tschaeck]you could try setting up your hp-printer with cups using your webbrowser just like this tutorial explains: [http://hpinkjet.sourceforge.net/install.php#print_queue](http://hpinkjet.sourceforge.net/install.php#print_queue)

and when you install the package "hplip" with adept you will get a qt-gui showing some info about your printer e.g. ink levels.[/QUOTE]

Thanks for the reply.....I looked at this and it appears the printer is setup ok
in cups yet the hplip gui tells me no hp devices found...cups also tells me that
I do not have the correct permission for /dev/lp0 so I change the permission
to allow all users but still get the same message from cups...
   As I mentioned it works ok from the live cd and printing is ok in pure Debian
but not in Ubuntu...

---

### Post by keithmantell on 2005-12-11
STOP PRESS:
The answer is here !!!
[http://ubuntuforums.org/showthread.php?t=87164](http://ubuntuforums.org/showthread.php?t=87164)

Simple fix !!

=============================================

Hi,

Just to add that I also have this problem.

The printer appears ok in the Printer admin tool and in lpstat.

The printer test page does not print.  Using lpr returns no error,but nothing happens.

Note that from the desktop i can see a printer icon appear and then disappear, but still no output.

Amazingly this is the first Linux not to work first time with the printer since I bought in in 1997!

Any ideas would be most welcome

---


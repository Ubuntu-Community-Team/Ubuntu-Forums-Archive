---
title: "'BadName (named color or font does not exist)'"
date: 2006-06-16
forum: Desktop Environments
---

### Post by dud on 2006-06-16
After doing an apt-get update and upgrade, I ran into problems starting firefox, synaptic (and some other programs possibly).
> dud@shadowplay:~ $ firefox
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadName (named color or font does not exist)'.
  (Details: serial 492 error_code 15 request_code 45 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

dud@shadowplay:~ $ synaptic
The program 'synaptic' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadName (named color or font does not exist)'.
  (Details: serial 147 error_code 15 request_code 45 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
I've tried 'dpkg-reconfigure fontconfig' and 'fc-cache -f -v' but nothing helps :( 

Getting slightly desperate here, as I'd really hate to reinstall ubuntu...

> 
uname -a:
Linux shadowplay 2.6.15-20-amd64-generic #1 SMP PREEMPT Tue Apr 4 17:45:39 UTC 2006 x86_64 GNU/Linux


> 
dud@shadowplay:~ $ Xorg -version

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux shadowplay 2.6.15-20-amd64-generic #1 SMP PREEMPT Tue Apr 4 17:45:39 UTC 2006 x86_64
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present


---


---
title: "after update gmail is crashing firefox (repost)"
date: 2014-05-16
forum: Desktop Environments
---

### Post by danielsender on 2014-05-16
I already posted this issue but I got absolutely no answers so far. So I will try again. I have a Dell Dimension running 14.04. Whenever I open gmail on firefox, firefox crashes. The problem does not occur if I use the "basic html" option on the page. If I open gmail with google chrome, the problem does not occur in any case. I tried removing completely firefox and re-installing and the problem persists. I will really  appreciate any  pointers. I'm inserting the output of 'firefox -g' (gdb on firefox).

```

GNU gdb (Ubuntu 7.7-0ubuntu3) 7.7
Copyright (C) 2014 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from /usr/lib/firefox/firefox...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/lib/firefox/firefox
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1".
[New Thread 0xb2db6b40 (LWP 2570)]
[Thread 0xb2db6b40 (LWP 2570) exited]

(process:2566): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
[New Thread 0xb2db6b40 (LWP 2572)]
[New Thread 0xb1529b40 (LWP 2573)]
[New Thread 0xb0bffb40 (LWP 2574)]
[New Thread 0xb03feb40 (LWP 2575)]
[New Thread 0xaf7ffb40 (LWP 2576)]
[New Thread 0xaee49b40 (LWP 2577)]
[New Thread 0xae648b40 (LWP 2578)]
[New Thread 0xade47b40 (LWP 2579)]
[New Thread 0xad646b40 (LWP 2580)]
[New Thread 0xace45b40 (LWP 2582)]
[Thread 0xade47b40 (LWP 2579) exited]
[New Thread 0xade47b40 (LWP 2583)]
[New Thread 0xac7ffb40 (LWP 2584)]
[New Thread 0xa3bffb40 (LWP 2585)]
[New Thread 0xa33feb40 (LWP 2586)]
[New Thread 0xa2cffb40 (LWP 2587)]
[New Thread 0xa25ffb40 (LWP 2588)]
[New Thread 0xa1bffb40 (LWP 2589)]
[New Thread 0xa0dffb40 (LWP 2590)]
[New Thread 0x9f8ffb40 (LWP 2591)]
[Thread 0x9f8ffb40 (LWP 2591) exited]
[New Thread 0x9f8ffb40 (LWP 2592)]
[New Thread 0x9eaffb40 (LWP 2593)]
[New Thread 0xa134db40 (LWP 2594)]
[New Thread 0x9dfffb40 (LWP 2595)]
[New Thread 0x9d4ffb40 (LWP 2596)]
[New Thread 0x9ccfeb40 (LWP 2597)]
[New Thread 0x9b9ffb40 (LWP 2598)]
[New Thread 0x9b1feb40 (LWP 2599)]
[New Thread 0x9a9fdb40 (LWP 2600)]
[New Thread 0x9a1fcb40 (LWP 2601)]
[New Thread 0x999fbb40 (LWP 2602)]
[New Thread 0x991fab40 (LWP 2603)]
[New Thread 0x989f9b40 (LWP 2604)]
[New Thread 0x97dffb40 (LWP 2605)]
[New Thread 0x975feb40 (LWP 2606)]
[Thread 0xad646b40 (LWP 2580) exited]

Program received signal SIGSEGV, Segmentation fault.
0xb58ea88c in ?? () from /usr/lib/firefox/libxul.so
(gdb) quit
A debugging session is active.

    Inferior 1 [process 2566] will be killed.

Quit anyway? (y or n)

```

Thanks.

---

### Post by pfeiffep on 2014-05-17
Sadly I'm unable to confirm ...on my Dell running Ubuntu 14.04  FF launches web based gmail just fine

---

### Post by danielsender on 2014-05-17
I understand, in fact gmail runs just fine on another system with 14.04 that I have. I just upgraded firefox to v30 and the problem remains. I'm almost certain that is a problem with some library not directly belonging to the firefox package, but the output of gdb sometimes doesn't say anything and sometimes it says about libxul.so that is a library that comes with firefox.

---

### Post by bapoumba on 2014-05-17
[https://bugs.archlinux.org/task/38085?](https://bugs.archlinux.org/task/38085?)
Arch Linux bug with the same output for segfault. The users located to problem with nvidia drivers. Would that apply to you ?

---

### Post by danielsender on 2014-05-17
That was one of the experiments I ran: disable the Nvidia 173 driver and use nouveau - unfortunately no difference, is still crashing.

Thanks

---

### Post by bapoumba on 2014-05-18
Maybe try disabling hangouts (bottom left) ? If you have enough time tafter login before it crashes.
Does it happen with a new user profile ? [https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles#w_starting-the-profile-manager](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles#w_starting-the-profile-manager)

---

### Post by brunolabs on 2014-07-07
I also have the same problem. Gmail causes the segmentation fault error on Firefox.
I have already submitted the bug to Mozilla.

---

### Post by Aditya_Kashi on 2014-11-01
I have this problem as well. I'm using Xubuntu 14.04.

---

### Post by Nitin_Reddy on 2014-11-16
I had Firefox v33 crash all the time with GMail on Ubuntu 14.04 LTS after running one of the updates. GDB reported the error occurring in the libxul library.

I went to Edit > Preferences > Advanced, and unchecked everything under Browsing. No crashes ever since.

---

### Post by bumparocky on 2015-03-10
Same problem here.....Firefox 36.0 with all extensions disabled...still does it.....been going on for months now...

when system first comes up, I can launch gmail and get the initial listing of messages, if I go to reply to one, the new send pop up window appears and a few characters into the reply, firefox crashes and offer to send a report and restart.  If I select restart,  gmail will run without crashing again and seems to have reverted to the old basic html.....IE, a reply will not use the pop up but the older in-line type layout.

---

### Post by pfeiffep on 2015-03-11
I have no problems with Gmail using:
Ubuntu 14.04.2
Firefox 36.0.1

---


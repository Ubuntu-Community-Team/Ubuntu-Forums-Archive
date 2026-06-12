---
title: "[SOLVED] minicom aborts after connect"
date: 2009-01-04
forum: General Help
---

### Post by hubiedo on 2009-01-04
i am using minicom to connect to an old sco-unix box. i am on unbuntu 8.04.

minicom is all setup, has the serial port config ttyS0, sets the modem, dials out and connects. it gives me a message "connected hit enter to continue". when i hit enter it gives me this message and then aborts.

minicom: ../iconv/loop.c:430: internal_utf8_loop_single: Assertion `inptr - bytebuf > (state->__count & 7)' failed.                                            
                                   Aborted 

i have tried it w/ sudo and reg user all no good. can anyone help.

---

### Post by spiderbatdad on 2009-01-04
Workaround:
```
LANG=C minicom
```
This was the first result when typing your error into a google search...try that. There are several results. I'm assuming that goes in your wvdial.conf file.

Edit: nope...it doesn't go in wvdial.conf. You actually run minicom that way as an alias, or edit .bashrc

---

### Post by hubiedo on 2009-01-05
spider--

i will try it this evening and let you know how it goes

---

### Post by hubiedo on 2009-01-05
spider,

it worked. initially i could tell i was in but had a lot of "?" on the lines interspersed with the welcom message & computer name etc. i also had to tweak it some by changing to an ansi terminal, 7E1 and software flow control. now i have to map the F keys for my data base programming and create a "bat" file to bring it up right. but one thing at a time. just getting into the system and it working helps a bunch. 

working with this old unix and by database is tricky but i am getting it now.

my final command line looks like this:

$ LANG=C minicom -c on

thanks a bunch

---


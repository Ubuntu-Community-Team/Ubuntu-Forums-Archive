---
title: "evolutiuon crashing on startup"
date: 2005-07-15
forum: Desktop Environments
---

### Post by yadnem on 2005-07-15
Hi, 

Everytime I start evolution it crashes immediately. This is tough as all my archived email is stored in evolution. 

I have a feeling that it has something to do with it trying to recover unsent mail. Is there a way of deleting these recovered mails ? or is there a way of somehow 'cleaning up' my evolution data ? 

The trace follows. I tried to submit this with bug-buddy but I get a message "the application has bug information, but bug buddy doesn't know about it. Please choose another application" which I select evolution on the 'select product or application' page. 

Thanks in advance for any help ... 

Roger

--- 


Backtrace was generated from '/usr/bin/evolution-2.2'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1228744320 (LWP 8222)]
[New Thread -1287652432 (LWP 8232)]
[New Thread -1277711440 (LWP 8231)]
[New Thread -1268925520 (LWP 8230)]
[New Thread -1260319824 (LWP 8229)]
[New Thread -1251927120 (LWP 8226)]
[New Thread -1243534416 (LWP 8225)]
[New Thread -1235141712 (LWP 8224)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7aa547b in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7831d97 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7a28175 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7a297d8 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xbfffe890 in ?? ()
#8  0x00000000 in ?? ()
#9  0x00000020 in ?? ()
#10 0x00000000 in ?? ()
#11 0x00000000 in ?? ()
#12 0x00000000 in ?? ()
#13 0x00000000 in ?? ()
#14 0x00000000 in ?? ()
#15 0x00000000 in ?? ()
#16 0x00000000 in ?? ()
#17 0x00000000 in ?? ()
#18 0x00000000 in ?? ()
#19 0x00000000 in ?? ()
#20 0x00000000 in ?? ()
#21 0x00000000 in ?? ()
#22 0x00000000 in ?? ()
#23 0x00000000 in ?? ()
#24 0x00000000 in ?? ()
#25 0x00000000 in ?? ()
#26 0x00000000 in ?? ()
#27 0x00000000 in ?? ()
#28 0x00000000 in ?? ()
#29 0x00000000 in ?? ()
#30 0x00000000 in ?? ()
#31 0x00000000 in ?? ()
#32 0x00000000 in ?? ()
#33 0x00000000 in ?? ()
#34 0x00000000 in ?? ()
#35 0x00000000 in ?? ()
#36 0x00000000 in ?? ()
#37 0x00000000 in ?? ()
#38 0x00000000 in ?? ()
#39 0x00000000 in ?? ()
#40 0x00000000 in ?? ()
#41 0x08b2b890 in ?? ()
#42 0x080e8b80 in ?? ()
#43 0xbfffe928 in ?? ()
#44 0xb6cbac2d in g_free () from /usr/lib/libglib-2.0.so.0

---

### Post by scoon on 2005-07-15
Hey there, 

Try to start it w/ strace instead.

regards, 

scoon

---

### Post by yadnem on 2005-07-15
I tried 

strace evolution 

there's a lot of output ...

When I try just 'evolution' from the prompt (before I was using the menu) I get :

es menu class init
adding hook target 'source'
requesting object classid: attachment.0x8743ed8.1350.alternative.2
object_found: 1
requesting object classid: itip:///.0x8743ed8.1350.alternative.2

** ERROR **: file itip-formatter.c: line 1343 (format_itip_object): should not be reached
aborting...


Any comments ?

Thanks, 

Roger

---

### Post by scoon on 2005-07-15
Hey there, 

No comments here.  Look for a bug in bugzilla either with ubuntu or evolution.  Strace's output is a ton and the last few lines before the seg fault could be the most usefull.

regards, 

scoon

---

### Post by yadnem on 2005-07-18
An additional thing : 

The reason I think that one of my 'recovered' email is causing this : when I start evoluition, the 'recover unfinished messages' dialog pops up, followed immediately by the 'application has quit unexpectedly').

So I can get back to my archive of emails, is there a quick fix to this. i.e. is there a way of 'tidying up' my .evolution ? Where are the recovered emails stored in .evolution (so that I can maybe delete them manually) - so that it doesn't try to recover them ? 

Roger

---

### Post by scoon on 2005-07-18
Hey there, 

Try renaming .evolution to something else and then restarting evolution.  If it works then you can work on re-importing your old mail.

regards, 

scoon

---

### Post by yadnem on 2005-07-18
Great Stuff ! 
It's working again. 
Thanks.

---


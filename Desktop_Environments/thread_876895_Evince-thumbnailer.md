---
title: "Evince-thumbnailer"
date: 2008-08-01
forum: Desktop Environments
---

### Post by jrz on 2008-08-01
This process seems to take total control of my cpu at times. Searching I saw an old post related which had SOLVED in the title, and looking it claimed the problem was related to viewing? pdf files. I opened a pdf file earlier, well over an hour ago, viewed it briefly, and closed it. System monitor continues to display "Processor: 100% in use" and the system is very slow. The post I referred to claimed SOLVED, but I don't consider "wait" to be a solution, especially when the wait is expressed in hours.
Does anyone know if there is a genuine solution to this problem, or perhaps a work around?

F   UID   PID  PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
4     0     1     0  16   0   2908   404 -      Ss   ?          0:01 /sbin/init
1     0  4758     1  15   0  12212   516 -      Ss   ?          0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
5     0  4759  4758  15   0  12580   940 -      S    ?          0:18 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
4  1000  4965  4759  17   0  76696  6084 -      Ssl  ?          0:01 /usr/bin/gnome-session
0  1000  5374  4965  15   0 159272 29548 -      Sl   ?          5:07 nautilus --no-default-window --sm-client-id default2
0  1000 19053  5374  25   0  75960 45160 -      R    ?        139:35 evince-thumbnailer -s 128 file:///home/joe/Desktop/Doc002.pdf

---

### Post by mannheim on 2008-08-01
A workaround is to disable thumbnailing of pdf files altogether. (This is something I did ages ago, because I find that all thumbnails of documents look pretty much indistinguishable. I prefer to see an icon.)

Anyway, if you want to, you can launch gconf-editor and navigate to /desktop/gnome/thumbnailers/application@pdf. Once there, uncheck the check-box marked "enable". This will turn off thumbnailing specifically for pdf files. Not really a "solution", I know.

---

### Post by jrz on 2008-08-01
Thank you mannheim, the CPU speed had just reduced after more than 6 hours at 100%, but I took the action you suggested, and hope that will help. I think I would prefer an icon instead of a thumbnail also as I can't really tell what the thumbnails are trying to show. I really appreciate the quick response.

---

### Post by Razmear on 2010-09-09
A thank you bump for this thread being out there. 
I have a directory with about 500 PDF files and evince-thumbnailer was spiking to 100% and locking up my machine (Ubuntu 10.4, AMD X2, 2gig Ram). 
Disabling solved the problem. Not a clean fix, but better than locking it up.

eb

---

### Post by cmcanulty on 2010-12-10
I just developed the same issue and disabled all thumbnailers but no difference, how can that be?

---


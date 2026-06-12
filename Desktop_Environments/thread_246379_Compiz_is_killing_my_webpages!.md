---
title: "Compiz is killing my webpages!"
date: 2006-08-29
forum: Desktop Environments
---

### Post by jcrnan on 2006-08-29
I got compiz finally properly installed yesterday but now Im having problems with certain sites I went into a site and firefox closed, tried again and firefox closed. So I just tought **** it and mooved on. But now I found it it closes if I try to enter my gmail as well. And I need my gmail :(

Any help here?

---

### Post by jcrnan on 2006-08-29
Okey, so it might not be compiz afterall. I got the sites up and running in Konqueoror but I want to continiue to use firefox. Anyone know whats wrong with my firefox? I only gmail notifier and adblock installed as far as plugins go.

---

### Post by jcrnan on 2006-08-29
Please! Anyone? I really need to get this working :(

---

### Post by christhemonkey on 2006-08-29
> **jcrnan said:**
> Please! Anyone? I really need to get this working :(

Have you tried running it in a terminal?

Then it will sprout any errors upon quiting (hopefully)

```
firefox 
```

---

### Post by jcrnan on 2006-08-29
uhm, so I tried that.. Didnt get any error log in terminal tough when it crashed.

---

### Post by jcrnan on 2006-08-30
uhm, update, I managed to get an error log this time:

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
nan@THE-HOLY-LAPTOP:~$

I have no idea what it means or why its called gecko tough -_-

---

### Post by Timokl on 2006-08-30
Gecko is the Mozilla Foundation's rendering engine which is used in Firefox, Mozilla, Netscape, Camino, the gnome help system, and other applications.

See: [http://en.wikipedia.org/wiki/Gecko(layout_engine)]("http://en.wikipedia.org/wiki/Gecko_%28layout_engine%29")

---

### Post by ButteBlues on 2006-08-30
This is due to Java or Flash (most likely this) media that is not working in the current code for Firefox, and causes it to crash abruptly.

GMail is one I've had issues with as well.

For Gmail, using [www.gmail.com/mail/h/](www.gmail.com/mail/h/) will work (this is the Basic HTML version of GMail, rather than AJAX one).

---

### Post by Meck1982 on 2006-08-31
Hi, I have the same problem with GMail and i already suspected the compiz/aiglx. Now the only brower that does not crash is konqueror. If you configure him pretending as a firefox some of the GMail ajax features work, but not all. I'd love to get a fix for this and use the full features with Firefox (or with Konqueror). Anyone any ideas? Aiglx/compiz works like a charm and I am not willing to give it up.

---

### Post by jcrnan on 2006-08-31
Meck1982: As I said its not compiz thats the problem, its firefox itself. The problems are still there wether or not compiz is turned on.

---

### Post by Meck1982 on 2006-08-31
Ok you are right, it is not compiz itself as turining off effects does not solve the situation, but I suspect it has something to do with it or the underlying X-Server. I personally use the newest Xorg for my AIGLX and I have two friends who use dapper drake without compiz/aiglx/xgl. And none of them has probs with firefox crashs. Also my update to newest kde-version is not to blame as one of the guys did this too and still no probs.
So what are you using? AIGLX or XGL? By the way it makes no difference weather I use the quinn or the vanilla version of compiz.

---

### Post by jcrnan on 2006-09-01
Im using AIGLX as XGL doesnt work with my gfx. But I dont think its compiz because I have checked gmail and such after I installed compiz. It just happend rather suddenly.

---

### Post by Meck1982 on 2006-09-01
I hope you are right. For now I installed Firefox for Windows with wine (and flashplayer 9). This works like a charm. I am satisfied with this solution so far as I normally use Konqueror.

---


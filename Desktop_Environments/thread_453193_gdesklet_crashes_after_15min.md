---
title: "gdesklet crashes after 15min"
date: 2007-05-24
forum: Desktop Environments
---

### Post by Peverel on 2007-05-24
Hi,

I don't know what the problem is, gdesklet starts up fine, looks funky and crashes after 10-15min. When I start it again, the shell freezes and I have to force quit it...

Any suggestions would be appreciated... :)

I'm running Edgy and Beryl as window manager...

---

### Post by AZzKikR on 2007-05-24
So if I understand you correctly, you started it from a shell? And there's no output whatsoever?

---

### Post by Peverel on 2007-05-24
I started it via Applications>Accessories>gDesklets
Then it crashes after 15min with no message at all, it just disappears.
When I try to start it again via Applications>Accessories>gDesklets the desklets managing window comes up (gDesklet shell window) and freezes up...

---

### Post by AZzKikR on 2007-05-25
OK, weird. Try opening a terminal, and then executing the gdesklets from there, see if there is any output on the screen describing what might went wrong.

Also, I did a quick search through the forums, and it seems GDesklets and Beryl do not combine very well for some people. Perhaps you are one of them :(

---

### Post by orb9220 on 2007-05-25
Also list which desklets you are using. Could be a faulty one. I have two which i use with no problems.

---

### Post by walkerk on 2007-05-25
> **AZzKikR said:**
> OK, weird. Try opening a terminal, and then executing the gdesklets from there, see if there is any output on the screen describing what might went wrong.

Also, I did a quick search through the forums, and it seems GDesklets and Beryl do not combine very well for some people. Perhaps you are one of them :(


I know I am one of the above.. with Beryl I have problems with both a & gDesklets.. Runs fine with Compiz

---

### Post by marcozs on 2007-05-25
If you are using beryl/compiz you may wanna try out screenlets:
[http://hendrik.kaju.pri.ee/screenlets/](http://hendrik.kaju.pri.ee/screenlets/)
dapper&feisty repos available too:
```

deb http://hendrik.kaju.pri.ee/ubuntu edgy screenlets
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

```

---

### Post by Peverel on 2007-05-25
Thanks for the tips so far, I wasn't aware of the issues with Beryl...

I am using an analog clock, goodweather, and 3 Side Candy desklets, network monitor, cpu monitor and ram monitor. I had problems with the WLAN signal monitor, so i deleted it. Problem was still coming up. When it crashes again, I'll try to run it in the terminal and post the output if there is one.

I'll check out the screenlets in the meantime :)

---

### Post by srg84 on 2007-05-25
this happens to me too, but i haven't got beryl, I use the ATI propietary drivers :(

---

### Post by shen-an-doah on 2007-05-25
If you're just using gDesklets for stuff like system monitoring, try GkrellM. It's not quite as pretty, but it works fine with Beryl.

---

### Post by orb9220 on 2007-05-25
> network monitor, cpu monitor and ram monitor
are problematic. I use a clock and good weather with no problems.

For system activity I use Conky which with alot less features is alot like samurize for windows.
But has CPU Load,Ram,Hd space on multiple drives,Running apps,Network activity. 
Just seach **conky** for info.

---

### Post by srg84 on 2007-05-26
Thanks!!!, that was the problem **(those problematic desklets)**, do you thing running it by terminal and seeing the problem could help to solve it??

---

### Post by srg84 on 2007-05-26
......

---

### Post by srg84 on 2007-05-26
This is the error of that Desklets , >Hope someone could help 

 The program 'gdesklets-daemon' received an X Window System error.
This probably reflects a bug in the program.

[B]The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 564106 error_code 9 request_code 55 minor_code 0) [/B]

  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by srg84 on 2007-05-26
I've Found This!!!!!!!!!!!!!!!


RE: GDK BadDrawable error on many gtk/gdk programs
Subject: 	RE: GDK BadDrawable error on many gtk/gdk programs
To: 	<dougl@charter.net>, <ljacques@fyma.ucl.ac.be>
From: 	"Ted Goodridge, Jr" <tedgoodridgejr@acm.org>

One workaround I have heard of is to build these apps without the
screensaver.  That stops the proggie from checking the screensaver idle
time.  It's not just AIM programs, but anything that checks the idle
time/screen saver.


Yes, this is a problem in other distros.  Redhat as well.  Also FreeBSD
alpha has the same problem.  Which leads me to think this is a bug in a
library.

---

### Post by Peverel on 2007-06-02
Thanks for the tip about Conky, it's a great small app... :)

How can I change the internet device address? It shows network activity of eth0 which is my wired connection, how can I change it to eth1 which is my wireless connection (which I use)?

---

### Post by Peverel on 2007-06-12
I found out, edit the .conkyrc file :)

---


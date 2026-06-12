---
title: "Nautilus not responding"
date: 2010-09-03
forum: Desktop Environments
---

### Post by finneyabraham on 2010-09-03
I have 64-bit Lucid on my AMD/ATI system. I have not been able to use nautilus for the last 2 months. 
When I use Places to open a folder, I get 'Starting -----" in the gnome panel, but nothing more. I tried to open nautilus using the terminal, for which I get the response,
```

finney1972@AMD-Ubuntu:~$ nautilus

(nautilus:3936): Unique-DBus-WARNING **: Error while sending message: Message did not receive a reply (timeout by message bus)

(nautilus:3936): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Then, I tried to open nautilus as root using sudo, for which the response was,
finney1972@AMD-Ubuntu:~$ sudo nautilus
[sudo] password for finney1972: 
The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 256 error_code 8 request_code 1 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

```

I don't know what is causing it. If anyone has an ideas, please write back.
Thanks

---

### Post by siddhanathan on 2010-09-04
Maybe reinstalling nautilus from software center would help...

---

### Post by finneyabraham on 2010-09-11
I solved the problem accidentally.

I had been using a dual monitor setup configured through ATI Configuraion utility. I changed my setup to a single monitor, and lo and behold, nautlius started opening the windows for Places and other folders.

---


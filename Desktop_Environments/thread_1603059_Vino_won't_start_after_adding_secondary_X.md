---
title: "Vino won't start after adding secondary X"
date: 2010-10-22
forum: Desktop Environments
---

### Post by melhe on 2010-10-22
I have recently added a second screen and uses separate X screens as my x screen settings. No xinerama. After adding the display Vino refuses to start. IIRC using dual X screens with xinerama works as expected.

Starting it manually results in:
```
henrik@bacchus:~$ /usr/lib/vino/vino-server  
22/10/2010 01:22:52 PM Autoprobing TCP port in (all) network interface
22/10/2010 01:22:52 PM Listening IPv6://[::]:5900
22/10/2010 01:22:52 PM Listening IPv4://0.0.0.0:5900
22/10/2010 01:22:52 PM Autoprobing selected port 5900
22/10/2010 01:22:52 PM Advertising security type: 'TLS' (18)
22/10/2010 01:22:52 PM Advertising authentication type: 'VNC Authentication' (2)
22/10/2010 01:22:52 PM Advertising security type: 'VNC Authentication' (2)
22/10/2010 01:23:00 PM Autoprobing TCP port in (all) network interface
22/10/2010 01:23:00 PM Listening IPv6://[::]:5900
22/10/2010 01:23:00 PM Listening IPv4://0.0.0.0:5900
22/10/2010 01:23:00 PM Problems in NewSocketListenTCP()
22/10/2010 01:23:00 PM Listening IPv6://[::]:5901
22/10/2010 01:23:00 PM Listening IPv4://0.0.0.0:5901
22/10/2010 01:23:00 PM Autoprobing selected port 5901
22/10/2010 01:23:00 PM Advertising security type: 'TLS' (18)
22/10/2010 01:23:00 PM Advertising authentication type: 'VNC Authentication' (2)
22/10/2010 01:23:00 PM Advertising security type: 'VNC Authentication' (2)

** ERROR **: Failed to register GObject with DBusConnection
aborting...
Aborted
henrik@bacchus:~$ 

```

I am running 64 bits 10.10.

Is it even possible to use vino with two server-side x screens? I would be perfectly happy with only one X screen exposed via VNC if it is impossible in the VNC client to choose which X screen to connect to.

Has anyone experienced the same problem?

---

### Post by ndgeek on 2010-11-09
I'm having the same issue but didn't realize it was due to adding a second X server.  I use the second X server to separate and run my VirtualBox Windows 7 system.

---

### Post by rodrigorc on 2010-11-24
I have the same issue with the 32 bit version.

I tried to debug & patch the vino-server but it is useless: it creates two servers but they both use the same port!

So here is my quick and dirty workaround:

```

/* File: one_display.c */
int gdk_display_get_n_screens(void *p)
{ return 1; }

```

Compile and install it with:
```

$ gcc -o one_screen.so -shared -fPIC -s one_screen.c
$ sudo mv one_screen.so /usr/lib/vino

```

Then go to the "Startup Applications" applet, edit the "Remote Desktop" program and change the command to:
```

env LD_PRELOAD=/usr/lib/vino/one_screen.so /usr/lib/vino/vino-server --sm-disable

```

And done!

Hope this helps.

---

### Post by Stefan Björk on 2010-11-29
Nobody seem to have filed a bug with the Ubuntu team?

---

### Post by Stefan Björk on 2010-11-29
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/682578](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/682578)

---

### Post by ndgeek on 2010-12-08
> **rodrigorc said:**
> I have the same issue with the 32 bit version.

I tried to debug & patch the vino-server but it is useless: it creates two servers but they both use the same port!

So here is my quick and dirty workaround:

```

/* File: one_display.c */
int gdk_display_get_n_screens(void *p)
{ return 1; }

```

Compile and install it with:
```

$ gcc -o one_screen.so -shared -fPIC -s one_screen.c
$ sudo mv one_screen.so /usr/lib/vino

```

Then go to the "Startup Applications" applet, edit the "Remote Desktop" program and change the command to:
```

env LD_PRELOAD=/usr/lib/vino/one_screen.so /usr/lib/vino/vino-server --sm-disable

```

And done!

Hope this helps.

Notice one typo in the post, the code section says one_display.c and then you compile one_screen.c.  Should be obvious to people, but wanted to make a comment, just in case there were newbies around.

This worked!  Thanks!

Chris

---

### Post by skippycostin on 2011-04-26
> **rodrigorc said:**
> I have the same issue with the 32 bit version.

I tried to debug & patch the vino-server but it is useless: it creates two servers but they both use the same port!

So here is my quick and dirty workaround:

```

/* File: one_display.c */
int gdk_display_get_n_screens(void *p)
{ return 1; }

```Compile and install it with:
```

$ gcc -o one_screen.so -shared -fPIC -s one_screen.c
$ sudo mv one_screen.so /usr/lib/vino

```Then go to the "Startup Applications" applet, edit the "Remote Desktop" program and change the command to:
```

env LD_PRELOAD=/usr/lib/vino/one_screen.so /usr/lib/vino/vino-server --sm-disable

```And done!

Hope this helps.

Thank you! It worked great!

---

### Post by cyper.bg on 2011-06-28
I have 4x Ati 5870 video cards and stumbled across this thread when looking for a solution of the localhost problem.

Well it did the trick. I'm a complete newbie, but managed to compile and install the code. So it's not so hard :)

Thank you.

---

### Post by spaceli on 2011-10-04
> **rodrigorc said:**
> I have the same issue with the 32 bit version.

I tried to debug & patch the vino-server but it is useless: it creates two servers but they both use the same port!

So here is my quick and dirty workaround:

```

/* File: one_display.c */
int gdk_display_get_n_screens(void *p)
{ return 1; }

```

Compile and install it with:
```

$ gcc -o one_screen.so -shared -fPIC -s one_screen.c
$ sudo mv one_screen.so /usr/lib/vino

```

Then go to the "Startup Applications" applet, edit the "Remote Desktop" program and change the command to:
```

env LD_PRELOAD=/usr/lib/vino/one_screen.so /usr/lib/vino/vino-server --sm-disable

```

And done!

Hope this helps.
Nice! It works on my 64-bit ubuntu 11.04. Thanks!

---

### Post by masuch on 2011-10-04
> **rodrigorc said:**
> I have the same issue with the 32 bit version.

I tried to debug & patch the vino-server but it is useless: it creates two servers but they both use the same port!

So here is my quick and dirty workaround:

```

/* File: one_display.c */
int gdk_display_get_n_screens(void *p)
{ return 1; }

```

Compile and install it with:
```

$ gcc -o one_screen.so -shared -fPIC -s one_screen.c
$ sudo mv one_screen.so /usr/lib/vino

```

Then go to the "Startup Applications" applet, edit the "Remote Desktop" program and change the command to:
```

env LD_PRELOAD=/usr/lib/vino/one_screen.so /usr/lib/vino/vino-server --sm-disable

```

And done!

Hope this helps.


Thanks, works fine.

---

### Post by marcthenarc on 2012-01-22
Excellent answer.  Works on Ubuntu 10.10 64-bits.  I also have two X servers and that patch did the trick.

---


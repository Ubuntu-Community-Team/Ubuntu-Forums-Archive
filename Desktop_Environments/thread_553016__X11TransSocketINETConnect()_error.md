---
title: "_X11TransSocketINETConnect() error"
date: 2007-09-17
forum: Desktop Environments
---

### Post by jtgalway on 2007-09-17
Hi all,

   surprisingly, I had a look through the forums and searched google before but couldn't seem to find a solution to this. I'm sure I'm just doing something stupid, so fill me in if you have any ideas.

   I am using Ubuntu Feisty and I'm trying to run a program I just compiled (custom physics analysis tool). It has a function which allows certain things to be displayed in a HIGZ window. When I run the program with this feature enabled, I get the following:

```
 Version 1.29/04 of HIGZ started
_X11TransSocketINETConnect() can't get address for host:6000: Name or service not known
 ***** ERROR in IOPWK : Can't open DISPLAY 
 ***** ERROR in IACWK : Workstation is not open 
 ***** ERROR in ISWKWN : Invalid workstation window parameters 
 ***** ERROR in ISWKVP : Invalid workstation window parameters 
xanalyze: reading gt018328.hdf ...
   searching for run information ...
   run date:     1011015
   no. channels: 492
   no. pmts:     490
   padding is   ON
   nitrogen gain id is   018313
   padding pair is gt018329
   picture/boundary thresholds =  4.25/ 2.25
   ok ... processing
 ***** ERROR in ISWKWN : Invalid workstation window parameters 
 ***** ERROR in ISWKVP : Invalid workstation window parameters 
     gps    slope     yint   length    width    asymm       xc       yc       xo       yo    alpha
   0.000     0.87     0.74     0.10     0.07     0.63    -0.25     0.53    -0.63     0.19    73.75


```

   I have had similar problems with this kind of thing before, but it usually happens when I am exporting the display from a remote machine. This time I am running the program on a local machine. I have PAW etc all installed on this machine. The program is doing everything it should be doing - just not displaying the results the way I want it to.

   I have a different laptop running the same version of Feisty, with PAW and all other relevant software up-to-date. The program runs flawlessly on the laptop (Dell Inspiron 630m) , but not on my workstation (Dell GX-270). It seems to be an X-problem though. When I tried to run the program remotely by exporting the display from my laptop to my workstation, I got a similar error with port 6010 being listed instead of 6000. The following remedied it, as you would expect:

```
export DISPLAY=127.0.0.1:10.0
```

   Nothing like this solves the problem of running it entirely on my workstation though.

   Any help appreciated.
   John T

---

### Post by jtgalway on 2007-09-17
Problem solved I think.

I thought it was a display problem (X or xhost or something) but it turned out that paw (the display tool) was just using the wrong file to get information on my system. Happy days!! :KS

---

### Post by MaskedMarauder on 2008-01-11
> **jtgalway said:**
> Hi all,

   surprisingly, I had a look through the forums and searched google before but couldn't seem to find a solution to this. I'm sure I'm just doing something stupid, so fill me in if you have any ideas.

   I am using Ubuntu Feisty and I'm trying to run a program I just compiled (custom physics analysis tool). It has a function which allows certain things to be displayed in a HIGZ window. When I run the program with this feature enabled, I get the following:

```
 Version 1.29/04 of HIGZ started
_X11TransSocketINETConnect() can't get address for host:6000: Name or service not known 
...[snip]...

```

 ...[snip]...

   I have a different laptop running the same version of Feisty, with PAW and all other relevant software up-to-date. The program runs flawlessly on the laptop (Dell Inspiron 630m) , but not on my workstation (Dell GX-270). It seems to be an X-problem though. When I tried to run the program remotely by exporting the display from my laptop to my workstation, I got a similar error with port 6010 being listed instead of 6000. The following remedied it, as you would expect:

```
export DISPLAY=127.0.0.1:10.0
```

   Nothing like this solves the problem of running it entirely on my workstation though.

   Any help appreciated.
   John T


Are you using ssh with X11 forwarding?

I just encountered this problem when I upgraded an old system into the feisty/gutsy realm.

The error message is a resolver problem, not X11 per se.  Apparently something changed in the feisty+ generation such that the socket stuff can't resolve 'localhost' as it used to; it doesn't know that 'localhost' = '127.0.0.1'

My solution is to put 'localhost 127.0.0.1' in /etc/hosts on the remote system, then it is able to map 'localhost' to '127.0.0.1' as it should.

This may or may not work for what you're trying to do, but I use ssh a lot to run X11 applications on remote machines, e.g.:

> machine1> ssh machine2 gnome-terminal

and this had me stymied for a while.  I was a little surprised that the problem hadn't been reported more often.  I guess people don't run applications remotely much.

---


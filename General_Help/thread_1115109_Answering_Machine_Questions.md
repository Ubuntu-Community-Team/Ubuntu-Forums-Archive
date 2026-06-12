---
title: "Answering Machine Questions"
date: 2009-04-03
forum: General Help
---

### Post by kronix_00 on 2009-04-03
I have an old dialup modem that I'd like to use to record incoming voice calls.  From what I see, mgetty is the way to go.  However, most of the [_[COLOR="Blue"]help I find[/COLOR]_]("http://frank.harvard.edu/~coldwell/answering_machine/") is a bit too technical for a newbie like me.

The above site talks about setting up my 'inittab'.  From what I gather, Ubuntu [_[COLOR="blue"]doesn't have[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=292507") an inittab.  It appears that /etc/event.d is the replacement for inittab?  What exactly does this file do?  I'm vaguely thinking it's akin to autoexec.bat in the old Windows world.  Am I close?


I don't suppose anyone has a newbie's guide to setting up mgetty to pick up my phone line, record for a while, and hang up...?

Thanks for any direction you can give.

---

### Post by PhrankDaChickenGeek on 2009-04-12
I'm working on a similar idea. Except all I want is the caller ID info. I almost have something working, and hope to post back soon on this issue. I will also be making a blog post on my website: [http://ubuntu.online02.com](http://ubuntu.online02.com)

Testing events.d stuff....

---

### Post by PhrankDaChickenGeek on 2009-04-13
Ok, I've got the blog post - [http://ubuntu.online02.com/node/28]("http://ubuntu.online02.com/node/28")
It will at least help you set up events.d stuff. 

What you want is vgetty, though:
```

sudo apt-get install mgetty mgetty-voice
```

edit the config (Read through it - I haven't set it up, but there's lots of comments!)
```
sudo nano /etc/mgetty/voice.conf
```

setup events.d so vgetty will run at all time
```
sudo nano /etc/event.d/vgetty
```
Put in the following:
```

start on startup

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

respawn
exec /sbin/vgetty /dev/ttyS1 # The serial port your modem is attached to!

```
And start vgetty:
```
sudo start vgetty
```

And start testing!
killing vgetty will reload any configuration changes. Be sure to have some free time when no one will call you - I tied up the phone line for quiet some time getting mgetty to work.
To stop vgetty (if things are going wrong)
```
sudo stop vgetty
```

Mess around with it and tell me what happens! I would setup my own answering machine, but we already have that service from our telephone provider and others in my household wouldn't approve!

---

### Post by kronix_00 on 2009-04-14
Thank you, Phrank!  This provides a clear (and coherent!) blueprint for the direction I need to go.

You mention (in your excellent blog):

> *To detect the modem in Linux, I used wvdialconf. For newer (PCI) modems, I suggest using ScanModem*

I've got a PCI modem, so I used ScanModem as per your suggestion.  Instead of a ttyS# value, though, ScanModem gives me a PCI slot instead (02:08.0).  The only port info that looks remotely like ttyS(#) is found at the very end of ScanModem's report (under the section that says I don't need to worry about this info, it's for 'experts'!) and mentions a symbolic link created at /dev/ttySL0.  Does that sound like a valid port?

Also, Is there a way I can turn on the modem, just to listen for a dial tone?  I remember the good old DOS days, where I could send 'AT commands' (ATDT, etc.).  Is that still possible?  I want to check that Ubuntu (heh, and me!) knows where my modem is, and that it's got access to the phone line.

Anyway, much thanks for the simple introduction to this whole ustart business!

---

### Post by PhrankDaChickenGeek on 2009-04-17
Sorry, I'm unsure about the PCI modem configuration.

Yes, you can send AT commands in mgetty.config - I use it to turn on caller ID:
```
init-chat "" AT#CID=1 OK # Turn on Caller ID
```
There are other 'init' options available for mgetty.config - You'd have to google for them...

---

### Post by DHCline on 2009-05-01
> **kronix_00 said:**
> I've got a PCI modem, so I used ScanModem as per your suggestion. Instead of a ttyS# value, though, ScanModem gives me a PCI slot instead (02:08.0). The only port info that looks remotely like ttyS(#) is found at the very end of ScanModem's report (under the section that says I don't need to worry about this info, it's for 'experts'!) and mentions a symbolic link created at /dev/ttySL0. Does that sound like a valid port?

I'm not sure if that is a valid port or not (I'm new to Linux) but you can also try 
```
 
sudo wvdialconf /etc/wvdial.conf

```
and see if it gives you any more information.
 
> **kronix_00 said:**
>  
Also, Is there a way I can turn on the modem, just to listen for a dial tone? I remember the good old DOS days, where I could send 'AT commands' (ATDT, etc.). Is that still possible? I want to check that Ubuntu (heh, and me!) knows where my modem is, and that it's got access to the phone line.

Yeppers, use minicom! It's actually a great way to figure out if ttySL0 is really where your modem is located also. You will probably have to set up minicom with 
```

sudo minicom -s

```
first. Go to "serial port setup", and change setting A (serial device) to /dev/ttySL0. Hit enter to finalize input and enter again to return to the main setup menu. Then "Save setup as dfl" and "Exit". You should get an initialization string followed by OK. mine says 
 
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
OK 
 
If you don't get the init string or minicom exits, then you probably need to go back into minicom setup and change the /dev/ttySL0 to something else. (Mine is /dev/ttyS0 by the way. You can try some different values in there to see if you can randomly come accross your port if you have to. i.e. /dev/ttyS0, /dev/ttyS1, /dev/ttySL1 etc)
 
Anyways after you get minicom to give you that init string and "OK", to hear your dial tone take the phone "off hook" by typing ATH1 and hit enter. If you don't hear anything try typing ATM1 to set the speaker volume to "low" (ATM0 will silence your modem). To hang up / put the phone "on hook" type ATH0 and hit enter. To exit minicom use ctrl+A, X.

---

### Post by kronix_00 on 2009-05-13
Aha!  Excellent advice regarding minicom.  It's just what I needed.  Thanks for this -- y'all are helping this newbie inch forward.  :)

---


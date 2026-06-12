---
title: "How to get GnomePPP/wvdial working?"
date: 2005-12-04
forum: Desktop Environments
---

### Post by glennr on 2005-12-04
Hi,

I've just installed 5.10 on my Father's machine to replace another distro which wasn't working out for him. It all seems to be working great and everything "just works" except that I can't figure out how to get dialup internet access through GnomePPP working. I have used Linux for several years but I use linesrv at home so have limited experience with desktop diallers.

The external modem works and I'm posting this from the machine, having set it up and connected via the "Network settings" gui tool.

From the forums I see that I need to configure wvdial and have run
```

sudo wvdialconf /etc/wvdial.conf

```
 
When I try to dial in GnomePPP or wvdial the connection succeeds but there are messages about permssion denied to /etc/ppp/*secrets, which according to the wvdial man page is expected, and pppd fails to authenticate.

What else do I need to set up?

Also when I have been connected using "Network settings"  then GnomePPP or wvdial report "device or resource busy" until I reboot. How can I release the serial port without rebooting?

Thanks
Glenn

---

### Post by migueljacq on 2005-12-04
hmm, no expert on wvdial but whats your connection method? PAP? CHAP?

Sounds like it's trying to authenticate, thus checking the passwords in your secrets file, but it can't open them (that's a permissions issue on that particular file). 
I'd check my machine, but I'm at work so I can't help much.

Not sure with wvdial, if you need to configure the thing first? 

I run 'sudo pppconfig' in the terminal, follow all the steps, then I can simply connect to the net by typing 'pon provider' (if that's the name you've given the connection) into the terminal. Similarly, 'poff' to disconnect. To me, this is much less of a hassle than wvdial.

Re: device being busy, try this in the terminal:

sudo killall pppd

---

### Post by glennr on 2005-12-05
Thanks, I see what's going on and I suppose I could start editing things and changing permissions etc.

However I'm trying to put myself in my Father's shoes, it's his machine and there's no way he would have known what to do.

I was expecting that configuring an internet dialler would have been reasonably obvious and easy to do.

I'm thinking that this is way too hard and that I missed out something important. GnomePPP wasn't installed by default so maybe I need some packages as well?

---

### Post by glennr on 2005-12-05
I found out that there is a modem panel applet that can be added by right clicking on the panel.

This does what I wanted except that it requires you to enter your password every time you want to dial up.

---

### Post by migueljacq on 2005-12-05
Which means it requires sudo priviliges.
These may not be connected, but I know that you can nominate users to turn pppd on and off, in the pppconfig. Thus removing the requirement for sudo priviliges.
Don't know if it will affect the modem applet, though. But maybe worth a shot.

---

### Post by amohanty on 2005-12-05
IN the users tab in System->Administration->Users and Groups
right click on the user, select Properties and look at the permissions tab. Check (i think - am not sure) Use Modem.

HTH
AM

---

### Post by glennr on 2005-12-05
That sounds like it should work but it doesn't.
 
The /dev/ttyS0 files are in the group dialout with g=rw and the user is in that group too but I still get "To connect to your Internet service provider, you need administrator privileges"

---

### Post by amohanty on 2005-12-06
Ok in System->Administration->Networking 
Configure your modem with information from you ISP.

Once you have done that, see if you can connect and disconnect from the terminal using:
```
pon
```
to connect and

```
poff
```
to disconnect.

If you cant then you can set the suid bit on /usr/bin/pon and /usr/bin/poff and add them as custom launchers to your panel.

HTH
AM

---

### Post by glennr on 2005-12-06
Thanks,

I take it that in order to be able to dial up without entering your password each time then you have to do some custom configuration, eg use pon/poff as you suggest.

In my opinion that's not very convenient and way too hard for a beginner.

I still don't believe that it can't be done using the default install especially since in the user control panel there is a check box that says "Allow connecting to the Internet" (or something like that).

Perhaps this is a bug?

---


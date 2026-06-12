---
title: "VNC password rejected"
date: 2005-10-19
forum: Desktop Environments
---

### Post by singlecell on 2005-10-19
I'm trying to connect from an XP box to ubuntu using VNC.

On ubuntu I have the vnc enabled, a password set to something simple, "password mode" is set to vnc, and alert user etc disabled. I try to connect from the XP machine, get the password prompt and enter the password. Unfortunately, the password fails and the connection is refused.

I can connect successfuly when I disable the password on the ubuntu machine ("password mode" set to "none"), so vnc IS working and the machine is reachable. I've tried Realvnc and ultravnc viewers on the windows, and both have the same effect.

Any ideas what could be wrong with the passwords?

---

### Post by Fanskapet on 2005-10-19
[QUOTE=singlecell]I'm trying to connect from an XP box to ubuntu using VNC.

On ubuntu I have the vnc enabled, a password set to something simple, "password mode" is set to vnc, and alert user etc disabled. I try to connect from the XP machine, get the password prompt and enter the password. Unfortunately, the password fails and the connection is refused.

I can connect successfuly when I disable the password on the ubuntu machine ("password mode" set to "none"), so vnc IS working and the machine is reachable. I've tried Realvnc and ultravnc viewers on the windows, and both have the same effect.

Any ideas what could be wrong with the passwords?[/QUOTE]

What windows client are you using? if not using tight vnc..
[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html) :rolleyes:

---

### Post by singlecell on 2005-10-19
I've tried UltraVNC, realVNC before but get the same result using tightVNC as well. 
The exact error is: "VNC authentication failed!". 
The password is a short and simple lowercase password.

---

### Post by Koning_Floris on 2006-10-31
I'm using UltraVNC, and I'm having the same problem.

I set the password, I check if it works at home. On my lan the password works and I get a VNC window with my ubuntu machine. Then when I try from work (with the right portmaps at home, since I DO get connection and a request for authetification) I fill in the password, and then it says authetification failed.

Is it a new security measure or something? 

(I did it all the same with Ubuntu 6.06 wich did work like a charm.

---

### Post by neocon2005 on 2006-10-31
I too have the same problem with the tightvncserver. I recently upgraded my home machine from Dapper to Edgy (upgraded fine though not totally smooth). I could access Dapper no problems. Since my upgrade to edgy, my VNC password gets rejected always (I tried to access my home machine from work both from Win XP and Ubuntu).

---

### Post by jameso on 2006-11-01
I too am having trouble with VNC passwords after upgrading from dapper to edgy.

Does anyone know the cause of this?

Thanks.

James

---

### Post by jameso on 2006-11-01
Well, it seems that when going to System | Remote Desktop, when you type in a password, it limits the password to 8 characters.

After connecting via VNC and entering the first 8 characters of my password, it connected successfully.

---

### Post by Sweezel on 2006-11-01
I believe the password is getting lost after a reboot.

I have had to enter the password twice (8 characters) to get connected. I haven't tried rebooting then testing again. Not enough time right now.

---

### Post by Sweezel on 2006-11-01
Yes, it does not work after a reboot. You must reenter the password.

Someone else please test before I make a bug report.

Thanks

---

### Post by jameso on 2006-11-02
Well, it seems I cannot connect to my server via VNC after rebooting yesterday.

Is anyone else having this problem?

---

### Post by Koning_Floris on 2006-11-02
Yes, I also believe it has to do with losing the password on reboot.

I did the following. I configured remote desktop to not use any password, with this I could log in from work. Off course this is no way to go in terms of security. But now I changed my password via VNC on my remote login. And now, it asks for the password, I fill in the password and it connects and works. I believe that when I reboot it will lose the password again, but I cannot test that right now.

So a fix would be to find out where the password is stored and make that none-changeable or something.

---

### Post by macnerd on 2006-11-03
I just updated to Edgy last night and I'm having the same problems with VNC connections.  Just an FYI, you guys aren't the only ones.

---

### Post by Oldbean on 2006-11-06
@Sweezel - Yes, please do file a bug report. I can recreate the problem - password lost/corrupted after a reboot. Works fine again if password is re-entered.

Cheers,

OB.

---

### Post by tufkal on 2006-11-06
I can also confirm this on 2 of my edgy boxes, VNC password is lost on reboot.

---

### Post by wpwood3 on 2006-11-06
This is a well known bug that was reported in [THIS BUG REPORT]("https://launchpad.net/distros/ubuntu/+source/vino/+bug/65795").
There should be a fix coming out soon.

In the mean time there is a workaround [HERE]("https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff").

---

### Post by Oldbean on 2006-11-06
Thanks very much wpwood.

Since you've pointed me at it, I've found a couple of useful things from Launchpad...

OB.

---

### Post by Buggin on 2006-11-12
is there any way to reset the password from a ssh terminal?

---

### Post by coastdweller on 2006-11-14
Here here, same problem. I'm at a loss of how to get around this.

---

### Post by dissdigg on 2006-11-16
> **wpwood3 said:**
> This is a well known bug that was reported in [THIS BUG REPORT]("https://launchpad.net/distros/ubuntu/+source/vino/+bug/65795").
There should be a fix coming out soon.

In the mean time there is a workaround [HERE]("https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff").

Tried this and had no success.

Followed directions and get this far:

> $ sudo patch -p1 < /tmp/vino_2.16.0-0ubuntu2.1.dsc.debdiff
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -u vino-2.16.0/debian/patches/01_fix_password_free.patch vino-2.16.0/debian/patches/01_fix_password_free.patch
|--- vino-2.16.0/debian/patches/01_fix_password_free.patch
|+++ vino-2.16.0/debian/patches/01_fix_password_free.patch
--------------------------
File to patch:
Skip this patch? [y] 


Also, why would vino on a default Edgy install take up over 50% cpu on a p4 system?  Anyone have a good howto for installing a replacement...tightVNC server perhaps?

---


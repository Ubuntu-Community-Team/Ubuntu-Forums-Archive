---
title: "Why is Remoted Desktop provided if it's Useless?"
date: 2010-11-11
forum: Desktop Environments
---

### Post by xp_newbie on 2010-11-11
This question pertains to Ubuntu 8.04 but it was true for Ubuntu 6.06 (and perhaps relevant to Ubuntu 10 as well).

I am trying to set my desktop to be accessed remotely via LAN. 

Instead of repeating a tedious vnc4serve/xinetd install & setups procedure I did in Ubuntu 6.06, I tried to see whether the "user friendly" GUI based configuration (System > Preferences > Remote Desktop) would work.

It doesn't.

This is what I did:

```
System > Preferences > Remote Desktop.

General tab:
 > Check: Allow other users to view your desktop
   > Check: Allow other users to control your desktop
   Users can view your desktop using this command: vncviewer myubuntu:0

 > Uncheck: Ask you for confirmation
 > Check: Require the user to enter this password <usual VNC pass>

Advanced tab:
 > Check: Only allow local connections
 > Default port: 5900
```

It doesn't work, regardless whether I use vncviewer or Windows XP's remote desktop.

I then [found]("http://ubuntuforums.org/showthread.php?t=795036") the following thread:

[URL="http://ubuntuforums.org/showthread.php?t=855234"]http://ubuntuforums.org/showthread.php?t=855234
[/URL]
Which states that, like in Ubuntu 6.06, the GUI-based remote desktop setup in Ubuntu 8.04 is useless.

So, my question is: If it is useless, why is it provided in the default package?

---

### Post by mcduck on 2010-11-11
Because it actually works?

I just tried and had absolutely no problems accessing my Ubuntu system from a Mac after configuring the remote desktop using that tool. :)

as far as I can remember, it has worked on previous Ubuntu versions as well.

Check your network connections (and router configuration, if you use one) and of course the settings in the VNC client you are using.

---

### Post by Whiteice on 2010-11-11
I personally found the SSH into a system is by far the best way to remote. It's stupied simple to setup you just need to know some terminal commands for what you are trying to do. I can even connect to it via my driod and Iphone :P

---

### Post by CharlesA on 2010-11-11
> **mcduck said:**
> Because it actually works?

I just tried and had absolutely no problems accessing my Ubuntu system from a Mac after configuring the remote desktop using that tool. :)

as far as I can remember, it has worked on previous Ubuntu versions as well.

Check your network connections (and router configuration, if you use one) and of course the settings in the VNC client you are using.

The thing about the "Remote Desktop" server that Ubuntu uses by default (vino) is that it requires someone to be logged into the console for it to work.

There was a bug that was mentioned that selecting "configure the network automatically" screwed up the network connectivity in Maverick.

> **Whiteice said:**
> I personally found the SSH into a system is by far the best way to remote. It's stupied simple to setup you just need to know some terminal commands for what you are trying to do. I can even connect to it via my driod and Iphone :P

+1 for SSH. FreeNX works too, if you really *need* a GUI.

@OP: If you selected [COLOR="Red"]only allow localhost connections[/COLOR], you'd need to connect to that machine and forward VNC over something like SSH to connect from another machine, since the server is only listening on the lo interface, not the external interface.

---

### Post by mcduck on 2010-11-11
> **CharlesA said:**
> The thing about the "Remote Desktop" server that Ubuntu uses by default (vino) is that it requires someone to be logged into the console for it to work.

There was a bug that was mentioned that selecting "configure the network automatically" screwed up the network connectivity in Maverick.

That would indeed explain why people have troubles with it and I've never noticed anything. I've always been logged in on the Ubuntu machine when using the remote desktop.

(I've only used it for testing purposes, little actual need for a remote desktop when living in a 38m2 apartment... ;))

I agree that for any actual work SSH would be better. Especially if you need to work outside of the LAN.

---

### Post by xp_newbie on 2010-11-11
> **mcduck said:**
> Because it actually works?That's exactly the answer I wanted to hear.

I knew there must be a good reason for providing the GUI-based setup as part of the core Ubuntu install, but for some reason, I am receiving the following error when I am trying to connect:
> Unable to connect to host: Connection refused (10061)


Any idea what could be wrong in my setup? Do I have to configure a firewall setting in the Ubuntu desktop?

> **mcduck said:**
> Check your network connections (and router configuration, if you use one) and of course the settings in the VNC client you are using.
It's a LAN (same subnet), couldn't be simpler than that. Which VNC settings?

I have been using the [RealVNC 4.1]("http://www.realvnc.com/products/free/4.1/download.html") free viewer.

BTW, I *am* logged in when trying to make this work (I was aware of this limitation, but I want to solve this mystery once and for all).

Thanks.

---

### Post by CharlesA on 2010-11-11
> **mcduck said:**
> That would indeed explain why people have troubles with it and I've never noticed anything. I've always been logged in on the Ubuntu machine when using the remote desktop.

(I've only used it for testing purposes, little actual need for a remote desktop when living in a 38m2 apartment... ;))

I agree that for any actual work SSH would be better. Especially if you need to work outside of the LAN.

I've got 2 VMs running Ubuntu desktop that I access with FreeNX. Works so much better then VNC.

Granted I needed to install the NX client, but it works well. :)

I don't really use VNC much, if at all at home, but at work it's another store (since everything in windows).

EDIT: If you are logged into the console, post the output of this please:

```
netstat -nl
```

---

### Post by xp_newbie on 2010-11-11
> **CharlesA said:**
> @OP: If you selected [COLOR="Red"]only allow localhost connections[/COLOR], you'd need to connect to that machine and forward VNC over something like SSH to connect from another machine, since the server is only listening on the lo interface, not the external interface.
**Bingo!** That was my problem. I (mis)interpreted "Only allow local connections" as LAN connections, not as local loop. I now see the balloon tip that says "local connections" means local loop.

Thanks you!!! :guitar:

---

### Post by CharlesA on 2010-11-11
Verbage is everything. ;)

---


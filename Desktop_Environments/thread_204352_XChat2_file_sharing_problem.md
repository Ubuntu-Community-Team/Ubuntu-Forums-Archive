---
title: "XChat2 file sharing problem"
date: 2006-06-26
forum: Desktop Environments
---

### Post by DoomedTX on 2006-06-26
I'm having a continuing problem that has followed me over several distros and continues in Dapper with the latest version of XChat. I'm copying my xchat.org post, which has received no helpful replies, below:

> I think this is more of an XChat problem, but as it's always manifested in a script I'm writing here. I have tried several file serving scripts including Asoka, SDClone, and lately Sky. I have them installed correctly and in each case a list is built correctly.

If a user finds a file they want via @find and requests it, the file is offered and sent correctly. However, when they request my list via @DoomedTX, it always fails. The request is acknowledged and my list file appears in the XChat send window, but my entire internet connection stalls. I stop getting messages in IRC, my instant messengers in GAIM logoff, and I can't load web pages. The file transfer reports aborted in a few minutes but nothing improves. If I close XChat and/or reconnect to the server, the internet starts working again.

I'm using XChat 2.6.0 (has happened with previous versions) on Ubuntu Breezy (also happened in Hoary and Mandrake 10). I have my router configured to allow ports 4000-4009 to pass through to my Linux box and those are the ports I have configured in settings.

Again let me emphasize that any other file will transfer just fine but "DoomedTX-03-11-06.zip" brings down the house.

Any ideas?

](*,)

---

### Post by DoomedTX on 2006-07-20
For the benefit of anyone else who might have this problem, I was able to find the answer after giving up and loading mIRC on my Windows machine. When mIRC had the same problem I went looking on the net based on its slightly more descriptive error.

Anyway, it turns out that the Netgear MR314 Router has an undocumented, unchangeable feature that "protects" me from using port 6667 to send files. When the user at the other end tried to accept the file xfer, the router reads that as an attack and shuts down, which is why I also tend to lose instant messenger connections, etc.

In any event, I changed the port to 6668 by putting "/6668" after the server name in the server list, and now everything seems to be working fine. Thanks, Netgear for the 2-year headache!

---


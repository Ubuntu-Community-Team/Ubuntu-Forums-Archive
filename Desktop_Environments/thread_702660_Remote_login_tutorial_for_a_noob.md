---
title: "Remote login tutorial for a noob?"
date: 2008-02-20
forum: Desktop Environments
---

### Post by eeefresh on 2008-02-20
I have searched the forums for this topic several times, but everything is a bit over my head.  Let me start with what I am looking for:

When using XP at home, I am able to log into my work computer using VPN client.  Our IT guys posted a tutorial on our intranet that explains everything.  You simply download the exe file, install it, run another "update" file, then you are done.  I can then connect VPN client to my network at work, then login using Windows' Remote Desktop.

Now that I am using Ubuntu more, I want to do the same thing, but I don't know where to start.  I consider myself pretty computer literate, but my networking abilities are limited to setting up my router and laptop at home!

Some questions:

1. What software do I need on Ubuntu?  Is there a VPN equivalent?
2. Once I have the software installed, how do I configure the settings?  Most of the settings in VPN were already installed, from the "update" file, I assume.  I can probably open VPN in Windows and get those settings, but I am not sure what I am looking for.
3. Once I am connected, where is the Linux equivalent of "Remote Desktop?"

Any help, or a link to a basic tutorial, would be appreciated!

---

### Post by amohanty on 2008-02-20
Hi.

I am oversiplifying but think of VPN as a protocol/technique for secure communication between different networks (work and home). There are many differend kinds of VPN servers, each of which have there own clients. A good OSS example is OpenVPN. Most network vendors like Cisco et.al provide there own servers and clients when they sell the VPN server/hardware to you co.

Now, you can only do the VPN thing from ubuntu if the VPN server that your IT team uses has a linux client, or a compatible linux client (ie not released by vendor but works with the server). The exe you installed was the VPN client provided by the vendor whose VPN hardware/software solution your IT guys bought. You probably want to ask them what VPN server software they are using and if they have a linux client for it (for e.g. cisco does and so do some other major vendors). If not you can google around to see if there is a compatible linux client you could use.

If not, you are out of luck. OTOH, at least it is not an IE/ActiveX based VPN client because then you would be truly out of luck.

HTH
AM

---

### Post by sandgathe on 2008-02-21
Are there any secure remote login services for Ubuntu such as Windows and Mac have LogMeIn (logmein.com) ? (I am a Linux-n00b)

---

### Post by eeefresh on 2008-02-21
thanks amohanty.  I talked to one of our IT guys at work, and he said he actually uses Ubuntu at home and can show me how to remote in, although "they technically only support XP" according to him.

On a related note, I also found [this tutorial]("http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php") on Lifehacker for anyone that is interested, but be sure to read the comments, which offer a better way than what the tutorial offers.

I love Ubuntu, but I still think it has a long way to go in converting new users, mainly because everything is written by very experienced users who assume you are on the same level as they are.  While I have found several simple tutorials for noobs on this and other sites, many are written well over the heads of guys like me.  Hopefully this will get better in the future as Ubuntu becomes a more mainstream OS.

---


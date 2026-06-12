---
title: "Help! Trying to get files from Ubuntu to VMWare Windows XP"
date: 2006-08-19
forum: Desktop Environments
---

### Post by The Waco Kidd on 2006-08-19
Please help! I've installed VMware on Kubuntu 6.06 and set up a virtual machine with XP. I don't know anything about networking so accepted the default setting, which is "NAT: Used to share the host's IP address" (on my BT Voyager ethernet connection). When In XP I can access the router's configuration page and nothing else.

I'm starting to get the hang of Ubuntu but networking makes me feel like an idiot, so please phrase your response accordingly.

<edit> Okay, I'm getting Internet Access via IE but I can't figure out how to navigate to see my Ubuntu partition files. Confused.

---

### Post by petersjm on 2006-08-19
> **The Waco Kidd said:**
> networking makes me feel like an idiot

I know how you feel and I'm probably not going to be of any help, but until someone tells you a way to access ext3 drives in a virtual WinXP (I'm sure there's a way!), maybe you could just flash-drive them, or burn them to CD or something? Just until you figure out a way?

---

### Post by tkiesel on 2006-08-19
There are some good HOWTOs on the forums about getting Samba networking going to network Ubuntu with Windows computers.  Use one of those.

Set up Ubuntu and your VMware'd Windows to use the same workgroup and you can share files. It will look on the network as if they are two entirely separate computers!

<end Ubuntu/Linux knowledge>
<begin Windows knowledge>

After that, in Windows mount the shared directory that Ubuntu is offerring as a network drive and you're on your way to moving files back and forth transparently!

---

### Post by The Waco Kidd on 2006-08-19
> **petersjm said:**
> I know how you feel and I'm probably not going to be of any help, but until someone tells you a way to access ext3 drives in a virtual WinXP (I'm sure there's a way!), maybe you could just flash-drive them, or burn them to CD or something? Just until you figure out a way?

Yeah, I think this is the short term answer.

I did figure out that I can copy + paste small amounts of text between the two, which is going to be a great timesaver.

---

### Post by The Waco Kidd on 2006-08-19
> **tkiesel said:**
> There are some good HOWTOs on the forums about getting Samba networking going to network Ubuntu with Windows computers.  Use one of those.

Set up Ubuntu and your VMware'd Windows to use the same workgroup and you can share files. It will look on the network as if they are two entirely separate computers!

<end Ubuntu/Linux knowledge>
<begin Windows knowledge>

After that, in Windows mount the shared directory that Ubuntu is offerring as a network drive and you're on your way to moving files back and forth transparently!

Right, I'm going to give this a shot. Thanks!

---

### Post by galileon on 2006-09-05
[http://www.ubuntuforums.org/showthread.php?t=248272&page=2&highlight=samba+vmware](http://www.ubuntuforums.org/showthread.php?t=248272&page=2&highlight=samba+vmware)

---


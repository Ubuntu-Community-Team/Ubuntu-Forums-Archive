---
title: "No network connection information"
date: 2012-05-30
forum: Desktop Environments
---

### Post by ammofreak on 2012-05-30
Hi ):P
Now using Ubuntu 12.04LTS with Unity desktop on my Dimension 8400. My question: although I have a network connection (wired), the *Connection Information* in the Network applet menu reveals no info other than "Error displaying connection information: No valid active connections found!". I am not overly concerned about this but I am curious as to why. Have already done the basic 
T/S. If anyone has had a similar problem & solved it, I would appreciate the I/P. Thanks in advance....:)

---

### Post by codemaniac on 2012-05-30
You can retrieve all the network information of the wired interface by issuing the following command on a terminal .
Press alt+ctrl+T

```
ifconfig
```

---

### Post by ammofreak on 2012-05-30
TY for the post! However, I am more interested in finding out why the connection info does not work from the applet. I appreciate your I/P. TY again...:)

---

### Post by ammofreak on 2012-06-01
Hi everyone ):P
_Found the solution_: interface appears in */etc/network/interfaces*. By default, NetworkManager does not manage interfaces that appear in /etc/network/interfaces. One can change this behaviour.

To do this - in a terminal:

*sudo nano /etc/NetworkManager/NetworkManager.conf*

change the line* managed=false* *to managed=true*

Save, stop and start network manager:

*sudo service network-manager restart*

I am paraphrasing (& thanking) [COLOR="Red"]fossfreedom[/COLOR] from **AskUbuntu**...:)

---

### Post by psrdotcom on 2012-06-01
Hi,

I hope you have tried this. But let us make sure that you have done this before proceeding further.

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

If that is the problem, then please re-install the drivers.

---

### Post by edgicat on 2012-07-14
> **ammofreak said:**
> Hi everyone ):P
_Found the solution_: interface appears in */etc/network/interfaces*. By default, NetworkManager does not manage interfaces that appear in /etc/network/interfaces. One can change this behaviour.

To do this - in a terminal:

*sudo nano /etc/NetworkManager/NetworkManager.conf*

change the line* managed=false* *to managed=true*

Save, stop and start network manager:

*sudo service network-manager restart*

I am paraphrasing (& thanking) [COLOR="Red"]fossfreedom[/COLOR] from **AskUbuntu**...:)


====


Worked like a charm for me

Thanks :p

---

### Post by Phil Usher on 2012-08-12
> **ammofreak said:**
> Hi everyone ):P
_Found the solution_: interface appears in */etc/network/interfaces*. By default, NetworkManager does not manage interfaces that appear in /etc/network/interfaces. One can change this behaviour.

To do this - in a terminal:

*sudo nano /etc/NetworkManager/NetworkManager.conf*

change the line* managed=false* *to managed=true*

Save, stop and start network manager:

*sudo service network-manager restart*

I am paraphrasing (& thanking) [COLOR="Red"]fossfreedom[/COLOR] from **AskUbuntu**...:)
This worked for me also.  Thanks.

---

### Post by turter2 on 2013-05-07
> **ammofreak said:**
> TY for the post! However, I am more interested in finding out why the connection info does not work from the applet. I appreciate your I/P. TY again...:)


register an account to thank you for solve my problem

thank you very much

---

### Post by jsc315 on 2013-12-27
> **ammofreak said:**
> Hi everyone ):P
_Found the solution_: interface appears in */etc/network/interfaces*. By default, NetworkManager does not manage interfaces that appear in /etc/network/interfaces. One can change this behaviour.

To do this - in a terminal:

*sudo nano /etc/NetworkManager/NetworkManager.conf*

change the line* managed=false* *to managed=true*

Save, stop and start network manager:

*sudo service network-manager restart*

I am paraphrasing (& thanking) [COLOR="Red"]fossfreedom[/COLOR] from **AskUbuntu**...:)

Sorry for resurrecting a old thread but I just wanted to say thank you. I was installing ubuntu on a older computer and I was having this issue and this fixed it! THANK YOU!

---

### Post by oldos2er on 2013-12-29
Old thread closed.

---


---
title: "Bibus 1.2 lacks Openoffice menu"
date: 2006-07-07
forum: Desktop Environments
---

### Post by jukkem on 2006-07-07
Hi! 
 
I am using ubuntu dapper amd64. I installed bibus 1.2 using debian/ubuntu istallation method as suggested in the wikipage and I am using sqlite as database. Bibus installation went smoothly. When starting bibus there was no first start Wizard only first connection wizard. Pubmed searches work well. However i cannot insert my citations since there is no Openoffice menu. Paths in /usr/share/bibus/bibus.cfg should be correct. I launced manually UnoConnectionListener.sxd. I choose the "get current uno connection status" and the response was: "connection is active and use a socket". So i Chose the socket. In bibus I am able to choose in the preference menu the preferred word processor (Oo2) and TCP/IP. For some reason bibus does not save these settings. Word processor settings is set to NONE when I am checking the preferences again during same bibus session. So it seems that the connection between bibus and openoffice 2 is not working. Has anyone got bibus 1.2 working together with openoffice 2 on Dapper/Dapper amd64? :-k 

Jukka

---

### Post by jukkem on 2006-07-09
I have suspicion that pyuno bridge is not working in openoffice 2.0.2. That is the reason why bibus 1.2 is lacking openoffice.org menu. Openoffice package in amd64 dapper is not amd64 spesific since in fails to build in amd64 see: [https://launchpad.net/distros/ubuntu/dapper/+source/openoffice.org/2.0.2-2ubuntu12](https://launchpad.net/distros/ubuntu/dapper/+source/openoffice.org/2.0.2-2ubuntu12)

BIBUS developer suggests that Pyuno is not 64bits clean:
[http://www.oooforum.org/forum/viewtopic.phtml?p=142634&highlight=&sid=a17aefe23fe9119811dfe674347fc2e0#142634](http://www.oooforum.org/forum/viewtopic.phtml?p=142634&highlight=&sid=a17aefe23fe9119811dfe674347fc2e0#142634)

If someone has got bibus working in i386 that is further suggesting that the problem is related to openoffice and amd64 issues.

Any ideas/comments?

Jukka

---

### Post by MagnusL on 2006-08-09
Hi!

I recently installed dapper and have similar troubles getting bibus to work. I have one i386 laptop and an AMD64 desktop. On the i386, the openoffice menu shows in bibus but does not connect to openoffice - it says "could not connect to pipe". Running the wizard works well, and the test of pipe in the OO-setup document says that connection is ok. But still doesnt work. 

On my AMD64 I get no openoffice menu in bibus, as you said, and fail to find any python-uno package to install. However, when running the wizard, it looks ok. 

Any advice or ideas on how to proceed?

Magnus Larsson

---

### Post by jukkem on 2006-12-01
Bibus works great on Edgy. AMD64 issues seems to be sorted out. I suggest to upgrade from dapper.

---


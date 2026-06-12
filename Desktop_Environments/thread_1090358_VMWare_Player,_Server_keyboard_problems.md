---
title: "VMWare Player, Server keyboard problems"
date: 2009-03-08
forum: Desktop Environments
---

### Post by kribjo on 2009-03-08
Hi,

I had a setup with two computers like this, working without any problems:

Computer:1
-OpenSuse 10.3 running VMWare Server 2.0, Build: 122956
 - Virtual Ubuntu 8.04 Server
 - Virtual Windows XP SP3
 - Virtual Kubuntu 8.10 Desktop

Computer:2
-Ubuntu 8.04, connecting to the Virtual computers on computer 1.

After reinstalling computer 2 with Ubuntu 8.10, several of the keys on my keyboard is not working as it should when connecting to the virtual computers. Arrow-keys, Windows-keys etc.

Arrow-down now functions as a Windows Start key. And the other ones I don't know. I'm using a Norwegian keyboard.

Any help will be greatly appreciated.

Regards,

Bjørn

---

### Post by kribjo on 2009-03-09
This one has really been driving me mad. I found a fix at [http://www.nalinmakar.com/2008/11/12/vmware-player-and-ubuntu-810-keyboard-mapping-issues/](http://www.nalinmakar.com/2008/11/12/vmware-player-and-ubuntu-810-keyboard-mapping-issues/)
:) So the arrows problem is no longer a problem. And the Win-Start button is also working again. But I still do not have Norwegian keyboard setup :(

YES!!!! The solution at [http://communities.vmware.com/message/1101765#1101765](http://communities.vmware.com/message/1101765#1101765) did it. (I removed the line I added from the link above, before I followed the instructions from the Community pages at VMWare) :)

---


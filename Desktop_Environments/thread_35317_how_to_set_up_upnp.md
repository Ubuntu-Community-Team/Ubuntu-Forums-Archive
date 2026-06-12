---
title: "how to set up upnp"
date: 2005-05-18
forum: Desktop Environments
---

### Post by earobinson on 2005-05-18
Anyone know how to set up upnp?

Thanks

---

### Post by jcooper on 2005-05-19
What application needs uPnP support? Its normally only XP that uses this protocol, most linux apps tend to expect firewall ports to be open etc.

---

### Post by earobinson on 2005-05-20
[QUOTE=jcooper]What application needs uPnP support? Its normally only XP that uses this protocol, most linux apps tend to expect firewall ports to be open etc.[/QUOTE]
 well i use amule and i was told that using uPnP with my linksys router will stop the network form getting really slow?

see: [http://www.emule-project.net/home/perl/help.cgi?l=1&rm=show_topic&topic_id=129](http://www.emule-project.net/home/perl/help.cgi?l=1&rm=show_topic&topic_id=129)

---

### Post by Blues- on 2005-05-20
Get the UPnP Package from Sourceforge -> [UPnP SDK](http://upnp.sourceforge.net/) 

If you are not using the RPM package, proceed as following:

  Installation of this package is not straight forward.
    tar zxvf libupnp-1.2.1.tar.gz
    cd libupnp-1.2.1
    cd upnp
    make
    make install
    cd ../ixml
    make
    make install
    cd ../threadutil
    make
    make install
    cd ..
    cp upnp/inc/ixml.h /usr/include/



Cheers,
Blues-

---

### Post by earobinson on 2005-05-20
no deb for this yet? thats to bad.

will this make it run all the time in the backround?

---

### Post by Blues- on 2005-05-20
There is a UPnP package that is already patched under the MediaTomb Project page .. You can get it [here](http://sourceforge.net/project/showfiles.php?group_id=129766&package_id=150120) .

Get the libupnp-1.2.1a-3.i386.rpm, works for me :)
And yes it's a lib that will be loaded everytime you boot you box.

ps. Use the Alien command to convert the RPM to DEB
"man alien"

Cherrs,
Konni.

---

### Post by earobinson on 2005-05-20
thanks for all the help

---

### Post by earobinson on 2005-05-23
how do i check if this is working?

---


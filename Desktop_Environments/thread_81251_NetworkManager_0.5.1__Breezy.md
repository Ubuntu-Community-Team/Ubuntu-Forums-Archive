---
title: "NetworkManager 0.5.1 / Breezy"
date: 2005-10-24
forum: Desktop Environments
---

### Post by tvoss on 2005-10-24
Hi,

the following repository provides NetworkManager 0.5.1 for Ubuntu Breezy:

deb [http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/) ./
deb-src [http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/) ./

Just apt-get update && apt-get install network-manager to install:-)

Have fun with it, it works just fine.

Greetz

Thomas

---

### Post by akseli on 2005-10-24
[QUOTE=tvoss]Hi,

the following repository provides NetworkManager 0.5.1 for Ubuntu Breezy:

deb [http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/) ./
deb-src [http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/) ./

Just apt-get update && apt-get install network-manager to install:-)

Have fun with it, it works just fine.

Greetz

Thomas[/QUOTE]

What are the changes? Got a changelog around?

---

### Post by akseli on 2005-10-24
[QUOTE=tvoss]Hi,

the following repository provides NetworkManager 0.5.1 for Ubuntu Breezy:

deb [http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/) ./
deb-src [http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/) ./

Just apt-get update && apt-get install network-manager to install:-)

Have fun with it, it works just fine.

Greetz

Thomas[/QUOTE]

I only just tried it and it didn't work. 0.5.1 seems to have more issues with wireless networking (WAP encryption through HEX key) than the 0.4.1 release which I downgraded to after trying this release. 
Does anyone have an explanation? The program just continued to ask for the WEP key even after I typed it in like 1000 times and furthermore the key is in my gnome-keyring and nm-applet has full access to the key for the network in question...

Thank anyway!

---

### Post by TheOtherShoe on 2005-10-25
Thanks for posting this!

I seem to be getting an error though,
```

Setting up network-manager (0.5.1-0ubuntu1) ...
 * Stopping Network connection manager daemon:                                                                        [ ok ]
 * Starting Network connection manager daemon: chown: `bind:bind': invalid user
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 network-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bidd on 2005-10-25
0.5.1 works great for me with ndiswrapper and wep.

But I also get the irritating prompt for the keyring password everytime I log in to GNOME. I've granted nm-applet full access via the keyring manager.

Anyone know why it keeps asking for my password. It's driving me nuts.

:confused:

---

### Post by Fratus on 2005-10-26
Same as you akseli.
Using NM 0.5.1 from the aforementionned repository, and getting the same results.
Someone on the NM mailing list had this problem and solved it by updating his bind, dhcbdb and wireless-extensions, but he was using FC4. He gave me the versions of his files :

bind9_9.3.1-14
dhcdbd_1.9-1
wireless-tools_28-0.pre10-4

In the repository above we have :
bind9_9.3.1-2ubuntu2
dhcdbd_1.9-0ubuntu1
wireless-tools_27+28pre10-1

I haven't tried to compile the newer versions of them (wieless tools especially), but it might solve this problem.

Cheers.

---

### Post by MrStu on 2005-11-03
[QUOTE=TheOtherShoe]Thanks for posting this!

I seem to be getting an error though,
```

Setting up network-manager (0.5.1-0ubuntu1) ...
 * Stopping Network connection manager daemon:                                                                        [ ok ]
 * Starting Network connection manager daemon: chown: `bind:bind': invalid user
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 network-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```[/QUOTE]

I get that exact same error, and anyone who can tell me the answer I will love forever.

---

### Post by emendelson on 2005-11-03
I can't get 5.1 to connect to a wireless network; the icon keeps spinning, and I get prompted for a WEP password, but it never connects. Uninstalled, went back to 4.1, and all is well again.

---

### Post by FallDog on 2005-11-09
I've been trying to install networkmanager, tried the version from cvs in the repo (.4.* i think), then i tried this version, but with same problem: i cannot seem to get the thing to run - i believe the service is running, although i'm not sure how to verify that in ubuntu -

the only sign that something has changed after install is the battery monitor crashes (everytime, bizarre), i've tried running nm-applet from command line, and adding it to the sessions start up programs

what could be preventing the applet from showing up?

a note: the first time i installed it (.4.*), it seemed to run fine from commandline(sys out displaying essids of accesspoints found) and the applet ran: the next time i ran it, the applet didnt load but it still displayed output in terminal, tried uninstalling/reinstalling, and now there is no response at all, results the same postupgrade

any help or alt. solutons would be very appreciated: switching wifi networks in the default network tool seems rather primitive

perhaps it is a problem with gnome-panel itself? i've tried refreshing the panel, doesnt help

ciao

---

### Post by FallDog on 2005-11-13
Not sure what the issue was, but deleting all gnome prefs(to revert to default behaviour), reinstalling network-manager, and adding it to the sessions startup programs seems to have done the trick

love it

---

### Post by bryan986 on 2005-11-13
I don't understand why they dont add a GUI in networkmanager for wpasupplicant, it is a good authentication program for wpa purposes, all they would need to do is write an GUI for the command line interface

---

### Post by theine on 2005-11-16
[QUOTE=bryan986]I don't understand why they dont add a GUI in networkmanager for wpasupplicant, it is a good authentication program for wpa purposes, all they would need to do is write an GUI for the command line interface[/QUOTE]

I think I might have an interesting read for you: [http://www.gnome.org/projects/NetworkManager/developers/](http://www.gnome.org/projects/NetworkManager/developers/)

---


---
title: "How to Install FreeNX on Breezy"
date: 2005-10-14
forum: Desktop Environments
---

### Post by poison on 2005-10-14
Hi 

Can someone help me with this as all the new repositories don't have this? Do I have to install this using the source or is there a way to use apt-get install in Breezy 5.10?

---

### Post by julakali on 2005-10-15
I used this two lines in sources.list:
> deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main universe multiverse restricted

I guess nobody will recommand using hoary sources with breezy, but it worked for me and i got freenx installed.
But i got a big problem with running freenx, i'm getting the error 
> Info: Established X server connection.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.
on the client side, and the server log says:
> NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1001 Bye.
NX> 105 NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001 Bye.


So there is no error, but the connection doesn't work..
maybe someone can help me with this

---

### Post by julakali on 2005-10-15
I just figured out how it works :)
The freenx hoary package is incompatible with breezy.
You have to use 
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) ubuntu-seveas freenx

which provides you with a running version.
see [http://www.ubuntuforums.org/showthread.php?t=75892](http://www.ubuntuforums.org/showthread.php?t=75892)

---

### Post by Marcos.Rufino on 2005-10-17
[QUOTE=julakali]I just figured out how it works :)
The freenx hoary package is incompatible with breezy.
You have to use 
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) ubuntu-seveas freenx

which provides you with a running version.
see [http://www.ubuntuforums.org/showthread.php?t=75892](http://www.ubuntuforums.org/showthread.php?t=75892)[/QUOTE]


I configured the seveas repository but get this error message when using Synaptic:

> W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) ubuntu-seveas/freenx Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_ubuntu-seveas_freenx_binary-i386_Packages) - stat (2 No such file or directory)

Is it a temporary outage of the repository or I'm doing something wrong?

---

### Post by paulicat on 2005-10-17
It seems they changed pathing use:
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx
instead...

---

### Post by Marcos.Rufino on 2005-10-17
[QUOTE=paulicat]It seems they changed pathing use:
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx
instead...[/QUOTE]

Thank you Paulicat. It is working now!

---

### Post by A-star on 2005-10-18
Forget about my previous message
It works yay me!

---

### Post by poison on 2005-10-20
Hi 

Is seveas.ubuntulinux.nl still up as when I do an apt-get update it hangs on 99% [Waiting on headers]. Also if I try ping or browse to the url there is no responce.

Any idea

Thanks

---

### Post by poison on 2005-10-20
I am having endless issues trying to install freeNX on my Ubuntu 5.10. I even tried to compile from source and once I got it installed I received authentication erros  

(NX> 204 Authentication failed.)

even installing with the --setup-nomachine-key option. I have a windows Xp machine and need to connect to my linux box can someone help.

Thanks

---

### Post by Marcos.Rufino on 2005-10-20
[QUOTE=poison]I am having endless issues trying to install freeNX on my Ubuntu 5.10. I even tried to compile from source and once I got it installed I received authentication erros  

(NX> 204 Authentication failed.)

even installing with the --setup-nomachine-key option. I have a windows Xp machine and need to connect to my linux box can someone help.

Thanks[/QUOTE]

I used to get this error message too. I solved it using a private DSA key instead of the nomachine one. So I copied the server key (from the machine I want to connect to) into the client machine (the machine I'm using the client FreeNX).
You shouldn't forget to unable SSL encryption on all traffic.

---

### Post by titaniumone on 2005-10-24
[QUOTE=Marcos.Rufino]I used to get this error message too. I solved it using a private DSA key instead of the nomachine one. So I copied the server key (from the machine I want to connect to) into the client machine (the machine I'm using the client FreeNX).
You shouldn't forget to unable SSL encryption on all traffic.[/QUOTE]

which file is this? i installed freenx using seveas' binaries and i am having the same problem as poison. i have been trying to get nx to work for hours and i am losing my mind.

---

### Post by Marcos.Rufino on 2005-10-24
[QUOTE=titaniumone]which file is this? i installed freenx using seveas' binaries and i am having the same problem as poison. i have been trying to get nx to work for hours and i am losing my mind.[/QUOTE]

The file is named "client.id_dsa.key" and you can locate it in the server machine, in this folder: /var/lib/nxserver/home/.ssh/

You should copy the content of this file into the client machine through the FreeNX GUI. Do you remember that "Key..." button in the General tab?

Good Luck!

---

### Post by titaniumone on 2005-10-24
[email]root@opti:/var/lib/nxserver/home/.ssh[/email]# ls -la
total 16
drwx------  2 nx root 4096 2005-10-24 14:17 .
drwx------  3 nx root 4096 2005-10-24 14:17 ..
-rw-------  1 nx root  690 2005-10-24 14:17 authorized_keys2
-rw-r--r--  1 nx root  229 2005-10-24 14:17 known_hosts


???

---

### Post by Marcos.Rufino on 2005-10-24
[QUOTE=titaniumone][email]root@opti:/var/lib/nxserver/home/.ssh[/email]# ls -la
total 16
drwx------  2 nx root 4096 2005-10-24 14:17 .
drwx------  3 nx root 4096 2005-10-24 14:17 ..
-rw-------  1 nx root  690 2005-10-24 14:17 authorized_keys2
-rw-r--r--  1 nx root  229 2005-10-24 14:17 known_hosts


???[/QUOTE]

It seems you have installed Nomachine with the standard Nomachine-key as default. I believe you should create a fresh and exclusive key for you. How?

Try: "nxsetup --keygen". Well, that's a suggestion from Nomachine ([http://www.nomachine.com/ar/view.php?ar_id=AR01C00126)](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126)).

If it doesn't work, maybe you can force the nxserver to use the standard nomachine-key, using this: "nxsetup --setup-nomachine-key".

Anyway, you can always explore the nxsetup command (try also the nxsetup --install) and the "/etc/nxserver/node.conf" configuration file.

Well, I don't believe I can help you besides that. My knowledge around FreeNX stops here.

---

### Post by titaniumone on 2005-10-24
thanks but that doesn't work either. when i try to connect it immediately dies saying 'nx server not running' still.

---

### Post by Marcos.Rufino on 2005-10-24
[QUOTE=titaniumone]thanks but that doesn't work either. when i try to connect it immediately dies saying 'nx server not running' still.[/QUOTE]

Have you enabled the sshd daemon? Remember FreeNX uses ssh to work. You can check it by going >>System>>Administration>>Services. When there, the "Remote Shell Service (ssh)" should be checked. If you don't have this service running you should resolve this problem first.

If you need help with the ssh, take a look at the Ubuntu Wiki pages: [https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh%29](https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh%29)

If this sshd thing is not the problem... Have you installed the nxserver through apt-get or synaptic? They usually make all necessary configurations to get the nxserver running. You can also try to uninstall and install it again through synaptic.

---


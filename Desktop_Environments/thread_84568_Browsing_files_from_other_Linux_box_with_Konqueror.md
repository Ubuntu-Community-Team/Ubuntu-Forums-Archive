---
title: "Browsing files from other Linux box with Konqueror"
date: 2005-10-31
forum: Desktop Environments
---

### Post by Navyblue on 2005-10-31
Forgive me for this noobish question.

How do I browse files from other Linux box with Konqueror. Can anyone point me to a good resource?

Thank you.

---

### Post by beefsprocket on 2005-10-31
You've got two very good options: samba and nfs. Since NFS is quite particular to *nix, I'd say use it -- I find transfer speeds are more stable and faster in general using it. To configure it, read the excellent howto at tldp (linked below). Note that some parts may not be exactly the same as the how to -- don't worry. Just work through it in general. If you get absolutely stuck and cannot progress, the something is wrong, otherwise, just continue with the howto. Note that you'll want to install nfs-user-server and nfs-common on both boxes.

There are some howtos and threads on this site too, but you wanted a good resource, and tldp is one of the better ones for the more common and useful features of our dearly beloved OS ;)

[http://tldp.org/HOWTO/NFS-HOWTO/index.html]("http://tldp.org/HOWTO/NFS-HOWTO/index.html")

---

### Post by Navyblue on 2005-10-31
Thanks a lot. :)

Would look into NFS.

---

### Post by HermanAB on 2005-10-31
Actually, the best method is with ssh, since sshd is usually running on every Linux computer by default.  In Konqueror, use the fish ioslave.  Here is the syntax:
fish://ip.of.other.computer
fish://username@ip.of.other.computer
fish://username@ip.of.other.computer:22
fish://username@ip.of.other.computer:22/home/joesoap/whatever

The same thing works with smb:, ftp: and so on.

You can split the screen, log into one computer via ftp, another via fish and drag and drop files between them for example.  Very powerful.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by Navyblue on 2005-11-01
Thanks Herman,

That sounds interesting. Is there any prior setting to be done before that? I guess we need to fix the IP of both PC and the permission thingie? If yes how can I do it?

---

### Post by alvonsius on 2005-11-01
[QUOTE=Navyblue]Thanks Herman,

That sounds interesting. Is there any prior setting to be done before that? I guess we need to fix the IP of both PC and the permission thingie? If yes how can I do it?[/QUOTE]

Humm, sure I think. Beside of the IP (you can use DNS), First you must make sure that you have an account on the other linux box you're trying to connect. So whenever you were asked for username and password you cant supply the right one for you. About the permission stuff, I think you can contact the owner of that other linux box (maybe you :D ) and set some permission for you (ps: by default konqi will send you to your /home directory -- of course on that other linux box). Last but not least, make sure the other linux box is running SSH daemon.

PS: wew, how many "other linux box" were written on my posting??? :D

---

### Post by beefsprocket on 2005-11-01
[quote=HermanAB]The same thing works with smb:, ftp: and so on.

You can split the screen, log into one computer via ftp, another via fish and drag and drop files between them for example. Very powerful.
[/quote]

Not to be belligerent, but can't you do the same thing with nfs? No prefix necessary, just browse the directory that the nfs share is mounted on. 

Question: can an nfs share be mounted over an ssh connection? If so, isn't this likely one of the best combinations of a secure tunnel with transparent filesystem access? No idea how or if this idea works. If ssh can be accessed (through fish) as easily as a mounted nfs share, I might just think about switching.

---

### Post by Navyblue on 2005-11-01
[QUOTE=alvonsius]Humm, sure I think. Beside of the IP (you can use DNS), First you must make sure that you have an account on the other linux box you're trying to connect. So whenever you were asked for username and password you cant supply the right one for you. About the permission stuff, I think you can contact the owner of that other linux box (maybe you :D ) and set some permission for you (ps: by default konqi will send you to your /home directory -- of course on that other linux box). Last but not least, make sure the other linux box is running SSH daemon.

PS: wew, how many "other linux box" were written on my posting??? :D[/QUOTE]

If I were to have the same user name and password for both PC, does it mean that what is accesible to me on one machine would apply to the other machine as well?

How can I fix the IP thingie? If I fix the IP address of both machine, would it affect the DHCP stuff? Would anyone be able to guide me on what fiels to edit and stuff?

Thanks.

---

### Post by iH8forcedRegistration on 2005-11-01
I'm not sure what you actually mean by 'fix the ip thingie.'

If both machines can see the internet, then they both have an IP address. Let's say machine A is the machine you normally use, and machine B is the machine you want to get files from.

If you open up a terminal on machinine B, and type
```
/sbin/ifconfig
```
That should give you more information than you'd ever need about that computer's internet connection. Somewhere in there, you should have some lines like this:
```
eth0      Link encap:Ethernet  HWaddr 00:10:DC:7E:6C:2D
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.252.0

```

Then, if you open konqueror on machine A, and type 'fish://' followed by whatever your username is on machine B, followed by an '@', followed by machine B's inet addr (in my case 192.168.0.100) it should prompt you for a password, and just open the remote folder, which will then let you seamlessly access everything on machine B that you have access to on machine B.

In this example, the full url would be something like
fish://navyblue@192.168.0.100

---

### Post by Navyblue on 2005-11-02
ifconfig from PC1:
inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0

ifconfig from PC2:
inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0

From PC1's Konqueror, I typed fish://navyblue@192.168.1.2. I get this:

```

An error occurred while loading fish://navyblue@192.168.1.2:
Could not connect to host 192.168.1.2.

```

From PC2's Konqueror, I typed fish://navyblue@192.168.1.3. Konqueror says the same thing.

Did I do anything wrong? Firewall blocking? Does it need to have certain feature of Konqueror's turned on? I have most of the feature turned off as I only use it as a file manager.

---

### Post by iH8forcedRegistration on 2005-11-02
assuming your username on PC2 is navyblue, then no, you didn't do anything wrong.

At this point, I'd check to see whether PC2's ssh daemon is actually running. Open up a terminal on PC1, and try to do this:
```
ssh navyblue@192.168.1.2
```

On PC2, try this:
```
ssh navyblue@localhost
```

If it works from PC2, but not from PC1, then the problem is either your ssh configuration or a firewall. Make sure the following lines appear somewhere in PC2's /etc/ssh/sshd_config
[LIST]
[*]Subsystem sftp /usr/lib/openssh/sftp-server
[*]Port 22
[/LIST]
and also make sure that any line beginning with "ListenAddress" has been commented out.

If it works on neither machine, then there's a chance that sshd just isn't installed or isn't running for some reason.
```

# on PC2, do
sudo apt-get install openssh-server
sudo /etc/init.d/ssh start

```

---

### Post by peanut butter on 2005-11-02
just use saba it is very easy

just go to snaptic and install samba and sambe server (possibly abbreviated SMB) 

after that just right clickonthe folder you want to share and say SMB or samba inthe dropdownbox.
this should be easy if you were a window$ user

then just start konquer and in the address bar type:
smb:/[computer name or ip]

---

### Post by Navyblue on 2005-11-03
[QUOTE=iH8forcedRegistration]assuming your username on PC2 is navyblue, then no, you didn't do anything wrong.

At this point, I'd check to see whether PC2's ssh daemon is actually running. Open up a terminal on PC1, and try to do this:
```
ssh navyblue@192.168.1.2
```

On PC2, try this:
```
ssh navyblue@localhost
```

If it works from PC2, but not from PC1, then the problem is either your ssh configuration or a firewall. Make sure the following lines appear somewhere in PC2's /etc/ssh/sshd_config
[LIST]
[*]Subsystem sftp /usr/lib/openssh/sftp-server
[*]Port 22
[/LIST]
and also make sure that any line beginning with "ListenAddress" has been commented out.

If it works on neither machine, then there's a chance that sshd just isn't installed or isn't running for some reason.
```

# on PC2, do
sudo apt-get install openssh-server
sudo /etc/init.d/ssh start

```[/QUOTE]

Thanks for your very speedy response. :) I have actualually typed a reply soon after that but unfortunately the forum server went down and my reply is gone.

On PC1, "ssh navyblue@192.168.1.2" gives something like connection timeout.

On PC2, "ssh navyblue@localhost" gives:
ssh: connect to host 192.168.1.2 port 22: Connection refused

On /etc/ssh/sshd_config, I have added "Port 22", ssh complained that the "Subsystem" line has "Bad configuration option". Adding these two lines doesn't seems to have any difference.

On the firewall (firestarter) I have listed the IP address of another PC under "Allow connections from host".

And now on PC1, "ssh navyblue@192.168.1.2" gives:
ssh: connect to host 192.168.1.2 port 22: Connection refused

Any clue?

---

### Post by Navyblue on 2005-11-03
[QUOTE=peanut butter]just use saba it is very easy

just go to snaptic and install samba and sambe server (possibly abbreviated SMB) 

after that just right clickonthe folder you want to share and say SMB or samba inthe dropdownbox.
this should be easy if you were a window$ user

then just start konquer and in the address bar type:
smb:/[computer name or ip][/QUOTE]

I have tried what you have suggested.

If I were to use IP address, Konqueror would say connection time out and ask me to file a bug report.

If I were to use computer name, it would say that "can not connect to the host smb://pc2/".

Is there any prior configuration needed?

Thanks

---

### Post by Navyblue on 2005-11-03
[QUOTE=Navyblue]I have tried what you have suggested.

If I were to use IP address, Konqueror would say connection time out and ask me to file a bug report.

If I were to use computer name, it would say that "can not connect to the host smb://pc2/".

Is there any prior configuration needed?

Thanks[/QUOTE]

After playing with some of the Samba setting, I've been able to see the shared directory of another PC, but when I click on the directory, it prompts for a username and a password, when I key them in and click "OK", the same window pop up again prompting me for password, this goes on and on. Btw I have also set the inherit permission from parent directory thingie.

---

### Post by beefsprocket on 2005-11-03
Editing the smb.conf file to allow guest only access should do away with the pesky password prompt. There are instructions on a secure setup here:
[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure)

Specifically the part about smbpassword should fix things for you.

---

### Post by iH8forcedRegistration on 2005-11-03
[QUOTE=Navyblue]
On the firewall (firestarter) I have listed the IP address of another PC under "Allow connections from host".

And now on PC1, "ssh navyblue@192.168.1.2" gives:
ssh: connect to host 192.168.1.2 port 22: Connection refused

Any clue?[/QUOTE]

It looks like you're going the smb route, which is fine, but if you'd still like to try to make this work, let me know what happens when you run
```
sudo /etc/init.d/ssh stop
sudo /etc/init.d/ssh start

```

---

### Post by Navyblue on 2005-11-03
[QUOTE=beefsprocket]Editing the smb.conf file to allow guest only access should do away with the pesky password prompt. There are instructions on a secure setup here:
[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure)

Specifically the part about smbpassword should fix things for you.[/QUOTE]

I have followed the instruction in the link, it is sort of worse now, I can't even see the folders now.

Something must be quite wrong with both my systems.

---

### Post by HermanAB on 2005-11-03
Here is a Samba debug guide:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

smbclient is your friend... ;-)

Cheers,

H.

---

### Post by Navyblue on 2005-11-04
[QUOTE=iH8forcedRegistration]It looks like you're going the smb route, which is fine, but if you'd still like to try to make this work, let me know what happens when you run
```
sudo /etc/init.d/ssh stop
sudo /etc/init.d/ssh start

```[/QUOTE]

For some weird reason, I missed your post yesterday. If possible, I would like to try all method (provided that they are not too intimidating) and see whick works the best for me. I'd also prefer not to use a cannon to kill a fly. ;)

Btw, for some reason, it now works! I can browse file from one PC to another.

Just that if I include the "Subsystem" line is included it would complain that "Bad configuration option". And at the beginning of the connection Konqueror would complain that it can't authenticate or something like that. However, that only happen on the first connection. Not sure if it should be a concern.

Editted:

My network router actually automatically assign IP address, which means my network IP would not be always the same everytime I turn on my PC. Is there a way to ask ssh to automatically look for the right PC?

Thanks a lot for your help. :)

---

### Post by stimpack on 2005-11-06
If you are wanting the same IP address each time, edit /etc/network/interfaces

should be a line like 'iface wlan0 inet dchp'

change it to somthing like this

iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255

change 'address' to your prefered static ip. Your interface may be eth0 instead of my wlan0

---

### Post by Navyblue on 2005-11-07
[QUOTE=stimpack]If you are wanting the same IP address each time, edit /etc/network/interfaces

should be a line like 'iface wlan0 inet dchp'

change it to somthing like this

iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255

change 'address' to your prefered static ip. Your interface may be eth0 instead of my wlan0[/QUOTE]

I have done the changes as you have suggested. Internet works fine, but SSH cease to work. Other than the change of IP destination for the SSH, is there any other stuffs that need to set?

Thanks.

---

### Post by Navyblue on 2005-11-07
[QUOTE=Navyblue]I have done the changes as you have suggested. Internet works fine, but SSH cease to work. Other than the change of IP destination for the SSH, is there any other stuffs that need to set?

Thanks.[/QUOTE]


Ooops, I forgot to change the firewall setting. Everything is working great now. Thanks. :)

---


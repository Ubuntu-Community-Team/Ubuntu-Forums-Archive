---
title: "Samba - Do I need to install anything?"
date: 2016-01-10
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-01-10
Folks,

I have Ubuntu-Mate installed on a R-Pi, checking synaptic package manager I notice smbclient is installed and a smb.conf file is in /etc/samba

There are quite a few options in synaptic for samba so I don't want to install anything unnecessarly, does it run by default?

Geffers

---

### Post by Edward_Fish on 2016-01-11
Yes, Samba should run by default, but you'll need to fiddle with the config to share exactly what you want. I'm not sure if any changes are applied immediately, after a service restart, a full reboot, or something else. I personally prefer to use SFTP over Samba - it's a lot simpler.

---

### Post by Morbius1 on 2016-01-11
Samba - the server package - isn't installed by default in any Ubuntu release regardless of DE that I know of so you will have to install it yourself.

[I][COLOR=#0000cd]Note: The last Ubuntu MATE I installed was 14.10 so I don't know how many of these things have been "fixed" in the current release. I'm in the process of downloading 15.10 but given my current location this may take a few hours.

[/COLOR][/I][COLOR=#000000]I would make sure the following packages are installed:

The samba server package:
```
sudo apt-get install samba
```[/COLOR]

Just like Gnome/Unity MATE can create samba shares directly from it's file manager but that isn't installed by default either:
```
sudo apt-get install caja-share
```

There is ( or was back in 14.10 ) another problem with Printers not being able to "browse" for printers using samba. Back then you also needed to install this:
```
sudo apt-get install python-smbc
```
I think that's been replaced with a python3 package but I will know more when I install 15.10. Sorry I'm not more current.

---

### Post by Morbius1 on 2016-01-11
OK, 15.10 installed. Here's what I had to do:

Install the following packages:
```
sudo apt-get install samba
```
```
sudo apt-get install caja-share
```
```
sudo apt-get install cifs-utils
```

Then logoff and log back in again. This is to activate caja-share.

The issue with Printers has been fixed so it can browse for smb printers without you having to add anything.

---

### Post by Geoff_Lane on 2016-01-11
> **Edward_Fish said:**
>  I personally prefer to use SFTP over Samba - it's a lot simpler.

Agree but my daughter uses Windows and don't think she is familiar with sftp

Geffers

---

### Post by Geoff_Lane on 2016-01-11
> **Morbius1 said:**
> OK, 15.10 installed. Here's what I had to do:

Install the following packages:
```
sudo apt-get install samba
```
```
sudo apt-get install caja-share
```
```
sudo apt-get install cifs-utils
```

Then logoff and log back in again. This is to activate caja-share.

The issue with Printers has been fixed so it can browse for smb printers without you having to add anything.

Thanks Morbius, shall do that.

Geffers

---

### Post by Geoff_Lane on 2016-01-11
> **Morbius1 said:**
> OK, 15.10 installed. Here's what I had to do:

Install the following packages:
```
sudo apt-get install samba
```
```
sudo apt-get install caja-share
```
```
sudo apt-get install cifs-utils
```

Then logoff and log back in again. This is to activate caja-share.

The issue with Printers has been fixed so it can browse for smb printers without you having to add anything.

Damn,

keep getting this error;

> Net usershare returned error 255  Net usersshare add cannot convert name Everyone to a SID The connections was refused. Maybe smbd is not running

I ran smbd via /etc/init.d/smbd start just in case but same error.

Geffers

---

### Post by QDR06VV9 on 2016-01-11
Hi Geoff_Lane
See if this is of any help to you Post#3 and down
[http://ubuntuforums.org/showthread.php?t=1927243](http://ubuntuforums.org/showthread.php?t=1927243)
Regards

---

### Post by Edward_Fish on 2016-01-11
You might also need to install samba-common-bin.

sudo apt-get install samba-common-bin

---

### Post by deadflowr on 2016-01-11
> **Edward_Fish said:**
> You might also need to install samba-common-bin.

sudo apt-get install samba-common-bin

It's auto-pulled in by samba's installation,
apt ftw

---

### Post by Morbius1 on 2016-01-12
Run the following command:
```
testparm -s
```
And look for a line that looks like this:
> encrypt passwords = no
It could list it as "False" instead of no.

If it does edit /etc/samba/smb.conf, find the line above, and change no ( or False ) to yes.

Then restart samba:
```
sudo systemctl restart smbd
```
Or 
```
sudo /etc/init.d/smbd restart
```

You also might get that error message if you have a firewall in the way so disable it for the time being and see if the error message goes away.

---

### Post by Edward_Fish on 2016-01-13
> **deadflowr said:**
> It's auto-pulled in by samba's installation,
apt ftw

Oh really? I didn't know that. In my MagPi magazine (issue 40) it said that to install Samba do:
sudo apt-get install samba samba-common-bin
and so I guessed that it wasn't automatically added as a dependency. My bad!

And you can install SSH into Windows by using OpenSSH. Won't that also make it so you can type sftp://user@ip/folder into the address bar like in Ubuntu?

---

### Post by Edward_Fish on 2016-01-13
> **Edward_Fish said:**
> And you can install SSH into Windows by using OpenSSH. Won't that also make it so you can type sftp://user@ip/folder into the address bar like in Ubuntu?
Turns out that OpenSSH does NOT add SFTP to Windows Explorer but this tool here - Swish - does! Also it's free! Happy days!
[http://www.swish-sftp.org/](http://www.swish-sftp.org/)

---

### Post by Geoff_Lane on 2016-01-13
I am totally confused now.

It appears that a Windows10 machine can see the contents of shared drive running on Raspberry Pi (Mate) but if I click on Windows Network on the Raspberry Pi it says Unable to Mount, failed to retrive share list from server, connection times out.

So, remote machine can see it but not via network connection on host machine.

Geffers

---

### Post by Morbius1 on 2016-01-13
90% of the time it's the mecanism that translates host names to ip addresses is reversed.

On the ubuntu machine edit /etc/samba/smb.conf and under the "workgroup = workgroup" line add[I][COLOR=#0000cd]:
[/COLOR][/I][COLOR=#0000cd][/COLOR]
```
name resolve order = bcast host lmhosts wins
```
Save smb.conf and restart samba in this order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```

Wait a few minutes for things to settle down since this discombobulates Windows for a while. And see if it resolves the issue.

There is another way to do this but you would have to change the firewall for the Win10 private network to permit it.

Of course there is a more direct way to do this and that's to connect to the Windows machine directly by ip address:
```
caja smb://192.168.0.100
```

---

### Post by Geoff_Lane on 2016-01-13
Morbius,

Thank you for prompt reply; my mistake, the files are visible on the Win10 machine via media centre, not the file manager :(

That is a slight problem trying to do this remotely.

I'll keep this thread updated.

Geffers

---


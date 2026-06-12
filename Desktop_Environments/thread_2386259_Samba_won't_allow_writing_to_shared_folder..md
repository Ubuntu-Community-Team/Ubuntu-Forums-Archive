---
title: "Samba won't allow writing to shared folder."
date: 2018-03-03
forum: Desktop Environments
---

### Post by elpidiovaldez5 on 2018-03-03
I want to do file sharing.  I have two machines with Samba installed as follows:

  sudo apt install samba samba-common-bin
  sudo gedit /etc/samba/smb.conf

Add the following at end of smb.conf.  Note 'Public' names the share. The path can be anything.
    
```
[Public]

comment = needs username and password to access
path = /home/paul/Public/
browseable = yes
guest ok = no
writable = yes
valid users = @sambashare
```

    
  Add my account to samba by setting a samba password.
  sudo smbpasswd -a paul

  Create group:
  sudo groupadd sambashare

  Now add myself to samba group
  sudo gpasswd -a paul sambashare

  Make sure /home/paul/Public has correct permissions:
  sudo setfacl -R -m "g:sambashare:rwx" /home/paul/Public

  Try mounting a network share
  sudo mkdir /media/Data
  sudo mount -t cifs -o username=paul //192.168.1.100/Public /media/Data/

I am asked for the password and give the password I set with smbpasswd.

There is no error message and the share is mounted - I can see the remote contents under /media/Data.
However I cannot create a new file in /media/Data. 
  touch /media/Data/tmp.txt
  touch: cannot touch 'tmp.txt': Permission denied

The setup on the remote machine is (as far as I can tell) identical, both can see folders on the other machine, but neither can write to remote folders.

I think that the samba installation is incorrect on ONE of the machines because when I click on 'Network' in pcmanfm I see 'The specified location is not supported'. On the
other pcmanfm works fine.  However I can't find any difference in the samba set up or the file permissions.  

The file permissions on both machines are:

/home/paul/Public 
  owner=paul 
  group=paul 
  view content=anyone
  change content=only owner and group
  access content =anyone

/media/Data
  owner=root
  group=root
  view content=anyone
  change content=only owner
  access content =anyone

I notice that one machine can ping the other by name and the other can only ping by ip.

---

### Post by ubname on 2018-03-03
Are you using a server install without GUI? It's very simple to activate a samba share, just right click on the folder you would like to share:

[ATTACH=CONFIG]278768[/ATTACH]

---

### Post by elpidiovaldez5 on 2018-03-03
I am indeed doing all this without GUI.  I am using lubuntu.  Isn't the method you describe from Ubuntu ?

That being said, I'll happily install GUI if it will fix the problems without taking me down another rabbit hole.  Is there a single, simple package that will do that for me ?

---

### Post by ubname on 2018-03-03
Yes i'm using Ubuntu, so if you want you can switch to Ubuntu and you'll get the simple interface,
sorry did not realized you were using Lubuntu, I see it's in the title.

---

### Post by elpidiovaldez5 on 2018-03-03
I do not want to switch to Ubuntu at the moment.

I think it was a mistake to mount the remote folders on /media (although I got that from an guide on the internet).
I created ~/Shared on both machines and mounted the remote folders there.  Now one machine has write access
and the other does not.  I can't see the differences !  

The key seems to be that ./Shared shows owner as paul BEFORE mounting the remote folder.  Afterwards it switches
to root.  I can't see why !  The folder at the other side is ./Public owned by paul with permissions set by:
  sudo setfacl -R -m "g:sambashare:rwx" /home/paul/Public
  smb.conf says writeable=yes.

---

### Post by Morbius1 on 2018-03-03
> sudo mount -t cifs -o username=paul //192.168.1.100/Public /media/Data/
Take possession of the mounted share ( uid=1000 if your uid number on the client is 1000 ) and make sure there are no permissions interference from the server ( nounix ).

> sudo mount -t cifs -o username=paul[COLOR=#0000cd]**,uid=1000,nounix**[/COLOR] //192.168.1.100/Public /media/Data/
Can you write to the share now?

---

### Post by elpidiovaldez5 on 2018-03-03
Yes ! That solved it.  I had changed from using /media/Data as a mount point to a folder in my home directory to try to avoid ownership issues.

So I mounted using Morbius1's suggestion:

```
  sudo mount -t cifs -o username=paul,uid=1000, nounix //192.168.1.100/Public /home/paul/Share


```....and could write with no problems !  I tried another couple of tests and ascertained that it is is sufficient to do:

```
  sudo mount -t cifs -o username=paul,uid=1000 //192.168.1.100/Public /home/paul/Share


```Thank you VERY much, this problem took me to the brink of insanity, and on the far side.

Why do you think the systems are asymmetric ?  I don't need to do that for the connection the other way.

---

### Post by Morbius1 on 2018-03-03
Good question. Don't know.

Maybe the other machine has "unix extensions" set to "no". Run this command on that machine to find out:
```
 testparm -sv | grep "unix extensions"
```

---

### Post by elpidiovaldez5 on 2018-03-07
Both machines have "unix extensions = yes", so mystery continues.  Still my actual problem of getting bidirectional file updates is completely solved.

---


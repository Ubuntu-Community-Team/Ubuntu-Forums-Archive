---
title: "Ubuntu 10.04 Lucid Lynx: SAMBA issues?"
date: 2010-05-02
forum: Desktop Environments
---

### Post by egd on 2010-05-02
I've spent a good few hours struggling to access my Ubuntu PC from a W2K3 machine.  Prior to installing Lynx I had the same W2K3 machine accessing my home folder on Karmic using SAMBA.

Whilst the Lynx PC is visible from W2K3 accessing any of the shares asks for a password and using the SAMBA user password results in an authentication error.

Extract from /etc/samba/smb.conf```

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = box

[egd]
    path = /home/egd
;    available = yes
    writeable = yes
;    browseable = yes
    valid users = egd

[HITACHI400GB]
    path = /media/HITACHI400GB
;    available = yes
    read only = no
;    browseable = yes
    public = yes

[egd_backup]
    path = /media/egd_backup
;    available = yes
    writeable = yes
;    browseable = yes
    valid users = egd

```cat smbusers shows:```

egd = egd
```Via Samba Server Configuration / Server Settings / Security, authentication mode is set to "User"

SAMBA username/ pw were set using **sudo smbpasswd -a egd**

---

### Post by egd on 2010-05-03
I've been an Ubuntu user for the past 6 years and I've got to say this forum is the most pathetic part of the Ubuntu ecosystem: 83 views and not a single reply.  Seems the broader community is either generally disinterested in helping others or otherwise has NFI.  Guess it's back to Google, this forum is an absolute damned waste of time.

---

### Post by egd on 2010-05-03
For the benefit of others that may encounter the same problem it's solved by removing the semicolons ';' shown in the first post.  For some reason the System/Administration/Samba GUI adds these, so use a text editor and manually make the requisite changes.  When done, restart SAMBA as follows:```
sudo restart smbd
```

---

### Post by Sciamano on 2010-05-03
I'm having the same problem, but removing the semicolons did not work.
I use samba to access a shared folder with my xbox (to view videos on my TV using XMBC). It used to work perfectly, now after upgrading to Lucid it asks for the password, but it does not work.

Here is my old smb.conf

```

[SHARES]
path = /home/luca/Shares
comment = /home/luca/Shares
guest ok = yes
writable = yes
public = yes
only guest = yes
guest account = nobody
browsable = yes
```

After reading your post I modified it this way:

```

[SHARES]
path = /home/luca/Shares
comment = /home/luca/Shares
available = yes
writable = yes
browseable = yes
public = yes
```

But it still asks for the password.
Any suggestion you might have would be very much appreciated.

---

### Post by dnpate on 2010-05-08
try adding
security = shares (or share)

I am having difficulty with samba also and in my searching I think others were having the same problem as you and the above line I think helped.

David

---

### Post by zekica on 2010-05-08
You could try adding:
```
        map to guest = bad password
```

in [global] part of smb.conf

---

### Post by Sciamano on 2010-05-08
@dnpate and zekica: I've already tried both your suggestions with no success. :(

---

### Post by timbba on 2010-05-11
LTS version with broken Samba network shares. Great work! 

ubuntu should release when it is stable enough. This is just a nightmare to always test and see that something is broken.

---

### Post by Sciamano on 2010-05-11
For the problem that I encountered, there is a solution [HERE]("http://ubuntuforums.org/showthread.php?t=1471602").
It's no applicable to everyone, but if you are having problems with samba, check the thread and see if it might help.

---

### Post by timbba on 2010-05-12
> **Sciamano said:**
> For the problem that I encountered, there is a solution [HERE]("http://ubuntuforums.org/showthread.php?t=1471602").
It's no applicable to everyone, but if you are having problems with samba, check the thread and see if it might help.

Doesn't help with mine if the solution was to change fstab.

---

### Post by Sciamano on 2010-05-12
> **timbba said:**
> Doesn't help with mine if the solution was to change fstab.

Either that or adding the "force user = USERNAME" option in the smb.conf

---

### Post by timbba on 2010-05-12
> **Sciamano said:**
> Either that or adding the "force user = USERNAME" option in the smb.conf

Actually that helps.. thanks a lot! 

But I'm still wondering that why do I need to "force user"?

I had the same config on Karmic, which worked ok without forcing user. I can get also Lucid work without forcing user, but before that I need to recreate user's password after every boot of the machine:
```
sudo smbpasswd -a user
sudo service smbd restart
```

If retyping the same password than before, the authentication starts working. So there is definetely something really wrong on smbd service on Lucid. That need to be fixed and should have been fixed before releasing the 10.04!

---

### Post by Sciamano on 2010-05-12
I don't know man.. I've been using the same configuration for four years, and it just stopped working after the upgrade to Lucid.
There's definitely something wrong (or at least changed) in the samba service in Lucid...

---

### Post by Chadarius on 2010-05-18
There is really something wrong here. I am having the same issue. Samba just plain stopped working in every way when I upgraded to Lucid. Nice work Ubuntu! :)

This is especially bad for an LTS release. I usually don't have too many issues but I've been wasting so much time on this and I've got things to do!

I noticed that when I ran testparm that I was getting errors with /var/run/samba

```
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
```

So I added those directories. I don't get the error but I wonder if there is still an issue? It didn't change anything. It still doesn't work. 

Here is my totally none working smb.conf.

```

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts host wins bcast
	add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
	add group script = /usr/sbin/addgroup --force-badname %g
	add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
	os level = 35
	preferred master = Yes
	dns proxy = No
	message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0700
	directory mask = 0700
	guest ok = Yes

[shared]
	path = /home/shared
	read only = No
	guest ok = Yes
```

---

### Post by Chadarius on 2010-05-18
I'm not sure if this helps but I got mine working. I'm pretty sure that this is an "upgrade" issue and not a install issue, but I haven't had time to test that out yet.

The issues that I had was that Samba would not except any connections. It was missing the /var/run/samba directories. It also would not use the upstart system properly. I could not run restart smbd. 

I created the /var/run/samba directory with 0755 and root as the owner.

I ran the following commands to see if I could jog something loose.

```
sudo aptitude purge samba-client samba-common samba-common-bin
sudo aptitude install samba

```

Once I did that I was able to use upstart commands properly like "restart smbd" and I could connect properly from other workstations.

Weird stuff!

---

### Post by timbba on 2010-05-22
> **Chadarius said:**
> I'm not sure if this helps but I got mine working. I'm pretty sure that this is an "upgrade" issue and not a install issue, but I haven't had time to test that out yet.

The issues that I had was that Samba would not except any connections. It was missing the /var/run/samba directories. It also would not use the upstart system properly. I could not run restart smbd. 

I created the /var/run/samba directory with 0755 and root as the owner.

I ran the following commands to see if I could jog something loose.

```
sudo aptitude purge samba-client samba-common samba-common-bin
sudo aptitude install samba

```

Once I did that I was able to use upstart commands properly like "restart smbd" and I could connect properly from other workstations.

Weird stuff!

I have to test this now, because even forcing the user is not working for me anymore.

Shame on you Ubuntu developers. This just sucks!

---

### Post by egd on 2010-05-23
I see people are still having issues with this.  Here are my shares in smb.conf, which are now all operational:```
[egd]
    path = /home/egd
    available = yes
    writeable = yes
    browseable = yes
    valid users = egd

[HITACHI400GB]
    path = /media/HITACHI400GB
    available = yes
    read only = no
    browseable = yes
    public = yes

[egd_backup]
    path = /media/egd_backup
    available = yes
    writeable = yes
    browseable = yes
    valid users = egd

```

after doing above I added a password for user egd as follows:```
sudo smbpasswd -a egd
```

---

### Post by timbba on 2010-05-23
> **egd said:**
> ```
sudo smbpasswd -a egd
```

I have to do this after every boot ans restart smbd service. Otherwise the authentication fails. It should work automatically!

---

### Post by christophevr on 2010-06-01
Hello All,

I used samba for very long time. A couple of years .... ago I started using linux on that time debian. Now since 1 year ubuntu. Yes I spended months in finding out on how to use samba perfectly and save . Finnally I had my own optimum smb.conf file. 

LIKE MANY OTHERS UPGRADING TO 10.04 CAUSED MY samba not to not run anymore. 

But samba is installed  using synaptic. of course i always replaced the smb.conf by my own adapted one

WELL it's quit stupid but there is just missing the file samba into /etc/init.d which was the samba start stop file script

and the link to samba  /etc/init.d/samba named  S20samba into rc2.d rc3.d rc4.d and rc5.d which causes samba to start on boot. (on ubuntu it was on all of them by 9.10. I do not now which is default run level from ubuntu gues it's 2)

I'll appent here the samba start stop script from ubuntu 9.10 which has to be extracted and copied into /etc/init.d  and then just make the link to it into folder /etc/rc2 to rc5.d folder using sudo ln -s command example

open console

Youruser@Yourpcname:~$ cd /etc/rc2.d
Youruser@Yourpcname:/etc/rc2.d$ sudo ln -s /etc/init.d/samba S20samba
 do the same for rc3.d till rc5.d 

Soon I gues the way how samba is started will change. But for now it didn't

---

### Post by timbba on 2010-06-08
Solution that works for me:
```
sudo apt-get remove libpam-smbpass
```

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/566560](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/566560)

---

### Post by rollOver on 2010-06-26
Thanks for all the help, didn't have problems with Lucid until a recent update (thanks Ubuntu!) the purge/reinstall worked once I created entries (as shown here)in smb.conf.

Should warn folks to have a backup of this handy **before** the purge!

---

### Post by rollOver on 2010-06-27
> **rollOver said:**
> Thanks for all the help, didn't have problems with Lucid until a recent update (thanks Ubuntu!) the purge/reinstall worked once I created entries (as shown here)in smb.conf.

Should warn folks to have a backup of this handy **before** the purge!

After restart same problem resurfaces, can access the Ubuntu machine remotely except SAMBA, authentication error!

What was changed?

---

### Post by timbba on 2010-06-30
@rollOver: Is the user's password the same for the Unix and Samba? If not, then see my recent post. You have to remove the libpam-smbpass, because that will change samba password to the same than Unix on every boot.

---

### Post by rollOver on 2010-06-30
> **timbba said:**
> @rollOver: Is the user's password the same for the Unix and Samba? If not, then see my recent post. You have to remove the libpam-smbpass, because that will change samba password to the same than Unix on every boot.

I did double-check this just to be certain, they are identical. I do have this box set to autologin, if that has any bearing. I also tried the libpam-smpass remove--the system said it was not installed. I did an upgrade to lucid, not a clean install, BTW. Thanks for trying to help, I appreciate it!

I am going to try the purge/reinstall again and only add my shares to the stock .conf. Failing that I am going to build a new .conf following [this guide]("http://www.jonathanmoeller.com/screed/?p=1590").

I will post back either way.

---

### Post by rollOver on 2010-07-08
[Simplifying the smb.conf]("http://ubuntuforums.org/showthread.php?t=751773") file worked for me, I suspect PAM

---

### Post by felixq78 on 2010-07-12
> **egd said:**
> I've been an Ubuntu user for the past 6 years and I've got to say this forum is the most pathetic part of the Ubuntu ecosystem: 83 views and not a single reply.  Seems the broader community is either generally disinterested in helping others or otherwise has NFI.  Guess it's back to Google, this forum is an absolute damned waste of time.

You can't blame Newbies with NFI because when they do get replies the information has massive holes in it. They forget what it was like to start Linux after 10 years of M$ and so their advice makes ridiculous assumptions about the Newbie's abilities.Newbies need STEP BY STEP instructions leaving nothing out, they don't know a Terminal from an Electric Dog Polisher.

---


---
title: "Synaptic and source. list - don't work"
date: 2006-08-09
forum: Desktop Environments
---

### Post by geovino on 2006-08-09
Because of trying to install files to play dvds Synaptic does not work anymore. I looked at the source.list and all that's there is:
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

But I have a:
/etc/apt/sources.list.save
/etc/apt/sources.list_backup
/etc/apt/sources.list_backup_200608090453
/etc/apt/sources.list_backup_automatix_temp
/etc/apt/sources.list-eu-2006-8-7-12-30-30

Why do I have so many? And now Synaptic gives me this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Until I can fix this problem, I'm stuck with WinXP. Please help me fix these problems. Thanks.

---

### Post by wieman01 on 2006-08-09
A useful "source.list" generator. I use it all the time. Check it out:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

Should resolve your problem.

---

### Post by x64Jimbo on 2006-08-09
Woah! Cool! Bookmarked. ;)

---

### Post by geovino on 2006-08-09
> **wieman01 said:**
> A useful "source.list" generator. I use it all the time. Check it out:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

Should resolve your problem.

Thanks.

Do I put this in the source.list and rem out the one line that's there?

What do I do with the backup source.lists? Do I need them?

---

### Post by geovino on 2006-08-09
> **wieman01 said:**
> A useful "source.list" generator. I use it all the time. Check it out:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

Should resolve your problem.

I did what you said and added to my source.list. But I still got the error to use this:
 
$ sudo dpkg --configure -a

But it just hangs and doesn't complete. Does it take a long time to complete? 

its at:

davek@davek-desktop:~$ sudo dpkg --configure -a
Password:
Setting up mjpegtools (1.8.0-0.0ubuntu1) ...

Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

why does it stale? With out this I can't get synaptic to work!

---

### Post by wieman01 on 2006-08-09
You don't need to the backup source-lists anymore. Synaptic seems to create them after an update. It's up to you to either keep or delete them.

As for your problem ("sudo dpkg --configure -a") could you wait for a few minute until it's finished? Also try to run this command and see if there is any output:
> sudo dpkg --configure -a --debug=2000
I've had this problem before but "dpkg" was usually the way I resolved it.

---

### Post by geovino on 2006-08-09
The terminal has been running for 30 min... doesn't finish. 

Now I'm trying it again and this is all that's showing:

Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

that's with the debug command.

---

### Post by maniacmusician on 2006-08-09
> **geovino said:**
> I did what you said and added to my source.list. But I still got the error to use this:
 
$ sudo dpkg --configure -a

But it just hangs and doesn't complete. Does it take a long time to complete? 

its at:

davek@davek-desktop:~$ sudo dpkg --configure -a
Password:
Setting up mjpegtools (1.8.0-0.0ubuntu1) ...

Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

why does it stale? With out this I can't get synaptic to work!


I've also had this problem in the past; not so coincidentally, it was also with flashplugin-nonfree. I think there is a purge command to make it discard the flashplugin. or you might be able to go to synaptic, find flashplugin-nonfree, and unselect it.

---

### Post by geovino on 2006-08-09
I can't get into Synaptic at all. it keeps telling me to run the 


$ sudo dpkg --configure -a

I've tried many times and it does not finish so I can't do anyting with Synaptic. 

I'm almost ready to reinstall Ubuntu altogether. but that would be more trouble. 

I never had this much trouble with PCLinuxOS. I was hoping that Ubuntu would be as good. 

I'll keep trying until something works.

---

### Post by cstudent on 2006-08-09
Try this:

```

sudo dpkg -r --force-remove-reinstreq flashplugin-nonfree

```

Follow up if it works with:
```

sudo apt-get update

```


Hope this works for you.


cstudent

---

### Post by geovino on 2006-08-09
The first command worked.

This is what I got:

davek@davek-desktop:~$ sudo dpkg -r --force-remove-reinstreq flashplugin-nonfreePassword:
(Reading database ... 87883 files and directories currently installed.)
Removing flashplugin-nonfree ...
davek@davek-desktop:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outReading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
davek@davek-desktop:~$

Should I try again later? or did it work?

---

### Post by geovino on 2006-08-09
thanks... I did get back into Synaptic and hit reload, it gets to 11 of 12 files and hangs...

I wonder if the lib files are still there to run Kaffeine or Streamtuner. Trying to get them to work is what's caused all the problems. 

This is the error messages:

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out

How do I correct this?

---

### Post by cstudent on 2006-08-09
Those errors are due to connection problems to the repositories. More than likely, waiting a bit and trying again would be the solution. You could also remove the us. from the repositories that have it in your sources.list. Instead of us.archive.ubuntu.com just have it say archive.ubuntu.com. Then run sudo apt-get update again.

---

### Post by geovino on 2006-08-09
Got it working! Yeah!

But get this, when using Totem the aduio and video aren't in sink with each other, but when I use Kaffeine it works fine. How do I make Kaffeine the default dvd player?

---

### Post by wieman01 on 2006-08-09
> **cstudent said:**
> Those errors are due to connection problems to the repositories. More than likely, waiting a bit and trying again would be the solution. You could also remove the us. from the repositories that have it in your sources.list. Instead of us.archive.ubuntu.com just have it say archive.ubuntu.com. Then run sudo apt-get update again.

Just to confirm... Some of the servers are done for maintenance or other reasons and it happens quite regularly that one of them cannot be reached. It's annoying but a minor issue.

---

### Post by cstudent on 2006-08-09
> **geovino said:**
> Got it working! Yeah!

But get this, when using Totem the aduio and video aren't in sink with each other, but when I use Kaffeine it works fine. How do I make Kaffeine the default dvd player?

Well, that one I can't answer. I suggest you start another thread asking how to make Kaffeine the default. But it's considered proper to at least make an effort to search the forums first for an answer. It may have already been asked. And don't forget tried and true Google. I find a lot of times a search there will bring me to the right post on these forums.


Good luck :)

cstudent

---


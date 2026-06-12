---
title: "Samba Users - adding"
date: 2007-11-18
forum: Desktop Environments
---

### Post by Geffers on 2007-11-18
I am having problems adding a new Samba user, I think it may be down to Ubuntu's use of the ROOT user.

If from a command line I enter sudo smbpasswd -a username userpassword  I get returned to a page outlining various smbpasswd options.

It seems to be that I need to be ROOT but I think ubuntu locks this user out.

I have also tried using WEBMIN and from the Samba page there is no option to ADD a USER and I cannot log in as ROOT.

I need to create Samba users that match my windows users but seem unable to do so.

I have read some of the posts from similar questions but have been unable to find a remedy, any pointers appreciated.

Geffers

---

### Post by oldgit on 2007-11-18
sudo smbpasswd -a username

---

### Post by Geffers on 2007-11-18
> **oldgit said:**
> sudo smbpasswd -a username

If I do that I get the following;
geoff@challenger:~$ sudo smbpasswd -a geffers
Password:
New SMB password:
Retype new SMB password:
Failed to modify password entry for user geffers
geoff@challenger:~$ 

That may be due to the fact I don't think I have yet created a user 'geffers'

So still no luck.

Geffers

---

### Post by tlayton_at_work on 2007-11-18
Try:

```

sudo smbpasswd -L -a geffers	(set a password)
sudo smbpasswd -L -e geffers	(enable user)

```

---

### Post by Geffers on 2007-11-19
> **tlayton_at_work said:**
> Try:

```

sudo smbpasswd -L -a geffers	(set a password)
sudo smbpasswd -L -e geffers	(enable user)

```

It fails at the first line as shown;

geoff@challenger:~$ sudo smbpasswd -L -a geffers
New SMB password:
Retype new SMB password:
Failed to modify password entry for user geffers

I think my problem may be that I haven't managed to CREATE the user geffers yet.

Geffers

---

### Post by toolagio on 2008-05-13
Hi Geffers,

I'm in the same state on a very new install (8.04) and am curious what it was you did to rectify this.

Thanks

---

### Post by Geffers on 2008-05-15
> **toolagio said:**
> Hi Geffers,

I'm in the same state on a very new install (8.04) and am curious what it was you did to rectify this.

Thanks

Strangely, at the moment I have two Linux ubunto machines and an XP laptop.

The XP laptop can access both Linux machines but the Linux machines cannot access each other.

I never did get my head fully round the samba command line entries so would suggest you install webmin, from this interface you can tweak a number of Linux utilities.

Go to [http://www.webmin.com/](http://www.webmin.com/) and use the debian package.

Geffers

---

### Post by mopey on 2008-06-10
This is an old thread, but I thought I'd reply just the same.

By default, I think the backend setup for Ubuntu requires for the user to also exist in /etc/passwd.  Most likely you're getting the error because this is not the case.

---

### Post by Geffers on 2008-06-12
> **mopey said:**
> This is an old thread, but I thought I'd reply just the same.

By default, I think the backend setup for Ubuntu requires for the user to also exist in /etc/passwd.  Most likely you're getting the error because this is not the case.

I use webmin for configuration and it has an option to convert samba users to unix, this worked on my previous set up and all now resolved.

Trouble is I'm not sure what resolved it :)

Geffers

---


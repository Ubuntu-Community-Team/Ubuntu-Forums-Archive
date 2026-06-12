---
title: "FTP Client for Gnome"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Donald F. Robertson on 2006-08-22
Can anyone recommend an easy-to-install and easy-to-use FTP client for Ubuntu-6.06 running Gnome?  There appear to be only two in the add software list, one conflicts with another program and one only works with KDE.

Thanks!

-- Donald

---

### Post by Roger Mudd on 2006-08-22
Give GFTP a shot.

---

### Post by jackn on 2006-08-22
Ncftp basically uses the same terms as 'ftp' and its ilk ('open', 'put', etc), so easy to get the hang of. It also has the added advantage of being able to upload directories.

It is CLI-based. but 'man ncftp' is well-written and you should be good to go in a giffy.

Jackn

---

### Post by aysiu on 2006-08-22
There are no FTP programs that work for only KDE.

Go ahead and install and use KFTPGrabber. It's a great program, and it'll work just fine in Gnome.

---

### Post by dlai on 2006-08-22
What is wrong with Places --> Connect to server ? I really like that feature!

---

### Post by Danny Boy on 2006-08-22
> **dlai said:**
> What is wrong with Places --> Connect to server ? I really like that feature!

Exactly that makes thing so simple, and works better than GFTP; IMO

---

### Post by aysiu on 2006-08-22
I don't know if this is the same thing, but you can also use Nautilus as an FTP client.

---

### Post by Donald F. Robertson on 2006-08-27
Thank you all, but I'm very frustrated.

I cannot install _any_ FTP client.  Add/Remove programs returns, not in any channel.  Manual installs fail because of some missing dependency that itself cannot be installed.

Places --> Connect to Server appears to work, but it puts me into a place on my provider's servers where I cannot find my directory, and the automatic re-direction that is supposed to take me to my directory does not work.

I have successfully logged into the correct directory with the terminal, but neither cp or put seem to work and I don't know enough command-line linux to trouble-shoot.

I have to ask why there isn't a working FTP client in Ubuntu-6.06?

-- Donald

---

### Post by taurus on 2006-08-27
What does your /etc/apt/sources.list look like then because gftp is in the repos???

```
more /etc/apt/sources.list
```

---

### Post by aysiu on 2006-08-27
As I said before, you can just use Nautilus. Type in the FTP address in the location bar.

As for the dependency issue, you probably having conflicting repositories. [**Get a fresh list**](http://www.psychocats.net/ubuntu/sources) and then try again.

---

### Post by Donald F. Robertson on 2006-08-27
Okay, I've managed to get into my directory on my provider's server.  Thanks again!

-- Donald

---

### Post by dlai on 2006-08-27
Good! You can log directly into the folder by writing the folder location in the Folder: field in Places --> Connect to server

---

### Post by infoseeker on 2006-08-27
If all fails .... use mc (midnight commander) :)

---

### Post by Raval on 2008-03-12
> **aysiu said:**
> There are no FTP programs that work for only KDE.

Go ahead and install and use KFTPGrabber. It's a great program, and it'll work just fine in Gnome.

is there a Gnome equiv. similar to KFTP?

I'm looking for a Gnome FTP prog. that does multi. tabs.

---

### Post by morningboat on 2008-03-12
You can check this list of FTP programs on GnomeFiles: [http://gnomefiles.org/subcategory.php?sub_cat_id=44](http://gnomefiles.org/subcategory.php?sub_cat_id=44)

---


---
title: "Apache HTTP Server"
date: 2006-07-25
forum: Desktop Environments
---

### Post by ssodhi on 2006-07-25
I just installed Apache Webserver, I'm 95% sure the install is fine.

I've used it on Windows before, however when I try to save a file to my "www" folder it says that I am not the owner and I do not have permission to make a file there.

Thing is, I am on the only account that there is, the one I created when I installed Ubuntu.


I am really at a loss as to what to do.

---

### Post by Clouseau__ on 2006-07-25
> **ssodhi said:**
> however when I try to save a file to my "www" folder it says that I am not the owner and I do not have permission to make a file there.

Hi,

try using the command line with sudo:

```
sudo cp /original/path/index.html /var/www/index.html
```

You can also use mv instead of cp to move the files ... sorta like cut/paste instead of copy/paste  :)


hope that helps!

Clouseau__

---

### Post by Jivicin on 2006-07-26
> **ssodhi said:**
> I've used it on Windows before, however when I try to save a file to my "www" folder it says that I am not the owner and I do not have permission to make a file there.

The /var folder is a system folder be default, and normal users won't have write access to it.  Two possible solutions would be:

1.```
sudo chmod 755 -R /var/www
```
If 755 doesn't work, try 777.

2. Copy the contents of /var/www to your desired www folder, remove the /var/www folder, and create a symlink to your desired folder.  Something like:
```
cp /var/www ~/public_html
sudo rm -r /var/www
sudo ln -s ~/public_html /var/www
```

---

### Post by ssodhi on 2006-07-28
Hurrah! I found an old post in these forums that told me to use "chown -R sanjeet /var/www"

Thanks to everyone who gave me help, nonetheless.


This is my only grievance with Ubuntu: The permissions sometimes get in the way of functionality

---

### Post by wthanna on 2006-07-28
permissions...   they also "get in the way" of Viruses.. Trojans.. Hackers..  accidental deletion of key system files, etc.    :D

---


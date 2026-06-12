---
title: "Install Tovid"
date: 2006-06-15
forum: Desktop Environments
---

### Post by cazz on 2006-06-15
I try to install tovid on my Ubuntu.

but when I run apt-get update it say something about


```
W: GPG error: http://packages.kirya.net stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EEFB43B2FBABB737
```

I have surf around a little and found I have to write gpg as root but my Ubuntu dont like if I write 

*sudo gpg --export -a FBABB737 | apt-key add -*

```
sudo gpg --export -a FBABB737 | apt-key add -
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error
```

I have even try without the last -

---

### Post by taurus on 2006-06-15
Download the latest version, tovid-0.27.tar.gz, from [http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page).  Unpackage, build, and install it by hand as
```

cd ~/Desktop
tar xvzf tovid-0.27.tar.gz
cd tovid-0.27
./configure
sudo make install

```
It will be installed in /usr/local/bin...

---

### Post by user1397 on 2006-06-15
Taurus, so doing "sudo make install" truly works? If you look at my last post in my thread[SIZE=2]:[/SIZE] 	 	  		 		 			 				 				 				 				 			 			 			 			 			 			 			 				[SIZE=2][Weird tovid problem..........]("http://ubuntuforums.org/showthread.php?t=195498") 			 			([IMG]http://ubuntuforums.org/images/lite/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=195498") [2]("http://ubuntuforums.org/showthread.php?t=195498&page=2")), you will see that there are some errors after I do that command.
[/SIZE]

---

### Post by user1397 on 2006-06-15
btw, tovid isn't in the repositories anyway, so don't even try looking for it with apt-get. :p

---

### Post by cazz on 2006-06-15
No I have add

deb [http://packages.kirya.net/debian/](http://packages.kirya.net/debian/) stable main contrib non-free 
deb-src [http://packages.kirya.net/debian/](http://packages.kirya.net/debian/) stable main contrib non-free 

in the sorce list.

So what do I have to do to install Tovid???

---

### Post by user1397 on 2006-06-15
[quote=cazz]No I have add

deb [http://packages.kirya.net/debian/]("http://packages.kirya.net/debian/") stable main contrib non-free 
deb-src [http://packages.kirya.net/debian/]("http://packages.kirya.net/debian/") stable main contrib non-free 

in the sorce list.

So what do I have to do to install Tovid???[/quote]just follow taurus's directions

---

### Post by cazz on 2006-06-15
ok :)

---

### Post by tuxcantfly on 2006-06-25
[http://tovid.sourceforge.net/download/kubuntu/](http://tovid.sourceforge.net/download/kubuntu/)

also has deb packages

---

### Post by thick0 on 2006-10-23
does the kubuntu deb package work for gnome ubuntu as well? If not does anyone know where I can find an ubuntu package

---

### Post by halitech on 2006-10-28
I tried them but didn't seem to do anything but the CLI instructions work like a charm

---

### Post by thepriest on 2008-01-27
Taurus - Thank you that worked like a charm. I tried following the instructions at the Tovid Wiki site, but they weren't very clear. Thanks again.

---


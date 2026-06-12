---
title: "Setting up CVS?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Airjoe on 2006-07-10
I'm sorry if this doesn't belong on these forums...

I want to install a CVS server on my kubuntu box. I got as far as apt-get install CVS, and that's it. Can anyone help me configure CVS? 

Thanks!

---

### Post by Sendervictorius on 2006-07-10
Plenty of good sites on the internet that explain. Google is your friend.

This link explains all:
[http://www.network-theory.co.uk/docs/cvsmanual/index.html](http://www.network-theory.co.uk/docs/cvsmanual/index.html)

---

### Post by Airjoe on 2006-07-11
I have CVS installed now, but whenever I try to login, it asks me for a password, and no matter what I put, I get:
cvs [login aborted]: reading from server: Connection reset by peer

Where/how do I set this password? I read somewhere that you need a passwd file, but you need to get an encrypted password using crypt() but I don't have the crypt command. I also read that if you don't have the passwd file, it'll just read from the computer's normal users. 

Any help? Thanks!

[edit]
When I telnet to localhost 2401, I get:
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.


I think something's wrong with connections on my box. I get a similar error with svn, and the same thing with telnet.

---

### Post by Airjoe on 2006-07-12
Bump?

---

### Post by Sendervictorius on 2006-07-13
Not sure I can help. I'm not an expert in CVS. 

This link explains how to set up CVS on ubuntu. The CVS section is about half-way down the page.

[http://doc.ubuntu.com/ubuntu/serverguide/C/version-control-system.html](http://doc.ubuntu.com/ubuntu/serverguide/C/version-control-system.html)

I'm not sure how far you have got, and how far you have succeeded. I assume you are trying to connect in client-server mode, using pserver. I assume you have read [The Manual]("http://ximbiot.com/cvs/manual/cvs-1.11.21/cvs_toc.html") and followed the instructions, and initialized a repository, using cvs init (or imported).

I suspect you have not configured or are not running xinetd (or inetd). They are not loaded into ubuntu by default - you will have to install xinetd (or netkit-inetd) in synaptic if you haven't already) 

Please say what steps you have taken, instructions you have followed. Then we can work out what is not working.

---

### Post by Airjoe on 2006-07-13
I did install netkit-inetd. I have edited inetd.conf in /etc and then I did /etc/init.d/inetd restart. I also believe this is where the problem lies, because I'm almost sure I did something wrong, as I've never used inetd (or xinetd?). 

Anyway, thanks for helping out so far, I'll check out that link.

inetd.conf:
#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd

cvspserver  stream  tcp  no  root  /usr/local/bin/cvs --allow-root=/usr/local/cvsroot -f pserver	

svn stream tcp nowait svnowner /usr/bin/svnserve svnserve -i

---

### Post by Airjoe on 2006-07-13
I just installed xinetd. That tutorial says to edit "/etc/xinetd/cvspserver", but there is no /etc/xinetd directory. 

I'm trying to use SVN now (It doesn't matter to me, I just want either one to work!), and when I try:
svn co file://192.168.1.105/home/myname/repos
from a computer on the network, I get:
svn: Unable to open an ra_local session to URL
svn: Unable to open repository 'file://192.168.1.105/home/myname/repos'

If I try svn co [http://192.168.1.105/svn](http://192.168.1.105/svn) I get
svn: PROPFIND request failed on '/svn'
svn: PROPFIND of '/svn': 405 Method Not Allowed ([http://192.168.1.105](http://192.168.1.105))


Any help?
THanks so much!

[edit]
Doing
svn so file://localhost/home/myname/repos

Works fine. I just need it so other people can use this. Thanks!

---

### Post by Sendervictorius on 2006-07-14
I think that's supposed to be in /etc/xinetd.d directory.

Anyway, check the contents of /etc/xinetd.conf file - which specifies the search directories.

I can't help with svn

---

### Post by Airjoe on 2006-07-15
I got SVN working now!

Thanks for all the help!

---

### Post by Sendervictorius on 2006-07-15
Good to hear.

From what I understand, it is a better choice than CVS anyway.

---

### Post by reformist on 2006-09-30
If you don't want to mess with xinetd, you can write a simple init.d script for svnserve to run it like other processes. I've posted a script here, along with instructions on how to use it-

[http://philisoft.com/blog/a-subversion-initd-script-for-ubuntu-linux/]("http://philisoft.com/blog/a-subversion-initd-script-for-ubuntu-linux/")

---


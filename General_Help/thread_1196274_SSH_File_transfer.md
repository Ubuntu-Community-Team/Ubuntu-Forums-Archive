---
title: "SSH File transfer"
date: 2009-06-24
forum: General Help
---

### Post by crzyone9584 on 2009-06-24
I jsut recently bought a vps. Unforntaly the host just took down HyperVM before I bought it. So now im stuck using ssh till I get my own control panel. I found this one for vps control

[http://www.vtonf.com/downloads.html](http://www.vtonf.com/downloads.html)

Its free although its in beta.  First is there any other free VPS control panels? But mainly im having trouble with transfering files from my laptop to the vps. This is what I'm using

```
scp -r /home/xxx/Desktop/vhcs-2.4.8.tar.bz2 crzyone9584@myserver ip:/

```

This is what the terminal gives me

> /home/crzyone/Desktop/vhcs-2.4.8.tar.bz2: No such file or directory


Any one know what im doing wrong?

The server is running ubuntu hardy 8.04 Server. I'm running Ubuntu Jaunty

---

### Post by NT4usB on 2009-06-24
Try scp -v bla bla bla...
for verbose output.

---

### Post by sedawk on 2009-06-24
1) The local file doesn't exist - typo?.
   This is not a problem of using "scp", Try to "ls -l" the file.

2) There is a underscore missing in the statement (4 arguments, should be 3)

3) You don't need recursive copy (-r) to copy just one file

4) You are trying to write to the root directory of myserver, this
   might not work if the user crzyone9584 doesn't have correct permissions.

```

scp /home//home/crzyone/Desktop/vhcs-2.4.8.tar.bz2 crzyone9584@myserver_ip:

```
This will copy the file (make sure it exists) to the home directory
of crzyone9584 on myserver.

---

### Post by bodhi.zazen on 2009-06-24
If you like you can try gftp.

gftp if a gui font end and will connect over ssh (scp).

With scp you sould specify a user and path. The user must have permission to the directory.

scp foo user@server:/home/user
scp foo root@server:/root

Use the second option if you do not have a user on your VPS .

---

### Post by geirha on 2009-06-24
Does it allow sftp as well (very likely)? If so, go to Places -> Connect to server ...
Choose SSH as the type, and fill in the server and username fields. Now you can drag and drop files to and from the server using nautilus.

---

### Post by crzyone9584 on 2009-06-24
Well as it stands all i have is SSH access. Hense im trying to get a Control panel up there. Even if its beta. Ill have to try gftp. see if it works. If it does ill be greatful and be able to install the control panel and start setting up my server. Just after i get the vps os re-installed. (once again) i love figureing things out i dont know how to use. Go host for tkaing down hypervm lol

Thanks for the suggestions all.

I'll post/edit to tell ya guys which one worked.

---

### Post by crzyone9584 on 2009-06-25
Sftp work jsut fine. Thank you for your guyses help.

Does anyone know any good free vps control panel. I found VPS Control Panel form here

[http://www.vtonf.com/features.html](http://www.vtonf.com/features.html)

But its still in beta. Lastly what is nativly installed on ubuntu server.

is all this installed by the install or do i have to install it myself?

> apache2
apache2-common
apache2-mpm-prefork
bind9
bzip2
courier-authdaemon
courier-base
courier-imap
courier-maildrop
courier-pop
diff
dnsutils
gcc
gzip
iptables
libapache2-mod-php4
libberkeleydb-perl
libc6-dev
libcrypt-blowfish-perl
libcrypt-cbc-perl
libcrypt-passwdmd5-perl
libdate-calc-perl
libdate-manip-perl
libdbd-mysql-perl
libdbi-perl
libio-stringy-perl
libmail-sendmail-perl
libmailtools-perl
libmcrypt4
libmd5-perl
libmime-perl
libnet-dns-perl
libnet-netmask-perl
libnet-perl
libnet-smtp-server-perl
libperl5.8
libsasl2
libsasl2-modules
libsnmp-session-perl
libterm-readkey-perl
libterm-readpassword-perl
libtimedate-perl
make
mysql-client-4.1
mysql-common-4.1
mysql-server-4.1
original-awk
patch
perl
perl-base
perl-modules
php4
php4-gd
php4-mcrypt
php4-mysql
php4-pear
postfix
postfix-tls
procmail
proftpd-mysql
sasl2-bin
ssh
tar
wget

thats the list of packages i need installed  inorder to install teh VPS COntrol panel i found.

When i do 
sudo apt-get update then
sudo apt-get upgrade after everythign runs i get this

> perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"


how can i fix this?

---

### Post by bodhi.zazen on 2009-06-25
That is a common error message in VPS

```
sudo apt-get install language-pack-en 
 sudo locale-gen en_US.UTF-8 
 sudo /usr/sbin/update-locale LANG=en_US.UTF-8
```

---

### Post by crzyone9584 on 2009-06-25
> **bodhi.zazen said:**
> That is a common error message in VPS

```
sudo apt-get install language-pack-en 
 sudo locale-gen en_US.UTF-8 
 sudo /usr/sbin/update-locale LANG=en_US.UTF-8
```

thank you. It fixed my errors. and now on to installing the Control panel when i get home from work.

---


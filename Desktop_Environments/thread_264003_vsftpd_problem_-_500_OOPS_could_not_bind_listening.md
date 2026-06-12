---
title: "vsftpd problem - 500 OOPS: could not bind listening IPv4 socket"
date: 2006-09-24
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-09-24
I just installed vsftpd when I run it I get :
```
500 OOPS: could not bind listening IPv4 socket

```
what does it  mean?

---

### Post by dannytherocker on 2006-09-24
> **seshomaru samma said:**
> I just installed vsftpd when I run it I get :
```
500 OOPS: could not bind listening IPv4 socket

```
what does it  mean?

If I'm not wrong you have to give 755 permissions to the folder /home/ftp to access anonymous....try...

---

### Post by seshomaru samma on 2006-09-24
Thanks , but it didn't work......
:-( :-( :-(

---

### Post by aaronfromchina on 2006-10-03
I'v got the exactly same problem.

Look forward to reply.

thanks.

---

### Post by stimulator on 2006-11-25
Same problem here. Any help appreciated

---

### Post by kyozo on 2007-01-03
I solved the problem (googling it), but I'm a Linux Noob, so I'm not quite sure what the solution acutally does, so use it at your own risk :) 

I had the same problem (I assume you're just executing the vsftpd executable, and have set the listen property to YES in the config file). I solved it by starting the server this way 
```
sudo /etc/init.d/vsftpd start
``` 
I don't know what it does, but I assume it starts the server in some managed way. There is a lot about the server running either standalone or under some other stuff.

I would like to know why you can't just start it as a standalone server by executing the vsftpd executable (according to the man pages it is the recommended way).

Hope it helps, and that someone who knows what he is doing can explain why the recommended way doesn't work.


Cheers,

Kyozo

---

### Post by c.los on 2007-04-24
Kyozo, that worked great! Thanks.

I noticed when I ran it though it said vsftp was already running, I guess by default from when I installed it(?). So I just changed it so it would pick up the changes from vsftpd.conf.

```
sudo /etc/init.d/vsftpd restart
```

C

---

### Post by duval on 2007-05-01
Edit the /etc/vsftpd.conf and make sure that you have commented out the "listen=YES", if you are trying to run vsftpd through xinetd.

---

### Post by Niels1 on 2007-10-18
Hello, i use mac OS x and still got problems with vsftpd...

I'm kinda new in these things so i'll paste everything i did.

1.
Niels:~ nielsvanhuffel$ sudo port install vsftpd
--->  Fetching vsftpd
--->  Verifying checksum(s) for vsftpd
--->  Extracting vsftpd
--->  Applying patches to vsftpd
--->  Configuring vsftpd
--->  Building vsftpd
--->  Staging vsftpd into destroot
--->  Installing vsftpd 2.0.5_0

You can now start vsftpd in 3 ways,
either via a super-server like xinetd or inetd,
in standalone mode or if you're using Darwin 8.x
and above, launchd(8).

By default, vsftpd will runs in standalone
mode.

--->  Activating vsftpd 2.0.5_0
--->  Cleaning vsftpd

2. 
Niels:~ nielsvanhuffel$ sudo vsftpd
500 OOPS: could not bind listening IPv4 socket
Niels:~ nielsvanhuffel$ sudo vsftpd vsftpd.conf
500 OOPS: vsftpd: cannot open config file:vsftpd.conf

3. 
I checked the .conf file in dir /opt/local/etc/vsftpd.conf and i changed it to:
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=samurai
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/Users/ftp

4. 
/Users/ftp has CHMOD 755 restrictions and looks like: 
Niels:/Users/ftp nielsvanhuffel$ ls
opendir


My mac os x 4.x is not using init.d , only xinetd.d. I also tried to run it via xinetd.d via sudo /etc/xinetd.d/vsftpd start but this also failed (command not found).

Who can help me out?

---


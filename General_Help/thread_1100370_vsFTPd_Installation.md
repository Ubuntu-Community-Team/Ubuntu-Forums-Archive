---
title: "vsFTPd Installation"
date: 2009-03-19
forum: General Help
---

### Post by QuietSun on 2009-03-19
Hi all,

I'm a newbie.

We've been using some freeware FTP software (on Win2k) that recently, after virtualisation, fails for no apparent reason (I suspect that some clever person is using BIOS Int21h vectors or similar that VMWare simply doesn't like)

So, as I use Xubuntu desktop at home, I thought that I'd give Ubuntu server a go, and give vsFTPd a whirl; it comes highly recommended by the all seeing sage, Google.

I've installed the Ubuntu Server (8.10) without any of the software install options and made the following 'tweaks':

```
sudo apt-get updates
sudo apt-get dist-upgrade
Edited /boot/grub/menu.lst to contain vga=791 in the kernel entry
sudo init 6
sudo apt-get install vsftpd
```

So far so good.

Once vsFTPd installs I then run

```
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.original
```

For sanities sake I check the installtion by running

```
netstat -a | grep ftp
```

which shows that there is something listening out for requests.

I create the following directory structure:

```
/ftp
/ftp/root
/ftp/root/data
```

I modify the vsftpd conf file so it looks like this: (#'s removed for easy of reading)

```
listen=YES
#listen_ipv6=YES
anonymous_enable=YES
anon_root=/ftp/root
anon_other_write_enable=YES
#local_enable=YES
write_enable=YES
local_umask=022
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=ftp
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
#ftpd_banner=Welcome to blah FTP service.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
#chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```

This leaves me with the behaviour (from a Windows Explorer client) of being able to upload files into the /data directory, but not being able to download any files, unless, ahem (*runs and hides*) I run

```
sudo chown -R ftp /ftp/root/data
sudo chmod -R 777 /ftp/root/data
```

Apart from the obvious security flaws, I have the following questions that I need to resolve:

We have an old VMS system that needs to be able to treat an FTP server pretty much in the same way windows treats it's files system (add, remove, rename, delete files and directories) It's on the internal network.

How can I push further on this to achieve this end?

(Sorry for my nooby-ness)

---

### Post by QuietSun on 2009-03-19
I forgot to mention that after every change to the conf file I always run

```
sudo /etc/init.d/vsftpd restart
```

Missed that bit out

---


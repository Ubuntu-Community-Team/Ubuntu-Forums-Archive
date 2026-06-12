---
title: "How to create root user and login as root"
date: 2009-01-25
forum: General Help
---

### Post by elf_cleric on 2009-01-25
Hi Guys,
I have just installed ubuntu 8.4 and I am going to use it as an FTP server with vsftpd.

Question 1) Does ubuntu do the job as FTP server?
Question 2) Is it possible to create a root user or login as root?
If yes, how this can be done?

Cheers:p

---

### Post by sp0nge on 2009-01-25
Hello, 

As far as FTP, Ubuntu will work nicely.. I have a home server running that serves media and documents through the network and it is nearly flawless.

As for root, yes this s possible. However, I ask why you would want to do this? This will severely limit the security of the system, especially if you're running root as the account that is serving your network.

root is already created. You can become root like this:
```
me@home:~$ sudo su
```

[-XBut again, I caution you ***[COLOR="Red"]not to run this on a regular basis[/COLOR]***.[-X

---

### Post by HereInOz on 2009-01-25
For starters, one of the security measures in Ubuntu is that the root account is disabled.  Having said that, you can enable it in a terminal by typing:  sudo passwd root   then entering your own password to satisfy sudo, then inputting the root password.

for FTP, install proftp, and if you want a GUI to configure it, install gproftp.  Takes a bit of working out, but it does the job.  Essentially, to set up users in proftp, first set them up as system users.  Makes it a lot easier.  That is actually all you have to do if you just want them to have FTP access to their home folder, but if you want to create an FTP server environment, you need to get stuck into the configuration files or gproftp to do that.

---

### Post by HereInOz on 2009-01-25
Sorry, missed the bit in your post that you are going to use vsftpd.  Ignore my rantings on proftpd.

---

### Post by elf_cleric on 2009-01-25
Thanks guys,
I don't know if I understand correct?
Are you guys saying ProFTP is better?

By the way,
I am going to use the ftp server for my small company use not for home.

Users are gonna be our clients.

Can you please make a little clear?
What ftp server is good?

How do I configure the ftp ports etc...?

About the root acount,
I would like to have both user and root but make configs as root.
Login as normal user :)

Cheers

---

### Post by xc1024 on 2009-01-25
@elf_cleric, there's sudo to do such a thing.
you use it as ```
sudo <root_command>
```.
when you run a command with sudo, only this command is ran as root. all the commands after sudo work as usually.

---

### Post by elf_cleric on 2009-01-25
> **xc1024 said:**
> @elf_cleric, there's sudo to do such a thing.
you use it as ```
sudo <root_command>
```.
when you run a command with sudo, only this command is ran as root. all the commands after sudo work as usually.

Many thanks mate :)
This is clear now!

I am now wondering about the ftp server :)

---


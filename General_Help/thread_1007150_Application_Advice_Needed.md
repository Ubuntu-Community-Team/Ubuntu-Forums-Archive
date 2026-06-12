---
title: "Application Advice Needed"
date: 2008-12-10
forum: General Help
---

### Post by Tom_T on 2008-12-10
Hi
First post, please go easy !! :)

I'm a long time windows user, who works with Linux devices on a daily basis.

Normally I access the devices using FTP, Telnet or Web and this has always been done via an XP based laptop.

I've decided to move to Ubuntu and have installed 8.10 fine. I've got Firefox and Filezilla working with out any issues.

But now I'm looking for a Telnet client. I know I can use telnet via the terminal, but I was hoping to find something that would remember logins etc.

On XP I use IVT: Telnet/Ssh VT220 emulator [http://home.planet.nl/~ruurdb/IVT.HTM](http://home.planet.nl/~ruurdb/IVT.HTM)

I have search but can't seem to find anything similar.

Can Anyone offer some advise ??

Many Thanks

---

### Post by albandy on 2008-12-10
You can use putty:
sudo apt-get install putty

---

### Post by Tom_T on 2008-12-10
Thanks for the reply.

Will Putty remember previous login details and then log me in automatically ??

IVT will remember the username and password for each IP address I access. When I next visit that IP it will automatically log me in.

I can also specify the IP and username and it will pick the correct password, this allows for multiple usernames and passwords per IP address.

Any way to do this ??

Many Thanks :)

---

### Post by albandy on 2008-12-10
Putty can create profiles, but don't store users and passwords, let me look for something else.

---

### Post by Tom_T on 2008-12-10
> **albandy said:**
> Putty can create profiles, but don't store users and passwords, let me look for something else.

Thanks

---

### Post by binbash on 2008-12-10
+1 for putty

---

### Post by Tom_T on 2008-12-10
How about GPuTTY ??  That seems to offer support for saving profiles.

Next I will need to find a good tail and mysql front end..!!

---

### Post by albandy on 2008-12-10
For tail you have the command tail:

tail -f log.txt

And a good SQL manager is squirrel sql
supports mysql, postgresql, db2, oracle, etc ... works with jdbc, so any database that has a jdbc connector will work.

---

### Post by Tom_T on 2008-12-10
Thanks again for your help and support.

In XP I use baretail [http://www.baremetalsoft.com/baretail/](http://www.baremetalsoft.com/baretail/)

This allows you to open multiple files and highlight key words.. is that possible ??

If I can get the basic apps I use everyday sorted, it will make the move simpler !!

Thanks

---


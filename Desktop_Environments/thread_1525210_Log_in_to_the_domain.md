---
title: "Log in to the domain"
date: 2010-07-06
forum: Desktop Environments
---

### Post by evstevemd on 2010-07-06
Hi all,
I have my Box and I need to be able to Login in Company's Domain with my Ubuntu. I can login with my XP but I have not yet figured out how-to do that in Ubuntu. Any tutorial?
I should do that if possible without Doing Administrative stuffs on Server (I'm not IT Admin) :D

---

### Post by cutekazuya on 2010-07-06
Hi mate,

I have just setup ubuntu 10.04 at work on windows win2003 domain and am really pleased with it.

I have decided to contribute by helping people out.

1) First Iinstall likewise open

```
sudo apt-get install likewise-open 
```2) Join Domain```
sudo domainjoin-cli join mydomain.local Administrator
```                    replace "mydomain.local" with your domain name & Administrator with obviously your admin

enter password and thats it you should be able to log out and log in using yourdomain "backslash" username. my backslash key is broken lol

If the above dont work try:

   ```
 sudo apt-get remove likewise-open 
    sudo dpkg --purge likewise-open 
    sudo apt-get install likewise-open 
    sudo domainjoin-cli join mydomain.local Administrator
```Above commands will completely remove likewise open and then reinstall it and the last command is attempt to join again.

I would then add the domain user to the suoders by:

```
sudo gedit /etc/sudoers or sudo visudo 
```add the following line at the end of the file near:     # Members of the admin group may gain root privileges %yourdomain\\domain^users ALL=(ALL) ALL

Any domain user logged in will be able to sudo this way, if you want just a paticular user which would be yourself then add the line e.g.

%yourdomain\\username ALL=(ALL) ALL

I hope this helps you.

---

### Post by evstevemd on 2010-07-08
Suppose my domain is hosanna.co.in and my name is [email]steve@hosanna.co.in[/email] then would you help me re-write your way with the two info especially 
> sudo domainjoin-cli join mydomain.local Administrator 

Will it be  like this below. Am I right?
> sudo domainjoin-cli join hosanna myUbuntuRootUser

---

### Post by evstevemd on 2010-07-10
Ok I have made a little dug and found likewise-open GUI. I have filled in details but I'm normal domain user NOT admin. The GUI demands an admin!
Is there a way I can login to windows domain without dabbling with admin thing?
I can access shared network resources via samba but I need to login with my domain name and ubuntu box

Thanks

---

### Post by cutekazuya on 2010-07-11
By default all users in the domain have the permission to join upto 10 machines, but this depends on your domain setup. you have to use domain user credentials not the ubuntu root user.

You need to do something like this:

```
sudo domainjoin-cli join hosanna.co.in steve
```

once you enter the above you should see the following:

```
Joining to AD Domain:   hosanna.co.in
With Computer DNS Name: youcomputername.hosanna.co.in

steve@HOSANNA.CO.IN's password: 
```

at this point enter the password you used to log into the domain for user steve.

if you get the following error:

Error: Lsass Error [code 0x00080047]
```

9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS
server. Potentially the requested address does not exist.
```

try ```
sudo domainjoin-cli join hosanna.local steve
```
or ```
sudo domainjoin-cli join hosanna.com steve
```

if none of the above work, use the below 3 commands to completely remove and then install likewise-open

```
sudo apt-get remove likewise-open 
sudo dpkg --purge likewise-open 
sudo apt-get install likewise-open
```

Try now the domainjoin commands again.

---

### Post by evstevemd on 2010-07-12
Thanks a lot.
I was missing Admin password and I have contacted someone and have added me.
I hope after reboot I will be able to login.
Again, thanks a lot :P

---

### Post by evstevemd on 2010-07-12
How do I mark it solved?

---

### Post by gradysghost on 2010-07-26
Not sure if anybody's following this still.  I did the Likewise AD addition, and it worked flawlessly without any problems.  However, I cannot figure out how to log in with the domain user after the computer has been added to the domain.  FWIW, I'm in Ubuntu 10.04, and I've tried using my domain username with and without the domain prefix.  Is there a character other than backslash that I should use to delimit the domain name from the username?

---

### Post by de Silentio on 2010-07-28
At the login screen, click 'Other' then enter:
 
domain\username
 
where username is NOT [EMAIL="username@domain.local"]username@domain.local[/EMAIL]

---


---
title: "tasksel install mail-server.  now what?"
date: 2009-05-27
forum: General Help
---

### Post by whatch on 2009-05-27
what do I do to get a mail server going after I issue the command "tasksel install mail-server" and follow the prompts.  How do I log in the first time? Does webmail come with this?  It installed, but now what?  How do I create accounts or check mail?  Is the best way to get a mail server going?  I've read about citadel.  Thanks!

---

### Post by SOULRiDER on 2009-05-27
Check out:
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

### Post by albinootje on 2009-05-27
> **whatch said:**
> what do I do to get a mail server going after I issue the command "tasksel install mail-server" and follow the prompts.  How do I log in the first time? 

You would log in with the username that you did choose during the installation.
Which Ubuntu release did you use, by the way ?

> 
Does webmail come with this? 

With the command "dpkg -l|grep mail" you can see whether squirrelmail is installed.

See also here : [https://help.ubuntu.com/8.04/serverguide/C/email-services.html](https://help.ubuntu.com/8.04/serverguide/C/email-services.html)

---

### Post by albinootje on 2009-05-27
I recommend Postfix and Dovecot. If you want a simple mailserver it will take you about 5 minutes to set that up.

If you need help with it, report back here.

---

### Post by whatch on 2009-05-27
This is installed on 8.04.  I didn't give a username/password during install. I chose internet site and that was it.  Isn't the tasksel command supposed to install postfix and devocot?  I installed squirrelmail via synaptic afterward.  I tried to access it through a web browser after, with no luck.  

I guess I was hoping this would involve minimal config file editing.  I once installed a system called deepofix; it involved almost no configuring.

---

### Post by albinootje on 2009-05-27
> **whatch said:**
> I installed squirrelmail via synaptic afterward.  I tried to access it through a web browser after, with no luck.  

Did you install apache and php ?
[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

> 
I guess I was hoping this would involve minimal config file editing.  I once installed a system called deepofix; it involved almost no configuring.

Deepofix's last release was in 2007, is the project abandoned or is it easy to upgrade the software after an installation ?

---

### Post by whatch on 2009-05-27
I actually have moodle and ocs inventory installed on this machine, so yes I have apache2 and php.  I like deepofix, but want my moodle and mail server to be public.  This is a school we're talking about here.  I am lucky to get one public ip address.  I might use drupal or joomla on this box too.  I have an issue with young students using their own email accounts, which we do not want.  I my server hosts the email I can monitor their use.

---

### Post by albinootje on 2009-05-27
> **whatch said:**
> I have apache2 and php.

If you would be logged into the server, it would be [http://localhost/squirrelmail/](http://localhost/squirrelmail/) to check whether squirrelmail is available. 
Perhaps you need to copy a config file for apache from /etc/squirrelmail/ into the apache config directory and restart apache.

But for squirrelmail to be working properly, you need a working imap server (dovecot), and also have squirrelmail configured properly.

To check whether dovecot is already installed :
```

dpkg -l|grep dovecot

```
To check whether dovecot is running :
```

ps auxw|grep dovecot

```

---

### Post by whatch on 2009-05-27
This is what I see when I follow your instructions.  When I use my browser to access squirrelmail I get a page not found.  Does the following confirm I have dovecot installed and running?  Is copying the squirrelmail config file next? Thanks for the great assistance! -Will

root@vues-web:~# dpkg -l|grep dovecot
ii  dovecot-common                             1:1.0.10-1ubuntu5.1                  secure mail server that supports mbox and ma
ii  dovecot-imapd                              1:1.0.10-1ubuntu5.1                  secure IMAP server that supports mbox and ma
ii  dovecot-pop3d                              1:1.0.10-1ubuntu5.1                  secure POP3 server that supports mbox and ma
root@vues-web:~# ps auxw|grep dovecot
root     13348  0.0  0.0   2072   616 ?        Ss   May26   0:02 /usr/sbin/dovecot
root     13351  0.0  0.2   9008  2204 ?        S    May26   0:02 dovecot-auth
dovecot  13356  0.0  0.1   3484  1552 ?        S    May26   0:03 pop3-login
dovecot  13357  0.0  0.1   3484  1556 ?        S    May26   0:02 pop3-login
dovecot  13358  0.0  0.1   3484  1552 ?        S    May26   0:02 pop3-login
dovecot  13359  0.0  0.1   3492  1556 ?        S    May26   0:02 imap-login
dovecot  13360  0.0  0.1   3492  1556 ?        S    May26   0:02 imap-login
dovecot  13361  0.0  0.1   3492  1556 ?        S    May26   0:02 imap-login
root     18144  0.0  0.0   3008   776 pts/1    R+   13:44   0:00 grep dovecot

---

### Post by albinootje on 2009-05-27
> **whatch said:**
> This is what I see when I follow your instructions.  When I use my browser to access squirrelmail I get a page not found.  Does the following confirm I have dovecot installed and running?  

Yes, dovecot is running as imap and pop3 server.
> 
Is copying the squirrelmail config file next? 

Yes, I just checked that, try the following :
```

sudo cp /etc/squirrelmail/apache.conf /etc/apache2/conf.d/
sudo /etc/squirrelmail/conf.pl

```

---

### Post by whatch on 2009-05-27
Ok, your instructions worked and I can now get to the squirrelmail login screen.  However, I have not set up any usernames/passwords and none of the credentials I use are working (root/password).  How do I login for the first time, to create user accounts ect.?  Or, how do I find out what the administrator credentials are?  Thanks, I think I'm almost there!

---

### Post by albinootje on 2009-05-27
> **whatch said:**
> How do I login for the first time, to create user accounts ect.? 

If you have not changed anything in your dovecot configuration, then you can just create a new user with "adduser" or with the GUI for that : -> System -> Administration -> Users and Groups.

And, after logging in via squirrelmail, the new user's mail will be, in the future, located in ~/Maildir/

---

### Post by albinootje on 2009-05-27
Oh, forgot something, since you are using the most simple email setup (and not one with MySQL or LDAP), you should realise that those new users are also "normal" users, if you're also running things like ssh and ftp on that servers you probably want to think about that, and restrict access to that for them.

Another, perhaps easier, option is to change their default shell (bash) into something like "/bin/false", I just tested that, and it works fine with squirrelmail.

---

### Post by whatch on 2009-05-27
I can't login as an existing user?  Or, do I have to create new accounts?  I know how to create new user accounts through the gui, or through webmin.  I notice that dovecot and postfix are now groups.  I'm not sure I understand what you are saying.  Is there an existing administrator account that I can log in as now?  I can't log in with the same credentials as the root of the system; tried and it didn't work.  Confusion!!!

---

### Post by albinootje on 2009-05-27
> **whatch said:**
> I can't login as an existing user?  Or, do I have to create new accounts?

On the Ubuntu forum here we're not allowed to talk extensively about having a password for the root user. Besides that the root user has its home in /root, and all the others users have it in /home by default, perhaps that is the reason you can't log in via squirrelmail ?

And there is no special admin account for squirrelmail,dovecot, and postfix.
You should be able to login via squirrelmail with another user, unless you have changed the server section in the squirrelmail settings. I've testing the default squirrelmail settings (Ubuntu 9.04 -> localhost, port 143) and those worked fine.

I tested it with another user account, and I didn't have to create the ~/Maildir/ directory tree structure.

---

### Post by albinootje on 2009-05-27
Can you try adding another user ? For example :
```

sudo adduser test1

```
And test squirrelmail with that ?
If it again fails, try looking at the apache log files in /var/log/apache2/ to possibly find out more information.

---

### Post by whatch on 2009-05-28
When I try to login with a new user I created I get this message:

ERROR
Error connecting to IMAP server: localhost.
-1080097580 :
Go to the login page

---

### Post by albinootje on 2009-05-28
> **whatch said:**
> When I try to login with a new user I created I get this message:

ERROR
Error connecting to IMAP server: localhost.
-1080097580 :
Go to the login page

Make sure you can connect to dovecot via localhost on port 143.
[http://wiki.dovecot.org/TestInstallation](http://wiki.dovecot.org/TestInstallation)

---


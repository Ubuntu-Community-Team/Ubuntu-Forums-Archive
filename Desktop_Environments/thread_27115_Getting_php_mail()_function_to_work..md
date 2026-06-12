---
title: "Getting php mail() function to work."
date: 2005-04-14
forum: Desktop Environments
---

### Post by Levander on 2005-04-14
I'm trying to get the php mail() function to work under Ubuntu Warty, but the email never shows up in the recipients box.

When I pull this php script up in a browser:

<?php mail('levander@mindspring.com', 'testing php mail()', 'test') ?>
Did the mail get sent?

This gets output to my /var/log/mail.log file

Apr 14 22:37:15 bread postfix/pickup[4090]: 7318B205F4: uid=33 from=<www-data>
Apr 14 22:37:15 bread postfix/cleanup[5261]: 7318B205F4: message-id=<20050415023715.7318B205F4@mindspring.com>
Apr 14 22:37:15 bread postfix/cleanup[5261]: 7318B205F4: to=<unknown>, relay=none, delay=0, status=bounced (No recipients specified)
Apr 14 22:37:15 bread postfix/cleanup[5264]: 81982205FB: message-id=<20050415023715.81982205FB@mindspring.com>
Apr 14 22:37:15 bread postfix/qmgr[31460]: 81982205FB: from=<>, size=1921, nrcpt=1 (queue active)
Apr 14 22:37:15 bread postfix/smtp[5265]: 81982205FB: to=<www-data@mindspring.com>, relay=smtpauth.earthlink.net[207.69.189.202], delay=0, status=sent (250 OK id=1DMGhn-0005cz-Mt)
Apr 14 22:37:15 bread postfix/qmgr[31460]: 81982205FB: removed

Relevant lines in /etc/php4/apache2/php.ini:

[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = [email]me@example.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail
sendmail_from = [email]levander@mindspring.com[/email]

And, mail does work fine from the command line, but the relevant lines from /etc/postfix/main.cf I had to add / modify to get it working:

myhostname = mindspring.com
# myorigin = /etc/mailname
mydomain = mindspring.com
myorigin = $mydomain
relayhost = smtpauth.earthlink.net

---

### Post by heimo on 2005-04-14
Your php script is correct. No problems there. But to me it looks like you haven't reloaded Apache (or restarted) since editing php.conf? The from address is still www-data, not the one specified in conf. Try restarting Apache. It may or may not be the problem (for me the default mail settings ini php.conf worked).

---

### Post by Levander on 2005-04-16
[QUOTE=heimo]No problems there. But to me it looks like you haven't reloaded Apache (or restarted) since editing php.conf? [/QUOTE]


I see what you're saying, and have concentrated my efforts on php.ini.  I assume you meant php.ini, and not php.conf

I re-ran the phpinfo() call, to make sure I was editing the right php.ini - I was.

I am using the /etc/init.d/apache2 script to restart apache2 after I make changes to php.ini

Really not sure what else to check.

I am kind of wondering if I'm getting an error parsing the php.ini file or something.  I changed php.ini so that display_startup_errors is on, and moved the php errors out of the apache2 log.  All I see in there is a lot of messages like this:

[16-Apr-2005 16:13:39] PHP Warning:  Function registration failed - duplicate name - mysql_connect in Unknown on line 0
[16-Apr-2005 16:13:39] PHP Warning:  Function registration failed - duplicate name - mysql_pconnect in Unknown on line 0

I think those have always been in there though, don't know why I'm getting those.  I'm not running anything during these test besides the script to send a test mail above.  Not doing anything with mysql.

---

### Post by Levander on 2005-04-16
Just found out that you can pass arguments to phpinfo().  phpinfo(INFO_CONFIGURATION) reports that sendmail_from is [email]levander@mindspring.com[/email] and that sendmail_path is /usr/sbin/sendmail.

Still trying...

---

### Post by Levander on 2005-04-16
Okay, figured it out.  sendmail_path has to be "/usr/sbin/sendmail -t -i".  Not "/usr/sbin/sendmail".

No idea how the default php.ini settings worked for you.  On my system, nothing shows up in /var/log/mail.info if I don't explicitly set sendmail_path, and I'm pretty sure that variable is not set by default.

But, thanks for posting.

---

### Post by heimo on 2005-04-17
Ok, here's my observations. When I tried your settings (sendmail_path=/usr/sbin/sendmail) I was able to send mail to local addresses with mail-function, but external domain mail addresses failed just the way you reported.
(I have postfix configured to accept mail on the same server that my websites are.)

I put in the */usr/sbin/senmail -t -i *and everything is ok. Then I commented out the sendmail_path from config (this was the initial setting) and checked phpinfo(). Guess what? The default is [i]/usr/sbin/sendmail -t -i

[/i]Here we see nice example of the situtation where configuration file filled with key-values and set to default values (even if by default commented out) would help to configure the server correctly.

But hey! Nice work solving it! :)

---

### Post by Levander on 2005-04-21
Yeah, did cross my mind that it was kind of stupid to have changed that file to begin with.  When, from what I read, the compiled in defaults would have worked, and you shouldn't have to change the php.ini at all to set sendmail_path.

My excuse is that when the php mail() function did not work, the first thing I did was to check the php docs, which mostly said to check your php.ini.  After getting nowhere with that, I started looking into my mail configuration.  Turned out postfix was not setup to deliver mail from my machine.  So, after I got postfix configured, I had already modified php.ini to something that didn't work.

Took quite a bit of fumbling around to figure out it wasn't php or postfix, but the way the two were inter-operating, and then reading the comment in the php.ini file that "-t -i" was the defaults.  And, figuring out that I had overridden those defaults by explictly setting the sendmail path in the php.ini....  Finally just added these options back in, by explicitly setting them in php.ini.

Yeah, It also would have been good if the package maintanier had explicitly listed what the value of that setting.

What I've been meaning to do though is figure out enough to set up cvs to version all the sysadmin changes I make.  That way, I never forget that I've already modified a configuration file, and I know why I made that change.  If, after setting up postfix, I went back to php.ini and could easily see that I had already made a change to that file, and, be able to easily revert the changeI think it would have saved me quite a bit of time.

I usually only change a line or two of a system service's configuration file, but it often takes a few hours to figure out how to make that change.  So, the cvs repository would be very small, and only need to be available for one user.  Since, it's so small, I'm wondering if cvs wouldn't be better than subversion.  Since subversion is more "fully-featured", and I probably don't need any of the additional features.  But, I don't really know much about either, that's a project for another time...

Plus, having a cvs (or subversion) repository would make it very easy to come up with a back up strategy for all my sysadmin changes. In case something happens to my system.

---


---
title: "mutt Error sending message, child exited 77"
date: 2010-03-12
forum: Desktop Environments
---

### Post by bluethundr on 2010-03-12
hey guys,

 I seem to have my mutt accessing my gmail account using on the command line with mutt. however when I send mail as my user account I get this error:


```

echo 'test' | mutt -s testmessage myuser@mymail.com

Error sending message, child exited 77 


```

If I issue the same exact command as my root user I get unixy thumbs up! (that is no response), yet no actual mail is sent. I can see my entire gmail inbox under mutt, so this is a partial win, but I need to send mails this way also.

I am attempting to use this guide..

[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

thanks in advance!

---

### Post by andrew.46 on 2010-03-13
Hi bluethundr,

Great guide that one :). BTW you may find the Ubuntu version of this guide a bit more straightforward:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

Sending mail is done with msmtp so could you post the log file from  ~/.msmtp.log? If there is a certificate error try including the syntax I have suggested for ca-certificates.crt.

Andrew

---

### Post by bluethundr on 2010-03-13
Hello again!

 Here are the contents of my .msmtp.log file. The players in this little dramatis personae are this: [email]my@gmail.com[/email] is my external gmail account, bluethundr is my local unix account name and [email]my@externalmail.com[/email] is the address I am attempting to send to. 

```

Mar 13 11:29:50 host=smtp.gmail.com tls=on auth=on user='my@gmail.com' from=bluethundr recipients=my@externalmail.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at                   \n535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 22sm1992975qyk.10' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM


Mar 13 11:36:13 host=smtp.gmail.com tls=on auth=on user='my' from=bluethundr recipients=my@externalmail.com smtpstatus=535 smtpmsg='535-5.7.1 Username and Password not accepted. Learn more at                   \n535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 7sm6104073qwb.40' errormsg='authentication failed (method PLAIN)' exitcode=EX_NOPERM

```

This is odd..it's telling me that it's not accepting my password. Yet my entire pop mailbox downloaded. So obviously something in the send mechanism is busted. 

What I did on the second run you see in the log file was change the user information in .msmtprc to just 'my' (that is my gmail account user name, and not including the full address) on that last run. In the first run that you see in the log I had it as 'my@gmail.com'. This change did not affect anything. I am still getting the same error.

```
Error sending message, child exited 77 (Insufficient permission.).
Segmentation fault
```


This is my .mstmprc config file, with the true values changed slightly according to the "dramatis personae" indicated above. 

```

account default
host smtp.gmail.com
port 587
from 'my@gmail.com'
tls on
tls_starttls on
tls_trust_file /home/bluethundr/mail/certs/Thawte_Premium_Server_CA.pem
#tls_trust_file /home/john/mail/certs/Equifax_Secure_CA.pem
auth on
user 'user'
password 'xxxxxxx'
logfile ~/.msmtp.log

```

I have also tried entering the password without single quotes and with single quotes, I have a bang somewhere in my password, and I tried escaping it and not escaping it both ways. Am I at least barking up the right tree?

---

### Post by andrew.46 on 2010-03-13
Hi bluethundr,

he easiest way to eliminate any possible problems with the certificates is to run the following:

```

sudo apt-get install openssl ca-certificates

```

and then alter the following line in ~/.msmtprc from:

```

tls_trust_file /home/bluethundr/mail/certs/Thawte_Premium_Server_CA.pem

```

to this:

```

tls_trust_file /etc/ssl/certs/ca-certificates.crt

```

Could you check the permissions on your ~/.msmtprc file in the following fashion:

```

andrew@skamandros~$ **[COLOR="Red"]ls -l ~/.msmtprc[/COLOR]**
-rw------- 1 andrew users 950 2009-12-09 10:20 /home/andrew/.msmtprc

```

Hopefully we will be getting close to the solution :).

Andrew

---

### Post by bluethundr on 2010-03-13
Hi Andrew!

 Thanks, I really appreciate the input! And yes, I have a confession to make. I apologize for deceiving you but the system in question is in all actuality centOS 5.4. The reason I didn't shed light on this fact earlier is that I am usually skilled enough to make the translation from one distro to another, however as I still am stumped I will plug away here.

 
 This is how the permissions are set on .msmtprc 

 ```

 -rw------- 1 bluethundr bluethundr 464 Mar 13 18:43 .msmtprc
 
```

 

 openssl is already installed is at this version:

 ```

 OpenSSL 0.9.8e-fips-rhel5 01 Jul 2008
 
```

 I believe on a centOS box the openssl certs location is 
 
 ```

 /etc/pki/tls/certs/
 
```


 I changed the location of certs in .msmtprc from here:
 
 ```

 tls_trust_file /home/bluethundr/mail/certs/Thawte_Premium_Server_CA.pem
 
```

  to here:

  ```

  tls_trust_file  /etc/pki/tls/certs/ca-bundle.crt
  
```

  I am including the particular ca-bundle.crt file I am using with this post.I had to gzip it so that the site would allow me to upload it. 

  This cert file was made by moving to /etc/pki/tls/certs and issuing the command make server.key (if I recall correctly). 


 The error I am receiving has changed ever so slightly. Here it is:

 ```

 [bluethundr@lcent5-2 mail]$ echo 'test' | mutt -s mylocaluser myuser@gmail.com
Error sending message, child exited 77 (Insufficient permission.).
Segmentation fault
 
```


 Again profuse apologies on distro obfuscation. I am posting to ubuntu forums because of the robust, responsive community normally found here.

---

### Post by andrew.46 on 2010-03-13
Hi bluethundr,

> **bluethundr said:**
> Thanks, I really appreciate the input! And yes, I have a confession to make. I apologize for deceiving you but the system in question is in all actuality centOS 5.4.

That is not a problem, I am typing this on Slackware :).


>  The error I am receiving has changed ever so slightly. Here it is:

 ```

 [bluethundr@lcent5-2 mail]$ echo 'test' | mutt -s mylocaluser myuser@gmail.com
Error sending message, child exited 77 (Insufficient permission.).
Segmentation fault
 
```

It sounds a little odd, and in particular the Segmentation Fault should not be happening. I presume you are calling msmtp from your ~/.muttrc:

```
set sendmail="/usr/bin/msmtp"  # Use msmtp rather than sendmail
```

using the appropriate path to msmtp. A further small check would be the version of msmtp that you are using, on my system:

```

andrew@skamandros~$ msmtp --version
msmtp version 1.4.19
**[COLOR="Red"]TLS/SSL library: GnuTLS[/COLOR]**
Authentication library: built-in
Supported authentication methods:
plain cram-md5 external login 
IDN support: enabled
NLS: enabled, LOCALEDIR is /usr/share/locale
Keyring support: none
System configuration file name: /etc/msmtprc
User configuration file name: /home/andrew/.msmtprc

Copyright (C) 2009 Martin Lambers and others.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

```

If all of this is in place I am at a bit of a loss and it might be time to start [the guide]("http://www.andrews-corner.org/mutt.html") from scratch. I can assure you that is does work as I use the same setup every day :).

Andrew

---

### Post by bluethundr on 2010-03-13
hello hello! yes slackware rules! ;)

Well I believe I am using the correct msmtp. Here is the line from .muttrc that calls it:

```
 
# Use msmtp rather than sendmail. Check that 
# the path is correct for your system:
set sendmail="/usr/local/bin/msmtp"

```

 And I am _pretty_ darn sure that's the right one!

 ```

 [bluethundr@lcent5-2 skype-2.1.0.81]$ whereis msmtp
msmtp: /usr/local/bin/msmtp
 
```

 This is the output I get from msmtp --version

 ```

 [bluethundr@lcent5-2 skype-2.1.0.81]$ msmtp --version
msmtp version 1.4.19
TLS/SSL library: OpenSSL
Authentication library: built-in
Supported authentication methods:
plain cram-md5 external login 
IDN support: disabled
NLS: enabled, LOCALEDIR is /usr/local/share/locale
Keyring support: none
System configuration file name: /usr/local/etc/msmtprc
User configuration file name: /home/bluethundr/.msmtprc

Copyright (C) 2009 Martin Lambers and others.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

```

 Well, if we are BOTH stumped at this point, I guess it's back to the drawing board for me! :-({|= heh!

---

### Post by bluethundr on 2010-03-15
Well thanks for the suggestion to go through the tutorial once more! I was able to catch the fact that the -----END CERTIFICATE----- tag in one of the certs I used in reality read -----END CERTIFI ... d'oh! Not sure how that one happened 

At any rate thanks again for the wonderful tutorial and I am now sending and receiving gmail from the command line using mutt!

---

### Post by andrew.46 on 2010-03-15
Hi bluethundr,

Glad to hear it all worked out in the end and I wish you all the best in your continued exploration of mutt. And perhaps one day you will join the Ubuntu community as well :).

Andrew

---


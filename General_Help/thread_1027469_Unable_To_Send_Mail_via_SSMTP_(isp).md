---
title: "Unable To Send Mail via SSMTP (isp)"
date: 2009-01-01
forum: General Help
---

### Post by Frank_F on 2009-01-01
Hello,

Unable to send email in command line using my isp provider



frank@name-desktop:/etc/ssmtp$ ssmtp [email]name@rogers.com[/email]
From: [email]name@rogers.com[/email]
To: [email]name@rogers.com[/email]
Subject: Test Subject
This is the body
ssmtp: 553 From: address not verified; see [http://www.rogershelp.com/verify-email](http://www.rogershelp.com/verify-email)


SSMTP.CONF

frank@frank-desktop:/etc/ssmtp$ cat ssmtp.conf
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=f.falco@rogers.com

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.broadband.rogers.com

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=frank-desktop

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

AuthUser=name
AuthPass=password
#AuthMethod=CRAM-MD5

---

### Post by dcstar on 2009-01-01
> **Frank_F said:**
> Hello,

Unable to send email in command line using my isp provider



frank@name-desktop:/etc/ssmtp$ ssmtp [email]name@rogers.com[/email]
From: [email]name@rogers.com[/email]
To: [email]name@rogers.com[/email]
Subject: Test Subject
This is the body
ssmtp: 553 From: address not verified; see [http://www.rogershelp.com/verify-email](http://www.rogershelp.com/verify-email)


SSMTP.CONF

frank@frank-desktop:/etc/ssmtp$ cat ssmtp.conf
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=f.falco@rogers.com

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.broadband.rogers.com

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=frank-desktop

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

[B]AuthUser=name
AuthPass=password[/B]
#AuthMethod=CRAM-MD5

What do you think you are supposed to have there for a system that uses secure transport?

---

### Post by CharlieNixon on 2009-01-27
I am having a similar problem with some differences. I would like to send email from the command line (eventually from a script) through a local MS Exchange server to the Internet. First, I installed sSMTP via Synaptic. Then I configured the /etc/ssmtp/ssmtp.conf file (as below). I am not connecting to an ISP mail server. I am connecting to a local MS Exchange server (which has been configured to allow relaying for my LAN IP). 

/etc/ssmtp/ssmtp.conf 

#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=user@mydomain.com

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=10.1.1.2  #IP of my MS Exchange server

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=mydomain.com

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

AuthUser=user
AuthPass=password
AuthMethod=CRAM-MD5


Then I input:

jnixon@ets-tirian:~$ ssmtp [email]user@gmail.com[/email]
From:user@mydomain.com
To:user@gmail.com
Subject:test
This is the body.
.


And received:

ssmtp: Server rejected AUTH CRAM-MD5 (504 5.7.4 Unrecognized authentication type.)


Since the authentication was rejected I commented out the last line of my conf file and tried it again. This time I received nothing, no error, eventually the session timed out.

Any help is appreciated

---

### Post by CharlieNixon on 2009-01-27
update:

I AM able to send at this point. The strange thing is that sSMTP does not return me to my shell. It just sits there even though the message is sent.

idea?

---

### Post by CharlieNixon on 2009-02-04
I did some reading and found that ssmtp was supposed to be invoked indirectly via an MUA (such as the command **mail**). I also noticed that once in installed ssmtp it created a sym link from the old location of sendmail to the location of ssmtp. Thus when any application attempts to invoke the sendmail binary it actually just follows the link and invokes ssmtp. This means that ssmtp must take similar arguments and parameters as sendmail (which it apparently does). 

Anywho, using the command **mail** now invokes ssmtp correctly and all I had to do was configure **/etc/ssmtp/sstmp.conf**.

Thanks for all the responses!

---


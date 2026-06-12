---
title: "Fail2Ban and Email Formats"
date: 2009-05-10
forum: General Help
---

### Post by xefialtis on 2009-05-10
This isn't (I don't think) a directed question to Fail2Ban, but maybe it is... I think, however, that it is more directed to the proposed email formats that Fail2Ban uses in their config files...

Here is the problem:

I have the Fail2Ban config " sendmail-whois.conf " being used...
In it, it will send me an email in a specified format:

> 
actionban = echo -en "Subject: [Fail2Ban] <name>: banned <ip>
            From: Fail2Ban <<sender>>
            To: <dest>\n
            Hi,\n
            The IP <ip> has just been banned by Fail2Ban after
            <failures> attempts against <name>.\n\n
            Here are more information about <ip>:\n
            `/usr/bin/whois <ip>`\n
            Regards,\n
            Fail2Ban" | /usr/sbin/sendmail -f <sender> <dest>


I don't get the email in the expected format.
I get NOTHING in the subject line (it is blank)
I get the WRONG sender (the from is ROOT when it should be FAIL2BAN)
and the Message Body contains the following lines:

> 
-en Subject: [Fail2Ban] ssh: banned 98.242.240.55
From: Fail2Ban <fail2ban>
To: root@localhost


So, I was wondering...
What is WRONG with the sendmail (email) formatting in the config file that causes me to get bad emails?

A little background:
My server which runs fail2ban is also my email server, web server, router, firewall, etc. Everything is handled on that box. It is running Ubuntu Server 8.10

Thanks for any help!

---


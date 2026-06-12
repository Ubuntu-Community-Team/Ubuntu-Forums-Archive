---
title: "configration file problem"
date: 2008-12-20
forum: General Help
---

### Post by abhilashm86 on 2008-12-20
There is a single configuration file to be altered: $HOME/.msmtprc. It can be created and permissions set as follows:

Code:

$ touch $HOME/.msmtprc
$ touch $HOME/.msmtp.log
$ chmod 0600 $HOME/.msmtprc

Below is the required configuration for a Gmail server:

Code:

account default              
host smtp.gmail.com          
port 587                     
from [email]full.gmail.address@gmail.com[/email]   
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user gmail.username        
password mypassword        
logfile ~/.msmtp.log

where should i create and do the code for gmail server,i want the path where it should be stored,also in home directory,no .msmtprc is existing

---

### Post by Titan8990 on 2008-12-20
Where did you get the server app that uses that config file?

---

### Post by abhilashm86 on 2008-12-20
> **Titan8990 said:**
> Where did you get the server app that uses that config file?

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)
i am doing gmail mail using this thread........

---


---
title: "Need to open a port so that I can send e-mail"
date: 2006-07-07
forum: Desktop Environments
---

### Post by NMUrugbysteve on 2006-07-07
So i've got what seems like a simple problem. I can't send e-mails through my school account when I'm using a e-mail client. I've tried evolution, sylpheed, and seamonkey, none of them work. I know it's a ubuntu issue because when I still had windows i could send mail with seamonkey no problem. I know this is some kind of port issue, but the usual fix to open the port for POP accounts isn't working. Any help would be greatly appreciated.

---

### Post by NMUrugbysteve on 2006-07-15
Bump

---

### Post by cptnapalm on 2006-07-15
what program are you using for sending mail?

---

### Post by jimmygoon on 2006-07-15
Almost all ISP's block the default port for outgoing mail and thus yhou must use the alternative port, make sure that you are using the same config and most importantly port that you are using in Windows, because Ubuntu doesn't have any firewalls built in...

---

### Post by NMUrugbysteve on 2006-07-15
@Cptnapalm
I'm just trying to use evolution with the supplied server information that my university gave me to check my e-mail.

@Jimmygoon
Is there anyway for me to find out what the alternative port is? I can't check the windows settings as I removed windows permanently from this computer.

---

### Post by jimmygoon on 2006-07-15
> **NMUrugbysteve said:**
> @Cptnapalm
I'm just trying to use evolution with the supplied server information that my university gave me to check my e-mail.

@Jimmygoon
Is there anyway for me to find out what the alternative port is? I can't check the windows settings as I removed windows permanently from this computer.

OH! um... It depends on the ISP and I can't remember what (my mom's workplace) used as the alt port... you will probably have to call up your ISP

---

### Post by fragos on 2006-07-15
If you're using SSL like with Gmail POP access, the port could be 465 for SMPT.  Specify port in evolution as smtp.gmail.com:465 -- gmail example.

---

### Post by NMUrugbysteve on 2006-07-16
For the record, this is a dapper issue. I could send and recieve e-mail fine with breezy with the exact same settings as I have now.

The ssl port 465 didn't work. The errors that evolution give me are either "no route to host" or "connection refused".

---

### Post by stanz on 2006-07-16
Some details on your settings would help....
In Both Recieving & Sending Mail, under Security, 
do you have encryption enabled? If So...Try **NONE**.
Did you try different Authentication Types? ALL of them?
And does this all match, your school's pref's? As THEY can block your path.

---

### Post by Dubbayoo on 2006-07-16
Here are the instructions for Gmail.

[http://mail.google.com/support/bin/answer.py?ctx=%67mail&hl=en&answer=12103](http://mail.google.com/support/bin/answer.py?ctx=%67mail&hl=en&answer=12103)


Yes, I know you're not using gmail but the ports are shown.

---


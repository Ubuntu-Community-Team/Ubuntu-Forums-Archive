---
title: "help with mailing"
date: 2009-04-09
forum: General Help
---

### Post by lahp on 2009-04-09
need help with my mailing tried loads i can get mail to send i probly just going bout it wrong way i have mailx sendmail dovcot you name it i probly installed it... can some one just type what i need to type (i dont use gmail. and i dont care who it says its from really i just need outgoing mail working at the momment )

---

### Post by Wayne_V on 2009-04-09
That's a loaded question.   Are you talking about using a mail client (thunderbird, evolution, etc) or from the command line?

For a mail client you need the proper setup from your ISP.

If you want command line email (or your daemons to email you off box), you need to make sure sendmail is setup properly.   There are loads of issues.  Try this command:

$ echo hello | mail -v -s hello <your email address>

---

### Post by lahp on 2009-04-09
im using command line, what would u recomend if anything? and i will try that in a tick

---

### Post by Wayne_V on 2009-04-09
Unless you have your own domain and have your own DNS setup many smtp servers will reject your connection (since your reverse IP lookup isn't going to match who you say you are).

The quickest check?  'vi /etc/mail/sendmail.cf' and look for the line that starts DS.  Set that to be your ISP smtp server (i.e.  DSsmtp.myisp.com).   Restart sendmail (/etc/init.d/sendmail restart) and try the command given earlier:

$ echo hello | mail -v -s hello <your email address>

Depending on if you get errors you may also have to configure masquerading in sendmail.

---

### Post by lahp on 2009-04-09
tried all that dont know wot im looking for thou :/ it just keep saying my sender address dose not exsist (sam@ubuntu)

---

### Post by Wayne_V on 2009-04-10
so you are trying to send mail to yourself at your computer?   What does 'hostname' and 'nslookup <your IP>' say?

---

### Post by lahp on 2009-04-10
it says my network is ubuntu2 :S and i get 4 authritive answers one non on my nslookup

---

### Post by Wayne_V on 2009-04-10
I don't think we have a clear picture of the problem.  If you have your own domain registered and have the capability of adding mx records to dns for your domain you can follow this how-to:

[http://www.wikihow.com/Configure-Sendmail](http://www.wikihow.com/Configure-Sendmail)

If, on the other hand, you just have an Ubuntu workstation and you want  emails sent to root by local daemons to be forwarded to your personal email (gmail, yahoo, etc), that is something quite different.

---

### Post by lahp on 2009-04-10
sorry ok a bit more detail of my situ

i use a linux server server edition 8.04 i belive sinc ei last upgraded... i want to send emails from my server out to the real world... so hotmail accounts ect i own a website that needs to forward emails from it to but that specific is later... just need to get it to send outgoing mail at the momment :P dont care how just to get settingds right

---

### Post by Wayne_V on 2009-04-11
If you have the ability to configure the DNS MX record for your domain to point to your system  then you can set up sendmail to send and receive directly.

I not, you likely need to configure sendmail to use a smart relay host (normally your ISPs SMTP server) and also configure masquerading -- any mail your host sends to the smart relay needs to have the envelope rewritten so that the mail is from [email]your_name@your_isp.com[/email], not root@yourlocalhostname for example.  There are many linux sendmail how-to's on the net -- the one mentioned above is good.  Here's another:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers)

You can then configure /etc/mail/aliases so that any mail to root gets fwd'd to your real email address.   If you have to use a smart relay or can't configure DNS with an MX record pointing to your IP you won't be able to receive mail on your system -- only send.

---


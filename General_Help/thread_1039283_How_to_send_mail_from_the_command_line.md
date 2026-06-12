---
title: "How to send mail from the command line?"
date: 2009-01-14
forum: General Help
---

### Post by mattr12 on 2009-01-14
Hello,

I have Ubuntu 8.04 and I can send mail using Evolution without problems. What I need to do is to be able to send mail with binary attachments from the terminal.

I looked around and found "mutt" but after installing it I only get an error saying "Child exited - error 127". Apparently I have to install sendmail, so I installed sendmail and my machine would take about 15mn to boot and when I tried mutt again it just stayed there doing nothing.

I tried to send mail using mailutils but my mail never arrived to its destination, I couldn't figure out where to put my smtp address, username and password so I guess that's why.

I don't understand what Evolution can send mail but I can't send mail using the command line. I don't need to receive mail, just send.

Can someone give me instructions on what to install? It should be something easy to do I find it hard to believe that I have to edit configuration files that are thousands of lines long just to send mail?

I'm a newbie, so please make it very detailed and yet simple :) As I said I just need to send an email with a binary attachment to a gmail account. My internet provider is cox.net and I have the outgoing smtp address as "smtp.west.cox.net" and my username and password.

Thanks so much!

mattr.

---

### Post by Titan8990 on 2009-01-14
I would like to start by saying that email servers are amongst the hardest to set up, configure, and manage.

Sendmail would be considered the most difficult of them all.


I would recommend Exi4 which will function as a drop-in replacement for sendmail. It is available in Synaptic. You will want to look in to configuring Exim4 to use a "smarthost." 


This guide should get you started: [http://www.lexspoon.org/linux/smtp-relay.html](http://www.lexspoon.org/linux/smtp-relay.html)

---

### Post by cdtech on 2009-01-14
You'll need to set up a basic mail server telling your mail transport agent (sendmail) how to send mail via the command line. Have a look at this site:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers)

---

### Post by whoop on 2009-01-14
? Am I missing something? Why is everybody talking about servers? Doesn't he just need a CLI email client?
Something like pine?

I never used pine so I don't know if you can use it for automated cronjobs, but isn't that what the command line is all about?

---

### Post by Titan8990 on 2009-01-14
Yes, but you need a MTA to send mail via the CLI in the way in which he wants to do it.

Not sure about PINE, have never used it.

---

### Post by cdtech on 2009-01-14
Pine is a terminal based mail client not a transport agent in itself.

---

### Post by Titan8990 on 2009-01-14
I was aware that PINE was a MUA but the user was asking if automated mailing via the CLI can occur with PINE without the need for a MTA.

---

### Post by albinootje on 2009-01-14
> **mattr12 said:**
> 
I looked around and found "mutt" but after installing it I only get an error saying "Child exited - error 127". 


Mutt is great! :)    [http://www.mutt.org/](http://www.mutt.org/)

See here for a solution :
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

section -> "Sending the Mail"

```

I have formerly been an advocate for the simple MTA ssmtp, which some would call a Mail Sending Agent (MSA). However I believe that development of ssmtp has ceased and I have moved with some regret on to msmtp. A single configuration file is required for msmtp: $HOME/.msmtprc and the following section gives the required details to access Gmail and reference the required certificate:

account default              
host smtp.gmail.com          
port 587                     
from john.example@gmail.com     
tls on                       
tls_starttls on              
tls_trust_file /home/john/mail/certs/Thawte_Premium_Server_CA.pem
auth on                     
user john.example        
password rover          
logfile ~/.msmtp.log

I need not mention again, Gentle Reader, that there should be some fairly obvious changes here to substitute your own username, password and email address? And then the final touch, since the username and password are openly in this file, you should make the file readable only by the file owner:

$ chmod 600 ~/.msmtprc

msmtp is a great program that has many features that quite frankly I am still exploring, feel free to point out anything that I have missed, there is an email link at the base of this page for that purpose.

```

Here's another howto :
[http://ubuntu-tutorials.com/2007/07/08/configuring-mutt-to-use-an-alternate-mta-esmtp/](http://ubuntu-tutorials.com/2007/07/08/configuring-mutt-to-use-an-alternate-mta-esmtp/)

---

### Post by mattr12 on 2009-01-14
Hi,

thanks for all the responses.

First, yes I don't understand why I need a server to just send mail. Why is Evolution capable of sending mail without me having to install sendmail/procmail or whatever those products do?

If I look at the example albinootje gives me, I see this sentence:

"I have formerly been an advocate for the simple MTA ssmtp, which some would call a Mail Sending Agent (MSA). However I believe that development of ssmtp has ceased and I have moved with some regret on to msmtp. A single configuration file is required for msmtp: $HOME/.msmtprc and the following section gives the required details to access Gmail and reference the required certificate:"

I have no idea of what that means, I don't have .msmtprc on my home directory.

Titan8990 I downloaded "mailutils" and that added exim4. I tried to configure it but when it talked about "smarthost" i was lost. I don't have another computer that will act as a mail agent? Or am I not understanding what a smart host is?

What is Evolution using to send mail? Can't I use whatever it uses?

Thanks a lot!

mattr.

---

### Post by Titan8990 on 2009-01-14
a SmartHost is an SMTP server that will relay mail for you. Typically, this will be your ISP's SMTP server.


Like I said before, mail servers are not good for a Linux beginner.


> I have no idea of what that means, I don't have .msmtprc on my home directory.


This is because you don't have the application that uses that config file, or you are expected to make your own.


You should read this article to learn a bit more about how mail gets across the internet: [http://en.wikipedia.org/wiki/Mail_transfer_agent](http://en.wikipedia.org/wiki/Mail_transfer_agent)

Evolution is MUA that sends the mail to a MTA to be relayed.

---

### Post by albinootje on 2009-01-14
> **mattr12 said:**
> 
I have no idea of what that means, I don't have .msmtprc on my home directory.

You would need the msmtp package first, you can install it with :
```

sudo apt-get install msmtp

```
> 
What is Evolution using to send mail? Can't I use whatever it uses?

Evolution has build in software which can talk directly to a smtp "smart host" or "relay host", which would be the smtp server of your ISP, which you already mentioned.
I'm not sure that mutt can handle that, just the same, without a "helper" application, like msmtp, or postfix, or exim4 etc.

---

### Post by SoCalChris on 2009-01-14
If you just want to send an email from the command line, using an existing mail server (For example, your ISP's server), install the sendEmail package.

[http://www.digipedia.pl/man/sendEmail.1.html](http://www.digipedia.pl/man/sendEmail.1.html)

To install:
```
sudo apt-get install sendEmail
```

To use:
```
sendEmail -t to@emailaddress -f from@emailaddress -u Email subject -m Email body -a ~/path/to/attachment -s smtp.west.cox.net -xu yourusername -xp yourpassword
```

---

### Post by andrew.46 on 2009-01-14
Hi albinootje,

> **albinootje said:**
> 
See here for a solution :
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)


I believe that the owner of the guide has published an Ubuntu-specific version on these very forums:

[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

The Ubuntu version in particular makes the whole SSL certs thing a little easier :-).

Andrew

---

### Post by mattr12 on 2009-01-14
> **SoCalChris said:**
> If you just want to send an email from the command line, using an existing mail server (For example, your ISP's server), install the sendEmail package.

[http://www.digipedia.pl/man/sendEmail.1.html](http://www.digipedia.pl/man/sendEmail.1.html)

To install:
```
sudo apt-get install sendEmail
```

To use:
```
sendEmail -t to@emailaddress -f from@emailaddress -u Email subject -m Email body -a ~/path/to/attachment -s smtp.west.cox.net -xu yourusername -xp yourpassword
```

Ha that looks promising, i will try that tomorrow and let you know :)

Thanks!

---

### Post by mattr12 on 2009-01-14
> **Titan8990 said:**
> a SmartHost is an SMTP server that will relay mail for you. Typically, this will be your ISP's SMTP server.


Like I said before, mail servers are not good for a Linux beginner.





This is because you don't have the application that uses that config file, or you are expected to make your own.


You should read this article to learn a bit more about how mail gets across the internet: [http://en.wikipedia.org/wiki/Mail_transfer_agent](http://en.wikipedia.org/wiki/Mail_transfer_agent)

Evolution is MUA that sends the mail to a MTA to be relayed.

Thanks Titan. My Linux knowledge is basic, I admit, and I have a hard time understanding why it is so complicated to send an email from a command line it is so complex to configure it's unbelievable !!!

I'm glad you explained what a SmartHost is, I didn't know it was the ISP, so I will try that too.

Thanks much :)

Mattr.

---

### Post by mattr12 on 2009-01-14
> **andrew.46 said:**
> Hi albinootje,



I believe that the owner of the guide has published an Ubuntu-specific version on these very forums:

[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

The Ubuntu version in particular makes the whole SSL certs thing a little easier :-).

Andrew

Yeah I saw that but it was trying to do too much. I just wanted to send an email.

Mattr.

---

### Post by mattr12 on 2009-01-14
> **albinootje said:**
> You would need the msmtp package first, you can install it with :
```

sudo apt-get install msmtp

```

Evolution has build in software which can talk directly to a smtp "smart host" or "relay host", which would be the smtp server of your ISP, which you already mentioned.
I'm not sure that mutt can handle that, just the same, without a "helper" application, like msmtp, or postfix, or exim4 etc.

Thanks. I heard bad stories about "relay hosts" that block email so I thought this was a bad idea to use a relay host. I didn't think that my ISP was a relay host and that it would be a good thing. That's why when mutt configuration asked me about SmartHost/Relay Host I said no.

Mattr.

---

### Post by dcstar on 2009-01-15
> **mattr12 said:**
> Hello,

I have Ubuntu 8.04 and I can send mail using Evolution without problems. What I need to do is to be able to send mail with binary attachments from the terminal.
.......
Can someone give me instructions on what to install? It should be something easy to do I find it hard to believe that I have to edit configuration files that are thousands of lines long just to send mail?
......

Install the **mailx** and **postfix** packages. The postfix configuration is reasonably simple (there are numerous HOWTOs you can search out, just set it to use your ISP's SMTP server - but you don't have to).

---


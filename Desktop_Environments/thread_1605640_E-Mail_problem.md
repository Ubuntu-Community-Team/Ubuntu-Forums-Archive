---
title: "E-Mail problem"
date: 2010-10-25
forum: Desktop Environments
---

### Post by Adillo303 on 2010-10-25
Hi everyone, this is my first post. If I am in the wrong forum, please move me and I will try to behave better next time.

I am reasonably new to Ubuntu, however, I have 48 years in the mainframe / PC Industry and have been working PC tech since 1980. Hopefully, I am trainable. 

I recently loaded Ubuntu on one of my machines and really like it I had to do a bit of this and that to get various things working, I am taking some time each day to learn more Linux commands, They are not that far off DOS. Hope that does not offend anyone.

Anyway. My obstacle today is my e-Mail. I use Thunderbird on windows and found that I can transfer it to Ubuntu and keep all my mail, etc. I Installed Thunderbird 

sudo apt-get update
sudo apttitude install mozilla-Thunderbird

I am running V10.10

I got Thunderbird V3.0. Receive is OK. I cannot send. I have checked all the server settings and matched them against my windows settings. 

I noticed that V 3.1 is available and I downloaded it. I just cannot figure out how to install it.

Any suggestions would be appreciated.

Thank You

Andy

---

### Post by deezer on 2010-10-25
What type of e-mail server are you using?  Double check all settings, especially security settings.  Also, can you even ping your e-mail server from your machine?  If SMTP, can you directly telnet/ssh to the port and interact with it from your box?

Best to stick with 3.0 (regular Ubuntu package) as your problem is likely a connection issue.  You might also try the pre-installed e-mail client (evolution) with your settings to see if you have any success there.

---

### Post by Adillo303 on 2010-10-25
My server is an SMTP server. The system, at the moment, is a dual boot with Windows. I am using the settings copied from the windows side. The windows side sends and receives just find.

I (hopefully) set up pop before SMTP. I can telnet into the server. I will double check everything tonight.

Once I get mail, and a couple things set up, I will whack windows and reformat the machine for Ubuntu only.

---


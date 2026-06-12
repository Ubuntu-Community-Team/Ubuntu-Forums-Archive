---
title: "Hotmail sending mail hotsmtp"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Osamabingandhi on 2006-06-02
I have tried to set up evolution so i can send email through my hotmail account. It works great to recieve mail.

What i understand is that i have to setup inetd to use smtp, but how do i do this? I have used ubuntu for only a couple of days so i am not good at it...

Anyone know how to fix this? I have searched and read through the forum and cannot find anything.

---

### Post by Osamabingandhi on 2006-06-05
Don't seem to get any replies. Anyone knows a guide how to set up evolution so i can send emails? I have tried gotmail but don't understand how to configure it.

Got another question too, When evolution receive mail from hotmail it automaticly deletes the mail in my hotmail inbox. It is really anoying when i want to keep my hotmail inbox full.

Keeping my fingers crossed and hoping for help:)

---

### Post by Lunar_Lamp on 2006-06-06
You set up evolution to use hotmail?  How did you do that may I ask?

Also - depending what kind of access you have, it could be like this for a POP account:

edit>preferences> select account >edit>receiving options>leave message on server

Hope that helps :-)

---

### Post by Osamabingandhi on 2006-06-06
ahhh found it....i crossed the leave on server option in evolution.

i just installed hotway(simulates a pop-email) program from synaptics and then i just filled in my email and the pop adress was 127.0.0.1

Thanks for the help!!!:)

---

### Post by Osamabingandhi on 2006-06-06
But still i don't know how to set up evolution to send hotmails....anyone???

---

### Post by Lunar_Lamp on 2006-06-06
As a work around you may be able to use the gmail smtp server.

Steps:

1 - sign up for a gmail account (if you need an invite just pm me and give me your hotmail addy and I;ll send you one).
2 - log in and go to settings>accounts>add another email address.
3 - follow the instructions and reply to the authentication email
4 - you should now be able to send emails from your hotmail address using your gmail account
5 - i think you may have to enable pop access in gmail - but i dont see why you would need to (but i have done)
6 - setup your smtp details as given in the gmail instructions

Note - if you don't add your hotmail account ot the gmail account all emails you send will register as being from your gmail account.


I'm having problems setting up hotwayd - did yo need to do anything about xinetd format etc?

---

### Post by Lunar_Lamp on 2006-06-06
I was able to find a bit more info using googles cached pages as the hotwayd site is currently down.  Try these forums: [http://sourceforge.net/forum/forum.php?forum_id=80217](http://sourceforge.net/forum/forum.php?forum_id=80217)

They are not down :-)

---

### Post by Osamabingandhi on 2006-06-08
Thanks Lunarlamp, i will try this out and see if it works. But i think i still need your help to get this gmail account working. I will send you a pm.

Cheers

---

### Post by unisol on 2006-08-18
i was advised todo this
sudo apt-get update
Now, install the inet daemon


Code:
sudo apt-get install inetutils-inetd
This takes care of all of our dependencies. Now on to the good stuff...


Code:
sudo apt-get install hotway hotsmtp
This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP. By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.


Code:
sudo gedit /etc/inetd.conf
Look for a line like this:


Code:
pop3 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd
By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:


Code:
pop3 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd -r
And we also need to add a line to get hotsmtpd working, just paste this at the bottom:


Code:
2500 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotsmtpd
This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server:


Code:
sudo /etc/init.d/inetutils-inetd restart
If everything is working properly, you'll see this pop up on your screen:


Code:
* Restarting internet superserver inetd [ ok ]
Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard, you can use that if you like. Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left. However you choose to do it, here's your information:

Email Address: [email]xxx@hotmail.com[/email] (fill in your normal e-mail address that you use to login to hotmail)

Receive Server type: POP
Server: 127.0.0.1
Username: [email]xxx@hotmail.com[/email] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: 127.0.0.1:2500
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [email]xxx@hotmail.com[/email] (same as above)
(Optional Remember password checkbox)
:KS 
-------------------------------

---

### Post by oldgoat on 2006-08-22
unisol - this is a great how to!  However, when I hit send/recieve I get 'Host look up failed: Server: Name or service not known'.  When I go Edit>Preferences>thehotmailaccountIcreated>Edit> and wind up at the account editor, the server has changed from what I enter, 127.0.0.1 to 127.  I read this about hand editing config files for evolution ;

After you have shutdown Evolution, run "killev" to remove the daemon
processes which remain after the shell has quit (specifically
bonobo-conf which manages the configuration files).

Is it possible that the 'ev' daemon is not allowing the server to be saved as 127.0.0.1 for some reason and if so which evolution file should be edited?

---

### Post by oldgoat on 2006-08-22
unisol, anyone interested in recieving hotmail in evolution - this is a beautiful how to!!  I was pasting 'Server: 127.0.0.1' into the Server: textbox.  Sorry for the bad post.

---

### Post by unisol on 2006-08-23
its not my own doing some showed me how to doit and i thought i would share with all
+

---

### Post by unisol on 2006-08-24
what did you do different that made it work please post so we can help others

---

### Post by shunthemask on 2006-08-28
Thanks! This is beautiful, got my hotmail up and running in less than 5 minutes.

---

### Post by dominicg on 2006-12-12
I followed the instructions from the original post and can happily read my hotmail inbox, but I still cannot sent mail using hotsmtp.  I get a "Welcome response error.  Operation in progress" but nothing gets sent.  Any suggestions anyone.

---

### Post by noelene46 on 2007-01-12
I tried what you said for Hotmail. Did not work. We are using Ubuntu on a client  on LAN with the host on WinXP. It cannot find server 127.0.0.1. What is the server to use when on a LAN? Do I use the host Number 192.168.0.1? Getting very frustrated trying to get Hotmail to work with Evolution!

---

### Post by al881 on 2007-01-14
Just to send an update.
After adding all of the material I rebooted.
Then in my Evolution setup I had an exchange account "checked" and the hotmail retrieve would not work. Uncheck the exchange account and it will work.

al

---


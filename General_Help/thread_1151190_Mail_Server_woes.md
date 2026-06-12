---
title: "Mail Server woes"
date: 2009-05-06
forum: General Help
---

### Post by renegadeandy on 2009-05-06
Hi Guys.

I have my website hosted privately using zoneedit and their services. Basically when you go to the domain : [www.upsetpc.com](www.upsetpc.com) its nameservers point to zoneedits servers which automatically forward them onto my server at home where the page is loaded.

What I want now is to be able to have a mail server running on this same server so I can have my address : [email]support@upsetpc.com[/email] running from this box - but I dont understand how to do this. I run an ubuntu box with no x and have tried setting up dovecot and some other stuff but nothings worked and I dont really understand what I am doing.

Can anybody please guide me!

---

### Post by dacorr on 2009-05-06
So you have DDNS set up for the domain upsetpc.com that redirects traffic to your home connection and your webserver. I believe you will need an MX record to point mail to the same location, using [email]email@upsetpc.com[/email] if you had to port forward 80 you will need to do the same to the mail server.

it would need to be somthing that zoneedit provide. they maybe a third party email available that can be forwarded there.

Dac

---

### Post by renegadeandy on 2009-05-06
Well yeah I need an MX record which zoneedit provides, but how do i setup the mail server part on the actual ubuntu box?

---

### Post by rhcm123 on 2009-05-06
read this guide: [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

it's what i used to setup my server. use postfix and courier, dovecot is a pain. support may have to be a system account, just keep it secure by having it's shell point at /bin/false and it's home directory at /nothing. Grab the program mail (sudo apt-get install mail; it runs from the commandline command 'mail', which will tell you the write package) if you want to send mail from the command line. Post here if you have problems, but the guide is pretty straightforward.

EDIT: If you have already grabbed postfix and other such mail programs, delete them with this command: sudo apt-get --purge remove <package names>

---

### Post by renegadeandy on 2009-05-06
Well thats the guide i followed and failed with.

How long did it take you - id be willing to give you ssh access to help me out if you are interested in helping directly and it doesnt take long?!

Thanks mate

Andy

---

### Post by rhcm123 on 2009-05-06
> **renegadeandy said:**
> Well thats the guide i followed and failed with.

How long did it take you - id be willing to give you ssh access to help me out if you are interested in helping directly and it doesnt take long?!

Thanks mate

Andy

giving me ssh access is a bad idea. Don't trust anybody on the internet. It took about an hour.

Here, give me about 10 minutes and ill give you some commands to copy-paste into your terminal, then you should be good to go.

---

### Post by renegadeandy on 2009-05-06
I trust a valued member of the ubuntu community though and it doesnt contain anything which cannot be replaced.

Regardless your idea of giving me the commands is superb and I am very thankful!

I await your reply with baited breath - on the MX record side of things im supposing this makes sense:

MailServer = mail.upsetpc.com handles mail RANK 1st for domain upsetpc.com - all editted via the zoneedit site.

In preparation should i remove my previous attempts?

Thanks

Andy

---

### Post by rhcm123 on 2009-05-06
Ok, here goes. This all can take a while...

Housekeeping:
```
sudo apt-get --purge remove postfix exim4 sendmail dovecot-imapd dovecot-pop3d courier-imap courier-imap-ssl courier-pop courier-pop-ssl
```

Install Postfix:
```
sudo apt-get install postfix
```

Configure it:
```
sudo dpkg-reconfigure postfix

use the following options for the questions it asks (in order):
-Internet Site
-mail.upsetpc.com
-root
-mail.upsetpc.com, upsetpc.com, localhost.upsetpc.com, localhost
-No
-127.0.0.1/8
-0
-+
-all

```

Tell it to use maildir:
```
sudo postconf -e 'home_mailbox = Maildir/' && sudo postconf -e 'mailbox_command ='
```

Tell it to use saslauthd (important, just cut and paste all this in):
```
sudo postconf -e 'smtpd_sasl_local_domain =' &&
sudo postconf -e 'smtpd_sasl_auth_enable = yes' &&
sudo postconf -e 'smtpd_sasl_security_options = noanonymous' &&
sudo postconf -e 'broken_sasl_auth_clients = yes' &&
sudo postconf -e 'smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination' &&
sudo postconf -e 'inet_interfaces = all'
``` 

Make that permanent:
```
sudo echo pwcheck_method: saslauthd >> /etc/postfix/sasl/smtpd.conf && sudo echo mech_list: plain login >> /etc/postfix/sasl/smtpd.conf
```

Courier pop-ssl and imap-ssl will complain unless you have a secuirty cert. If you do, (for https) then don't do this. This is gonna ask a bunch of questions, and your name should be mail.upsetpc.com
```
sudo cd /root && 
sudo touch smtpd.key &&
sudo chmod 600 smtpd.key &&
sudo openssl genrsa 1024 > smtpd.key &&
sudo openssl req -new -key smtpd.key -x509 -days 3650 -out smtpd.crt &&
sudo openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out &&
sudo cacert.pem -days 3650 &&
sudo mv smtpd.key /etc/ssl/private/ &&
sudo mv smtpd.crt /etc/ssl/certs/ &&
sudo mv cakey.pem /etc/ssl/private/ &&
sudo mv cacert.pem /etc/ssl/certs/ &&
sudo echo Now we Configure postfix... &&
sudo postconf -e 'smtp_tls_security_level = may' &&
sudo postconf -e 'smtpd_tls_security_level = may' &&
sudo postconf -e 'smtpd_tls_auth_only = no' &&
sudo postconf -e 'smtp_tls_note_starttls_offer = yes' &&
sudo postconf -e 'smtpd_tls_key_file = /etc/ssl/private/smtpd.key' &&
sudo postconf -e 'smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt' &&
sudo postconf -e 'smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem' &&
sudo postconf -e 'smtpd_tls_loglevel = 1' &&
sudo postconf -e 'smtpd_tls_received_header = yes' &&
sudo postconf -e 'smtpd_tls_session_cache_timeout = 3600s' &&
sudo postconf -e 'tls_random_source = dev:/dev/urandom' &&
sudo postconf -e 'myhostname = mail.upsetpc.com'
```

Finally, restart postfix to make all this appear:
```
sudo /etc/init.d/postfix restart
```
:shock:... that was a lot of code... :D

**Now for courier!**
Install it:
```
sudo apt-get install courier-imap courier-imap-ssl courier-pop courier-pop-ssl
```

Make the mailboxes:
```

sudo maildirmake /etc/skel/Maildir &&
sudo maildirmake /etc/skel/Maildir/.Drafts &&
sudo maildirmake /etc/skel/Maildir/.Sent &&
sudo maildirmake /etc/skel/Maildir/.Trash &&
sudo maildirmake /etc/skel/Maildir/.Templates
```

This will require a little work. Users added after this will get this done automatically. Add any other user already on the system a mailbox:
```
sudo cp -r /etc/skel/Maildir /home/YOUR USERNAME/ &&
sudo chown -R YOUR USERNAME:YOUR GROUP /home/YOUR USERNAME/Maildir &&
sudo chmod -R 700 /home/YOUR USERNAME/Maildir
```

restart everything:
```

sudo /etc/init.d/courier-imap restart &&
sudo /etc/init.d/courier-imap-ssl restart &&
sudo /etc/init.d/courier-pop restart &&
sudo /etc/init.d/courier-pop-ssl restart
```

add the user you want, called support:
```
sudo useradd -g users -s /bin/bash -p -d/home/support -m support
```

To make support login-ready (this is nessecary):
```
sudo passwd support
```

---

### Post by rhcm123 on 2009-05-06
> **renegadeandy said:**
> I trust a valued member of the ubuntu community though and it doesnt contain anything which cannot be replaced.

Regardless your idea of giving me the commands is superb and I am very thankful!

I await your reply with baited breath - on the MX record side of things im supposing this makes sense:

MailServer = mail.upsetpc.com handles mail RANK 1st for domain upsetpc.com - all editted via the zoneedit site.

In preparation should i remove my previous attempts?

Thanks

Andy

wow, I'm a good guesser :D.... and yes, you should remove your previous attempts, but i did that for you in the guide

---

### Post by renegadeandy on 2009-05-06
wow great guide cheers

stuck on one point tho:

Make that permanent:
Code:
sudo echo pwcheck_method: saslauthd >> /etc/postfix/sasl/smtpd.conf && sudo echo mech_list: plain login >> /etc/postfix/sasl/smtpd.conf

that returns to me permissions denied every time - how the heck do i run that command!

---

### Post by rhcm123 on 2009-05-06
> **renegadeandy said:**
> wow great guide cheers

stuck on one point tho:

Make that permanent:
Code:
sudo echo >> /etc/postfix/sasl/smtpd.conf && sudo echo mech_list: plain login >> /etc/postfix/sasl/smtpd.conf

that returns to me permissions denied every time - how the heck do i run that command!

Strange, it works fine on my system...

run this:
```
sudo chmod 444 /etc/postfix/sasl/smtpd.conf
```
and try again.

EDIT:
If not (the file probably dosen't exist yet), just open up a text editor (i prefer nano), and put this in:
```

pwcheck_method: saslauthd
mech_list: plain login

```
and that will get it working. Make sure to keep pwcheck and mech_list on different lines (i.e. hit enter).

---

### Post by renegadeandy on 2009-05-07
ok on checking that file the contents were already what you suggested.

Next problem - the large list of commands to follow after that last problem throws more permissions errors:

I get to this line :

**sudo openssl genrsa 1024 > smtpd.key**

by doing the previous commands line by line i.e touch smtpd.key and chmodding it but doing that line gives permission denied again.

I really dont know what to do about this!

---

### Post by renegadeandy on 2009-05-07
Ok progress - logged in as root 'su -u' and was able to complete i think the big box before courier - the console output looks as follows:

```

......++++++
e is 65537 (0x10001)
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:UK
State or Province Name (full name) [Some-State]:Midlothian
Locality Name (eg, city) []:Edinburgh
Organization Name (eg, company) [Internet Widgits Pty Ltd]:mail.upsetpc.com
Organizational Unit Name (eg, section) []:upsetpc
Common Name (eg, YOUR name) []:mail.upsetpc.com
Email Address []:armcompservices@yahoo.co.uk
req [options] <infile >outfile
where options  are
 -inform arg    input format - DER or PEM
 -outform arg   output format - DER or PEM
 -in arg        input file
 -out arg       output file
 -text          text form of request
 -pubkey        output public key
 -noout         do not output REQ
 -verify        verify signature on REQ
 -modulus       RSA modulus
 -nodes         don't encrypt the output key
 -engine e      use engine e, possibly a hardware device
 -subject       output the request's subject
 -passin        private key password source
 -key file      use the private key contained in file
 -keyform arg   key file format
 -keyout arg    file to send the key to
 -rand file:file:...
                load the file (or the files in the directory) into
                the random number generator
 -newkey rsa:bits generate a new RSA key of 'bits' in size
 -newkey dsa:file generate a new DSA key, parameters taken from CA in 'file'
 -newkey ec:file generate a new EC key, parameters taken from CA in 'file'
 -[digest]      Digest to sign with (md5, sha1, md2, mdc2, md4)
 -config file   request template file.
 -subj arg      set or modify request subject
 -multivalue-rdn enable support for multivalued RDNs
 -new           new request.
 -batch         do not ask anything during request generation
 -x509          output a x509 structure instead of a cert. req.
 -days          number of days a certificate generated by -x509 is valid for.
 -set_serial    serial number to use for a certificate generated by -x509.
 -newhdr        output "NEW" in the header lines
 -asn1-kludge   Output the 'request' in a format that is wrong but some CA's
                have been reported as requiring
 -extensions .. specify certificate extension section (override value in config file)
 -reqexts ..    specify request extension section (override value in config file)
 -utf8          input characters are UTF8 (default ASCII)
 -nameopt arg    - various certificate name options
 -reqopt arg    - various request text options


```

That to me looks like it didnt complete correctly....

---

### Post by renegadeandy on 2009-05-07
Regardless I continued and completed the setup.

Now im guessing my setup for outlook is as follows:

pop3 server: mail.upsetpc.com - authentication port 110
smtp server: mail.upsetpc.com - no authentication port 25
email address: [email]support@upsetpc.com[/email]
username : support???
password : <myPass chosen on last step of the guide>

It connects to the server but when i send a mail to [email]support@upsetpc.com[/email] it doesnt seem to arrive, the mailbox just is empty - but it defo checks it. And as for sending mail it reports a socket error.



Thanks for your continued support.

---

### Post by rhcm123 on 2009-05-07
> **renegadeandy said:**
> Regardless I continued and completed the setup.

Now im guessing my setup for outlook is as follows:

pop3 server: mail.upsetpc.com - authentication port 110
smtp server: mail.upsetpc.com - no authentication port 25
email address: [email]support@upsetpc.com[/email]
username : support???
password : <myPass chosen on last step of the guide>

It connects to the server but when i send a mail to [email]support@upsetpc.com[/email] it doesnt seem to arrive, the mailbox just is empty - but it defo checks it. And as for sending mail it reports a socket error.



Thanks for your continued support.

it seems i may need to take you up on your offer of ssh access - im not on my main computer now, but when i am ill elaborate

---

### Post by renegadeandy on 2009-05-07
Thanks so much - it cannot be far off tbh, because the pop3 now connects just returns no mail - and the smtp doesnt connect :S

When you are ready to connect give me a message or if you have got msn / teamspeak etc I can communicate that way - or email!

---

### Post by rhcm123 on 2009-05-07
> **renegadeandy said:**
> Thanks so much - it cannot be far off tbh, because the pop3 now connects just returns no mail - and the smtp doesnt connect :S

When you are ready to connect give me a message or if you have got msn / teamspeak etc I can communicate that way - or email!

It will take me about an hour, and in the meantime, would you make me an an account with the the username ussr, the shell of bash, the home of ussr, the group of admin (do that with this):

```
useradd -g admin -G users -s/bin/bash -p -d/home/ussr -m ussr
```

When i'm ready, I will private message you with the password I want (i have a function i have to go to in about 20 minutes)

---

### Post by renegadeandy on 2009-05-07
Yeah no problem the users been made and awaiting your password :D

Enjoy the function:popcorn:

---

### Post by rhcm123 on 2009-05-07
Just for the benefit of the forums:
I honestly could not get it working either. I tried to get postfix started, but everytime/everything i tried ended in dysmal failure. I do not know why this is not working. I ran sudo /etc/init.d/postfix start and sudo postfix start, both of which reported no errors, but when i ran sudo postfix check - it said it was down. I don't know how to fix this, but i may be able to help later - i have to go out again (i hate "comitments").

Just to let you know what i did
-setup postfix, and the setup had no errors, at least
-setup courier to run pop and imap
-ran apt-get autoremove to remove dovecot (which remnants were still existent).

---

### Post by renegadeandy on 2009-05-08
ok cool - am waiting for further support!:confused:

---

### Post by rhcm123 on 2009-05-09
> **renegadeandy said:**
> ok cool - am waiting for further support!:confused:

if there is nothing on this pc, then perhaps a reinstall will fix this - apt-get --purge dosen't always fix the problem. After the reinstall, run what i said and it should get right up and running - don't select mail server from the list, it's too poorly setup.

---

### Post by renegadeandy on 2009-05-12
How do you mean dont select mail server from the list :S

SO run the command you just said and redo all steps??!?

---

### Post by rhcm123 on 2009-05-12
> **renegadeandy said:**
> How do you mean dont select mail server from the list :S

SO run the command you just said and redo all steps??!?

Sorry, i use the aleternate CD as my main one - i've gotten so used to it, it think it's the primary :D. On the list, there is an option called mail server, but it's alot easier to configure these manually with the commands' i've suggested.

If you don't want to reinstall, then apt-get --purge your mail server and run my commands.  However, if you can't apt-get --purge ALL mail server related packages (which is likely), then just reinstall - i do this all the time for my main server cause iv'e broken somthing critical.

---

### Post by rhcm123 on 2009-05-23
Well, it's working. Sort of.

Have you done anything to it recently? Cause if you have, whatever you did got it working.

I tried to send myself an email from your systems to my email. I just reccieved it. The email was generated 7 may 19:10 and hit 23 may 17:00.
Did you do anything? Cause i haven't touched it since the 7'th

---

### Post by renegadeandy on 2009-05-28
It works for you?!

SO what should my mail server settings be : 

currently i have in outlook:

mail.upsetpc.com server
address: [email]support@upsetpc.com[/email]
account name: support
password : pass i chose

no ssl settings

With those outlook reports the following:
The connection to the server has failed. Account: 'mail.upsetpc.com', Server: 'mail.upsetpc.com', Protocol: SMTP, Port: 25, Secure(SSL): No, Socket Error: 10061, Error Number: 0x800CCC0E.

The connection to the server has failed. Account: 'mail.upsetpc.com', Server: 'mail.upsetpc.com', Protocol: POP3, Port: 110, Secure(SSL): No, Socket Error: 10061, Error Number: 0x800CCC0E

---

### Post by renegadeandy on 2009-05-28
Oh wow ! Now incoming emails work - outgoing emails give the following message:

The message could not be sent because one of the recipients was rejected by the server. The rejected e-mail address was 'armcompservices@yahoo.co.uk'. Subject 'Re: Testing', Account: 'mail.upsetpc.com', Server: 'mail.upsetpc.com', Protocol: SMTP, Server Response: '554 5.7.1 <armcompservices@yahoo.co.uk>: Relay access denied', Port: 25, Secure(SSL): No, Server Error: 554, Error Number: 0x800CCC79

Something to do with sending emails to external client and removing localhost from some file is what I read or changing something so it authenticates ...?

---

### Post by Blue Sassley on 2009-05-28
> **renegadeandy said:**
> Oh wow ! Now incoming emails work - outgoing emails give the following message:

The message could not be sent because one of the recipients was rejected by the server. The rejected e-mail address was 'armcompservices@yahoo.co.uk'. Subject 'Re: Testing', Account: 'mail.upsetpc.com', Server: 'mail.upsetpc.com', Protocol: SMTP, Server Response: '554 5.7.1 <armcompservices@yahoo.co.uk>: Relay access denied', Port: 25, Secure(SSL): No, Server Error: 554, Error Number: 0x800CCC79

Something to do with sending emails to external client and removing localhost from some file is what I read or changing something so it authenticates ...?

I ran a test on your mail server using MX Toolbox and its reporting that you don't have relying open (which is a very good thing)

[http://www.mxtoolbox.com/diagnostic.aspx?HOST=mail.upsetpc.com](http://www.mxtoolbox.com/diagnostic.aspx?HOST=mail.upsetpc.com)

So the next question I have for you is in Outlook on the accounts settings page there is a button "More Settings..." then a tab "outgoing server" do you have anything checked?

Thanks,
Blue

---

### Post by renegadeandy on 2009-05-28
ok i use outlook express so looks kinda different, but the outgoing server authentication box is unchecked...

---

### Post by Blue Sassley on 2009-05-28
Enable it and try the top button in my screen shot. "Use same settings as my incoming mail server."


Blue

---

### Post by renegadeandy on 2009-05-28
Well i tried and all this does it it brings up the send and receive window, prompts for the username and pass - i enter them but it just continually cycles back and shows me the same enter username and pass window?!

No idea!

---

### Post by Blue Sassley on 2009-05-28
Yeah, when you get the username and password boxes over and over in any Outlook/Outlook Express thats the Microsoft lazy error code saying Bad Username/Password. 

The problem you are having is you have the SMTP server setup as a closed rely (which you need to do otherwise almost all mail servers will reject your mail thinking you are a spammer)

So is what you need to figure out is a way to either send authentication to the SMTP server (which your telling me is giving you the Username password box over and over), or somehow white list yourself as a safe sender. I wish I could help you more but I'm really lazy when it comes to this part of my Linux server administration and I cheat and just use Plesk.

Blue

---

### Post by renegadeandy on 2009-05-28
I dont mind any solution - please tell me yours!

---

### Post by Blue Sassley on 2009-05-28
Well Plesk costs money, and its more for hosting multiple domains.

[http://www.parallels.com/products/plesk/](http://www.parallels.com/products/plesk/)

I'll see if I can look over all the stuff you have currently done and see find I can find anything about the SMTP authentication.

Blue

---

### Post by renegadeandy on 2009-05-28
Eek! Money! haha no that wouldnt be suitable then!

Thanks for having a look to help me though!:popcorn:

---

### Post by Blue Sassley on 2009-05-28
Can you post what is in the 
```
etc/postfix/sasl/smtpd.conf
```

Thanks,
Blue

---

### Post by renegadeandy on 2009-05-28
Here it is!

```

pwcheck_method: saslauthd
mech_list: plain login
pwcheck_method: saslauthd
mech_list: plain login

```

---

### Post by Blue Sassley on 2009-05-28
Lets trim out the bottom two lines so its just:

```
pwcheck_method: saslauthd
mech_list: plain login

```
Then restart PostFix

```
sudo /etc/init.d/postfix restart
```

Blue

---

### Post by renegadeandy on 2009-05-28
ok done - problem still exists...

---

### Post by Blue Sassley on 2009-05-28
With SMTP authentication enabled in Outlook Express?

Blue

---

### Post by rhcm123 on 2009-05-28
Woah, it works now?

I see your problem. I think it is that you are trying to connect via SSL (which is good, it's secured) but, because your certificate is self-generated, outlook express is dropping the connection due to a bad certificate. I had the same problem with evolution. unless you want to pay for a certificate (which costs lotta $$). I just closed ports 993 and 995 (imaps and pop3s, repsectively) via iptables, so that evolution/my blackberry connect via 25(smtp) and 110/143 (pop3/imap), unsecured. 

I don't do any financial banking on my home server, it's just a hobby, so I'm ok with not using SSL. I do have my online access point over https though, if that means anything. If you are ok with unsecured server access (not unPASSWORDED, just unENCRYPTED), then try this. I think outlook defaults to the secured version.

---

### Post by renegadeandy on 2009-05-28
Yeah doesnt work even with the authentication for smtp enabled - its weird cos my outlook seems to be using 25 and 100, and ssl is defo disabled on my outlook....

---

### Post by rhcm123 on 2009-05-28
> **renegadeandy said:**
> Yeah doesnt work even with the authentication for smtp enabled - its weird cos my outlook seems to be using 25 and 100, and ssl is defo disabled on my outlook....

can you change the default ports/your settings to use the proper ones (100 is unassigned at the moment)? Sorry, im not that familiar with outlook.

---

### Post by renegadeandy on 2009-05-29
Sorry was a typo - using 25 for smtp and 110 for pop access

---

### Post by renegadeandy on 2009-05-30
So - any ideas!?

---

### Post by rhcm123 on 2009-05-30
> **renegadeandy said:**
> So - any ideas!?

yes actually - can you nmap your server locally? (e.g. on the server run nmap localhost) nmap probably won't be installed, so apt-get it and then run it, i want to see what ports are open on this machine (maybe somthing's blocking 110 or 25 and it's going for the ssl servers)

---

### Post by renegadeandy on 2009-06-01
Disappointing news im afraid:

21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
110/tcp   open  pop3
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
993/tcp   open  imaps
995/tcp   open  pop3s
3306/tcp  open  mysql
5432/tcp  open  postgres
5800/tcp  open  vnc-http
5900/tcp  open  vnc
10000/tcp open  snet-sensor-mgmt

---

### Post by renegadeandy on 2009-06-02
,.,,,..,

---

### Post by rhcm123 on 2009-07-03
im sorry about not responding for the last month - i have actually been away for a while. But now im back! From what i read and what your nmap output says, your outlook profile is not configured properly. Try these settings (these are standard across all mail-client platforms, but i don't know where they are located in outlook). 

under the "reccieving/downloading" tab (or similar), have these settings:
-Server type: POP3
-Server name/address: mail.upsetpc.com (or whatever yours is called)
-Username: your username
-Security: none
-Authentication: password

Under the "sending" tab, use this:
-Server type: SMTP
-Server name: mail.upsetpc.com
-Authentication Required: Yes, (enter your password + username in a box below)
-Security: none

that should get your system online.

---


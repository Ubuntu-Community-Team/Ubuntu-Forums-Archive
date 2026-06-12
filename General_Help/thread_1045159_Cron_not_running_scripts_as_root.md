---
title: "Cron not running scripts as root"
date: 2009-01-20
forum: General Help
---

### Post by bhaskar_goel on 2009-01-20
I have been trying to run the a script as root recurrently ( every minute) .
I have logged in as root and run crontab -e. I gave the following enty:
* * * * * ls -l
But no mail is being sent to me(root).
The same thing i tried as a normal user, and i received the mail.
Can anyone please help me out.

---

### Post by handband2 on 2009-01-20
> **bhaskar_goel said:**
> I have been trying to run the a script as root recurrently ( every minute) .
I have logged in as root and run crontab -e. I gave the following enty:
* * * * * ls -l
But no mail is being sent to me(root).
The same thing i tried as a normal user, and i received the mail.
Can anyone please help me out.

To setup emails with the following information do the following:
```
sudo apt-get install exim4
```
```
sudo dpkg-reconfigure exim4-config
```
[LIST]
[*]General type of mail configuration -> [COLOR="Red"]internet site;....[/COLOR]    
[*]System mail name -> [COLOR="Red"]servername.com[/COLOR] (.com is important)
[*]IP-addresses to listen on for incomping SMTP connections -> [COLOR="Red"]127.0.0.1[/COLOR]
[*]Other destination for which mail is accepted -> [COLOR="Red"]localhost[/COLOR]
[*]Domains to relay mail for -> [COLOR="Red"]through your internet providers SMTP relay server.[/COLOR]
[*]Machines to relay - [COLOR="Red"]leave blank[/COLOR]
[*]Keep number of DNS-queries minimal -> [COLOR="Red"]No[/COLOR]
[*]Delivery method for local mail -> [COLOR="Red"]mbox format in /var/mail/[/COLOR]
[*]Split configuretion into small files? -> [COLOR="Red"]No[/COLOR]
[/LIST]

Then place the following in your crontab:
```
* * * * * ls -l | cat | mail -s "$(hostname) - List Files" "[COLOR="Red"]youremail@something.com[/COLOR]"
```
***Change what is in red**

---

### Post by hyper_ch on 2009-01-20
and that only works if the recipient mailserver plays nicely and lets you allow to send email from a dynamic ip :)

You could of course send it to your mail account queue by using your "username" which you use to login instead of the email address. And the email address doesn't need to be in quotes :)

---

### Post by dagnabit dang doohickey on 2009-01-20
Check for an alias in /etc/aliases that may be redirecting root's mail.

---

### Post by bhaskar_goel on 2009-01-21
the problem as such is that no action other than removing a file is ie rm -/directory name is getting done as a cron as root ,but the all the actions are getting done if i login as a normal user.i gave the following to script to run as the root crontab:-

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
33 16 * * * bash -x /etc/init.d/test.sh>/etc/init.d/test.txt

any ideas ???

---

### Post by dagnabit dang doohickey on 2009-01-21
Not knowing the contents of test.sh is a big blind spot on my side of the intertubes. That aside, the output of the xtrace is sent to stderr, so the command needs a slight modification: bash -x script.sh **2>** xtrace.log

---


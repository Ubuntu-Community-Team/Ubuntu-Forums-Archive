---
title: "HOWTO: Send and Receive Hotmail, Gmail, Yahoo (trough ypos) - In one single place"
date: 2009-01-04
forum: General Help
---

### Post by Adrian Nania on 2009-01-04
](*,)
I've had to spend a lot of time to gather pieces of information on how to set all my hotmail, gmail, yahoo accounts in Evolution. I hope this HOWTO could spare somebody else's time. Once all your accounts are up and running, don't forget to back-up Evolution's accounts, emails, etc. like this:
Start Evolution -> Backup Settings -> select backup file name/directory -> Save
I know, this is mighty silly and there are no settings at all. Nevertheless, this is how you backup Evolution. On a very personal note, I believe people involved in developing these tools are not quite open to usability. Everything MUST be a single-click automatic install for people to be comfortable switching from Window$$$ to Linux.

Now to the juicy part: follow step by step all these instructions:

# HOWTO: Send and Receive Hotmail, Gmail, Yahoo (trough ypos) - In one single place
# HOWTO: Send and Receive Hotmail through Evolution
# from [http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)
sudo apt-get install -y inetutils-inetd hotway hotsmtp
sudo gedit /etc/inetd.conf
# Look for a line like this:
#^^^^^^^^pop3 stream tcp	nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd
# and replace if you want to REMOVE original messages from server (not recommended) with:
#^^^^^^^^pop3 stream tcp	nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd -r
# And we also need to add a line to get hotsmtpd working, just paste this at the bottom:
#^^^^^^^^2500 stream tcp	nowait nobody /usr/sbin/tcpd /usr/bin/hotsmtpd
# Now, save your file, exit gedit, and restart your inetd server:
sudo /etc/init.d/inetutils-inetd restart
# If everything is working properly, you'll see this pop up on your screen:
#^^^^^^^^* Restarting internet superserver inetd                            [ ok ]
# Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard
# for this example [email]UserName@alumni.sauder.ubc.ca[/email] is linked with [email]AnotherUserName@hotmail.com[/email] but you can use the Hotmail one only
# you can use all over "localhost" or "127.0.0.1"
#^^^^^^^^Edit -> Preferences -> Mail Accounts -> Add
# Mail Configuration
#^^^^^^^^Forward
# Identity
#^^^^^^^^Full Name: [email]UserName@alumni.sauder.ubc.ca[/email]
#^^^^^^^^Email Address: [email]UserName@alumni.sauder.ubc.ca[/email]
#^^^^^^^^[X] Make this my default account
#^^^^^^^^Reply-To: [email]UserName@alumni.sauder.ubc.ca[/email]
#^^^^^^^^Organization: home
#^^^^^^^^Forward
# Receiving Email
#^^^^^^^^Server Type: POP
#^^^^^^^^Server: localhost
#^^^^^^^^Username: [email]AnotherUserName@hotmail.com[/email]
#^^^^^^^^Use Secure Connection: No encryption
#^^^^^^^^Authentication Type: Password
#^^^^^^^^[X] Remember Password
#^^^^^^^^Forward
# Receiving Options
#^^^^^^^^[X] Check for new messages every [10] minutes
#^^^^^^^^[X] Leave messages on server
#^^^^^^^^[ ] Delete after [7] day(s)
#^^^^^^^^[ ] Disable support for all POP3 extensions
#^^^^^^^^Forward
# Sending Email
#^^^^^^^^Server Type: SMTP
#^^^^^^^^Server: localhost:2500
#^^^^^^^^[X] Server requires authentication
#^^^^^^^^Use SecureConnection: No encryption
#^^^^^^^^Authentication Type: PLAIN
#^^^^^^^^Username: [email]AnotherUserName@hotmail.com[/email]
#^^^^^^^^[X]Remember password
#^^^^^^^^Forward
# Account Management:
#^^^^^^^^Name: [email]UserName@alumni.sauder.ubc.ca[/email]
#^^^^^^^^Forward
# Timezone
#^^^^^^^^Selection: America/Los_Angeles
#^^^^^^^^Forward
# Done
#^^^^^^^^Apply
# Start Evolution again -> Edit -> Preferences -> Mail Accounts -> Add and repeat for:
#^^^^^^^^[email]UserName2@hotmail.com[/email]
#^^^^^^^^[email]UserName3@hotmail.com[/email]
#^^^^^^^^[email]UserName4@msn.com[/email]
#^^^^^^^^[email]UserName5@msn.com[/email]


# HOWTO: Send and Receive Gmail through Evolution
# from [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)
# Login to your gmail account and select Forwarding and POP
# Enable pop and set pop up in the way you prefer (At least make sure pop is enabled)
# Open evolution, select: Edit > Preferences > Mail Accounts -> Add
# Identity
#^^^^^^^^FullName: [email]UserName@gmail.com[/email]
#^^^^^^^^ Email Address: [email]UserName@gmail.com[/email]
#^^^^^^^^[ ] Make this my default account
#^^^^^^^^Reply-To: [email]UserName@gmail.com[/email]
#^^^^^^^^Organization: home
#^^^^^^^^Forward
# Receiving Email
#^^^^^^^^Server Type: POP
#^^^^^^^^Server: pop.gmail.com
#^^^^^^^^Username: [email]UserName@gmail.com[/email]
#^^^^^^^^Use Secure Connection: SSL encryption
#^^^^^^^^Authentication Type: Password
#^^^^^^^^[X] Remember Password
#^^^^^^^^Forward
# Receiving Options
#^^^^^^^^[X] Check for new messages every [10] minutes
#^^^^^^^^[X] Leave messages on server
#^^^^^^^^[ ] Delete after [7] day(s)
#^^^^^^^^[ ] Disable support for all POP3 extensions
#^^^^^^^^Forward
# Sending Email
#^^^^^^^^Server Type: SMTP
#^^^^^^^^Server: smtp.gmail.com
#^^^^^^^^[X] Server requires authentication
#^^^^^^^^Use Secure Connection: SSL encryption
#^^^^^^^^Authentication Type: Plain
#^^^^^^^^Username: [email]UserName@gmail.com[/email]
#^^^^^^^^[X] Remember password
#^^^^^^^^Forward
# Account Management:
#^^^^^^^^Name: [email]UserName@gmail.com[/email]
#^^^^^^^^Forward
# Timezone
#^^^^^^^^Selection: America/Los_Angeles
#^^^^^^^^Forward
# Done
#^^^^^^^^Apply


# HOWTO: Send and Receive Yahoo through Evolution
# from [http://www.geocities.com/t_skariah/ypops/](http://www.geocities.com/t_skariah/ypops/)
cd /home/work/src/email/ypops/install
wget [http://tskariah.net78.net/t_skariah.asc.gpg](http://tskariah.net78.net/t_skariah.asc.gpg)
sudo apt-key add t_skariah.asc.gpg
sudo su
cat >>/etc/apt/sources.list<<"EOF"
deb [http://tskariah.net78.net/ubuntu](http://tskariah.net78.net/ubuntu) ubuntu main
EOF
exit
sudo apt-get update
sudo apt-get purge ypops
# or
sudo apt-get remove ypops
sudo apt-get install -y ypops
# How to start YPOPs! for Ubuntu manually:
sudo /etc/init.d/ypops start
# How to start YPOPs! for Ubuntu manually:
sudo /etc/init.d/ypops restart
# How to stop YPOPs! for Ubuntu manually:
sudo /etc/init.d/ypops stop
# How to (Re)configure YPOPs! for Ubuntu:
sudo dpkg-reconfigure -fgnome ypops
# Don't tick "Add a new account", just press Forward
# YPOPS!: global: Receiving Email
#^^^^^^^^[ ] Empty Trash on exit?
#^^^^^^^^[ ] Empty Bulk mail folder on exit ?
#^^^^^^^^[ ] Mark messages as unread on Yahoo! Mail server ?
#^^^^^^^^Maximum number of emails to download per pass ? [10000]
#^^^^^^^^[ ] Apply limit to message list ?
#^^^^^^^^Download email category [All]
#^^^^^^^^Witch YAHOO! domain to use ? [yahoo.com]
#^^^^^^^^Forward
# YPOPS!: global: Download Folders
#^^^^^^^^What folders should be checked for emails (comma separated list)? [inbox, set items, bulk]
#^^^^^^^^[X] inbox
#^^^^^^^^[X] Bulk Mail folder
#^^^^^^^^Forward
# YPOPS!: global: Sending Email
#^^^^^^^^[X] Save email in Yahoo's sent items folder ?
#^^^^^^^^Forward
# YPOPS!: global: Session
#^^^^^^^^Session timeout in seconds: 120000
#^^^^^^^^Forward
# YPOPS!: global: Proxies
#^^^^^^^^[ ] Connect to internet via an HTTP proxy server ?
#^^^^^^^^Forward
# YPOPS!: global: Proxies 
#^^^^^^^^[ ] Enable Proxy Authentication ?
#^^^^^^^^Forward
# YPOPS!: global: Network
#^^^^^^^^ Bind address: localhost
#^^^^^^^^POP3 port: 5110
#^^^^^^^^[X] Enable SMTP
#^^^^^^^^Forward
# YPOPS!: global: Network
#^^^^^^^^SMTP port: 5025
# YPOPS!: global: Activity Log
#^^^^^^^^[X] Create an Activity log ?
#^^^^^^^^Forward
# YPOPS!: global: Activity Log
#^^^^^^^^ Set the log level: Advanced
#^^^^^^^^Maximum size of the log file in KB: 500000
#^^^^^^^^Forward
# YPOPS!: global: Miscellaneous
#^^^^^^^^User agent string to use [Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)]
#^^^^^^^^[X] Enable UIDL (unique msg id) support (recommended)
#^^^^^^^^[X] Automatically start YPOPs! when the system start
#^^^^^^^^[X] Restart YPOPs! now ?
#^^^^^^^^Forward


# There is a bug with automatic ypops startup. For auto start at boot:
cd /etc/rc2.d/
sudo ln -s ../init.d/ypops S99ypops


# to disable the very annoiyng pesky keyring request for Evolution passwords:
# from [http://ubuntuforums.org/showthread.php?t=157808](http://ubuntuforums.org/showthread.php?t=157808) [by ronmarley1]
rm -rf /home/YourUserName/.gnome2/keyrings
# after starting Evolution, the account passwords are requested again
# after first account password validation the pesky "Create Default Keyring" pops up asking to create a default one
# Leave "Password:" and "Confirm password:" empty -> Create -> Use Unsafe Storage. There is nothing unsafe here, is just dumb to ask for multiple layers of password confirmation.


# Start Evolution and add an Yahoo account:
# Evolution Setup Assistant
# Welcome
#^^^^^^^^Forward
# Restore from backup
#^^^^^^^^Forward
# Identity
#^^^^^^^^Full Name: [email]UserName@yahoo.com[/email]
#^^^^^^^^Email Address: [email]UserName@yahoo.comm[/email]
#^^^^^^^^[ ] Make this my default account
#^^^^^^^^Reply-To: [email]UserName@yahoo.com[/email]
#^^^^^^^^Organization: home
#^^^^^^^^Forward
# Receiving Email
#^^^^^^^^Server Type: POP
#^^^^^^^^Server: localhost:5110
#^^^^^^^^Username: [email]UserName@yahoo.com[/email]
#^^^^^^^^Use Secure Connection: No encryption
#^^^^^^^^Authentication Type: Password
#^^^^^^^^[X] Remember Password
#^^^^^^^^Forward
# Receiving Options
#^^^^^^^^[X] Check for new messages every [10] minutes
#^^^^^^^^[X] Leave messages on server
#^^^^^^^^[ ] Delete after [7] day(s)
#^^^^^^^^[ ] Disable support for all POP3 extensions
#^^^^^^^^Forward
# Sending Email
#^^^^^^^^Server Type: SMTP
#^^^^^^^^Server: localhost:5025
#^^^^^^^^[X] Server requires authentication
#^^^^^^^^Use SecureConnection: No encryption
#^^^^^^^^Authentication Type: PLAIN
#^^^^^^^^Username: [email]UserName@yahoo.com[/email]
#^^^^^^^^[X]Remember password
#^^^^^^^^Forward
# Account Management:
#^^^^^^^^Name: [email]UserName@yahoo.com[/email]
#^^^^^^^^Forward
# Timezone
#^^^^^^^^Selection: America/Los_Angeles
#^^^^^^^^Forward
# Done
#^^^^^^^^Apply
# Start Evolution again -> Edit -> Preferences -> Mail Accounts -> Add and repeat for:
#^^^^^^^^[email]UserName2@yahoo.com[/email]
#^^^^^^^^[email]UserName3@yahoo.com[/email]
\\:D/

---

### Post by Zebra_ on 2009-01-05
Nice guide. Any info for setting up IMAP with GMail?

---

### Post by Adrian Nania on 2009-01-05
Sory, I never tried IMAP. Maybe you can use Thunderbird settings:
[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)
Cheers,
Adi

---

### Post by jrusso2 on 2009-01-05
The new zimbra client does all them.

---

### Post by Adrian Nania on 2009-01-05
I have checked this Zimbra stuff. The main yahoo account is the one not working for me, it is complaining "Invalid token. Please report this error ..."
Once there, it is some sort of forum support.

---

### Post by delpol on 2009-01-09
> **Adrian Nania said:**
> ](*,)
I've had to spend a lot of time to gather pieces of information on how to set all my hotmail, gmail, yahoo accounts in Evolution. I hope this HOWTO could spare somebody else's time. Once all your accounts are up and running, don't forget to back-up Evolution's accounts, emails, etc. like this:
Start Evolution -> Backup Settings -> select backup file name/directory -> Save
I know, this is mighty silly and there are no settings at all. Nevertheless, this is how you backup Evolution. On a very personal note, I believe people involved in developing these tools are not quite open to usability. Everything MUST be a single-click automatic install for people to be comfortable switching from Window$$$ to Linux.

Now to the juicy part: follow step by step all these instructions:

# HOWTO: Send and Receive Hotmail, Gmail, Yahoo (trough ypos) - In one single place
# HOWTO: Send and Receive Hotmail through Evolution
# from [http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)
sudo apt-get install -y inetutils-inetd hotway hotsmtp
sudo gedit /etc/inetd.conf
# Look for a line like this:
#^^^^^^^^pop3 stream tcp	nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd
# and replace if you want to REMOVE original messages from server (not recommended) with:
#^^^^^^^^pop3 stream tcp	nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd -r
# And we also need to add a line to get hotsmtpd working, just paste this at the bottom:
#^^^^^^^^2500 stream tcp	nowait nobody /usr/sbin/tcpd /usr/bin/hotsmtpd
# Now, save your file, exit gedit, and restart your inetd server:
sudo /etc/init.d/inetutils-inetd restart
# If everything is working properly, you'll see this pop up on your screen:
#^^^^^^^^* Restarting internet superserver inetd                            [ ok ]
# Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard
# for this example [email]UserName@alumni.sauder.ubc.ca[/email] is linked with [email]AnotherUserName@hotmail.com[/email] but you can use the Hotmail one only
# you can use all over "localhost" or "127.0.0.1"
#^^^^^^^^Edit -> Preferences -> Mail Accounts -> Add
# Mail Configuration
#^^^^^^^^Forward
# Identity
#^^^^^^^^Full Name: [email]UserName@alumni.sauder.ubc.ca[/email]
#^^^^^^^^Email Address: [email]UserName@alumni.sauder.ubc.ca[/email]
#^^^^^^^^[X] Make this my default account
#^^^^^^^^Reply-To: [email]UserName@alumni.sauder.ubc.ca[/email]
#^^^^^^^^Organization: home
#^^^^^^^^Forward
# Receiving Email
#^^^^^^^^Server Type: POP
#^^^^^^^^Server: localhost
#^^^^^^^^Username: [email]AnotherUserName@hotmail.com[/email]
#^^^^^^^^Use Secure Connection: No encryption
#^^^^^^^^Authentication Type: Password
#^^^^^^^^[X] Remember Password
#^^^^^^^^Forward
# Receiving Options
#^^^^^^^^[X] Check for new messages every [10] minutes
#^^^^^^^^[X] Leave messages on server
#^^^^^^^^[ ] Delete after [7] day(s)
#^^^^^^^^[ ] Disable support for all POP3 extensions
#^^^^^^^^Forward
# Sending Email
#^^^^^^^^Server Type: SMTP
#^^^^^^^^Server: localhost:2500
#^^^^^^^^[X] Server requires authentication
#^^^^^^^^Use SecureConnection: No encryption
#^^^^^^^^Authentication Type: PLAIN
#^^^^^^^^Username: [email]AnotherUserName@hotmail.com[/email]
#^^^^^^^^[X]Remember password
#^^^^^^^^Forward
# Account Management:
#^^^^^^^^Name: [email]UserName@alumni.sauder.ubc.ca[/email]
#^^^^^^^^Forward
# Timezone
#^^^^^^^^Selection: America/Los_Angeles
#^^^^^^^^Forward
# Done
#^^^^^^^^Apply
# Start Evolution again -> Edit -> Preferences -> Mail Accounts -> Add and repeat for:
#^^^^^^^^[email]UserName2@hotmail.com[/email]
#^^^^^^^^[email]UserName3@hotmail.com[/email]
#^^^^^^^^[email]UserName4@msn.com[/email]
#^^^^^^^^[email]UserName5@msn.com[/email]


# HOWTO: Send and Receive Gmail through Evolution
# from [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)
# Login to your gmail account and select Forwarding and POP
# Enable pop and set pop up in the way you prefer (At least make sure pop is enabled)
# Open evolution, select: Edit > Preferences > Mail Accounts -> Add
# Identity
#^^^^^^^^FullName: [email]UserName@gmail.com[/email]
#^^^^^^^^ Email Address: [email]UserName@gmail.com[/email]
#^^^^^^^^[ ] Make this my default account
#^^^^^^^^Reply-To: [email]UserName@gmail.com[/email]
#^^^^^^^^Organization: home
#^^^^^^^^Forward
# Receiving Email
#^^^^^^^^Server Type: POP
#^^^^^^^^Server: pop.gmail.com
#^^^^^^^^Username: [email]UserName@gmail.com[/email]
#^^^^^^^^Use Secure Connection: SSL encryption
#^^^^^^^^Authentication Type: Password
#^^^^^^^^[X] Remember Password
#^^^^^^^^Forward
# Receiving Options
#^^^^^^^^[X] Check for new messages every [10] minutes
#^^^^^^^^[X] Leave messages on server
#^^^^^^^^[ ] Delete after [7] day(s)
#^^^^^^^^[ ] Disable support for all POP3 extensions
#^^^^^^^^Forward
# Sending Email
#^^^^^^^^Server Type: SMTP
#^^^^^^^^Server: smtp.gmail.com
#^^^^^^^^[X] Server requires authentication
#^^^^^^^^Use Secure Connection: SSL encryption
#^^^^^^^^Authentication Type: Plain
#^^^^^^^^Username: [email]UserName@gmail.com[/email]
#^^^^^^^^[X] Remember password
#^^^^^^^^Forward
# Account Management:
#^^^^^^^^Name: [email]UserName@gmail.com[/email]
#^^^^^^^^Forward
# Timezone
#^^^^^^^^Selection: America/Los_Angeles
#^^^^^^^^Forward
# Done
#^^^^^^^^Apply


# HOWTO: Send and Receive Yahoo through Evolution
# from [http://www.geocities.com/t_skariah/ypops/](http://www.geocities.com/t_skariah/ypops/)
cd /home/work/src/email/ypops/install
wget [http://tskariah.net78.net/t_skariah.asc.gpg](http://tskariah.net78.net/t_skariah.asc.gpg)
sudo apt-key add t_skariah.asc.gpg
sudo su
cat >>/etc/apt/sources.list<<"EOF"
deb [http://tskariah.net78.net/ubuntu](http://tskariah.net78.net/ubuntu) ubuntu main
EOF
exit
sudo apt-get update
sudo apt-get purge ypops
# or
sudo apt-get remove ypops
sudo apt-get install -y ypops
# How to start YPOPs! for Ubuntu manually:
sudo /etc/init.d/ypops start
# How to start YPOPs! for Ubuntu manually:
sudo /etc/init.d/ypops restart
# How to stop YPOPs! for Ubuntu manually:
sudo /etc/init.d/ypops stop
# How to (Re)configure YPOPs! for Ubuntu:
sudo dpkg-reconfigure -fgnome ypops
# Don't tick "Add a new account", just press Forward
# YPOPS!: global: Receiving Email
#^^^^^^^^[ ] Empty Trash on exit?
#^^^^^^^^[ ] Empty Bulk mail folder on exit ?
#^^^^^^^^[ ] Mark messages as unread on Yahoo! Mail server ?
#^^^^^^^^Maximum number of emails to download per pass ? [10000]
#^^^^^^^^[ ] Apply limit to message list ?
#^^^^^^^^Download email category [All]
#^^^^^^^^Witch YAHOO! domain to use ? [yahoo.com]
#^^^^^^^^Forward
# YPOPS!: global: Download Folders
#^^^^^^^^What folders should be checked for emails (comma separated list)? [inbox, set items, bulk]
#^^^^^^^^[X] inbox
#^^^^^^^^[X] Bulk Mail folder
#^^^^^^^^Forward
# YPOPS!: global: Sending Email
#^^^^^^^^[X] Save email in Yahoo's sent items folder ?
#^^^^^^^^Forward
# YPOPS!: global: Session
#^^^^^^^^Session timeout in seconds: 120000
#^^^^^^^^Forward
# YPOPS!: global: Proxies
#^^^^^^^^[ ] Connect to internet via an HTTP proxy server ?
#^^^^^^^^Forward
# YPOPS!: global: Proxies 
#^^^^^^^^[ ] Enable Proxy Authentication ?
#^^^^^^^^Forward
# YPOPS!: global: Network
#^^^^^^^^ Bind address: localhost
#^^^^^^^^POP3 port: 5110
#^^^^^^^^[X] Enable SMTP
#^^^^^^^^Forward
# YPOPS!: global: Network
#^^^^^^^^SMTP port: 5025
# YPOPS!: global: Activity Log
#^^^^^^^^[X] Create an Activity log ?
#^^^^^^^^Forward
# YPOPS!: global: Activity Log
#^^^^^^^^ Set the log level: Advanced
#^^^^^^^^Maximum size of the log file in KB: 500000
#^^^^^^^^Forward
# YPOPS!: global: Miscellaneous
#^^^^^^^^User agent string to use [Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)]
#^^^^^^^^[X] Enable UIDL (unique msg id) support (recommended)
#^^^^^^^^[X] Automatically start YPOPs! when the system start
#^^^^^^^^[X] Restart YPOPs! now ?
#^^^^^^^^Forward


# There is a bug with automatic ypops startup. For auto start at boot:
cd /etc/rc2.d/
sudo ln -s ../init.d/ypops S99ypops


# to disable the very annoiyng pesky keyring request for Evolution passwords:
# from [http://ubuntuforums.org/showthread.php?t=157808](http://ubuntuforums.org/showthread.php?t=157808) [by ronmarley1]
rm -rf /home/YourUserName/.gnome2/keyrings
# after starting Evolution, the account passwords are requested again
# after first account password validation the pesky "Create Default Keyring" pops up asking to create a default one
# Leave "Password:" and "Confirm password:" empty -> Create -> Use Unsafe Storage. There is nothing unsafe here, is just dumb to ask for multiple layers of password confirmation.


# Start Evolution and add an Yahoo account:
# Evolution Setup Assistant
# Welcome
#^^^^^^^^Forward
# Restore from backup
#^^^^^^^^Forward
# Identity
#^^^^^^^^Full Name: [email]UserName@yahoo.com[/email]
#^^^^^^^^Email Address: [email]UserName@yahoo.comm[/email]
#^^^^^^^^[ ] Make this my default account
#^^^^^^^^Reply-To: [email]UserName@yahoo.com[/email]
#^^^^^^^^Organization: home
#^^^^^^^^Forward
# Receiving Email
#^^^^^^^^Server Type: POP
#^^^^^^^^Server: localhost:5110
#^^^^^^^^Username: [email]UserName@yahoo.com[/email]
#^^^^^^^^Use Secure Connection: No encryption
#^^^^^^^^Authentication Type: Password
#^^^^^^^^[X] Remember Password
#^^^^^^^^Forward
# Receiving Options
#^^^^^^^^[X] Check for new messages every [10] minutes
#^^^^^^^^[X] Leave messages on server
#^^^^^^^^[ ] Delete after [7] day(s)
#^^^^^^^^[ ] Disable support for all POP3 extensions
#^^^^^^^^Forward
# Sending Email
#^^^^^^^^Server Type: SMTP
#^^^^^^^^Server: localhost:5025
#^^^^^^^^[X] Server requires authentication
#^^^^^^^^Use SecureConnection: No encryption
#^^^^^^^^Authentication Type: PLAIN
#^^^^^^^^Username: [email]UserName@yahoo.com[/email]
#^^^^^^^^[X]Remember password
#^^^^^^^^Forward
# Account Management:
#^^^^^^^^Name: [email]UserName@yahoo.com[/email]
#^^^^^^^^Forward
# Timezone
#^^^^^^^^Selection: America/Los_Angeles
#^^^^^^^^Forward
# Done
#^^^^^^^^Apply
# Start Evolution again -> Edit -> Preferences -> Mail Accounts -> Add and repeat for:
#^^^^^^^^[email]UserName2@yahoo.com[/email]
#^^^^^^^^[email]UserName3@yahoo.com[/email]
\\:D/
i did all this but still getting the "sending password.........." error. everything was successfull in the terminal too i.e restarting the server was ok. rebooted but still no access and same thing for thunderbird.

any ideas, please help
thanks

---

### Post by halovivek on 2009-01-09
> **Adrian Nania said:**
> ](*,)
I've had to spend a lot of time to gather pieces of information on how to set all my hotmail, gmail, yahoo accounts in Evolution. I hope this HOWTO could spare somebody else's time. Once all your accounts are up and running, don't forget to back-up Evolution's accounts, emails, etc. like this:
Start Evolution -> Backup Settings -> select backup file name/directory -> Save
\\:D/
HI
could you make your thread more readable. really nice article.
Dont forget [Yahoo zimbra]("http://ubuntuforums.org/showthread.php?t=1030223&highlight=yahoo+zimbra") does this all.
Thanks

---

### Post by Adrian Nania on 2009-01-27
Hello delpol,

1) never copy/paste "#^^^^^^^^", it is used like some visual tab only
2) I used my personal folder like "/home/work/src/email/ypops/install". You must create your own folder and replace my folder code with your folder.
3) you can replace /home/YourUserName with $HOME

I see no other reason you can not get this up and running. Otherwise, you do not have to copy/paste everything all over, the post gets really looooong.

---

### Post by prince_niceguy on 2009-02-13
Zimbra the current version is working like charm for me... everything yahoo gmail hotmail and added bonus their contacts and the calendar too are working perfectly....

---

### Post by Adrian Nania on 2009-03-07
thanks buddy,
I have now zimbra working. Looks like from time to time are random and temporary errors.

---

### Post by Nicholasfaz on 2009-03-12
mwahahahaha I finally got evolution to work thank you so very much for the info!

from a Complete ubuntu novice

---


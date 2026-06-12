---
title: "Evolution won't work with my Exchange Server (2003)"
date: 2008-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sjledet on 2008-12-22
I just received my Dell Mini 9 and am trying to configure it to work with Exchange. The little Mini has network connectivity and runs Outlook Web Access fine from Firefox. But when i try to connect using Evolution, no matter what I do it says Exchange Server Offline.

I have a few noob questions:

1) Do I use just my regular username, domain\user, or domain/user under the Exchange account in Evolution?

2) Under mailbox should I use my user name or my full name (which is what shows under Outlook on a Windows box)?

3) I am pretty sure I got the URL right. I just copied and pasted from Firefox. Firefox works fine with Outlook Web access. But is there any known issue on the Exchange server that would prevent Evolution from working, even if OWA is running OK?

---

### Post by brown.hornet on 2008-12-24
Sjledet -

1. Enter your user name in the 'Username' field without your domain.

2. Verify your OWA URL and enter in the 'OWA URL' field.

3. DO NOT enter the mailbox information as this will fill in when you 'Verify' your user information.  

4.  Click the 'Verification' button and when prompted for your password.  If everything is good to go your mailbox will display in the Mailbox field.

5.  You should be good to go.  Please note that when you send messages from Evolution they will not show up in your 'Sent' box on your Exchange Server.  They reside on the workstation only.

Respectfully -

ingram

---

### Post by Hula2Pahoa on 2008-12-24
> **brown.hornet said:**
> Sjledet -

1. Enter your user name in the 'Username' field without your domain.

2. Verify your OWA URL and enter in the 'OWA URL' field.

3. DO NOT enter the mailbox information as this will fill in when you 'Verify' your user information.  

4.  Click the 'Verification' button and when prompted for your password.  If everything is good to go your mailbox will display in the Mailbox field.

5.  You should be good to go.  Please note that when you send messages from Evolution they will not show up in your 'Sent' box on your Exchange Server.  They reside on the workstation only.


Respectfully -

ingram


** Hi, I was wondering if someone could assist me with editing my Evolution settings? I am unable to send or receive e-mails, so I figure I must have configured it wrong from the start. **
mahalo!

---

### Post by brown.hornet on 2008-12-24
What seems to be the problem.  Also I assume that you so have OWA working on your exchange server?  If not you won't be able to access your exchange server using the exchange option.  

Respectfully -

ingram

---

### Post by JohnnyB98604 on 2008-12-29
I'm having a similar issue with getting Evolution to connect to my exchange box at work.  This is one of my last steps before I can completely junk my XP installation and move completely to Ubuntu.  So, I'm motivated. :)

I'm using Ubuntu 8.04 and Evolution 2.22.3.1

My MS Exchange server is 2007 but I'm not certain of the version/milestone.

I have my OWA address ([https://mail.progressive-solutions.com/owa](https://mail.progressive-solutions.com/owa)) and username/password.

When I enter the aforementioned username and choose "Authenticate" I'm prompted for my password (which I enter VERY carefully) and I get an error message: "Could not configure Exchange account because an unknown error occurred.  Check the URL, username and password and try again."

I'm wondering if it's related to the "https" address as it's a secure http.  Also, in order to get Outlook to work with Exchange via the http connection we set the "Proxy Authentication Setting" to "Basic Authentication"...but that's Outlook.

Any idea's anyone?  (Thanks in advance)

---

### Post by njsanders1 on 2009-02-25
Thus far I've not seen anyone get Evo to connect to an Exchange OWA entity using a secure protocol (i.e., https).

BIG shortcoming in the feature set of Evolution if you ask me...  Of course, Tbird won't do it either, apparently, so I'm stuck either using my browser to hit the OWA server (which stinks if you're not using -gag- IE), or load VirtualBox and use Outlook.

---


---
title: "Evolution/Exchange can't get past authentication"
date: 2005-04-29
forum: Desktop Environments
---

### Post by emendelson on 2005-04-29
When I try setup Evolution to connect to a Microsoft Exchange server, the configuraiton wizard takes me to the point where I authenticate with the server, but then I can't go onward. The "Next" button stays grayed out. Can anyone help sort this out? Here are the details:

Start Evolution form the Applications/Internet menu. In the Evolution Setup Assistant, I enter my full name and my address in the form [email]accountname@company.com[/email].

Click Next, and under Server Type, I choose Microsoft Exchange. I enter my user name in the form "accountname" (no quotes), and the OWA Url as [https://webmail.company.com/exchange/](https://webmail.company.com/exchange/) (which is what I use for browser access to the server). I click on Authenticate, enter a password - and the authentication SEEMS to succeed (I'll explain why in a moment), but the Next button never appears.

Authentication seems to succeed because IF I enter the wrong name or the wrong password, an error message pops up immediately. No message pops up when I enter the correct name and password. But the Next button doesn't appear.

I thought this might be a permissions problem, so I started Evolution as root, but got exactly the same result. I thought it might work I set up another account first, and did (a POP account somewhere else), and then tried to add the Exchange account, but this didn't work either. 

Has anyone experienced this problem? And can anyone suggest a solution? Thanks for any help.

---

### Post by kirsche on 2005-04-30
Hello,

I just set up a fresh Exchange2003 server and enabled OWA.
I can successfully retrieve/send mail.
In what way are you providing the user-credentials?
[email]user@domain.fqdn[/email] or netbios-domain\user ?

---

### Post by emendelson on 2005-04-30
Thanks for confirming that this *should* work! I wonder if something's weird in my setup or in the Exchange Server?

Anyway, to answer your question,

In the configuration dlalog, I've tried all of the following:

DOMAIN\username <-- no error message, but no Forward button ether
username <-- no error message, but no Forward button either
[email]username@company.com[/email] <-- error message

I also get an error message if I enter an invalid OWA Url. There is no error message if enter the correct username, with or without domain name, and the correct URL. But the Forward button never becomes accessible.

Thanks again for showing that this should work -- now all I need to do is figure out why it doesn't...!

---

### Post by emendelson on 2005-04-30
OK - I figured out what was wrong, but I'll need more informaiton to solve it. instead of using Evolution to set things up, I ran ximian-connector-setup-2.2. With this, after authenticating my username, it brought up a dialog saying it couldn't find the "Global Catalog replica" for my site. I can't figure out what that address is, and I'll have to find someone in IT at the company for the information.

The trouble seems to be that the standard Evolution wizard fails here without an error message, while the ximian-connector app shows clearly what's going wrong.

---

### Post by kirsche on 2005-05-01
Good to hear you found the problem.
Hope it'll work after you found your GC server (shouldn't be a problem).

---

### Post by sarimak on 2005-05-04
I have troubles with connecting to corporate Exchange server that maybe could be somehow connected to your problems...

I can't get over Receiving email page in Setup Assistant because I've got different username for logging to OWA (via browser) and real username that is shown in URL (when opening an email via browser and then This frame->Show only this frame).

In Evolution 2.0 series I could enter both usernames and it worked - now I can't be authenticated.

my_surname vs. [http://exchange_server.our_company.com/exchange/my_initials_and_a_strange_number.routing.eu/](http://exchange_server.our_company.com/exchange/my_initials_and_a_strange_number.routing.eu/)

It seems that it's well-known problems to Gnome developers but it takes too long to fix such serious trouble - see [http://lists.ximian.com/archives/public/connector/2005-April/000589.html](http://lists.ximian.com/archives/public/connector/2005-April/000589.html)

Any suggestions/quick and dirty fixes?
Thanks, Jirka

---


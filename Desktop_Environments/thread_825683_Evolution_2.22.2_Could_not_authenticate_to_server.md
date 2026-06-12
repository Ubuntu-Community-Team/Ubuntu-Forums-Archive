---
title: "Evolution 2.22.2 Could not authenticate to server"
date: 2008-06-11
forum: Desktop Environments
---

### Post by seoras on 2008-06-11
I set up Evolution quite some time ago in Ubuntu 7.10 with my corporate MS Exchange server. It was working very well even after I upgraded to Ubuntu 8.04. It was also working well this morning, then I downloaded some 40 updates via update manager and just clicked install (not sure if there was an Evolution update in there). Next thing I knew Evolution crashed twice while I was writing an email, then it crashed X, which had to restart. Now Evolution will not connect to the mail server at all and returns an error "Could not authenticate to server (password incorrect?)" when in fact the password is correct.

I appreciate that a lot of people have experienced this problem and I have not found any solution on the forums to date. I just find it odd that Evolution worked fine one minute and then suddenly crashed and couldn't connect.

I have tried creating a new account in Evolution, but could not authenticate it on the server. I can still access my mail via Firefox 
I have tried variations of the OWA URL, nothing works.
I have rebooted the PC.
I have tried to run Evolution from terminal with the same results, altough it did return the following (which is similar to what others have reported):

e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have key 'exchange:__myUserName;auth_Basic@OWA_URL_'
evolution-shell-Message: Killing old version of evolution-data-server...
 
** (evolution:10898): WARNING **: Invalid uri 'owaauth.dll'

(evolution:10898): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

** (evolution:10898): WARNING **: Unexpected kerberos error -1765328164

**Update 12th June**: This morning there was an update to the Evolution-Exchange package I installed in the hope this would solve the problem, but alas no. 

I also noticed this morning that my employer has changed the web page interface for OWA it asks if this is a private or public computer and is also defaulted to **Use Outlook Web Access Light**. Looks like they've upgraded to Exchange 2007 and from what I can gather from the forums Evolution does not work with Exchange Server 2007, although there seems to be a plugin in development over at [OpenChange]("http://www.openchange.org/index.php?option=com_content&task=view&id=65&Itemid=74")?

I really hope there is a fix for this soon as Evolution (as far as I'm aware) is the only Linux mail client that can work with MS-Exchange. I know some people use Thunderbird but this requires MS-Exchange to be configured to allow IMAP connections and most are not.

I really don't want to go back to Windows but web access to my mail is just too limited.

---

### Post by xixx on 2008-08-25
I have evolution 2.22.3 (ubuntu 8.04) and the same problem. Anybody know howto solve this issue?

---


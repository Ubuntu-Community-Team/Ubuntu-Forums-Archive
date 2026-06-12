---
title: "problem with evolution and yahoo pop server"
date: 2005-12-08
forum: General Help
---

### Post by tobozub-bu on 2005-12-08
I am using Evolution 2.4.1 
Configured it to retrive mail from my Yahoo mail account but it does not seem to work (see error message below) 

Error While fetching Mail
Host lookup failed:  pop.mail.yahoo.com: Name or service not known

I have the following configuration settings in Evolution Receiving Email tab:

Server Type : POP
Server: pop.mail.yahoo.com (as yahoo requires, also I am able to ping this name)
Username : ...
Use secure connection: whenever possible (tryied other settings as well)
Authentication Type: password

When I click on "Chcek for supported types" in this dialog box I get this message:
Error while Checking Service.
Could not connect to POP server  pop.mail.yahoo.com

Any recomenadations?

Thanks !

BTW
I have used Thunderbird in the past and it worked fine with the same (similar) settings. The only reason I am trying to switch to Evolution is that it claims that it supports address book and calendar synchronization with my Palm, which Thunderbird does not support yet.

---

### Post by Appolusionist on 2005-12-08
[quote=tobozub-bu]I am using Evolution 2.4.1 
Configured it to retrive mail from my Yahoo mail account but it does not seem to work (see error message below) 
 
Error While fetching Mail
Host lookup failed: pop.mail.yahoo.com: Name or service not known
 
I have the following configuration settings in Evolution Receiving Email tab:
 
Server Type : POP
Server: pop.mail.yahoo.com (as yahoo requires, also I am able to ping this name)
Username : ...
Use secure connection: whenever possible (tryied other settings as well)
Authentication Type: password
 
When I click on "Chcek for supported types" in this dialog box I get this message:
Error while Checking Service.
Could not connect to POP server pop.mail.yahoo.com
 
Any recomenadations?
 
Thanks !
 
BTW
I have used Thunderbird in the past and it worked fine with the same (similar) settings. The only reason I am trying to switch to Evolution is that it claims that it supports address book and calendar synchronization with my Palm, which Thunderbird does not support yet.[/quote]
 
I grabbed the info listed below from this [thread]("http://ubuntuforums.org/showthread.php?t=38757"). I don't use Evolution myself, but maybe it will point you in the right direction. 
 
> Start evolution. go to Edit/Preferences. Click the Add button. Step
through the wizard, adding your personal information. Once you get to
the "Receiving Email" step, you'll have to select some "Server type".
You have said you want POP, so select that. 
 
You'll need to get the connection information from your provider at this
point. If you intend to use POP from yahoo, you have to pay them money
(gmail allows POP access but does not require money for it). In any
event, if you want to use POP, you'll have to have a POP account
somewhere, and the people running that place should provide you with the
host and username information. 
 
Once you've entered that info, click Forward and you might want to
enable "Leave messages on server," otherwise your message will be
automatically deleted from your inbox when you download them in
evolution.
 
Click forward to get to the "Sending Email" page. Again, you'll need to
supply information given to you by either your ISP or your email
provider. Sometimes the host will be something like "smtp-server.rr.com"
or similar, but you really will have to find that out from your ISP or
email provider.
 
After that, you're basically done. Just click Send/Receive to download
your email into evolution.


---

### Post by hajk on 2005-12-08
Recommendation: play around with the various settings until you get it working.
For example: try "Never" to use a secure connection -- is it still giving you a login error message? Etc...

---

### Post by tobozub-bu on 2005-12-09
hajk,

Thanks for your recomendation. Tried everything still does not work. Can there be some firewall-like function that blocks pop traffic (I do not rembere installing or configuring anything that could do this, though). 

Any other advise would be greatly apretiated

Thanks!

---

### Post by bbpackwood on 2008-06-11
Hi, I was wondering if there's any way to disable the: "Host lookup failed: Name or service not known" login error message. Evolution is working fine on my notebook. I got my system of open Evolution on login. However, when I work away from a wifi spot I get that annoying error.

Thanks in advance.

---


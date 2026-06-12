---
title: "Yahoo not working with Pidgin"
date: 2009-06-20
forum: General Help
---

### Post by Sentience on 2009-06-20
When I start Pidgen I am able to sign into my MSN and AIM but not my yahoo accounts. Whats going on?

Is there a way to fix this or perhaps can I get yahoo messenger working on Ubuntu?

---

### Post by raymondh on 2009-06-20
> **Sentience said:**
> When I start Pidgen I am able to sign into my MSN and AIM but not my yahoo accounts. Whats going on?

Is there a way to fix this or perhaps can I get yahoo messenger working on Ubuntu?

Hi,

Edit your yahoo account settings (in pidgin) to change the server.  Mine is

cn.scs.msg.yahoo.com

Hope this helps.

---

### Post by Sentience on 2009-06-20
Change it to what?

Sorry, Im a noob and I dont know what I should type in there. Mine is

scs.msg.yahoo.com

---

### Post by JohnE1 on 2009-06-20
Yes, there's a fix with 2 ways of implementation.

My solution is local to each Pidgin Yahoo account, so it requires modifying each Yahoo account.

The alternate solution is global to all networking on your machine.

Details of local solution:
--------------------------

1. Go into your Yahoo account, Modify, Advanced

2. Replace the Pager server name:  scs.msg.yahoo.com

with its static IP address:  66.163.181.170

NOTE:  If necessary, disable your ethernet connection and re-enable it.

----------------------

The alternate solution is global to all networking on your machine.

Visit this link:
Fixing Pidgin for Yahoo Messenger
[http://www.dmcinfo.com/Blog/articleType/ArticleView/articleId/42/Fixing-Pidgin-for-Yahoo-Messenger.aspx]("http://www.dmcinfo.com/Blog/articleType/ArticleView/articleId/42/Fixing-Pidgin-for-Yahoo-Messenger.aspx")

---------------------------------

John

---

### Post by JohnE1 on 2009-06-20
> **raymondhenson said:**
> Hi,

Edit your yahoo account settings (in pidgin) to change the server.  Mine is

cn.scs.msg.yahoo.com

Hope this helps.

cn = China ??

I wouldn't want all my conversations going thru a server in China.

Use the fixed static IP address instead of scs.msg.yahoo.com.

66.163.181.170 = scs.msg.yahoo.com

John

---

### Post by raymondh on 2009-06-20
> **JohnE1 said:**
> 

66.163.181.170 = scs.msg.yahoo.com

John

Still cannot get  that IP address to work.   What works for me are

cn.scs.msg.yahoo.com
cs101.msg.mud.yahoo.com

Hmmm, now I'm curious.  Maybe yahoo still has not updated all its' servers. Oh well, I'll wait and see.

---

### Post by Sentience on 2009-06-20
Thanks. That worked but I sure hope somebody creates an update to fix this universally.

---

### Post by niket_a on 2009-06-21
Hey thanks that static IP worked for me :)

---

### Post by JohnE1 on 2009-06-23
> **Sentience said:**
> Thanks. That worked but I sure hope somebody creates an update to fix this universally.

If you mean, for all your Yahoo accounts, then that link I provided detailed that.

Here's the gist of it:

1. Open a terminal window (Applications, Accessories, Terminal)
      and at the prompt enter: gksudo gedit /etc/hosts

    You will be prompted to enter your user password,
      then gedit will run as root and
      will open /etc/hosts file for editing.

2. Add this line to /etc/hosts file:

66.163.181.170    scs.msg.yahoo.com

3. Restart Pidgin. If you still can't connect, then you'll need to disable and re-enable your network connection to force it to re-read the hosts file.

NOTE: If you already entered the static IP address into a Pidgin account, it will override the hosts file. In that case, you'll need to set the account's Pager server back to the server name, scs.msg.yahoo.com, to test that Pidgin is getting the IP address from the hosts file.

---------------

John

---

### Post by wncben on 2009-06-23
Yahoo! is phasing out the older yahoo messenger protocols.  The version of pidgin that ships with ubuntu uses these older protocols, and ubuntu does not automatically update pidgin except for security reasons.  As yahoo goes through each server and update it, the server will stop functioning with the old protocols, so switching servers is a temporary fix at best as sooner or later yahoo will update that server too.
  Pidgin has released a newer version that uses newer yahoo protocols.  they have also set up a ppa to automatically update pidgin.  

Go to the pidgin update page [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/) and follow the directions, and then go to your update manager (located under system > Administration > update manager) and check for new updates, which should bring up the new version of pidgin, click update and voila...

Cheers ~ Ben

---

### Post by petercool on 2009-06-23
> **wncben said:**
> Yahoo! is phasing out the older yahoo messenger protocols.  The version of pidgin that ships with ubuntu uses these older protocols, and ubuntu does not automatically update pidgin except for security reasons.  As yahoo goes through each server and update it, the server will stop functioning with the old protocols, so switching servers is a temporary fix at best as sooner or later yahoo will update that server too.
  Pidgin has released a newer version that uses newer yahoo protocols.  they have also set up a ppa to automatically update pidgin.  

Go to the pidgin update page [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/) and follow the directions, and then go to your update manager (located under system > Administration > update manager) and check for new updates, which should bring up the new version of pidgin, click update and voila...

Cheers ~ Ben
Thanks a million!!!!

---

### Post by jebblue on 2009-06-23
> **petercool said:**
> Thanks a million!!!!

Thanks too!

---

### Post by JohnE1 on 2009-06-23
> **wncben said:**
> Yahoo! is phasing out the older yahoo messenger protocols.  The version of pidgin that ships with ubuntu uses these older protocols, and ubuntu does not automatically update pidgin except for security reasons.  As yahoo goes through each server and update it, the server will stop functioning with the old protocols, so switching servers is a temporary fix at best as sooner or later yahoo will update that server too.
  Pidgin has released a newer version that uses newer yahoo protocols.  they have also set up a ppa to automatically update pidgin.  

Go to the pidgin update page [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/) and follow the directions, and then go to your update manager (located under system > Administration > update manager) and check for new updates, which should bring up the new version of pidgin, click update and voila...

Cheers ~ Ben

Hey Ben, thanks for that info!

IMPORTANT NOTE!: For those who took my earlier advice to replace the pager server name with a static IP address, you will need to set the "Pager server: " back to the server name, scs.msg.yahoo.com, after updating Pidgin.

Thanks again, Ben!

John

---

### Post by djmm on 2009-06-25
Deleted

---

### Post by spcwingo on 2009-06-25
You could also add the Pidgin PPA and upgrade to the latest version (which supports the new Yahoo protocol).  Because it won't be long until the cn server gets "upgraded" too.

---

### Post by Sef on 2009-06-25
> You could also add the Pidgin PPA and upgrade to the latest version (which supports the new Yahoo protocol). Because it won't be long until the cn server gets "upgraded" too.

[Launchpad Pidgin PPA ]("https://launchpad.net/%7Epidgin-developers/+archive/ppa")

---


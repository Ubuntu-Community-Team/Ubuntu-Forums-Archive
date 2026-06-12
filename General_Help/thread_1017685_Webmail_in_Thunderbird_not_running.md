---
title: "Webmail in Thunderbird not running"
date: 2008-12-21
forum: General Help
---

### Post by Godsbrother on 2008-12-21
Hi All,

I have a problem with Thunderbird (2.0.0.18 ) and WebMail (1.3.3b3) in that if I start it from the desktop icon or from the menu Thunderbird starts fine but the pop/smtp/imap servers in Webmail won't start.

Now I can force them to start by changing the ports but then they dont work.
Or I can run Thunderbird using the terminal and sudo at which point everything works great! But it all used to work from the icon's?

Anyone got any idea's why the pop/smtp/imap servers wont run under my login?

Cheers

Forgot to say I'm running Ubuntu 8.10 (upto date)

---

### Post by Godsbrother on 2008-12-22
Nobody got any suggestions?

---

### Post by Godsbrother on 2008-12-23
blimey can't believe no-one has any idea's?

---

### Post by benny bronx on 2008-12-23
I'm not sure why it would work as root but not user.  When you change the port in webmail, are you also changing it in the Thunderbird account settings-server settings.  I have to change mine to a port above 1024 and never had a problem like you are experiencing.  And where did you get the beta3? I have the one from the webmail site and it is 1.3.2.

---

### Post by Godsbrother on 2008-12-23
Good point about changing it in the server settings hadn't done that... rushes off to try.....

Oh I got the beta here - 

[http://thunderbird-webmail-extension.googlegroups.com/web/web-mail-1-3-3b3.zip?gda=p-XGZ0YAAAAQ7bpMYik_k5EMVy67u1NDeUPiBPsRWFWk_X7sNDGaxGlu7nHieHpV5Lf7I_sGQH9J7bz9tedoI9cRbqyUDqyTE-Ea7GxYMt0t6nY0uV5FIQ]("http://thunderbird-webmail-extension.googlegroups.com/web/web-mail-1-3-3b3.zip?gda=p-XGZ0YAAAAQ7bpMYik_k5EMVy67u1NDeUPiBPsRWFWk_X7sNDGaxGlu7nHieHpV5Lf7I_sGQH9J7bz9tedoI9cRbqyUDqyTE-Ea7GxYMt0t6nY0uV5FIQ")

---

### Post by Godsbrother on 2008-12-23
> **benny bronx said:**
> I'm not sure why it would work as root but not user.  When you change the port in webmail, are you also changing it in the Thunderbird account settings-server settings.  I have to change mine to a port above 1024 and never had a problem like you are experiencing.  And where did you get the beta3? I have the one from the webmail site and it is 1.3.2.

Your'e a genius that worked a treat! :KS

Now to work out why it's not remembering passwords!!!

---


---
title: "Hotmail in any Email App"
date: 2009-06-05
forum: General Help
---

### Post by mschraier on 2009-06-05
I am not sure how many people know this, but Hotmail is now a POP3 account that can be used in any email app,  Use the following setup.  No additiooanl software is required.


pop server: pop3.live.com
smtp server: smtp.live.com

set pop to listen to port 995 and make sure it is using SSL

set smtp to listen to port 587, make sure to use SSL and require authentication.

i used it in outlook on XP and kmail in kubuntu

:p:p:p:p:p:p:

---

### Post by jenkinbr on 2009-06-06
Good to know.

Don't use hotmail myself, but others I know do.

---

### Post by mike555 on 2009-06-06
I have an Hotmail account just to test it for my customers , and found that the setting for smtp you should use port  587 and TLS    if the other setting don't work (I tested them in Thunderbird).

---

### Post by Kevbert on 2009-06-06
This works fine in Evolution. For receiving use pop3.live.com:995 and sending smtp.live.com:587 (TLS used).
Thanks mschraier for the original post. Before I had to use Hotway.

---

### Post by bacardiandwatermelon on 2009-06-06
Didn't hotmail use pop3 years ago?

---

### Post by philinux on 2009-06-06
> **mschraier said:**
> I am not sure how many people know this, but Hotmail is now a POP3 account that can be used in any email app,  Use the following setup.  No additiooanl software is required.


pop server: pop3.live.com
smtp server: smtp.live.com

set pop to listen to port 995 and make sure it is using SSL

set smtp to listen to port 587, make sure to use SSL and require authentication.

i used it in outlook on XP and kmail in kubuntu

:p:p:p:p:p:p:

For smtp I had to use port 25 and TSL

---

### Post by Kevbert on 2009-06-07
> **bacardiandwatermelon said:**
> Didn't hotmail use pop3 years ago?

Yes, quite a few years back.
The official view:
> Outlook, Outlook Express, and Entourage use a legacy communications method (known as the DAV protocol) to access Hotmail. Because the DAV protocol is not optimally suited for programs to access large inboxes such as Hotmail which now provides users ever-growing storage*, new alternatives have been built. Last year, customers asked us to postpone plans to retire the DAV protocol until more options were available. Now that these options (including the POP3 protocol) are available, we are ready to retire the DAV protocol. 
This suggests that MS may make more changes in the near future.

---

### Post by MrDelish on 2009-06-11
I've been unable to log in to hotmail.com for a few days now. My ISP confirmed that they could duplicate the issue at first, but claimed that it started working for them later :---). I tried Chrome, IE, and Firefox in my VirtualBox XP installation with the same result.

I've already got my messages downloading to Thunderbird. Thanks very much for sharing.

---

### Post by Magnificence on 2009-06-11
Hey! Thanks for the info! I got it working now in Evolution Mail, I didn't needed to fill in the ports ^^.

---

### Post by redbook4574 on 2009-06-11
> **mschraier said:**
> I am not sure how many people know this, but Hotmail is now a POP3 account that can be used in any email app,  Use the following setup.  No additiooanl software is required.


pop server: pop3.live.com
smtp server: smtp.live.com

set pop to listen to port 995 and make sure it is using SSL

set smtp to listen to port 587, make sure to use SSL and require authentication.

i used it in outlook on XP and kmail in kubuntu

:p:p:p:p:p:p:
Give up on hotmail - use gmail (oh its free)

---

### Post by jenkinbr on 2009-06-11
> **redbook4574 said:**
> Give up on hotmail - use gmail (oh its free)
And GMail has 7336 MB of online storage! Google Rules!

<no offense to any hotmail or live users, I just never cared much for MS.

---

### Post by Lampi on 2009-06-12
> **mschraier said:**
> i used it in outlook on XP and kmail in kubuntu
I've set it up in kmail as well (kubuntu/jaunty)

It downloads my Inbox only, sentmail,trash,junkmail and folders I created are ignored.

This used to work better with Outlook Express (DAV) - any ideas what I need to change in config  to sync all folders I got there?

---


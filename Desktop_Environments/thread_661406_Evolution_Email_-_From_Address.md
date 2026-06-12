---
title: "Evolution Email - From Address"
date: 2008-01-07
forum: Desktop Environments
---

### Post by Ubee on 2008-01-07
When I send an email the person receiving it is displayed my name and email address. Like this:

From: Bob Smith (bsmith@cox.com)

I do not want  it to show [email]bsmith@cox.com[/email]. This address is not the reply address I set, which would be fine because that address is [email]Bobby@bigfoot.com[/email]. The bigfoot address is a pointer address and forwards all my mail to the cox.com address. I keep the cox.com address private so that if I change my ISP no one needs to know they just keep sending mail to the bigfoot.com address.

Any idea how to fix this? Thanks Ubee.

---

### Post by kyphi on 2008-01-07
There are two ways of accomplishing your wish.

First, go into Evolution then Edit then Preferences and then Add, to add another account.  Make an account for your bigfoot address.

If you want to send and receive via that account you must have a tick in the box next to that account.  All you have to remember is to go into Edit and then Preferences to enable or to disable whichever account you want to use.

Alternatively, open a Google mail account in which case all your mail addressed to that account goe to your gmail address regardless of which ISP you use.

---

### Post by Ubee on 2008-01-07
I think I see what you mean. The new account would then be the default account used when composing or replying to emails? This new account would never have any mail at it. It aways gets forward to the cox.com account. So I have two accounts, one where I pickup mail cox.com and one that is used as the default account for sending mail and replying to mail? I'll give it a try. Thanks.

---

### Post by kyphi on 2008-01-08
> This new account would never have any mailNo, that is not quite right.  If anyone decided to "Reply to Sender" you would get mail to that account.

---

### Post by bench on 2008-01-08
Go into Evolution and Preferences.  Create a new account.  Set the name and email address to what you want it to be, ie. Bob Smith and [email]bobby@bigfoot.com[/email].  Set the Receiving server type to be "None".  Set the SMTP server to your ISP/your SMTP server, and fill in the correct authentication details if that is necessary (the same as for [email]bsmith@cox.com[/email]).  Apply this.

This "account" will not show in the folder list on the left, but if you open a new email, you will see the account in the "From" drop down.  I think you can set this as the default account in the account setup.

If you send email using this "From" address there is no need for reply-to because it will go out with the name and email address specified in the dummy account settings, and any user who clicks reply will see [email]bobby@bigfoot.com[/email].

Hope it works.

---


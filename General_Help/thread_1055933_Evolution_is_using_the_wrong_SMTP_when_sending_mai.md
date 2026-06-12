---
title: "Evolution is using the wrong SMTP when sending mail"
date: 2009-01-31
forum: General Help
---

### Post by Milleman on 2009-01-31
Hi,

I have a problem with the Evolution Mail client. I have added several different mail accounts to the Evolution. Some accounts are from different mail providers. When downloading mails, everything works fine. I get each and every mail from respective mail provider, right into the inbox.

But when sending, it seems that the Evolution doesn't use the SMTP information that I've entered in each mail account. Seems like it's using the same SMTP for all accounts, regardless what I have entered in the accounts setup.

How do I solve this?

---

### Post by Bigneil on 2009-01-31
I am not an expert, but there is one thing that crosses my mind.
Is there a default account that it reverts to each time you try and send, regardless of which account is currently active?

---

### Post by labinnsw on 2009-01-31
When sending mail, use the from drop down menu to select the account you wish to use. Otherwise the default account will be used.

Sorry, this is not correct. Make sure that none of your accounts is set as default.

Under Edit> Preferences > Mail Accounts, Edit each account by make sure the default mail account check box is unchecked.

---

### Post by Milleman on 2009-01-31
You can select a default account, that will be the preferred account of choice when you compose new mails. I don't know if this also affects the sending of mails and which SMTP settings to be used for all accounts. If it does, it is indeed a flaw.

Using the dropdown list and select an account that uses different SMTP settings, doesn't make any difference. The SMTP settings that will be used, is still not the correct one. It doesn't use the SMTP settings that belongs to the selected account on the dropdown list.

I was hoping that anyone would have the answer...

---

### Post by labinnsw on 2009-01-31
I have edited my post see if that works.

---

### Post by labinnsw on 2009-01-31
On further examination of your last post. It looks like you have a bug which is beyond me.

---

### Post by Milleman on 2009-01-31
A bug that is just specific to me? :)

I'm using 19 different mail accounts. half of them is from one mail provider. The other half from another. It seems like the "default" account does have something to do with it. I have now verified that. Evolution will ALWAYS use the SMTP settings from the default mail account, even if you've selected a different account on the dropdown list, with different SMTP settings. How could that be?

Am I the first person on earth to have experienced this? :)

I'm using Intrepid, installed from the Intrepid installations CD. I have imported my mail and accounts from the earlier Hardy installation, which had the same problems.

---

### Post by labinnsw on 2009-01-31
I have 4 accounts and when replying Ubuntu uses the account that received the mail. On that basis, I believe your system has a bug. I just don't know how to fix it.

If it is any help, the first listed account has "(default)" beside it, but when I checked the Account Editor, the default account check boxes are all clear.

The account with "(default)" beside it is the one that is used when new mail is created, but I can opt to use one of the other accounts.

---

### Post by Milleman on 2009-01-31
Do they use different mail providers (different POP and SMTP settings)?

---

### Post by labinnsw on 2009-01-31
They are all different providers. All different POP and SMTP settings.

---

### Post by Milleman on 2009-02-01
> **labinnsw said:**
> They are all different providers. All different POP and SMTP settings.

Strange indeed. So I got a bug which you don't have. How can that be, if you booth are using the same system and version...? Could it be my accounts that are activating some kind of a residing bug?

What Ubuntu version are you using?

Anyway... I've signed up to the Evolution mailing list, in order to discuss my problems there.

---

### Post by labinnsw on 2009-02-01
What ever the problem is, it seems to be unique to your system. In the past when that has happened to me, (i.e. I have a unique problem) a fresh installation usually solves it.

It might be that in fixing some other problem this one was unwittingly created.

I am still using Hardy.

---

### Post by JueShire on 2009-03-12
I had this problem for many days, but it is NOT one of Evolution, its one of the settings!

Evolution tries to send over SMTP only if the **very** right settings are available.
So it didn't send my gMail-e-mails as long as I only had marked "SSL" or "TLS" in the settings, because the standard port for TLS is 25, and SSL is 465, but smtp.googlemail.com expects TLS ***and*** 465 or 587.
So I tried it with "TLS" and "smtp.googlemail.com:587" and - violá - **it works**!
In another case I simply had a typing error in my password, causing evolution to stop sending over this account.

So my tip: Check your smtp-settings in every detail!

---

### Post by schizoman on 2009-03-16
I'm having the same problem.  I'm guessing this is recent.  Accounts that I added months ago access the correct SMTP server.  Any accounts that I try to add now access the server for my private email account.  Quite annoying.

---

### Post by schizoman on 2009-03-17
Okay, I was having this problem, too.  Only, it turned out not to be a problem.  I visited a blog [here]("http://www.1earthadventures.com/2008/08/02/techie-stuff/evolution-uses-only-default-smtp-server/"), which said that Evolution was lying to me.  Even though Evolution reports that it's trying to contact the default SMTP server, it's actually trying to contact the configured server.

I was being too impatient.  I tried again, and walked away for awhile.  When I came back, Evolution had timed out and reported that it was unable to establish contact with the *configured* server, not the default server.

Contacting the wrong server was not the problem, despite what Evolution was saying.  It turned out that I'd made a mistake in configuring the account.  (In my case, the server in question requires the full email as a user name.)

Hope this helps others.

---

### Post by SabreWolfy on 2010-06-06
> **schizoman said:**
> Okay, I was having this problem, too.  Only, it turned out not to be a problem.  I visited a blog [here]("http://www.1earthadventures.com/2008/08/02/techie-stuff/evolution-uses-only-default-smtp-server/"), which said that Evolution was lying to me.  Even though Evolution reports that it's trying to contact the default SMTP server, it's actually trying to contact the configured server.

I was being too impatient.  I tried again, and walked away for awhile.  When I came back, Evolution had timed out and reported that it was unable to establish contact with the *configured* server, not the default server.

Contacting the wrong server was not the problem, despite what Evolution was saying.  It turned out that I'd made a mistake in configuring the account.  (In my case, the server in question requires the full email as a user name.)

Hope this helps others.

Similar frustrations for me -- thanks for the explanation.

---


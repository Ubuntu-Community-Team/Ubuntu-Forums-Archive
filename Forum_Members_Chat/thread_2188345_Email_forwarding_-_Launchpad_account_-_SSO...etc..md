---
title: "Email forwarding - Launchpad account - SSO...etc."
date: 2013-11-16
forum: Forum Members Chat
---

### Post by NikTh on 2013-11-16
As this is a matter for Ubuntu members only, I raise it up in the Ubuntu Members Area. 

In which e-mail address does the @ubuntu.com alias being forward ? 

As the preferred address in Ubuntu SSO ([https://login.ubuntu.com](https://login.ubuntu.com)) I have the @ubuntu.com alias. I cannot change it, because I will have problems with other Ubuntu related sites with SSO login (like this one). 

As the preferred contact address in launchpad , I have a @gmail.com address. I changed it recently (2-3 hours ago).  
Now, should I expect all the e-mails sent in @ubuntu.com alias to be forwarded in @gmail.com address ? Until now, it's not working. :(

---

### Post by sffvba[e0rt on 2013-11-17
If memory serves this as many other things are run by a script with a set interval... I would give it at least 24h before looking to much deeper.

---

### Post by Elfy on 2013-11-17
> Please note that if your contact address in Launchpad is a GMail address, then you cannot use that specific GMail account to test that forwarding is working. The reason is this pattern looks like an endless loop of e-mails between gmail.com and ubuntu.com; and GMail does not accept these e-mails.

It is a better idea to ask a friend to send you an email to your new address to test it, or use a non-Gmail account to test. 

Do that when you check it.
> 
The script which creates the email aliases runs every 2 days. So please wait at least 48 hours before checking if the email is working (or leave it a couple more days to be sure).

If you change your Launchpad ID or "Contact Address", there will also be up to 48 hour delay until this takes effect. 

and that

---

### Post by coffeecat on 2013-11-17
> **NikTh said:**
> I cannot change it, because I will have problems with other Ubuntu related sites with SSO login (like this one). 

Actually it won't, at least for this site. Once your Ubuntu One account and your forum account are linked you can change emails in either or both such that they don't match and you won't break the link. Email matching is only needed for initial account linking. The only way to disassociate the forum account from your Ubuntu One account is to ask a friendly forum admin to do it!

We like to preserve an air of mystery and clever voodoo in the many Resolution Centre threads about account linking, :wink: but in truth there is simply a hidden field in your profile with a unique openID string.

---

### Post by NikTh on 2013-11-17
Probably is what Elfy said. 
I read the Wiki page [https://wiki.ubuntu.com/UbuntuEmail](https://wiki.ubuntu.com/UbuntuEmail) . I had completely forgotten that this page even exist. 

I have to wait up until 48 hours for the script to run in order to change my settings (maybe little more). Until now isn't working. 
I have subscriptions in some mailing lists with the @ubuntu.com alias and the messages keep coming in old e-mail address. 

As I have understood, the one that matters is the preferred **contact** address in launchpad. It is completely different from the [Ubuntu SSO]("https://login.ubuntu.com") preferred e-mail address.

Thanks for the help.

---


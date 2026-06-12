---
title: "Windows Active Directory Authentication"
date: 2005-12-15
forum: General Help
---

### Post by karlharratt on 2005-12-15
Unfortunately for me, I have always been involved in companies that are Microsoft only environments and I am struggling to get a hold Linux of any flavour.

Although we have some very specific Windows environment packages at the company I currently work for, a good deal of the admin staff use either a Windows 2003 Terminal Server or Citrix environment or use just simple products such as Office, Outlook 2000 (e-mail client to a Windows Exchange Server) and the Internet.

I have been planting the seed that we could save a lot of money by using a Linux solution for our admin staff.

What I need is a solution that has full Active Directory Authentication using a single (at start up logon), where the Authentication will pass through the e-mail client and Firefox for proxy authentication, it will also need an RDP / ICA client to give access to the Terminal Server / Citrix for the applications that can’t (or won’t at the moment) be ported to Linux desktop.

Please reply to [email]karl@harratt.eclipse.co.uk[/email]

---

### Post by amohanty on 2005-12-15
Have you looked at this:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html)

HTH
AM

---

### Post by maphew on 2005-12-22
[https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto)

---

### Post by karlharratt on 2006-01-03
Please help further.

I still have two minor problems.
I have seen various replies for 5.10 but will they also work in 5.04?
What or where is the universal repository?

Karl Harratt
[email]karl@harratt.eclipse.co.uk[/email]

---


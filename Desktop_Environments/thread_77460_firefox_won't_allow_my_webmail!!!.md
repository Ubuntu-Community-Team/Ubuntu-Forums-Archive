---
title: "firefox won't allow my webmail?!!!"
date: 2005-10-16
forum: Desktop Environments
---

### Post by holiday on 2005-10-16
I pick up my isp email over the web. I've been doing this for years. YEARS! 
But now - suddenly - from Firefox I get a dialog saying that firefox and my isp don't share a common encryption algorithm. 

And I can't do anything about it -- except go to my fedora box or boot this laptop into windows.

This is sad

I've posted a previous message about how breezy on my system is falling apart. And I've been advised to blow it all away and re-install. 

I wonder why I would do that. I don't feel like I'm in capable hands. I said before that I think you're going too fast and now I think that even more. 

This isn't good. 

I understand what you're trying to do, but - people, humans... - the QA sucks

---

### Post by dtfinch on 2005-10-16
Just a guess. Go to the url about:config. Search on ssl. Toggle any disabled encryption methods to true. If your ISP only supports 40 bit encryption, which offers almost no protection, that might be the problem. I noticed that some easily breakable methods are disabled by default, to avoid giving users a false sense of security.

---

### Post by mrcbrown on 2005-10-16
[QUOTE=holiday]I pick up my isp email over the web. I've been doing this for years. YEARS! 
But now - suddenly - from Firefox I get a dialog saying that firefox and my isp don't share a common encryption algorithm. 

And I can't do anything about it -- except go to my fedora box or boot this laptop into windows.

This is sad

I've posted a previous message about how breezy on my system is falling apart. And I've been advised to blow it all away and re-install. 

I wonder why I would do that. I don't feel like I'm in capable hands. I said before that I think you're going too fast and now I think that even more. 

This isn't good. 

I understand what you're trying to do, but - people, humans... - the QA sucks[/QUOTE]


What webmail client? I have been using webmail on many computers from Linux->Win->OSX -- no issues with the common one I use:

Squirrelmail
Horde
NeoMail
OpenWebMail
Gmail
Yahoo Mail
MSN Hotmail
V-Webmail

Give me a better idea of what your trying to use, I might be able to give you some assistance as I have done webhosting for a number of years now and have many clients who use Linux/Mac vs. Windows.

---

### Post by mzaz on 2005-10-16
its actually not an ubuntu issue but rather a firefox one. 

You need to goto the address about:config in firefox.

Set these options to true.

security.ssl3.rsa_rc2_40_md5
security.ssl3.rsa_rc4_40_md5

I had the same issue with my providers webmail. (shaw.ca)

---


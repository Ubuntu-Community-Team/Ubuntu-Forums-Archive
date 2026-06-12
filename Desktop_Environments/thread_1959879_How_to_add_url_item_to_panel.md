---
title: "How to add url item to panel"
date: 2012-04-16
forum: Desktop Environments
---

### Post by wah fun on 2012-04-16
Recently I encountered a bit of frustration. I have never had this problem before with any distro. Here it is: because I like a clean desktop, I put my frequently used items in the panel. So, I tried adding the following url info into a launcher and it will not connect to the desired page. I have added other url items to the panel so it must have something to do with this address but I can't figure it out.

[https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%3A%2F%2Fwww.amazon.com%2Fgp%2Fseller-account%2Fmanagement%2Fyour-account.html%3Fie%3DUTF8%26ref_%3Dya_2&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select](https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%3A%2F%2Fwww.amazon.com%2Fgp%2Fseller-account%2Fmanagement%2Fyour-account.html%3Fie%3DUTF8%26ref_%3Dya_2&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select)

I know I can create a url link on the desktop but I don't want to do that. I have searched and haven't found anything to help. So, if you can help with a suggestion on how to resolve this issue only, please post it.

thx

---

### Post by LewisTM on 2012-04-16
Yep, that's a long address.
What command do you use for your launcher?

[FONT="Courier New"]exo-open URL[/FONT] would be the most obvious.
 
The special characters in the address mean that you need to enclose it in "quotes". You could also use a URL shortening service to make it more palatable.

Cheers!

---

### Post by wah fun on 2012-04-16
Thank you. I had tried exo-open with no luck. I also included " around the url and that did not work. So alas, I did the url shortening thing. I am surprised this is an issue with Xfce. Surely since other de's can do this Xfce should be able too. I will keep searching.

thx

---

### Post by Toz on 2012-04-16
This procedure does work in xfce - it works for me. Where did you put the command **exo-open "www.amazon.com"**?

What happens if run the exo-open command in a terminal window?

---

### Post by LewisTM on 2012-04-16
Funny, it works if we paste the command in a run dialog or a terminal but not inside a launcher.
So yes, I would think it's a bug with the Xfce launcher handler.
If I use the launcher command
```
bash -c 'echo "https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%3A%2F%2Fwww.amazon.com%2Fgp%2Fseller-account%2Fmanagement%2Fyour-account.html%3Fie%3DUTF8%26ref_%3Dya_2&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select" > ~/cmd.txt'
```
.. and run it I get cmd.txt with contents:
```
https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=httpsAFFwww.amazon.comFgpFseller-accountFmanagementFyour-account.htmlFieDUTF86ref_Dya_2&openid.mode=checkid_setup&openid.ns=httpAFFspecs.openid.netFauthF2.0&openid.claimed_id=httpAFFspecs.openid.netFauthF2.0Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=httpAFFspecs.openid.netFextensionsFpapeF1.0&openid.identity=httpAFFspecs.openid.netFauthF2.0Fidentifier_select
```
So all % signs have been removed by Xfce. No such thing if the command is run from a terminal.
The solution would be to hide the address inside a script or to shorten it online.

---

### Post by Toz on 2012-04-19
Apparently, if you want to use a % in the launcher exec command, you have to escape it with another % as per the spec here: [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html]("http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html").

Therefore, in your url, add a second % in front of every % and it should work"
```
https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%%3A%%2F%%2Fwww.amazon.com%%2Fgp%%2Fseller-account%%2Fmanagement%%2Fyour-account.html%%3Fie%%3DUTF8%%26ref_%%3Dya_2&openid.mode=checkid_setup&openid.ns=http%%3A%%2F%%2Fspecs.openid.net%%2Fauth%%2F2.0&openid.claimed_id=http%%3A%%2F%%2Fspecs.openid.net%%2Fauth%%2F2.0%%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%%3A%%2F%%2Fspecs.openid.net%%2Fextensions%%2Fpape%%2F1.0&openid.identity=http%%3A%%2F%%2Fspecs.openid.net%%2Fauth%%2F2.0%%2Fidentifier_select
```.

Or, use the suggestions that LewisTM notes above.

---

### Post by jefsview on 2012-04-19
XFCE does have a launcher specifically for opening favorite websites.

Xfce-smartbookmark-plugin

--jeff

---


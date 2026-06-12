---
title: "jUploadr authorization problem"
date: 2007-02-09
forum: Desktop Environments
---

### Post by mr91nk on 2007-02-09
Hi,

I have a problem authorizing myself to use jUploadr with flickr.com. I managed well doing the same operation on an XP machine, but in Edgy I don't get it to work. The problem is that when I chose "Authorize" in XP, a browser window opened, but in Edgy it doesn't... I just get the window saying "Once you're done, Click the 'Complete authorization' button...".

Anyone? Thanks... :)

---

### Post by mr91nk on 2007-02-17
Hmm... Not much of support for a newbie. :p But well, I'm not giving up that fast. Since last time, I noticed some things going on in the terminal window, while trying to authorize jUploadr (had smth else covering the terminal window; yep, told ya i'm a noob... ;)). Anyway, when selecting "Authorize jUploadr" in the Preferences, the following appears in the terminal window, while the authorization dialog box opens:```
WARNING: Cookie rejected: "$Version=0; use_master_until=1171763195; $Domain=flickr.com; $Path=/". Domain attribute "flickr.com" violates RFC 2109: domain must start with a dot
<?xml version="1.0" encoding="utf-8" ?>
<rsp stat="ok">
<frob>7207764-0bf72ecfdb8d18b2</frob>
</rsp>

```Then I click "Authorize" and this is where a browser window should open, but apparently it doesn't. Instead I just the "Complete authorization" dialog box in jUploadr, and when clicking "Complete authorization", I get a "Authorization failed" message and the following appears in the terminal window:```
<?xml version="1.0" encoding="utf-8" ?>
<rsp stat="fail">
        <err code="108" msg="Invalid frob" />
</rsp>

```So, another cry for help... :) Thanks!!

---

### Post by moschops on 2007-05-09
Same problem here - and similar spew in the shell window.  

According to [http://juploadr.org/2006/04/17/authorization-failed/]("http://juploadr.org/2006/04/17/authorization-failed/") there is no fix yet.  All I can think of is that if you can get access to a Windows PC with Java installed then you can run jUploadr there and authorize it for you account and then it should work from Linux...

---

### Post by moschops on 2007-05-09
I also found info on the Flickr API pages and tried to follow the instructions on how to create the sign page URL so I could manually visit it with Firefox...

[http://www.flickr.com/services/api/auth.howto.desktop.html](http://www.flickr.com/services/api/auth.howto.desktop.html)

As best I could tell I should use something like:

[http://flickr.com/services/auth/?api_key=1892f5f9d32f01b86f53b50cdac89c8c&perms=write&frob=72157600198596501-073bf38b1251597d&api_sig=40e47e590d1ada52c8f747f514038826](http://flickr.com/services/auth/?api_key=1892f5f9d32f01b86f53b50cdac89c8c&perms=write&frob=72157600198596501-073bf38b1251597d&api_sig=40e47e590d1ada52c8f747f514038826)

Where the "frob" param value is whatever came back from Flickr after the initial flick "getFrob" request - it is displayed in the command window spew (and I snooped with Wireshark).  However when I visit that URL Flickr comes back with "Oops! The API key or signature is invalid." so I guess there must be some other problem.

---


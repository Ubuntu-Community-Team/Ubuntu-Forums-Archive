---
title: "DarkLooks, firefox, blogger.com"
date: 2010-08-02
forum: Desktop Environments
---

### Post by misha680 on 2010-08-02
Dear All:

Simple question, I'm using DarkLooks and am having a problem with some forms, esp on blogger.com.

The text is unreadable (see attachment).

Is there an easy way to fix? e.g., disabling CSS for one site?

Thank you
Misha

---

### Post by misha680 on 2010-08-07
Here is a hack.

Download Greasemonkey
[https://addons.mozilla.org/en-US/firefox/addon/748/](https://addons.mozilla.org/en-US/firefox/addon/748/)

Restart firefox

Tools->Greasemonkey->New User Script...

Name: blogger.com for DarkLooks
Namespace: [http://userscripts.org/users/useridnumber](http://userscripts.org/users/useridnumber)
(replace with your useridnumber if you have one; or just use
some test URL if not sharing)
Includes: [http://*.blogger.com/*](http://*.blogger.com/*)

Leave rest blank.

OK

Copy and paste following below header that appears in your favorite editor (I recommend typing in /usr/bin/gedit if you have not yet selected an editor when asked):
```


// based on http://userscripts.org/scripts/show/36850

GM_addStyle("input { background-color: white !important; }");
GM_addStyle("input { font-family: ; font-size: ; color: black !important; }");
GM_addStyle("textarea { background-color: white !important; }");
GM_addStyle("textarea { color: black; font-family: ; font-size:  !important; }");
GM_addStyle("option { background-color: white !important; }");
GM_addStyle("option { color: black; font-family: ; font-size:  !important; }");
GM_addStyle("select { background-color: white !important; }");
GM_addStyle("select { color: black; font-family: ; font-size:  !important; }");
GM_addStyle("button { background-color: white !important; }");
GM_addStyle("button { color: black; font-family: ; font-size:  !important; }");

```

File->Save, File->Quit if using gedit.

Now go to editing your blogger.com post (Reload if necessary) and you should have nice forms (see screenshot).

Thank you!

Misha

---


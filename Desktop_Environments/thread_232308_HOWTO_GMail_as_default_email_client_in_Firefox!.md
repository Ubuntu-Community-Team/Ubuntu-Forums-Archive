---
title: "HOWTO: GMail as default email client in Firefox!"
date: 2006-08-08
forum: Desktop Environments
---

### Post by PWill on 2006-08-08
EDIT: [B]I am working on systemwide support for email links. As for now, if you go to Sys > Prefs > Prefered Apps and for email, select custom, and enter this command: ```
firefox -remote "openurl(https://mail.google.com/mail/?view=cm&fs=1&to=%s)"
```
it will load the address in GMail, but the problem is it keeps the "mailto:" part attched. I am trying to squash this problem, but not having much luck :mad:[/B]

I have always wanted GMail to be my default email client, because I hate having to load thunderbird when I click on a mailto: link.
TO do this, you will need to install Google's Toolbar for Firefox.

[Google Toolbar for Firefox]("http://tools.google.com/firefox/toolbar/install.html")

After you install it, you can remove it from the main bar in Firefox by right clicking, and clicking "Customize..." or un-ticking "Google Toolbar"
You can make your Firefox tolbar much smaller by customizing it, like I did here:
[IMG]http://img304.imageshack.us/img304/6323/toolbarcustomfk2.png[/IMG]

Next, go to the Google Toolbar preferences menu. You can get to it by going to Tools > Extensions > Google Toolbar and clicking on "Preferences"

In the "Browsing" tab, go to the bottom, and tick "Send with GMail" and now when you click email links, they will open up right in GMail.

Test it out right here: [email me]("mailto:xiamcitizen@gmail.com")

If you don't have a gmail account, and would like one, email me at xiamcitizen (at) gmail (dot) com

---


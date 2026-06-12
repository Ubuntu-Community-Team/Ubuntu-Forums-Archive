---
title: "Native notifications for Office 365 webmail events"
date: 2012-11-08
forum: Desktop Environments
---

### Post by eugen_nicoara on 2012-11-08
My company uses Office 365. I did some research and it looks like there's no way to configure Evolution with Office 365 so I have to use webmail.

The only thing that bothers me is that the notifications (e.g. calendar notification for meeting) are not visible outside that particular browser tab where the webmail page is opened. I've found [this]("https://chrome.google.com/webstore/detail/dbmjjjonelodfeckmpfglmffhngdplal") Chrome/Chromium extension and [this]("http://code.google.com/p/ff-html5notifications/") Firefox add-on that should integrate browser events with desktop notifications but none of them work for me.

Does anybody have a solution to this problem?
Thanks!

Tip: If you want to the same experience on Office 365 webmail with Chrome as with Firefox try this:
```
/opt/google/chrome/google-chrome --user-agent="Mozilla/5.0 (Windows NT 6.0; WOW64) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.16 Safari/534.24" --enable-plugins %U
```

---


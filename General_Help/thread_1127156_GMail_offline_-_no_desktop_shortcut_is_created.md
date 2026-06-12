---
title: "GMail offline - no desktop shortcut is created"
date: 2009-04-16
forum: General Help
---

### Post by m4lte on 2009-04-16
I decided to give a try to the GMail offline feature available in the labs. However no desktop shortcut for GMail is created. When I go to >Settings >Offline and click on 'create a desktop shorcut', a message pops up asking for confirmation but **no shortcut is being created**.
Creating a shortcut for offline access to Google Calendars works without any problems.

Any ideas what might be the problem?
Could it be because I'm in Germany and there are some issues with the gmail domain which is called googlemail here?


Edit:
Also if I just open Firefox and go to 'http://mail.google.com/' while offline, no page is loaded from the local cache.

---

### Post by OrangeMediumGreen on 2009-04-29
Have the same problem here...

Offline access is possible though: Try "https://".

---

### Post by selinium on 2009-05-19
I had the same issue, maybe because I am using the 64bit version of gears, anyway...

I created a Desktop.shortcut file with the following info...

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Type=Application
Version=1.0
Name=Gmail
Icon=/home/james/.mozilla/firefox/7bhmcwv1.default/Google Gears for Firefox/mail.google.com/http_80/GoogleMail@minniebusiness.co.uk_managed[12]%23localserver/gmail_icon[4407].png
Exec="/usr/bin/firefox" "https://mail.google.com/mail/"
```

You will need to change the default to your own.

Basically I believe you need the /mail/ following the [https://mail.google.com](https://mail.google.com)

Hope this helps

---


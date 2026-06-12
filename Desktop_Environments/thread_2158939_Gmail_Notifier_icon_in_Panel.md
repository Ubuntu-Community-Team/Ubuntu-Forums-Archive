---
title: "Gmail Notifier icon in Panel"
date: 2013-07-01
forum: Desktop Environments
---

### Post by sf84 on 2013-07-01
Hello. I have just installed Gmail Notifier (gm-notify).
I get only the alter bubble but not the icon in the Panel.

Any advice ?

Thanks

---

### Post by Frogs Hair on 2013-07-01
The program description indicates it uses notify osd (alert bubble) and the indicator-applet. (vague) Is there a menu entry for the program ? I ask because sometimes show-icon is in preferences in programs that use the panel. I see two other notifiers for Gmail, but I am on Ubuntu.

---

### Post by mc4man on 2013-07-01
gm-notify hasn't been updated since 11.10 (quantal) & even there it's broken for new messaging menu. So I'd say it's no longer of much use except for the osd pop ups.
[https://bugs.launchpad.net/ubuntu/+source/gm-notify/+bug/1040259](https://bugs.launchpad.net/ubuntu/+source/gm-notify/+bug/1040259)

Here I use unity-mail, both for online & thru thunderbird access to gmail. (doesn't seem to do osd or do osd very well but the indicator, ect. work fine.

---

### Post by sf84 on 2013-07-01
Thanks for your replies. gm-notify has a preference menu but there is no such option.

I solved using Gmail Notifier (gmail-notify 1.6.1.1-2) and it works fine.

---

### Post by markbl on 2013-07-01
> **sf84 said:**
> 
I solved using Gmail Notifier (gmail-notify 1.6.1.1-2) and it works fine.
Unlike gm-notify which implements push notification, gmail-notify only checks for new mail periodically.

FYI, I implemented my own very basic [gmail indicator](https://github.com/bulletmark/gmail-indicator) which uses push notification and works on Ubuntu 13.04. Very lightweight though and does not provide a gui.

---

### Post by kennerc on 2013-07-02
> **mc4man said:**
> gm-notify hasn't been updated since 11.10 (quantal) & even there it's broken for new messaging menu. So I'd say it's no longer of much use except for the osd pop ups.
[https://bugs.launchpad.net/ubuntu/+source/gm-notify/+bug/1040259](https://bugs.launchpad.net/ubuntu/+source/gm-notify/+bug/1040259)

Here I use unity-mail, both for online & thru thunderbird access to gmail. (doesn't seem to do osd or do osd very well but the indicator, ect. work fine.

I din't knew about unity-mail, so I decided to check.
Just amazing!

---

### Post by JonPaul on 2013-10-03
> **markbl said:**
> Unlike gm-notify which implements push notification, gmail-notify only checks for new mail periodically.

FYI, I implemented my own very basic [gmail indicator]("https://github.com/bulletmark/gmail-indicator") which uses push notification and works on Ubuntu 13.04. Very lightweight though and does not provide a gui.

Thanks for this indicator. This works for me):P

---

### Post by Aaruni on 2014-04-20
I just installed the notifier from github, and I get the notify bubble, but it still doesn't show up in my messaging applet.

---

### Post by Aaruni on 2014-04-20
update : I have no idea how/why but it suddently started working.

Thanks! :)

---

### Post by searchtheskies on 2014-09-01
> **mc4man said:**
> gm-notify hasn't been updated since 11.10 (quantal) & even there it's broken for new messaging menu. So I'd say it's no longer of much use except for the osd pop ups.
[https://bugs.launchpad.net/ubuntu/+source/gm-notify/+bug/1040259](https://bugs.launchpad.net/ubuntu/+source/gm-notify/+bug/1040259)

Here I use unity-mail, both for online & thru thunderbird access to gmail. (doesn't seem to do osd or do osd very well but the indicator, ect. work fine.

Awesome! Works fantastic for Gmail account. I tried every other notifier in the repos; nothing comes close to this. Thank you!

---


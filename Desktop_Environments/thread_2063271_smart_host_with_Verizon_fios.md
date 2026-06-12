---
title: "smart host with Verizon fios"
date: 2012-09-26
forum: Desktop Environments
---

### Post by andrewjs18 on 2012-09-26
has anyone successfully set up a smart host using postix with their ISP being Verizon?

I used [this guide]("http://ubuntuforums.org/showpost.php?p=6348180&postcount=2") and everything seems to be ok, as far as the configuration is concerned, per the aforementioned guide (I think), but it doesn't seem to be sending out emails.

Here's the contents of my mail.log file:

```

Sep 26 13:30:03 web-server postfix/pickup[19169]: 15FCF348C12E: uid=1001 from=<Lee>
Sep 26 13:30:03 web-server postfix/cleanup[20490]: 15FCF348C12E: message-id=<20120926173003.15FCF348C12E@web-server>
Sep 26 13:30:03 web-server postfix/qmgr[20685]: 15FCF348C12E: from=<Lee@mail.removed.com>, size=342, nrcpt=1 (queue acti$
Sep 26 13:30:03 web-server postfix/smtp[20492]: CLIENT wrappermode (port smtps/465) is unimplemented
Sep 26 13:30:03 web-server postfix/smtp[20492]: instead, send to (port submission/587) with STARTTLS
Sep 26 13:30:55 web-server postfix/pickup[19169]: AAC0E348C12F: uid=1001 from=<Lee>
Sep 26 13:30:55 web-server postfix/cleanup[20490]: AAC0E348C12F: message-id=<20120926173055.AAC0E348C12F@web-server>
Sep 26 13:30:55 web-server postfix/qmgr[20685]: AAC0E348C12F: from=<Lee@mail.removed.com>, size=344, nrcpt=1 (queue acti$
Sep 26 13:30:55 web-server postfix/smtp[20511]: CLIENT wrappermode (port smtps/465) is unimplemented
Sep 26 13:30:55 web-server postfix/smtp[20511]: instead, send to (port submission/587) with STARTTLS

```any help would be greatly appreciated!

---


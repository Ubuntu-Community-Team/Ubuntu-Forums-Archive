---
title: "Cannot send email with attachment"
date: 2009-07-09
forum: Desktop Environments
---

### Post by Tech4Law on 2009-07-09
After updating as recommended by the update manager two days ago, I cannot seem to send any attachments - no wrong a .doc and a .org file did go through although very small.

I use Evolution, but also tried Thunderbird with the same result. Tried different SMTP servers, same result.

When I track with CAMEL_DEBUG, I get this (extract) 

< b34fcb90 >
restoring draft flag 'text/html'
CamelException.setv((nil), 2, 'Host lookup failed: malcolm-laptop: Name or service not known')
Thread b34fcb90 >
CamelFolder:get_message('Outbox', '80') =
class: CamelMimeMessage
mime-type: multipart/mixed; boundary="=-i16lIuF8meogbHY762MX"
content class: CamelMultipart
content mime-type: multipart/mixed; boundary="=-i16lIuF8meogbHY762MX"
  class: CamelMimePart
  mime-type: multipart/related; type="multipart/alternative";
	boundary="=-KOI2pzm7ei+hNiAhiHad"
  content class: CamelMultipart
  content mime-type: multipart/related; type="multipart/alternative";
	boundary="=-KOI2pzm7ei+hNiAhiHad"
    class: CamelMimePart
    mime-type: multipart/alternative; boundary="=-xbb8C6IFtn14zy6YyGD+"
    content class: CamelMultipart
    content mime-type: multipart/alternative; boundary="=-xbb8C6IFtn14zy6YyGD+"
      class: CamelMimePart
      mime-type: text/plain
      content class: CamelDataWrapper
      content mime-type: text/plain
      class: CamelMimePart
      mime-type: text/html; charset=utf-8
      content class: CamelDataWrapper
      content mime-type: text/html; charset=utf-8
    class: CamelMimePart
    mime-type: image/jpeg; name=tech4lawsignature.jpg
    content class: CamelDataWrapper
    content mime-type: image/jpeg; name=tech4lawsignature.jpg
  class: CamelMimePart
  mime-type: application/pdf; name=279days.pdf
  content class: CamelDataWrapper
  content mime-type: application/pdf; name=279days.pdf
< b34fcb90 >
CamelException.setv(0xb34fc26c, 2, 'DATA command failed: Connection timed out: mail not sent')
Thread b34fcb90 >
CamelFolder:get_message('Outbox', '84') =
class: CamelMimeMessage
mime-type: multipart/mixed; boundary="=-LR2FEcZPVyA76DCtY+hX"
content class: CamelMultipart
content mime-type: multipart/mixed; boundary="=-LR2FEcZPVyA76DCtY+hX"
  class: CamelMimePart
  mime-type: multipart/related; type="multipart/alternative";
	boundary="=-K2Ay0mXsOw0EAOkUTOpt"
  content class: CamelMultipart
  content mime-type: multipart/related; type="multipart/alternative";
	boundary="=-K2Ay0mXsOw0EAOkUTOpt"
    class: CamelMimePart
    mime-type: multipart/alternative; boundary="=-RS9GuaH9K6QBgRmRzsuD"
    content class: CamelMultipart
    content mime-type: multipart/alternative; boundary="=-RS9GuaH9K6QBgRmRzsuD"
      class: CamelMimePart
      mime-type: text/plain
      content class: CamelDataWrapper
      content mime-type: text/plain
      class: CamelMimePart
      mime-type: text/html; charset=utf-8
      content class: CamelDataWrapper
      content mime-type: text/html; charset=utf-8
    class: CamelMimePart
    mime-type: image/jpeg; name=tech4lawsignature.jpg
    content class: CamelDataWrapper
    content mime-type: image/jpeg; name=tech4lawsignature.jpg
  class: CamelMimePart
  mime-type: video/x-ms-wmv; name="Golf Betrayal.wmv"
  content class: CamelDataWrapper
  content mime-type: video/x-ms-wmv; name="Golf Betrayal.wmv"
< b34fcb90 >
CamelException.setv(0xb34fc26c, 2, 'DATA command failed: Connection timed out: mail not sent')
CamelException.setv(0x8a85fa4, 2, 'DATA command failed: Connection timed out: mail not sent

DATA command failed: Connection timed out: mail not sent')
Thread b34fcb90 >
CamelFolder:get_message('Outbox', '100') =
class: sending : EHLO [192.168.0.14]

received: 250-mr.bones.co.za
received: 250-PIPELINING
received: 250-SIZE 10240000
received: 250-VRFY
received: 250-ETRN
received: 250 8BITMIME
sending : MAIL FROM:<malcolm@bones.co.za>

received: 250 Ok
sending : RCPT TO:<manuela@ourcottage.co.za>

received: 250 Ok
sending : DATA

received: 354 End data with <CR><LF>.<CR><LF>
sending : A00007 NOOP

received: A00007 OK Success

sending : A00008 NOOP

received: A00008 OK Success



I have reinstalled all the Evolution files, and now don't know where to turn, what else can I try? Two days now and I need to get on with work.

Must appreciate any advice.

Malcolm

---

### Post by Tech4Law on 2009-07-09
I get the error after trying to send that says:

DATA command failed: Connection timed out: mail not sent

DATA command failed: Connection timed out: mail not sent

---

### Post by Tech4Law on 2009-07-10
Please guys I am lost here - I really need some help.):P

---

### Post by jamesesw on 2009-07-15
I'm now having the exact same problem, it's driving me crazy trying to find an answer.  I can only sen plain text attachments, nothing else - however small.  I also have tried two different SMPT servers.

Please help, thank-you, James

ubuntu 9.04
evolution 2.26.1

---

### Post by jamesesw on 2009-07-16
Solved it! After nearly a day of searching - my MTU setting was wrong - changing it in my router to 1458 has solved all my problems.  The setting in Ubuntu (System -> Prefs -> Network Pref was (and still is Auto) I'm suspecting in the past there was a lower entry - which guided my router......

Good luck. James

---

### Post by COVERTALIBI on 2009-07-16
I was able to fix the problem by just simply resetting my modem, router and conducting a restart. Seems to simple to be true. I can't imaging how that came to be.:confused:

That's the second time that this has happened this week. Weird.

Covert
_____________________________
[www.CovertAlibi.com]("http://www.CovertAlibi.com")
[www.AlibiHQ.com]("http://www.AlibiHQ.com")
[www.AbsoluteAlibis.com]("http://www.AbsoluteAlibis.com")

---


---
title: "firefox, gmail: how to block images from incredimail?"
date: 2009-03-09
forum: General Help
---

### Post by sanderj on 2009-03-09
<warning: not very ubuntu-related ;-) >

Is there any way to block the links and images from "incredimail"?

Setup: firefox and gmail on Ubuntu. A certain person mailing me always has the annoying incredimail 'signature' in their mail. I want to get rid of those signatures.

First try: right click in firefox, and then Block Images From. However, this does not work, as the images are embedded in the mail and are from ... mail.google.com.

The text (in Dutch) is:

"GRATIS animaties voor je e-mail - van IncrediMail! Klik hier!"

The HTML source is:

```
<img alt="GRATIS animaties voor je e-mail - van IncrediMail! Klik hier!" src="?ui=2&amp;ik=5057faba16&amp;view=att&amp;th=11fecce33525f7ca&amp;attid=0.2&amp;disp=emb&amp;zw" border="0">
```

Tips how to get rid of this?

---

### Post by Nano_ext3 on 2009-03-09
You could try installing the firefox addon "Ad-Block Plus" to firefox.  Google search "adblock plus firefox adddon,"  Other than that , there are settings in gmail to adjust junk and image control.  Setting an image as junk would do it, but Im guessing you do not want to do that.

Cheers!

-Nano

---

### Post by sanderj on 2009-03-10
I already use ABP, but I can't find a filter / description to filter out incredimail as the image is coming from mail.google.com ...

---

### Post by Nano_ext3 on 2009-03-10
Any email I receive on gmail, does not load any images until I click the button to do so.  I looked through the settings of gmail and found no settings to alter this.  I am wondering if this is an antivirus problem or not.  I wont stop looking for an answer for you, give me some time.

Cheers

-Nano

---

### Post by sanderj on 2009-03-10
Yeah, strange: in normal mails, the images are detected as 'external', and gmail will say something like:

> Images are not displayed.
Display images below - Always display images from [email]nieuwsbrief@cheaptickets.nl[/email]

However, not with the incredimail junk. Well, that's what I think.

---

### Post by Nano_ext3 on 2009-03-10
What you could do is make a filter in Gmail's settings, located in the upper right hand corner.  And create a filter based upon that persons or companies email address, this will auto-label the emails received from that person as "junk" and you can always unmark it as junk. I believe "junk" emails never have images loaded for safety reasons

Cheers!

-Nano

---

### Post by sanderj on 2009-03-10
Thanks. However: That would block all mails from that person, and I only want to block the built-in images...

---

### Post by sanderj on 2009-03-10
I've included the properties of the incredimail-image...

---

### Post by sanderj on 2009-03-11
FWIW: Gmail gives a method to NOT display messages anymore:

> If you choose to always display images from a particular sender, you can disable this functionality at any time by following these steps:

   1. Sign in to Gmail.
   2. Open the message.
   3. Click show details at the top of the message pane.
   4. Click Don't display from now on.

However, this works for a lot of (normal) mails / mail senders, but not for this person sending incredimail in their message. Reason, as said: those images appear to come from gmail itself, not external sites. Probably some other way of encoding images ... :-(

Very annoying.

---

### Post by crokett on 2009-03-11
> **sanderj said:**
> Thanks. However: That would block all mails from that person, and I only want to block the built-in images...

Don't make this your problem. Unless you work for this person I would say to them that you have tried blocking the images but are unsuccessful and if they persist in sending them to you then you will automatically dump their messages to the bit bucket in the sky until they stop. If they get annoyed and stop sending you email, problem solved.  If they take the annoying signature out, problem solved.

---


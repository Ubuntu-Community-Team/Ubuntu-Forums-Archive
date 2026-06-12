---
title: "HTML mail normal text in Evolution"
date: 2009-09-28
forum: Desktop Environments
---

### Post by jruden on 2009-09-28
I want to know:

Is there a way to make Evolution use a Times New Roman alike font for showing the "normal" paragraph style (the default text when editing a HTML mail)?

Many mail clients use this (including for example Thunderbird in Ubuntu and Outlook in Windows XP).

I would be more comfortable knowing that what I see while composing the mail is approximately what the Windows community will see when reading it.

Having browsed around in the basic configuration settings in Evolution I have been unable to find this type of setting (ie ~"compose html mail normal style font").

Anyone who knows a trick or have a suggestion for me (other than changing to another mail client...)?

Help appreciated.

---

### Post by SoftPops on 2009-10-09
The default font in Evolution can be changed by selecting "edit", "preferences", "mail preferences" and then the "general" tab. Unchecking the "use the same fonts as other applications" allows the default to be changed.
 
Unfortunately, there does not seem to be a "times new roman" font listed.
 
I have just been setting up a default signature block within Evolution and am quite disappointed with the list of available fonts.
 
Don't suppose anyone knows where to find more fonts (especially ones that will be more compatible with Windows users/systems)???

---

### Post by jruden on 2009-10-12
> **SoftPops said:**
> The default font in Evolution can be changed by selecting "edit", "preferences", "mail preferences" and then the "general" tab. Unchecking the "use the same fonts as other applications" allows the default to be changed.

Oh my god, totally missed it! Thanks a bunch for the help :-\"

---

### Post by mcduck on 2009-10-12
> **SoftPops said:**
> The default font in Evolution can be changed by selecting "edit", "preferences", "mail preferences" and then the "general" tab. Unchecking the "use the same fonts as other applications" allows the default to be changed.
 
Unfortunately, there does not seem to be a "times new roman" font listed.
 
I have just been setting up a default signature block within Evolution and am quite disappointed with the list of available fonts.
 
Don't suppose anyone knows where to find more fonts (especially ones that will be more compatible with Windows users/systems)???

Install the "msttcorefonts"-package. And of course Ubuntu uses exactly the same TTF fonts as other operating systems do, so you can get new fonts the very same way (and even copy your fonts from Windows/OSX to Ubuntu).

Still, e-mail really isn't a protocol where you should rely on fonts since in the end what the receiver sees depends on *he's* fonts and settings (and those settings will always override whatever you use even if you send HTML formated e-mail). In almost all cases simply using the plain text format gives best results.

---

### Post by SoftPops on 2009-10-14
> **mcduck said:**
> Still, e-mail really isn't a protocol where you should rely on fonts since in the end what the receiver sees depends on *he's* fonts and settings (and those settings will always override whatever you use even if you send HTML formated e-mail). In almost all cases simply using the plain text format gives best results.
 
Thanks mcduck. After many years in IT support I still find holes in my knowledge. I must admit I thought the e-mail was delivered "as written" (i.e. basic font information went with it). :oops: Oops - some of the e-mails I've sent over the years must have looked pretty naff.

---

### Post by mcduck on 2009-10-14
> **SoftPops said:**
> Thanks mcduck. After many years in IT support I still find holes in my knowledge. I must admit I thought the e-mail was delivered "as written" (i.e. basic font information went with it). :oops: Oops - some of the e-mails I've sent over the years must have looked pretty naff.

If you send your mail in HTML format, then the information about font of course goes with the mail. The fonts themselves don't. So the receiver must have the exact same fonts installed, and even then any settings the receiver has made in his e-mail client will override whatever you have defined in your mail. So the formatting you do in HTML e-mails is actually just a suggestion, not something that you could rely on.

And, in the end, many people disable HTML mails completely and just view all mail as plain text. Or use e-mail clients that don't even support HTML formatting. So all your mails should be readable in plain text, and HTML formatting should be considered as extra feature that might or might not work like you wanted it to.

Still, that doesn't mean that you couldn't use HTML mails at all, just that the receiver usually doesn't see them exactly as you formatted them. But as long as the receiver allows HTML mails the basic stuff still works, like defining headers and italic/bold text etc, things that don't depend on having the same fonts installed and don't break the message too badly if its viewed with all formatting disabled.

(I never send HTML mail, and always set my mail clients to view mail as plain text. If I want to send nicely formatted stuff I create a PDF document and send that as attachment. PDF's look the same regardless of the system you use to view them and also allow embedding the fonts used in the document.)

---


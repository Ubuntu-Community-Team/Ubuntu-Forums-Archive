---
title: "Outlook 2003 .pst import"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Philipp Gérard on 2005-04-09
Hi everybody,

before finally moving to Linux I used Windows XP Pro and Office 2003, i.e. Outlook _2003._ Now all my e-mails are stored within this .pst-file and I did not find any way to import them to Evolution. Can someone help me with this? I know the Windows-Mozilla-Copy-To-Linux-Mozilla-Workaround and think it's far too complicated to first (re)install windows to import my mail. If Mozilla-Windows can handly .pst-files Linux should, too. And *readpst* does not work with Outlook 2003 pst-files.  :) 

Thanks for your help!

Best wishes,
Philipp

---

### Post by jery_wang2002 on 2005-04-09
[QUOTE=Philipp Gérard]Hi everybody,

before finally moving to Linux I used Windows XP Pro and Office 2003, i.e. Outlook _2003._ Now all my e-mails are stored within this .pst-file and I did not find any way to import them to Evolution. Can someone help me with this? I know the Windows-Mozilla-Copy-To-Linux-Mozilla-Workaround and think it's far too complicated to first (re)install windows to import my mail. If Mozilla-Windows can handly .pst-files Linux should, too. And *readpst* does not work with Outlook 2003 pst-files.  :) 

Thanks for your help!

Best wishes,
Philipp[/QUOTE]

I had similar problem and I have spent considerable time in trying to find out what software/app can do the job. Finally, I just forward all emails in outlook.pst to another email account and download them to my thunderbird through pop3. And all your emails date becomes the date whenyou migrate.

Outlook uses its proprietary format and it's stored in MAPI format. You need to program a special reader in VB to run through the message store and store it in any format you want. A lot of coding. 

I could not find any decend exporter of Outlook.pst to MIME message. If therer is, let us know. I would like to use that too.

---

### Post by Philipp Gérard on 2005-04-10
[QUOTE=jery_wang2002]I had similar problem and I have spent considerable time in trying to find out what software/app can do the job. Finally, I just forward all emails in outlook.pst to another email account and download them to my thunderbird through pop3. And all your emails date becomes the date whenyou migrate.

Outlook uses its proprietary format and it's stored in MAPI format. You need to program a special reader in VB to run through the message store and store it in any format you want. A lot of coding. 

I could not find any decend exporter of Outlook.pst to MIME message. If therer is, let us know. I would like to use that too.[/QUOTE]
 Redirecting all emails isn't really a good solution. It's important for me to know the original date so that I can search for emails from a specific day or order them by date. Come on, thousands of people migrate from Windows to Linux, there have to be some who use Outlook 2003 and need their mails. Help! :)

---

### Post by odyssey on 2005-04-28
I believe you're looking for this: [http://www.neotek.hu/en/o2e_en.html](http://www.neotek.hu/en/o2e_en.html)

Works like a charm.

---


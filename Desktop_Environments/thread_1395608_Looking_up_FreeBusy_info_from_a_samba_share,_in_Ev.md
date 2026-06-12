---
title: "Looking up Free/Busy info from a samba share, in Evolution"
date: 2010-02-01
forum: Desktop Environments
---

### Post by ironblade on 2010-02-01
Hi all,

I'm hoping someone has this 'just right' and can tell me what the magic is, as my Google-Fu is failing me at this point.

I've set up Evolution to publish my Free/Busy info to a smb share on our intranet server, using a publishing location in the format:
smb://<username>@server/smbfolder/subfolder/user.name.vfb

That part work fine, my info gets published every day (and I got an annoying OK button to click confirming it).

The part that isn't working is when I try to READ other people's Free/Busy from that same share location.

There's no wizard to generate the read location (like the publishing wizard), so I've tried copying the format and substituting in the %u for username, as noted on the Free/Busy tab.
So, my "template" string is:
smb://domain_name;username@server/smbfolder/subfolder/%u.vfb
I have also tried without the domain_name.

Anyone have a solution as to what the magic string is supposed to be?

Thanks in advance!

---


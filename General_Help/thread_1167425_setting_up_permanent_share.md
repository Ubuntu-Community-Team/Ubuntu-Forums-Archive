---
title: "setting up permanent share"
date: 2009-05-22
forum: General Help
---

### Post by Stolea on 2009-05-22
I run two computers that are networked. #1 computer is a Ubuntu machine and #2 has both WinXp and Ubuntu.
For most time the #2 computer is in Winxp as it runs my accounts program. I have successfully permanently mounted one of the WinXp's drives on the #1 computer as that drive is also home to my Thunderbird emails and music files that both computers share.
I would like to be able to have access to and permanently mount that same drive when #2 computer is in Ubuntu.
Can someone please shed some light on this or tell me where to read up on the relevant information
Cheers

---

### Post by asmoore82 on 2009-05-22
If I follow correctly, you want the Ubuntu side computer #2 to have access to the WinXP side on the same Computer #2.

Is this correct?

---

### Post by Stolea on 2009-05-22
No.
When #2 computer is in Ubuntu mode, the partition that holds the Thiunderbird and music files is mounted as /windows on that computer.
I want to have access to and automatically mount that /windows folder on the #1 computer when #2 runs in Ubuntu mode.

---

### Post by asmoore82 on 2009-05-22
Ahh I see! now that's a challenge ;).

I can't believe I'm typing this, but I believe that this is the only situation where
I would ever condone the use of Samba for Linux-to-Linux file sharing.

That way the configuration on Computer #1 could stay streamlined,
with it always expecting Computer #2 to provide a "Windows Share."
I'll leave the task of "Howto setup a samba server on Ubuntu desktop" to more qualified men...

anyone?

---

### Post by Stolea on 2009-05-22
OK, so there is no qualified man. So, how about a qualified woman? :)Anyone??

---


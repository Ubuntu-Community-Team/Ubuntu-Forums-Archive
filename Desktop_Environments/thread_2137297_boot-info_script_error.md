---
title: "boot-info script error"
date: 2013-04-20
forum: Desktop Environments
---

### Post by afhx on 2013-04-20
I have been having boot-up problems. When running boot-info scripts repeatedly over a period I get the following message at the end of the script. I would be grateful if someone could enlighten me about its content and how to solve it..The message is:
unlzma(stdin): compressed data is corrupt

---

### Post by oldfred on 2013-04-20
I think I have seen that error, but is did not make any difference on at least some systems. I think I assumed it was unlzma issue.

Do you get a link to BootInfo report. If so post the link. 

I thought boot repair auto added any packages it needs, but it runs bootinfoscript and there was some discussion in changes to boot script that some systems did not have all the needed packages.

What happens if you run this?
 sudo apt-get install xz-utils

---

### Post by afhx on 2013-04-23
Thank you for replying. I  don't have continuous  broadband connection but  will try it when I am   pay a month's rent on my dongle.

---

### Post by afhx on 2013-05-03
sudo apt-get install xz-utils does not shift error I am afraid.

---


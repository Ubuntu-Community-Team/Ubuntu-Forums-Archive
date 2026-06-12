---
title: "[SOLVED] Program execution delayed when offline"
date: 2008-12-31
forum: General Help
---

### Post by abierwag on 2008-12-31
Hello,

I am running Ubuntu 8.04 on a Toshiba Dynabook MX/190DK. Whenever I disconnect from the network, there is an annoying delay (about 10 seconds) between the instant I call a program and the instant where the program window appears (console, editor, firefox, ..., anything). Once the program window is there (e.g. an editor) it works fine (e.g. loading and editing files).

The problem has been there since I installed Ubuntu 8.04 (from scratch) a couple of months ago. I have continuously upgraded, hoping the problem goes away; but it didn't.

I searched the web for information, but the only related page I found is:
July 19th, 2007
[http://ubuntuforums.org/showthread.php?t=504901](http://ubuntuforums.org/showthread.php?t=504901)
This thread, titled "Programs Load Slow Offline" says only: "solved".

I'd be thankful for any advice.

---

### Post by dcstar on 2008-12-31
> **abierwag said:**
> Hello,

I am running Ubuntu 8.04 on a Toshiba Dynabook MX/190DK. Whenever I disconnect from the network, there is an annoying delay (about 10 seconds) between the instant I call a program and the instant where the program window appears (console, editor, firefox, ..., anything). Once the program window is there (e.g. an editor) it works fine (e.g. loading and editing files).

The problem has been there since I installed Ubuntu 8.04 (from scratch) a couple of months ago. I have continuously upgraded, hoping the problem goes away; but it didn't.
.........
I'd be thankful for any advice.

Verify that you hosts file has the correct information in it, and you hostname also matches those entries.

You may also want to check your DNS lookup order.

---

### Post by abierwag on 2008-12-31
Thanks, David. This is new terrain for me, but I found that the second line of the following was missing in the /etc/hosts file:

127.0.0.1 localhost
127.0.1.1 [machine name]

I added it and now everything works fine.

Thanks a lot and Happy New Year.
Andreas

---


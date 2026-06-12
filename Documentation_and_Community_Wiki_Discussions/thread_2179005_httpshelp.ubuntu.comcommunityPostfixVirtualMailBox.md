---
title: "https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto"
date: 2013-10-06
forum: Documentation and Community Wiki Discussions
---

### Post by Rob_Donovan on 2013-10-06
Hi,

There is a mistake on this page, but I'm unable to edit the page (I've only just joined).

I presume someone else more senior has to fix it?

The problem is in the 2 scripts that are shown for adddovecotuser and deldovecotuser

The testing for the $domain variable is incorrect, and uses a -x flag, which is not going to work, as that means its testing that a file exists, rather than it has a value.

Currently, if you happen to be in a dir that has a dir named the same as the domain you are trying to add, then it gives an error saying "No domain give", which is incorrect.

In both scripts, you need to change the -x to a -z in the line near the top "if [ -x $domain ]"

HTHs,

Rob D.

---


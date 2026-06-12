---
title: "xterm 8-bit support"
date: 2005-05-23
forum: Desktop Environments
---

### Post by bhn on 2005-05-23
Hi all!

I have a newly installed ubuntu hoary hedgehog 5.04 laptop in front of me. One of the fist things I'd like to do is to get my xterm displaying 8-bit characters correctly.

Whenever I log in to a solaris server using ssh and then reading my mail with a text-based mail reader, special characters such as scandinavian characters, French accented characters, etc do not get displayed properly. I end up seeing just a dotted rectangular box in their place. This problem does not appear to manifest in other operating systems, when I do the same thing. 

I tried setting XTerm.VT100.eightBitInput and XTerm.VT100.eightBitOutput to true, but that didn't help. I'm sure there must be a solution to this, but I'm a relative newbie to linux and I'm not sure how to proceed.

I'd be really happy if someone has a solution to this. :-)

//bhn

---

### Post by bhn on 2005-05-30
After some poking around, I found some information from another ubuntu user's blog pages, which helped greatly.

In case you face the same trouble, I'd suggest you visit [http://joker.iki.fi/cms/?q=node/140&PHPSESSID=f069cac51595e82cffcb3652097ca943](http://joker.iki.fi/cms/?q=node/140&PHPSESSID=f069cac51595e82cffcb3652097ca943)


//bhn

---


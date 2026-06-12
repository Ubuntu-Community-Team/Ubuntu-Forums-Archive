---
title: "Ethereal save to file problem"
date: 2006-07-13
forum: Desktop Environments
---

### Post by SilverCloak on 2006-07-13
Hi,

Anyone can help ?  I'm using ethereal under Ubuntu Dapper and whenever I try to do a capture to file, I got an error (file not exist) and after the trace is saved under several file containing one packet each...

---

### Post by blademan on 2006-10-01
I would second this problem.

Ethereal in Ubuntu will save initial file as requested followed by files of 500B to 1K in size (that's right, 1000s of files less than 1K in size).

I typically save Ethereal traces in multiple files of 5-100MB. When I set Ethereal to save multiple files of 10MB, Ethereal will save the 1st file at 10MB in size, followed by thousands of files of <1K in size. I tried multiple sizes, and they all result in the correct initial size file, followed by 1000s of smaller files.

As a result of this dealbreaker, I reinstalled SuSE on my Thinkpad, and no problems with SuSE compilation of Ethereal.

---


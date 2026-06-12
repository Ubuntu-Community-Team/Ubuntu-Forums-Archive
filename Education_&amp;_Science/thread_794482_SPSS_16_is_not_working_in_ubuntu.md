---
title: "SPSS 16 is not working in ubuntu"
date: 2008-05-14
forum: Education &amp; Science
---

### Post by zuanazzi on 2008-05-14
Hi fellas, 

The SPSS 16 is not working after installation in ubuntu 8.04 and I don't know why. The installations was performed correctly. When I type spps in the terminal, says the software is not found. I installed as root in the /opt/SPSSInc/SPSS16/ directory.

Anyone could help me?

Thanks.

---

### Post by sfeone on 2008-05-15
Hi.

Yesterday I installed SPSS 16 for linux on my Ubuntu box. Its installation was no problem. But SPSS needed libstdc++5 so that I installed the library using:
> sudo apt-get install libstdc++5

Then, as usual, I typed the command 'spss'. But, it didn't work because there's no path on that.

I typed the command again with the full installed path:
> /opt/SPSSInc/SPSS16/bin/spss

Obviously, I could meet the neat SPSS logo.

Try it again with your installed full path.
It should be working for you.

Bye.

---

### Post by zuanazzi on 2008-05-15
Hi!

Thank you for the hint. It worked perfectly!

Thanks again.

bye.

---


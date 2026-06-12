---
title: "How do I reinstall Ubuntu without destroying everything?"
date: 2009-04-28
forum: General Help
---

### Post by MR.UNOWEN on 2009-04-28
Hello, I was just wondering if there's a way to reinstall Ubuntu without destroying everything. Right now 9.04 is driving me nuts... and I want to see if a fresh install of it or a downgrade will fix this problem. 

Can the user account information be kept intact?

If so, what are the steps for doing that?

---

### Post by michy99 on 2009-04-28
Do you have /home on a separate partition? If so, it can be done fairly easily.

---

### Post by coffeecat on 2009-04-28
With 8.10 and 9.04, you can choose manual at the partitioning stage, telling the installer to use your present root partition for root, and telling it **not** to reformat the partition. It will then delete the existing system directories such as /usr and /etc, but leave the /home directory intact, thus keeping all your account information.

I read this in a trustworthy source, but I haven't tried it myself.

---


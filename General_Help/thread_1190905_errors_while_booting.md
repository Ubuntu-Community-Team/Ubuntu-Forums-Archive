---
title: "errors while booting"
date: 2009-06-18
forum: General Help
---

### Post by zebsdad on 2009-06-18
Ubuntu 9.04. 

I have dual boot with XP. When I select to boot into Ubuntu, the screen says starting then it shows about 4 or 5 lines of errors (I think) that go so fast I cannot read them. Booting continues normally.

How can I stop the screen to see what the errors say?

Thanks for your help

---

### Post by ~sHyLoCk~ on 2009-06-18
> **zebsdad said:**
> Ubuntu 9.04. 

I have dual boot with XP. When I select to boot into Ubuntu, the screen says starting then it shows about 4 or 5 lines of errors (I think) that go so fast I cannot read them. Booting continues normally.

How can I stop the screen to see what the errors say?

Thanks for your help

It would be helpful if you could just note down the error message quickly (if possible...after a retry or two?)

---

### Post by zebsdad on 2009-06-18
I have tried over the last week to read anything. I get the lines of text all the way across the screen and there is no chance of reading them.

In Windows I can use the pause button to freeze the screen but this doesn't work with ubuntu.

Anyone?

---

### Post by jerrrys on 2009-06-18
If I understand correct, even with these errors you still can boot into ubuntu.  If this is the case try:

System>Administration>SystemLog

that should tell whats going on

---

### Post by zebsdad on 2009-06-18
Yes. Booting completes.

I view the System>Administration>Logfile viewer and there are many logs to view. To this N00b, it is all jibberish....

---

### Post by jerrrys on 2009-06-18
ok, sorry, try this instead

Accessories>Terminal

once in terminal type   **dmesg**

and then enter

this should give your boot log

---

### Post by zebsdad on 2009-06-18
Well, while I was gone, I opened my startup manager and it said there was something that needed fixing. I let it do the deed and also made some preferences I thought were necessary. 

When I rebooted, The messages were no longer there and all my external drives were mounted.

It was all caused by a sloppy edit of my grub file I had made.

Thank you for your help. No doubt I will be back asking for more assistance about other subjects.

---


---
title: "ubuntu 11.04 flash drive install question"
date: 2012-08-29
forum: Desktop Environments
---

### Post by user987 on 2012-08-29
i have ubuntu 11.04 installed on a 16G flash drive.

I have 3 questions.

1) why is it that every time i log on to linux os and then later when i log on to microsoft xp on my netbook ssd internal C drive, the time and date is reset to linux default date and time in XP?

My C drive should never have been touch when i am am the linux OS environment.

2)When i am in Linux, and i plug in another flash drive, it shows up on the back ground screen, but my 16g flash that is plug in with ubuntu does not show up.

why is that? So how can i get to it and check properties and see how much space i have left on my 16G flash drive?

3) when i plug the 16G flash drive in to my netbook in the XP environment.

Properties shows that i have 437 Byte used and 975M free.

It does not show the Ubuntu OS and the fact that it is a 16G flash drive.

It basically tells me i have a 9G flash drive in XP.
Why is that?

---

### Post by chubble10 on 2012-08-29
> **user987 said:**
> 
1) why is it that every time i log on to linux os and then later when i log on to microsoft xp on my netbook ssd internal C drive, the time and date is reset to linux default date and time in XP?
This is because Ubuntu will write the time settings to your BIOS configuration, which is the common place where all the systems get the time from (see [here]("http://blogs.msdn.com/b/oldnewthing/archive/2004/09/02/224672.aspx") for a tad more info)

> **user987 said:**
> 
2)When i am in Linux, and i plug in another flash drive, it shows up on the back ground screen, but my 16g flash that is plug in with ubuntu does not show up.

why is that? So how can i get to it and check properties and see how much space i have left on my 16G flash drive?

That is because it is mounted as the root file system. You can view it by choosing 'File System' from the computer menu in the sidebar of the file browser.

> **user987 said:**
> 
3) when i plug the 16G flash drive in to my netbook in the XP environment.

Properties shows that i have 437 Byte used and 975M free.

It does not show the Ubuntu OS and the fact that it is a 16G flash drive.

It basically tells me i have a 9G flash drive in XP.
Why is that?
That is because Ubuntu is written to your flash drive using a file system that XP cannot understand, and so it only shows the persistant storage part that is in a compatible file system. (It just ignores the rest).


Hope this answers your Qs!

---

### Post by user987 on 2012-08-29
Thanks, for the quick response.

When i log on later to ubuntu, i will check out your solution to my 2nd question.

---


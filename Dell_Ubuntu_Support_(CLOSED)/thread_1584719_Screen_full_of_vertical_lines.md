---
title: "Screen full of vertical lines"
date: 2010-09-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Satal Keto on 2010-09-29
Hi all,

I've been trying to install Ubuntu on my Dell Inspiron 1501 and when ever I try and install from the standard installation disk, I get lots of multicoloured vertical lines on my screen and that is it.
I've managed to install from the alternative installation disk and that gets around it, but then I get the vertical lines every time that I boot up, which obviously is quite a pain.

This has happened with the last few versions of Ubuntu and over several CDs/DVDs/USBs.

I was wondering whether anyone had come across this before and knows how to get it so that I can install Ubuntu with the standard installation disk without getting the vertical lines.

Thanks for any help in advance

Satal :D

---

### Post by gibbylinks on 2010-09-30
Hi Satal,

I have the same laptop and have been using Ubuntu for a few years now. Currently running 10.10 Beta.

what you need to do is use the "nomodeset" command in grub. I haven't got a clue what this does (there are far cleverer people than me around these forums) but hopefully I can help you get started. Curious thing is sometimes the live CD works OK.

When booting immediately after the boot screen has gone (when it turns black) you need to hold down the shift-key to access the grub menu. Then press "e" to edit the command line. Then add the word nomodeset to the end of the command line, you should be able to boot then.

Once you've booted you should be able to install. but afterwards you'll need to update the grub config so that you don't  need to hold down the shift key all the time.

I'm at work just now so sorry if what I'm saying is vague.

If you search the forums for "nomodeset" there are plenty of threads.

If you struggle let me know and I'll post more concise instructions. :)

Any queries on the 1501 just let me know.

---

### Post by migs73 on 2010-09-30
I use the 1501 and it has worked out the box since Jaunty.
I know this does not help your problem (try the previous posters recomendations, I know it works on other machines), but there should not be many other problems. My only problems are switching users can cause a lock out, and hibernate/suspend don't work. I just log out, and into the other account to solve the first and I don't use the other functions anyway.

---


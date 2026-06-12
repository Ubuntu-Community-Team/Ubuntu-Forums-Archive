---
title: "Nautilus &amp; Konqueror not reading CDs correctly"
date: 2006-11-02
forum: Desktop Environments
---

### Post by SirPecanGum on 2006-11-02
Nautilus & Konqueror are intermittently reading CDs (plural) incorrectly. Sometimes they see the CD correctly and sometimes they don't. Any ideas?

[IMG]http://www.metatext.co.uk/images/nacd.gif[/IMG]

---

### Post by chriscando on 2006-11-02
My guess is that the CD or the reader (or both maybe) is bad. If you dual boot does the same CD work ok in windows?

Some CDs I have with one of those sticker coatings throws my reader off balence and I have intermitten usage.

Also, is your CD reader struggling to read the CD? Can you hear it retrying over and over?

---

### Post by SirPecanGum on 2006-11-02
Thanks for your very speedy suggestions.

The problem is that the same CD is read/displayed correctly sometimes but not others. There is no scanning trouble with the drive and the CD works without any problems in Sabayon, Ubuntu 6.02 & XP. Sorry, I should have mentioned that before.

I have added a blank line to the fstab file and the CD is now read/displayed correctly. I wonder if that is it! I hope so, its driving me crazy!

---

### Post by chriscando on 2006-11-02
Just added a blank line in fstab. Did you comment out the line that refers to you cd drive?
Anyway hope it keeps working for you.

---

### Post by SirPecanGum on 2006-11-03
The missing blank line at the end of the fstab file appears to have fixed the problem. Just thought I'd mention it in case someone else has the same problem.

Thanks for the help.

---

### Post by SirPecanGum on 2006-11-07
Nope! This is still a problem. Any one have any other ideas? Thanks.

---


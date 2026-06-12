---
title: "Charset from Windows to Linux"
date: 2006-08-31
forum: Desktop Environments
---

### Post by jayce on 2006-08-31
Hi Everyone,
I apologize if this question was already answered but I search and could not find any appropriate answer.

prior installing Ubuntu Dapper (I deleted my windows partition :p ) I had windows installed. I believe everything is pretty much settled down but I have a few remaining issues.
One of them is the charset used in windows and Linux. I am using a European charset (French, so I assume this is UTF-8 ) but all my files that I had in windows are now seen with questions marks such as "inf&#65533;rieur" instead of "inférieur"

Similarly, I have a Virtual machine (Windows) with Vmware installed, when I copy a text from Linux with accent (French) and paste the text over in the virtual machine in windows, all characters with accent are removed/stripped.
Please note that the home folder is a separate partition and when I tried change the charset in the /etc/fstab, I could not longer read /home folder content.

Would you have any recommendation to solve this issue ?

Thank you much

---

### Post by Hasen_A on 2007-02-27
I have the same problem as I have german accents such as ä,ü,ö replaced by &#65533; in NTFS files.

How do you list all files with the char &#65533; in it?! Placing &#65533; in the search field doesn't work. I need to rename all files containing &#65533; because the cp command wont copy files containing this char and I am trying to make a backup of all my files. Neither will nautils copy function.

---


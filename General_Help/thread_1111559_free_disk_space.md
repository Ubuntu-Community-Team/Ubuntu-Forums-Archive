---
title: "free disk space"
date: 2009-03-30
forum: General Help
---

### Post by freonchill on 2009-03-30
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sda6 56094620 46937524 6330064 89% /
~6.14gb free

disk usage analyzer (installed by default with ubuntu 8.10)
/dev/sda6
53.5gb / 44.8gb used / 8.7gb free

gparted
/dev/sda6
53.92gb / 45.19gb uses / 8.73gb free

why do the different programs report different free space?

thanks,

---

### Post by ibuclaw on 2009-03-30
Best guess is differences in precision.

Take your first command:
```
df
```
It's job is to display the disk usage lighting fast. To do so it must get its information from a file stored in the Linux file system (either in **/sys** or **/proc**) *(edit: ok ... it uses the function statvfs, which returns a struct)*. If you were to carry out a few changes on your filesystem (ie: remove 2GBs of ISO images), and these files were updated in a timely manner, then that would explain why the listing on df is wrong.

As for the others, they take about 3-5 minutes to process as they count every single file and round up the overall size shared between them. Depending on how it adds up the data, and which user you are when you run the applications, it will show slightly varying results.

Remember, these applications you are comparing weren't built together at the same time, or by the same Author, and each one had his own unique way of carry out the task, no doubt.

Regards
Iain

---

### Post by freonchill on 2009-03-31
understandable

other than web surfing (cache) i have not downloaded or deleted and the "gap" remains constant despite fluctuation in free space.

e.g. i have not added, deleted multiple files (especially large files, iso's etc)

i dont think its a matter of seconds/minutes for the systems to upgrade and become accurate.

its been like this for a week or longer.

i would understand minor changes (+/- 100mb, but 2gb?!)

ideas? 

thanks,

---

### Post by freonchill on 2009-04-03
bump

---


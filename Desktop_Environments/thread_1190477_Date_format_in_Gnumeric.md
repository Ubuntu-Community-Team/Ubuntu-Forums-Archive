---
title: "Date format in Gnumeric"
date: 2009-06-17
forum: Desktop Environments
---

### Post by luiznetto on 2009-06-17
I recently changed my system default language in Ubuntu 8.04 from Portuguese to English. When it was in Portuguese I would click on a cell in Gnumeric 1.8.2 and choose from the menu **Insert**->**Special**->**Current date** and I would get today's date, which is 17/6/2009. Now that the system language is English, I am getting 6/17/2009. I'd like to change this behavior, so I right-click on the cell and get Format Cells... Date and under **Format:** there are lots of options, except the one that suits me. It would be something like d/m/yyyy but it's just not there. There **must** be a file that belongs to gnumeric - I do

$ dpkg -L gnumeric | less

**one** of these files **must** be the one that, when edited, will solve my problem; I just don't know which one.

Thanks in advance for your help, it will be immensely appreciated.
Luiz

---

### Post by jbrefort on 2009-06-18
You might set the LC_TIME environment variable to pt_PT.UTF8 or so, or you can use a custom format for the cell like "d/m/yyyy".

---


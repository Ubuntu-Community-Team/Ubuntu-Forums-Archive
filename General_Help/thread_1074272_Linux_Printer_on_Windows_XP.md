---
title: "Linux Printer on Windows XP?"
date: 2009-02-19
forum: General Help
---

### Post by iheartubuntu on 2009-02-19
Our main computer at home in Ubuntu 8.10. My wife is an accountant and absolutely hates Open Office Spreadsheet as it cant do the calculations shes needs that apparently MS Office can do. So, next best thing is for her XP laptop to see the printer that works fine in linux via a wi-fi network. But, Windows XP asks me for either of these when installing a network printer...

\\server\printer

[http://server/printers/myprinter/.printer](http://server/printers/myprinter/.printer)

How do I go about installing a linux printer on an XP machine? Thanks for any tips, I have not been able to find anything as of yet.

---

### Post by plucky on 2009-02-19
> **shirteesdotnet said:**
> Our main computer at home in Ubuntu 8.10. My wife is an accountant and absolutely hates Open Office Spreadsheet as it cant do the calculations shes needs that apparently MS Office can do. So, next best thing is for her XP laptop to see the printer that works fine in linux via a wi-fi network. But, Windows XP asks me for either of these when installing a network printer...

\\server\printer

[http://server/printers/myprinter/.printer](http://server/printers/myprinter/.printer)

How do I go about installing a linux printer on an XP machine? Thanks for any tips, I have not been able to find anything as of yet.



See this [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)


Good Luck

---

### Post by iheartubuntu on 2009-02-19
> **plucky said:**
> See this [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)


Good Luck

Thanks for the help, I will give it a try!

---

### Post by albandy on 2009-02-19
install it as a network printer (like an HP jetdirect)

First enter cups in your ubuntu machine with firefox:
[http://localhost:631](http://localhost:631)
go to administration
enter your user and password
enable allow printing from internet
apply the changes

go to you windows machine and install a new tcp/ip printer

[http://yourubuntuip:631/printers/printername](http://yourubuntuip:631/printers/printername)

now you can print

---


---
title: "Print Problem"
date: 2009-05-02
forum: General Help
---

### Post by davyC on 2009-05-02
Not sure whether this has cropped up before - but I'd appreciate some help. I have a desktop (wired) running Windows XP and a Laptop running Dual Boot - Windows Vista and Ubuntu (Jaunty Jackalope). The laptop connects wirelessly to the network via a Linksys Router and I'm able to share documents/files through Cisco's Network Magic. This also enables me to share an HP Officejet 5610 all in one, which is connected by USB cable to the desktop. I can print remotely (wirelessly) from my laptop when running Vista. The problem I have is when using Ubuntu, any print request results in the printer producing blank pages. The Officejet 5610 appears to respond perfectly normal, with the print head moving across the page, and completes the task, EXCEPT for the fact that the page is blank. Any help please?

---

### Post by cariboo on 2009-05-02
How did you setup the printer? Using hplip or System-->Administration-->Printing? I would suggest you go [here]("http://hplipopensource.com/hplip-web/index.html") and download the latest drivers for your printer.

---

### Post by davyC on 2009-05-02
Hi  - Thanks for that. I did as you suggsted and downloaded a file 
/hplip-3.9.4b_1.run - which went to my Temporary Downloads folder. When I clicked on it, a blank window in Abiword opened, ad then - nothing. What am i doing wrong?

---

### Post by davyC on 2009-05-02
Solved it - It was a configuration issue. The printer properties default, under "Printer options" was set to  "Normal(Colour Cartridge)" It so happened that on my printer, the colour cartridge was empty. When I changed the default to "Normal Grayscale -Black cartridge" - Result, Job Done.) - there was plenty of ink in the Black Ink Cartidge. Anyway, thanks for your help

---


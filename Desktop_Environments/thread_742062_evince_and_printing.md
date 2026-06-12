---
title: "evince and printing"
date: 2008-04-01
forum: Desktop Environments
---

### Post by nagylzs on 2008-04-01
Hi all,

I'm trying to use "evince" to print labels with a printer. The labels are in different PDF files and I would like to open the file and print the label immediatelly. However, it is not that easy. Each time I open evince, I need to change the printer settings:

"Format for any printer" -> "Phaser_6130N"
"Paper Size US Letter" -> "Paper Size A4"

If I do not change these settings then the printer won't print. It will display an error message telling that "incorrect paper size, not supported by the printer" etc.

My question is, how can I change the default printer and paper size in evince? It is very disturbing that I need to open dialog windows and answer questions. It should be two clicks to print a PDF from nautilus.

I tried to change the default printer to Phaser_6130N under system/preferences/default printer. It did not help.

Thanks,

   Laszlo

---

### Post by psychonauticos on 2008-07-08
This is a really annoying problem indeed.

Apparently it happens that in evince some language environment setting kicks in. So if you got an US language environment it'll set letter as default.

Look here: [https://answers.launchpad.net/ubuntu/+source/evince/+question/6846](https://answers.launchpad.net/ubuntu/+source/evince/+question/6846)

hth

---


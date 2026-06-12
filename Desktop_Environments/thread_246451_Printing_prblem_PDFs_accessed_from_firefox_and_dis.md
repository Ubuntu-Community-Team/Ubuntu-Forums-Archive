---
title: "Printing prblem: PDFs accessed from firefox and displayed in evince won't print"
date: 2006-08-29
forum: Desktop Environments
---

### Post by smcleish on 2006-08-29
I'm sure this used to work when I first installed Ubuntu (Breezy Badger). After upgrading to Dapper Drake, when I click on a PDF on a web page, and display it using evince, I can't print it. Evince stalls waiting for CUPS to give it a list of printers (all one of them). This happens if I start firefox from the gnome menus, but not if I start it from the command line: the printer is listed and printing is fine. (Does this suggest a permission problem somewhere?) If I download the PDF and open evince to look at it separately, it also prints fine.

It's not an urgent problem, but it is irritating and if anyone has any suggestions, I'd be pleased to solve it.

Thanks in advance,
Simon

---

### Post by Johnny K on 2008-02-26
Still an issue in Gutsy. I use kilz's Firefox32, could that have anything to do with it?

---

### Post by smcleish on 2008-02-26
I did eventually solve the problem: delete the printer from CUPS, and re-install. I'd guess this means that the upgrade messed the permissions somewhere.

---

### Post by Johnny K on 2008-02-26
When you open PDF documents directly from Firefox, do you also experience the problem of Evince not loading icons? Whenever I open a PDF directly from Firefox, none of Evince's icons are displayed. For example, the "Previous" and "Next" buttons do not display arrows, but just red X's (see screenshot). The same thing happens in all other applications that are launched directly by Firefox. I thought this might have something to do with the printing problem.

---

### Post by smcleish on 2008-02-27
Sorry, but icons are currently displayed fine and as far as I remember always have been. If setting up your printer again doesn't solve the problem, perhaps you can try uninstalling and re-installing evince? The unfound icons suggests to me that the graphics have either moved or had permissions altered by the upgrade, so doing that might fix the problem. But this is just a guess!

---


---
title: "Danish special letters won't work after clean Dapper install"
date: 2006-06-06
forum: Desktop Environments
---

### Post by zakos on 2006-06-06
After I did a clean Dapper Drake install, my danish letters (æøå) wouldn't work. I did an update from Breezy earlier where all buttons worked correctly. I'm using KDE 3.5.3 and kernel 2.6.15-23-k7. All my other buttons (mediabuttons inclusive) works perfectly as they should. But just not the three special letters.
Also when I try to shift from my graphical tty (tty 7) to tty 1 or so on, with Ctrl+Alt+F1/F2 nothing happens.
Are there anyone who knows an answer to what I shall do?
Best regards Emil aká Zakos

---

### Post by zakos on 2006-06-07
*bump*

---

### Post by pubwho on 2006-06-07
[QUOTE=zakos]After I did a clean Dapper Drake install, my danish letters (æøå) wouldn't work.[/QUOTE]

Do you have a Scandanavian style keyboard?

I too would like to be able to print the scandanavian letters, i use a UK layout keyboard. On Windows, I used <alt> + 0248, <alt>+0229 and <alt> + 0249 However this doesn't seem to work in Ubuntu.

Does anyone know how to input foreign characters using the keyboard?

---

### Post by zakos on 2006-06-22
I found the solution on linuxquestions, so there's no more need for answers. I'm not quite sure what I did to fix this, but I think it was that I changed the locale to ISO-8859-1 with localeconf. And after that I did a manually **locale-gen**.

---


---
title: "Problem installing: Wine MIcrosoft Windows Compatibility Layer"
date: 2008-12-06
forum: General Help
---

### Post by looi76 on 2008-12-06
Hi Everyone, I a new Ubuntu user. I wanted to install Wine but I keep geting an error. How can I solve it?

Here are the screen-shots:

[IMG]http://img242.imageshack.us/img242/9913/screenshotbu2.png[/IMG]

[IMG]http://img301.imageshack.us/img301/4416/screenshot1zs5.png[/IMG]

---

### Post by danwood76 on 2008-12-06
you probably need to refresh the sources list.

Open up synaptic package manager and click the 'reload' button and then search for wine from there and try and install it.

---

### Post by eBoxNet on 2008-12-06
did you try to install from terminal?
open a new terminal window and type : sudo apt-get install wine

---

### Post by looi76 on 2008-12-06
[FONT="Georgia"][SIZE="3"]I went to Synaptic Package Manager but also got an error over there :sad:. I clicked on Reload, then I did the following steps:

[IMG]http://img186.imageshack.us/img186/4453/screenshot3us8.png[/IMG]

[IMG]http://img67.imageshack.us/img67/1586/screenshot5vx0.png[/IMG]

[IMG]http://img71.imageshack.us/img71/1938/screenshot6jm5.png[/IMG]

[IMG]http://img186.imageshack.us/img186/2778/screenshot7gv5.png[/IMG]

What is the solution?[/SIZE][/FONT]

---

### Post by eBoxNet on 2008-12-06
it looks that synaptic can't find the proper package.

---

### Post by eBoxNet on 2008-12-06
did you refresh your source list?
try this on terminal :

sudo apt-get update
sudo apt-get install wine

---

### Post by danwood76 on 2008-12-06
Well the reload should hve refreshed the package list properly.
I'm assuming you followed the instructions on the wine hq website yeah?

You can download the deb installer directly here:
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.10~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.10~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)

and just run the file and it will prompt you to install.

---

### Post by looi76 on 2008-12-06
Thnx danwood76, I downloaded wine_1.1.10~winehq0~ubuntu~8.10-0ubuntu1_i386.deb and installed it perfectly!

---


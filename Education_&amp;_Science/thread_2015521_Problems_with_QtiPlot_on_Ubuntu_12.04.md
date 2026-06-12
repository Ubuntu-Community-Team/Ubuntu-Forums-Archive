---
title: "Problems with QtiPlot on Ubuntu 12.04"
date: 2012-07-03
forum: Education &amp; Science
---

### Post by The_Lunatic on 2012-07-03
Hi there!
I decided to try QtiPlot on Precise Pangoline and I installed it from the terminal.
I tried to do some plot and it seems it works fine.
The problem occurs when I try to open a file: it shows me the window with all the folder in my /home, then when I click on one of them it just closes without saying or notifying anything.

Do you know what problem is, or how can I fix it?

This is quite annoying, and this new ubuntu is making me very unhappy :(

Thanks in advance!

---

### Post by mdshaver on 2012-07-06
See if Veusz meets your needs. I have used both QtiPlot and Veusz for my research. Both make some nice graphs and each have their own advantages. Veusz is in the Ubuntu repos. You can also install the latest version from the PPA on their homepage. If you really prefer QtiPlot, you can either download a generic binary for free from the software website or you can purchase a maintenance contract for a very reasonable price to always have the latest deb packages.

---

### Post by Pand5461 on 2012-07-11
Hi The_Lunatic!

Did you launch QtiPlot from terminal? Some information about the error can be recovered from the terminal output.

---

### Post by jat255 on 2012-08-01
Looking at the terminal output would give you a good clue as to what is going one when you are running it. Did you install via the packages, or compile it yourself from source?

You could also attempt deleting QtiPlot.conf in your $HOME/.config/ProIndependent/ folder, which will reset all of your config options. Perhaps this might help?

The version available in the repos is slightly out of date, and a number of improvements have been made. The best way to get it onto your system is to either compile it yourself, or use one of the PPAs that stay more up to date with the development.

If you need instructions on how to install from source, please see my instructions here: [http://www.terpconnect.umd.edu/~jtaillon/qtiplot.php]("http://www.terpconnect.umd.edu/~jtaillon/qtiplot.php")

---


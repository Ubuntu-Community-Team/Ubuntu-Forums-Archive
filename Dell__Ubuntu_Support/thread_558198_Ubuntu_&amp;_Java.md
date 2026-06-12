---
title: "Ubuntu &amp; Java"
date: 2007-09-23
forum: Dell  Ubuntu Support
---

### Post by Cieran-Corten on 2007-09-23
If this is in the wrong section, I apologize.

I am dual-booting Windows Vista and Ubuntu on a Dell Inspiron E1705 laptop. In general, I love Ubuntu much more than Vista. However, I cannot get Java to work in my Ubuntu. I have tried at least 10 different options- I installed the Restricted Package deal, I searched for Java in Add/Remove Programs, I followed the instructions on [www.java.com](www.java.com), and I've followed instructions on at least 5 alternate sites- and I haven't been able to come up with anything that allows Java to run.

Any thoughts on this would be appreciated. (If you need more information, tell me what you need and how I can get it :))

---

### Post by odiseo77 on 2007-09-23
Hi, first, make sure you have extra repositories enabled: Open Synaptic Package Manager ('System>Administration'), click on 'Settings', then 'Repositories', then click on the first tab and check all the check boxes except 'Source code' (make sure the multiverse repository is checked) then close the window, click on reload (or refresh, something like that), after it finishes, search for the term 'sun java' and install the following packages: sun-java6-bin, sun-java6-jre and sun-java6-plugin. After they're installed, open a terminal window and type ***java -version*** it should show you the version of java you're using; in case it's not Sun's Java, type ***sudo update-alternatives --config java***, and select java 1.6 at the prompt menu.

---


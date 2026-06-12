---
title: "Epiphany Web Browser"
date: 2009-04-06
forum: General Help
---

### Post by ninjapirate89 on 2009-04-06
Okay so heres what up. I decided the other day that I wanted to try epiphany so I opened a terminal and typed sudo apt-get install epiphany-browser. It installed fine but I decided I didn't really like it over firefox so I opened up a terminal and typed sudo apt-get autoremove epiphany-browser and it seemed to uninstall fine, however  it is not actually uninstalled. It is still in my menu and it still runs. Any ideas?

---

### Post by ryanhaigh on 2009-04-06
Sincy Hardy (ubuntu 8.04) epiphany-browser has been a dummy package
[http://packages.ubuntu.com/hardy/epiphany-browser](http://packages.ubuntu.com/hardy/epiphany-browser)
A dummy package is basically a empty package with a dependancy on the real thing. In this case the package depended on is epiphany-gecko. If you tried epiphany specifically for the webkit version you will need to install epiphany-webkit.

---

### Post by ninjapirate89 on 2009-04-07
Thanks. I used sudo apt-get autoremove epiphany-gecko and that did the trick.

---


---
title: "mysql on ubuntu"
date: 2006-06-02
forum: Desktop Environments
---

### Post by christoforever on 2006-06-02
sorry guys i didnt know where to post this to get some answers. so here it goes. i've installed mysql on ubuntu, yet when i go into the bin directory and try to start the server nothing happends, when i click on any of the bin files nothing happends. I installed it under root. does anyone have any sollutions?

---

### Post by jon_gunnar on 2006-06-02
[QUOTE=christoforever]sorry guys i didnt know where to post this to get some answers. so here it goes. i've installed mysql on ubuntu, yet when i go into the bin directory and try to start the server nothing happends, when i click on any of the bin files nothing happends. I installed it under root. does anyone have any sollutions?[/QUOTE]

You did not use apt-get,is that the case?
If you did the install via : sudo apt-get 
you my try to start it with
```
sudo /etc/init.d/mysql start
```

---


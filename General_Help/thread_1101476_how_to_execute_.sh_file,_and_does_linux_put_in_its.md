---
title: "how to execute .sh file, and does linux put in its directorty automatically"
date: 2009-03-20
forum: General Help
---

### Post by sunseeker888 on 2009-03-20
Hello


I have a little problem

I have this file, install-crossover-pro-6.2.0.sh

This filed is saved in my desktop directory.


HOw can I install that program, and secondly will linux instal it in its appropriate directory without me instructing it? I am a dummy in Linux but really need this to work. I am having so much problem with vista 64 bits, I get getting blue screens daily. This crossover will make the programs that need work on Linux, and then I can finally say goodbye to that garbage windows.


Thanks in advance

---

### Post by taurus on 2009-03-20
From a terminal, run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod +x install-crossover-pro-6.2.0.sh
sudo ./install-crossover-pro-6.2.0.sh
```

---


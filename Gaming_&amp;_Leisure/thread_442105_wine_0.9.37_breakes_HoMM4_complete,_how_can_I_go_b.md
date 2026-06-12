---
title: "wine 0.9.37 breakes HoMM4 complete, how can I go back to 0.9.36?"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by clevin on 2007-05-13
I installed wine through wine's repositories for ubuntu 7.04. any way I can downgrade to 0.9.36?

---

### Post by hikaricore on 2007-05-13
Step one: Open a terminal.

Step two:  ???

```

wget http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.36~winehq0~ubuntu~7.04-1_i386.deb
sudo dpkg -i wine_0.9.36~winehq0~ubuntu~7.04-1_i386.deb
```

Step 3: Profit.

---

### Post by bastiegast on 2007-05-13
> **hikaricore said:**
> Step one: Open a terminal.

Step two:  ???

```

wget http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.36~winehq0~ubuntu~7.04-1_i386.deb
sudo dpkg -i wine_0.9.36~winehq0~ubuntu~7.04-1_i386.deb
```

Step 3: Profit.

Obviously you need to sudo apt-get remove wine first. And don't install wine updates the next two weeks xD

---


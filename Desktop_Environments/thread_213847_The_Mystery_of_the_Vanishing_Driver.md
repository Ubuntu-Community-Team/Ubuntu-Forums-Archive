---
title: "The Mystery of the Vanishing Driver"
date: 2006-07-11
forum: Desktop Environments
---

### Post by Paul Watson on 2006-07-11
Hello,

My experience with Ubuntu has been mostly positive, and I've worked through the minor challenges myself. However, there's one show-stopper that's just driving me nuts ](*,) .

I use wireless at home, and when I boot up Ubuntu, the wireless drivers will sometimes be in the Network settings, but usually they are missing. It seems random.

I checked the help file, which instructed me to click on the Add button and add the missing drivers. Sadly, despite a screen shot in the help file showing the Add button, the actual config app in my install of Ubuntu is missing this button.

Help me, Ubuntu forum! You're my only hope.

---

### Post by Dr. Nick on 2006-07-11
One way you can solve it is when the drivers load for you run this command from a terminal

lsmod

save the output of that command. Re run lsmod when the drivers dont load and compare the 2, which file is missing.


If you run lsmod now and see your wireless driver, then add it to the file /etc/modules and it should load on startup every time

---


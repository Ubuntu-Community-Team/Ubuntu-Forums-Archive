---
title: "problem with beryl"
date: 2007-02-06
forum: Desktop Environments
---

### Post by zetsumei on 2007-02-06
I installed beryl and the problems I'm having is that there are no title bars on my windows, my terminal is all white and I can't type in it, I have to right click on windows in the task bar to move them.  Whats the problem with this?

ALso, how do I get the 3d cube to show up?

---

### Post by Zzl1xndd on 2007-02-06
try right clicking on the Rudy and reload windows decorator. and as for the cube just use your mouse scroll on the desktop.

---

### Post by zetsumei on 2007-02-06
i fixed it, someone in #ubuntuforums helped me =)

---

### Post by Zzl1xndd on 2007-02-06
awesome man go IRC eh.

---

### Post by mrpeenut24 on 2007-02-13
Can you tell us what the problem was?  I'm having the same issue.

---

### Post by alinuxfan on 2007-02-14
yes, PLEASE tell us...same issue, after reinstalling nvidia drivers and beryl again and again

---

### Post by Adder on 2007-02-14
I had to revert back to version 0.1.99.2. Newest version of beryl doesn't work with XGL. I gave following command on terminal.

```
sudo apt-get install beryl=0.1.99.2~0beryl1 beryl-core=0.1.99.2~0beryl1 beryl-manager=0.1.99.2~0beryl1 beryl-plugins=0.1.99.2~0beryl1 beryl-plugins-data=0.1.99.2~0beryl1 beryl-settings=0.1.99.2~0beryl1 beryl-settings-bindings=0.1.99.2~0beryl1 emerald=0.1.99.2~0beryl1 libberyldecoration0=0.1.99.2~0beryl1 libberylsettings0=0.1.99.2~0beryl1 libemeraldengine0=0.1.99.2~0beryl1 emerald-themes=0.1.99.2~0beryl1 -V
```

Hope this helps you all.

---

### Post by PaulFXH on 2007-02-14
> Newest version of beryl doesn't work with XGL. 

It does on my computer!

I've had the "no window frames" problem but fixed this with the recommendations in post#8 in this thread ([http://www.ubuntuforums.org/showthread.php?t=353488&highlight=window+frames)](http://www.ubuntuforums.org/showthread.php?t=353488&highlight=window+frames)).

Once or twice, even with this fix, I've lost the window decoration again. This was resolved by removing all the Beryl stuff from Synaptic and then reinstalling with
```
sudo apt-get install beryl emerald-themes
```
Although this is a pain, it can all be done in 2-3 minutes.

Well,  Beryl is Beta but in my opinion its merits still far outstrip its shortcomings.

---


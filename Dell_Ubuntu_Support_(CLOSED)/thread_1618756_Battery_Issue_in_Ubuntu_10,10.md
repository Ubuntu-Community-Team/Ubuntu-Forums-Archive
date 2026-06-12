---
title: "Battery Issue in Ubuntu 10,10"
date: 2010-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lijinshyam on 2010-11-11
Hi....

   I have a Dell studio Laptop..and i just installed ubuntu 10.10 

Now i have an issue in battery .. While charging when i remove the charger ...It shows my battery is 84% remaining and then suddenly a screen shows "Laptop battery critically low...Computer will soon hibernate unless it is plugged in"

 When i press cancel then the system goes to sleep..

 Then i restart the system without plug-in charger it works fine for about 2 hrs....

whats happening...:(

---

### Post by animeshmeher on 2010-11-12
Hi!

Try this, 
Press Alt-F2 and type **gconf-editor**. Press Enter. 
Navigate to **Apps -> gnome-power-manager -> general**. 
**De-select** the option **use_time_for 1f40 _policy**.

No need to restart, just close the config editor.

That should help. 

I suggestion though. Please google your problem a bit before posting . Thatll save duplicate post. :smile:
Even i had the same problem and googled for the answer.

---

### Post by lijinshyam on 2010-11-12
Thanks....It worked.....:)

See u soonn....:)

---

### Post by CoolJohnB on 2010-11-12
Thanks for that I had the same problem on my Vostro 3700

---


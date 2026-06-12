---
title: "Beryl problem"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by Martinbr on 2007-05-14
Hi,

I have a problem with beryl. When i run beryl i am not able to move the windows. They just freeze up.

Here is what i have done :

Clean ubuntu feisty installation
Nvidia drivers installed with Envy
reboot
Beryl installed via Synaptic
reboot

Then i start ubuntu and beryl manager, and the windows cant be moved around :-(
I have the cube effect though.

Any suggestions?

---

### Post by keiwc on 2007-05-14
I have the exact same problem...you lose the window top plane, and the windows cant move. But the window previews and everything else work.

---

### Post by notwen on 2007-05-14
Do you have emerald installed?  Right-click on your Beryl gem and check the Window decorator to see see if you have the option of choosing emerald, if not open up a terminal and type this.

```
sudo apt-get install emerald emerald-themes
```

You may or may not have to restart X (CTRL+ALT+BACKSPACE) for emerald to show up as an option.  Hope this helps. =]

--EDIT--
To further clarify things Beryl alone is only a window manager, it needs Emerald(a window decorator) to give you your windows title bars, minimize, maximize , & close buttons. =]

---

### Post by keiwc on 2007-05-14
How do you make the Emerald themes work? WHen i click on them, nothing happens.

---

### Post by notwen on 2007-05-14
Do you have emerald selected as your window decorator?  If I recall, it should update to whatever theme you currently have selected.

---

### Post by Martinbr on 2007-05-15
> **notwen said:**
> Do you have emerald installed?  Right-click on your Beryl gem and check the Window decorator to see see if you have the option of choosing emerald, if not open up a terminal and type this.

```
sudo apt-get install emerald emerald-themes
```

You may or may not have to restart X (CTRL+ALT+BACKSPACE) for emerald to show up as an option.  Hope this helps. =]

--EDIT--
To further clarify things Beryl alone is only a window manager, it needs Emerald(a window decorator) to give you your windows title bars, minimize, maximize , & close buttons. =]

Thx man :-) It worked!! weeeeeeee!!! :guitar:

---

### Post by philipho on 2007-05-15
I encountered the same issue , i just rebooted and the problem was gone.

---


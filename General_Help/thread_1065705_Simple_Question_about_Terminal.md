---
title: "Simple Question about Terminal"
date: 2009-02-10
forum: General Help
---

### Post by Awesom on 2009-02-10
Just out of curiosity when you run a program through the terminal ie. frostwire do you have to keep the terminal running in the background or is it best to? Because I can still see it doing things as frostwire runs.

---

### Post by SeanTater on 2009-02-10
I don't know about frostwire specifically, but I'm fairly sure the answer changes, for example apt-get and dpkg may need your input, so they need to remain connected. Others may not. If you plan to close the terminal while you leave a command running, you should end the command with a "&".

---

### Post by Awesom on 2009-02-10
Oh ok spose I will just leave it running whenever I run a program from it to be safe. Thanks.

---

### Post by mb_webguy on 2009-02-10
You can safely append an ampersand to the end of a command from the terminal that starts a GUI application.  GUI apps get all their necessary input from the GUI, so unless you want to see all of the miscellaneous messages that get sent to the terminal, it's fine to run it outside of the terminal.

---

### Post by ibutho on 2009-02-10
You can do the following
```
nohup frostwire
```
If you close the terminal, frostwire should still be running.

---

### Post by DJ_Peng on 2009-02-10
Thanks for that info, ibutho. I was going to say that you need to leave the Terminal open after closing the Terminal while running apps and seeing them killed with the terminal but that little tip of yours is something I hadn't seen before. I"ll have to blog it so more people can find out about it.

---


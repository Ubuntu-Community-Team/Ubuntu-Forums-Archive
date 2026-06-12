---
title: "left and top panel is hidden after enable root login"
date: 2012-11-11
forum: Desktop Environments
---

### Post by Haika on 2012-11-11
Hi everybody,
I 'm new to Ubunto. I 'm using Ubuntu 12.04 
I tried to enable root login using the following commands:
```

sudo passwd root 

sudo sh -c 'echo "greeter-show-manual-login=true" >> /etc/lightdm/lightdm.conf' 
```After that i restart my laptop.
Now when i log in as **Haika**, left and top menu are hidden and i have no access to them! :confused: And when i log in as **root**, they are shown and there is no problem!!!
What 's wrong? please help me!
(I can only run terminal using Alt+Ctrl+T)

---

### Post by Haika on 2012-11-11
I solved it, you can use this instruction if you have same problem (i found it in [http://www.askubuntu.com](http://www.askubuntu.com))

First, try sudo apt-get -f install && sudo apt-get --reinstall install unity
  Then, try unity --reset, followed by unity --replace; try doing this from the desktop and also from the console (switch via Ctrl-Alt-F1).


enjoy :D
:guitar:

---


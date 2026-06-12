---
title: "Launcher doesn't show"
date: 2018-05-07
forum: Desktop Environments
---

### Post by john.jeijeu on 2018-05-07
[COLOR=#111111][FONT=Ubuntu]Hello,

I'm using ubuntu 16.04, and the launcher doesn't show anymore. I've tried many things on the web, such as apt-get install --reinstall ubuntu-desktop and rm -rf ~/.config or dconf reset -f / or activating the unity plugin in ccsm, but it still doesnt display the launcher after reboot. Any help please?

Thanks[/FONT][/COLOR]

---

### Post by Frogs Hair on 2018-05-07
Hello and Welcome

Try the following if you haven't already. 
```
sudo apt-get install dconf-tools
``````
dconf reset -f /org/compiz/
``` Reset Unity If Needed:  ```
setsid unity
```

---

### Post by john.jeijeu on 2018-05-09
Hello, thanks for the reply, but sorry, it does not work either. If i connect as a guest account, I can see the launcher, but as my account, it still doesn't show the launcher

---

### Post by Frogs Hair on 2018-05-10
Have a look [here]("https://askubuntu.com/questions/801742/ubuntu-16-04-launcher-is-missing-after-installing-new-updates/804442#804442") .

---


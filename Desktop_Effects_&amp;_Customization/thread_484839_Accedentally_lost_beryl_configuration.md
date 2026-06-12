---
title: "Accedentally lost beryl configuration"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by mpneerkaje on 2007-06-26
Hi there,

I was playing with beryl for sometime and I changed some settings to the beryl-manager by right-clicking on the panel applet. Suddenly the desktop icons disappeared and system is hanged. Only one thing working was CTRL+ALT_Backspace!

I tried reinstalling beryl, it did not help. I even tried removing and re-installing beryl, beryl manager but did not help.

Also, can somebody here post me a screen shot of the settings-menu of the beryl manager? (when you right click on the panel icon)

It would be a great help for me to identify the wrong-setting i have done,

Thanks in advance,
Mahesh

---

### Post by speaker219 on 2007-06-26
Make sure you remove everything. Try using the following command:
```
sudo apt-get --purge remove beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings beryl-settings-binding emerald libberyldecoration0 libberylsettings0 libemeraldengine0


sudo apt-get autoremove
sudo apt-get autoclean
rm -r ~/.beryl

rm -r ~/.emerald
rm -r ~/.beryl-managerrc
```

This will erase everything related to beryl, including your settings. Then reinstall beryl and it should work again. This worked for me. Hope it helps.

Also, you might want to remove everything related to Beryl and then install "Compiz Fusion". Beryl is no longer supported and there will not be any more updates to beryl. Compiz Fusion is a combination of Compiz/Beryl. It is supported and updates will be released. There is a howto on how to install it in a sticky at the top of the forum. Although the howto states it is not for beginners, I found it to be **VERY** easy to install and more stable then Beryl.

---

### Post by mpneerkaje on 2007-06-26
Thanks 'Ubuntu Fanatic', it worked for me!
Thanks for your suggestion too.

---

### Post by speaker219 on 2007-06-27
No Problem, Enjoy =)

---


---
title: "locked out/ bug?"
date: 2005-07-02
forum: Desktop Environments
---

### Post by caffemusse on 2005-07-02
Having just installed kubunto, and set up my lan as standard internet conection, I'd like to configure my wlan too. (ipw2200)

But when entering the settings and choosing administrator mode button, it does not open the functions after giving it the correct password. In terminal I can su myself and it accepts the password .

I need to get into the network settings in order to activate my wlan card. Any suggestions? 
If you suggest commands from a terminal window, please be detailed, since I am a Newbie to linux.

Thx

---

### Post by jshein on 2005-07-02
This is a bug that has not been fixed on every kubuntu install I have completed. Open a console and type

#sudo kcontrol

That will work.

Also, there are some problems with the KDE network setup module.

Install the Gnome system tools

#sudo apt-get install gnome-system-tools

Then there will be a gnome network setup tool in the System menu

---


---
title: "click does not respond in maximized window"
date: 2023-04-24
forum: Desktop Environments
---

### Post by l-cardenas83 on 2023-04-24
The minimize, expand, close button does not respond click when the window is maximized.
If reduce the window again. the buttons start working again. 
I have the problems with firefox, edge, brave, visual code, etc.
The problems started when I upgraded to Ubuntu 23.04.

[IMG]https://i.postimg.cc/tC0HkpHb/error1.png[/IMG]

Windows Maximized and click not respond :(

[IMG]https://i.postimg.cc/GmHJpwHB/error2.png[/IMG]

Sorry, me english.

---

### Post by idmbe on 2023-04-24
Hello,

Try this via terminal:
sudo apt-get install --reinstall gnome-shell

then:
reboot

if after that still not work, type this via terminal:
gnome-shell --version

then give me result

---

### Post by l-cardenas83 on 2023-04-25
I don't work with:
[COLOR=#000000]sudo apt-get install --reinstall gnome-shell[/COLOR]

i work with :
[COLOR=#000000]sudo apt-get remove gnome-shell
[/COLOR][COLOR=#000000]sudo apt autoremove
[/COLOR][COLOR=#000000]sudo apt-get install gnome-shell

[/COLOR]Without your help, I couldn't have done it. thank you so much

---

### Post by craig108 on 2023-04-28
Re-installing gnome-shell didn't work for me (tried both methods above).
I'm finding the problem in all my browsers (Brave, Firefox, Chrome).

Any other fixes found?

---

### Post by idmbe on 2023-04-28
> **craig108 said:**
> Re-installing gnome-shell didn't work for me (tried both methods above).
I'm finding the problem in all my browsers (Brave, Firefox, Chrome).

Any other fixes found?

do you mean only browsers had this problem with you ?

what about other windows in system ?

---

### Post by lateganm on 2023-04-30
In my case I had to fiddle around with my display settings. I have three monitors connected to two different screen cards. It worked on two of the three, but on the third one, when maximized, it did not work. So I opened display settings, disabled the monitor that did not want to work, rebooted and the reconfigured all the monitors again. Hope this helps.

---

### Post by khaledhu on 2023-05-03
I have the same problem after upgrading to 23.04, I tried the above solution but did not work with me, the problem with all web browsers I have, chrome, firefox and opera, 
I have 2 monitors connected to my PC

---

### Post by jpmorelli on 2023-08-09
Hi there ! It is happening to me too. Only with web browsers. When maximized, buttons for minimize, restore and close stopped working. If I restore the window with double click in the tittle, works again.

---

### Post by aytovera on 2023-09-30
The same for me on Ubuntu 23.10 with two monitors. The browser buttons that are in the area where the 2 monitors join do not work

---

### Post by gerst2 on 2023-10-29
Did you guys find any working solution?

---

### Post by mcklmo on 2024-07-28
There's an issue on the Microsoft VS Code Github repository addressing this. I shared my solution there: [https://github.com/microsoft/vscode/issues/210624#issuecomment-2254510825](https://github.com/microsoft/vscode/issues/210624#issuecomment-2254510825)

---

### Post by mcklmo on 2024-07-28
[COLOR=#000000][INDENT]There's an issue on the Microsoft VS Code Github repository addressing this. I shared my solution there: [https://github.com/microsoft/vscode/...ent-2254510825]("https://github.com/microsoft/vscode/issues/210624#issuecomment-2254510825")[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by erolhira on 2024-08-05
this happened to me within xorg.
i fixed it with the following actions:

logout
login with wayland
logout
login with xorg

---


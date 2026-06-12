---
title: "How to activate bluetooth daemon in kubuntu ?"
date: 2011-11-10
forum: Desktop Environments
---

### Post by lucky2103 on 2011-11-10
Hiya,
I just migrated away from Ubuntu and I'm very happy with the way Kubuntu 11.10 works.

However, I'm unable to activate bluetooth support on my ACER Aspire 4741G ([http://www.notebookcheck.net/Acer-Aspire-4741G.32734.0.html]("http://www.notebookcheck.net/Acer-Aspire-4741G.32734.0.html"))

Back on Unity, I had to hold down <Fn> and press <F3> for a few seconds to activate bluetooth.
However, this does not work on Kubuntu. Instead, only WLAN is switched on and off.

Does anyone know a solution ?
Thanks alot

---

### Post by mister_playboy on 2011-11-16
Click on the Kickoff menu (blue square with the letter K), then go Applications > Settings > System Settings > Bluetooth.

---

### Post by lucky2103 on 2011-11-17
Thanks for the advice, but there is no 'Bluetooth' icon in the 'System Settings' application.

However, after I switched back to 11.04 (on another partition), the icon is there and Bluetooth works hassle free.
Furthermore, when on 11.04, the <fn> <F3> combination does indeed start the bluetooth daemon, as it does in Unity.

I suspect the problem lies within Oneiric itself ?

---

### Post by lucky2103 on 2011-11-18
Ok, I was finally able to solve the problem by installing and using 'blueman' instead of the native KDE bluetooth daemon.

---

### Post by mister_playboy on 2011-11-18
Interesting you didn't have Bluetooth in System Settings by default... I don't even have Bluetooth on my computer and it gives it to me. :P

You can use the "Thread Tools" to mark this thread solved.

---


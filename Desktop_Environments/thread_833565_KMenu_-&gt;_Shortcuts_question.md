---
title: "KMenu -&gt; Shortcuts question"
date: 2008-06-18
forum: Desktop Environments
---

### Post by jambalaya on 2008-06-18
Hi.
I created an ALT+F shortcut for Firefox-2 this way:
right click on KMenu -> Menu Editor -> Found Firefox2 in Internet menu -> set Default shortcut key to ALT+F.
All was nice, but tomorrow I uninstalled firefox-2, and installed firefox-3. After that, when I used ALT+F I got a message that said firefox2.desktop file in /usr/share/applications does not exist. Also, when I tried to use the same shortcut for firefox-3 in the menu, I got a message that I can't because it is already used by something else.
So the question is, how can I disable the stale shortcut?
I tried looking in many different places but no luck. This time I just installed firefox-2 again, removed the shortcut, uninstalled it, used it for firefox-3 and worked fine. But, it is not a very elegant solution, and I am sure that such a great environment has some file or sth somewhere, where I could look for it.
Thanks.

---

### Post by jambalaya on 2008-06-19
Ok, I found it. Incase anyone ever need to do that:
* you need to start KDE Control Center(*)
* go to Regional & Accessibility -> Input Actions
* on the right, there is a menu "Menu Editor Entries", and there are all the shortcuts to all apps you have
I was affraid I had to find some keymap file to do that, but that was much much friendlier

However, I would like to ask a question. By default, my KMenu didn't have this KDE Control Center anywhere, and it turns out that it has a lot of the same configuration panels as System Settings, but it also has much more - like this one for example, and Security & Privacy -> Crypto panel, which let's you manage your certificates and the certificates you have accepted and so on, and also some SSL / TLS options, like allowing certain algorithms to be used or not. There is also a nice Samba server configuration panel, which I couldn't find in System Settings. Why is that such a nice feature like this Control Centre are not enabled by default? (Of course, I can run kcontrol in the konsole or add an applet to the taskbar, but that's not the same, and if I hadn't found it by accident, I wouldn't know.
Regards.

---


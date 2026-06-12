---
title: "How to run GSConnect Gnome extension"
date: 2022-03-30
forum: Desktop Environments
---

### Post by johnaaronrose on 2022-03-30
I've installed Gnome Shell Extension using Ubuntu 20.04. I was then able to install the Clipboard Indicator extension which then showed up on the top right of the screen (Systray?). I installed the GSConnect extension but it did not have an icon showing in the Systray. I've no idea how to run it. GSConnect is not showing as a process in Systems Monitor. I've put an appropriate comment issue on the extension's web page, but there's no reply. BTW KDE Connect app on my Android phone doesn't see any device: it should see the Ubuntu box if GSConnect was running Ok. Any ideas on how to make GSConnect run?

---

### Post by Frogs Hair on 2022-03-30
I have installed this extension and only see an indicator when I open the extensions settings to complete the installation. I have used kde connect in the past with some success  , but not the GSconnect extension.
There should be a window where a search for the device is prompted.

---

### Post by johnaaronrose on 2022-03-30
> **Frogs Hair said:**
> I have installed this extension and only see an indicator when I open the extensions settings to complete the installation. I have used kde connect in the past with some success  , but not the GSconnect extension.
There should be a window where a search for the device is prompted.

I've 'switched off" GSConnect. I've installed the KDE Connect, which installed a few dependent packages. It gave 4 apps for KDE Connect. I've tried 3 of them but they did nothing visible, although they didn't crash according to System Monitor. The other one gave a 'Configure KDE Settings' window but when I marked my box on it and clicked the Refresh button no devices were displayed. I'm going to submit   a ubuntu-bug for this as I'm not able to ask on KDE Forums as I don't have a KDE Identity Username  or KDE Identity Password.

---

### Post by Frogs Hair on 2022-03-30
Ether method requires a wifi card or device to connect your computer. KDE connect didn't have a stable connection when  I had tried it.

---

### Post by johnaaronrose on 2022-03-30
Both my phone & box have static NAT addresses and are both connected OK to the same router (on the same network) wirelessly.

---

### Post by Frogs Hair on 2022-03-30
> **johnaaronrose said:**
> Both my phone & box have static NAT addresses and are both connected OK to the same router (on the same network) wirelessly.

Did you find the settings for the shell extension when it was installed ?

---

### Post by johnaaronrose on 2022-03-30
When I start the Extensions app, it shows a line for each of the various extensions. When I click on the GSConnect settings icon, it displays a window titled desktop and displays a message "Searching for devices" but never finds my phone.

---

### Post by Frogs Hair on 2022-03-31
You may visited these pages already.I remember having to change a firewall setting when using kde connect on my laptop.     

[https://github.com/GSConnect/gnome-shell-extension-gsconnect/wiki/Help](https://github.com/GSConnect/gnome-shell-extension-gsconnect/wiki/Help)
[https://github.com/GSConnect/gnome-shell-extension-gsconnect/issues/804](https://github.com/GSConnect/gnome-shell-extension-gsconnect/issues/804)
[https://linuxstoney.com/how-to-fix-gsconnect-and-kde-connect-connecting-issue/](https://linuxstoney.com/how-to-fix-gsconnect-and-kde-connect-connecting-issue/)

---

### Post by johnaaronrose on 2022-03-31
Thanks for the links. I've opened an issue on GSConnect.

---


---
title: "messaging menu in notification panel"
date: 2011-08-10
forum: Desktop Environments
---

### Post by tigris666 on 2011-08-10
I have found some info on how to let apps put their icons in the notification panel. This involves using dconf-tools to whitelist some apps in the com.canonical.Unity.Panel gsetting.

Firstly, I'm using ubuntu classic, not unity. I assume the above would still apply for my notification panel settings?

Anyway, that is not my question. What I am wondering, The messaging icon in that panel, when you click it, you see things like "Setup Chat", "Setup Mail" etc. I don't plan on using empathy or evolution. In fact, I've uninstall them both and installed Pidgin instead.

Is there a way to edit that messaging menu to either remove those 2 options at the top that are useless to me, or have them look at other IM/email clients instead of the ones they are expecting to invoke. E.g. "Setup Chat" is irrelevant, as I have already set it up. Since I don't have empathy installed anymore, clicking that option has no effect.

---

### Post by tigris666 on 2011-08-11
I managed to get the "Setup Chat" option to change to "Chat" by re-installing empathy, setting it up and the uninstalling it. But obviously that "Chat" option is still linked to empathy so nothing happens when I click it.

Would love to know how to get these options to link to other clients. Or just remove the messaging menu from there all together and put a Pidgin one in instead.

---

### Post by Krytarik on 2011-08-12
First, make sure there is no file "/usr/share/indicators/messages/applications/empathy" still in place, which shouldn't be after the removal of "empathy":
```
sudo rm /usr/share/indicators/messages/applications/empathy
```Then create the link for the integration of Pidgin:
```
echo "/usr/share/applications/pidgin.desktop" | sudo tee /usr/share/indicators/messages/applications/pidgin
```
You need to relogin for the change/s taking effect.

Greetings.

---

### Post by tigris666 on 2011-08-13
There is no folder named /usr/share/indicators

Upon reboot, the "Setup chat" and "Setup mail" menu options have disappeared.

---


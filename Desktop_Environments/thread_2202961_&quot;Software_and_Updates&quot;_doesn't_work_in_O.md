---
title: "&quot;Software and Updates&quot; doesn't work in Openbox session"
date: 2014-02-01
forum: Desktop Environments
---

### Post by vasa1 on 2014-02-01
When I log into an Openbox session provided by Lubuntu 13.10, I find that "Software and Updates" (= software-properties-gtk) is unresponsive for what I want to do. In the image, I'd like to untick the line relating to dl.google.com. I can't do so. Nor can I untick the line for the ppa just below. If I switch to another tab, and try to tick or untick anything there, I can't do so.

However, if I exit the Openbox session and login to a regular Lubuntu session I can do what I want. So, there's nothing fundamentally wrong with software-properties-gtk.

Any idea on how to get "Software and Updates" to work in an Openbox session?

---

### Post by vasa1 on 2014-02-02
Can some other user of Lubuntu 13.10 please provide feedback?

---

### Post by stinkeye on 2014-02-03
In the openbox session I believe you would have to use ...
```
gksudo software-properties-gtk
```

or 

autostart an authentication agent.
eg for the openbox session, in my **~/.config/openbox/autostart**  file I have an entry to enable an authentication agent and also gnome-keyring...
```
## GNOME PolicyKit and Keyring
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
eval $(gnome-keyring-daemon -s --components=pkcs11,secrets,ssh,gpg) &
```


I think polkit-gnome-authentication-agent-1 is autostarted in the lubuntu session from **/etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop**

---

### Post by vasa1 on 2014-02-03
> **stinkeye said:**
> In the openbox session I believe you would have to use ...
```
gksudo software-properties-gtk
```
...
That worked perfectly. Thanks!

---


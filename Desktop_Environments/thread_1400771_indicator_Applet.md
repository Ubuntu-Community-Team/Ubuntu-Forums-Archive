---
title: "indicator Applet"
date: 2010-02-07
forum: Desktop Environments
---

### Post by kbrill on 2010-02-07
Is there a way to remove evolution and replace it with Thunderbird on the indicator applet?  I would also like to get rid of empathy as well.

thanks

---

### Post by Post Monkeh on 2010-02-07
just delete it altogether and make a luncher to run thunderbird with alltray or kdocker so it's docked to your system tray,

install the new mail icon addon in thunderbird and you have a mail client that sits in your system tray then displays an icon when you get a new email

---

### Post by kbrill on 2010-02-07
> **Post Monkeh said:**
> just delete it altogether and make a luncher to run thunderbird with alltray or kdocker so it's docked to your system tray,

install the new mail icon addon in thunderbird and you have a mail client that sits in your system tray then displays an icon when you get a new email
Doesnt it have something to do with notifications?  If I delete it will I still get notifications?

---

### Post by Post Monkeh on 2010-02-07
> **kbrill said:**
> Doesnt it have something to do with notifications?  If I delete it will I still get notifications?

don't think so, i think it's only to notify you of events in evolution/empathy.
i've never noticed it doing anything else

---

### Post by cviorel on 2010-03-18
> **kbrill said:**
> Is there a way to remove evolution and replace it with Thunderbird on the indicator applet?  I would also like to get rid of empathy as well.

thanks

```

# Create blacklist file
mkdir -p $HOME/.config/indicators/messages/applications-blacklist

# Add the applications you want to blacklist
ln -s /usr/share/indicators/messages/applications/empathy $HOME/.config/indicators/messages/applications-blacklist/
ln -s /usr/share/indicators/messages/applications/evolution $HOME/.config/indicators/messages/applications-blacklist/

# Add the applications you want to appear in the indicator applet
echo '/usr/share/applications/thunderbird.desktop' | sudo tee /usr/share/indicators/messages/applications/thunderbird


```
To see the changes immediately, run:
```
killall gnome-panel
```

---


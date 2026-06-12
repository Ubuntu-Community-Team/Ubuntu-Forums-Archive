---
title: "Remove Last Gnome Panel In Natty"
date: 2011-04-27
forum: Desktop Environments
---

### Post by darrenm on 2011-04-27
Hi there. In Maverick I could remove the last Gnome panel by editing gconf and removing gnome-panel from desktop > gnome > session > required_components.

I've just updated to Natty and doing this makes no difference. I assume Unity is doing it now, or maybe zeitgeist?

I've grep'd through .local and .config, and checked Startup Applications but it still loads gnome-panel every session.

Can anyone suggest anywhere to look?

Thanks.

---

### Post by KegHead on 2011-04-27
Hi!

Will this help?

system...admin..login..choose default?

KegHead

---

### Post by Copper Bezel on 2011-04-27
Right, are you using the Unity desktop or the Classic one? If it is the old Gnome-2-style one and the gconf key is being ignored for some reason, there are a couple of other tricks we can use (putting the panel on the widget layer or simply marking the panel binary as non-executable.) (Check your Startup Applications, too, as silly as that sounds.)

---

### Post by darrenm on 2011-04-28
> **KegHead said:**
> Hi!

Will this help?

system...admin..login..choose default?

KegHead

Sorry not in this case I don't think.

> **Copper Bezel said:**
> Right, are you using the Unity desktop or the Classic one? If it is the old Gnome-2-style one and the gconf key is being ignored for some reason, there are a couple of other tricks we can use (putting the panel on the widget layer or simply marking the panel binary as non-executable.) (Check your Startup Applications, too, as silly as that sounds.)

Using classic desktop. Unity causes issues with my dual-monitor setup and it's a bit pointless anyway for me when I want to remove all panels.

Can't see it in Startup Applications. Good shout on removing x from gnome-panel binary though. I'll try that thanks.

---

### Post by darrenm on 2011-04-28
And it did work. Thanks!

```
sudo chmod -x /usr/bin/gnome-panel
```

Log out and back in. Sorted :)

---

### Post by Krytarik on 2011-04-28
- Remove "panel" from the Gconf key "/desktop/gnome/session/required_components_list".

- If that doesn't help either, remove the content of "~/.config/gnome-session/saved-session".

Greetings.

---

### Post by Non Sek on 2011-05-04
Hi,

I solved this problem based on this bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/774357](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/774357)

Go to usr/share/gnome-session

Edit as root the file "classic-gnome.session" and change the following line

From:   Required-panel=gnome-panel        
To:       Required-panel=avant-window-navigator 
 (or your panel option)

I also "commented" the lines below, to avoid the test and the fallback.
## IsRunnableHelper=/usr/lib/nux/unity_support_test --compiz
## FallbackSessionsID=GNOME2d
## GNOME2d=2d-gnome

  In the user login page, choose "Classic Ubuntu".

  Then the last panel was gone. I believe this solution can be improved (it affect all users in the machine). So, comments will be appreciated.

Regards, NS.

---

### Post by kkjaergaard on 2011-09-02
> **Non Sek said:**
> ...
Go to usr/share/gnome-session

Edit as root the file "classic-gnome.session" and change the following line

From:   Required-panel=gnome-panel        
To:       Required-panel=avant-window-navigator 
 (or your panel option)
...

Is it possible to fully remove the last panel without root access and without affecting the other users of the system?

---


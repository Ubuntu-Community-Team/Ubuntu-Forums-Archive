---
title: "system tray notification from a script"
date: 2009-02-25
forum: Desktop Environments
---

### Post by lvm on 2009-02-25
I am looking for utility which will let scripts post system tray notifications. Can you recommend one? Something like

tray_notify "Wedding annivesary tomorrow"

and it will show an alert icon in system tray which when clicked shows the message.

kubuntu heron if it matters

---

### Post by mcduck on 2009-02-25
At least on Gnome you can use Zenity to create notification icons (as wella s lots of other dialogs and stuff):

```
zenity  --notification  --window-icon=youricon.png  --text "Wedding annivesary tomorrow"
```

This will show an icon in the notification area, and your message as tooltip when you move your mouse over the icon. Clicking the icon will make it disappear.

edit: I'm not sure how to get a proper notification when clicking the icon instead of just a tooltip. But since, when sued in scripts, the script will stop to wait until the icon is clicked, you could just use a normal dialog to display your message after the icon is clicked.

---

### Post by lvm on 2009-02-26
It works in KDE too, thanks.

---

### Post by jtsop on 2009-03-17
is there a way for this to work on another machine (when logged in remotely via ssh)

---


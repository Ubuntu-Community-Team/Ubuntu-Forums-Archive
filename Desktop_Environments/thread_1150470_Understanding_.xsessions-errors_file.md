---
title: "Understanding .xsessions-errors file"
date: 2009-05-06
forum: Desktop Environments
---

### Post by lesliek on 2009-05-06
I upgraded from v 8.04 to v 8.10. A consequence was that my desktop icons disappeared and using gconf-editor doesn't bring them back. I found an inconclusive bug report about the problem, from which it seemed that one might get a clue as to the problem from the .xsessions-errors file.

I looked at mine and also at the same file on another computer I have that's also running v 8.10, but which does show my desktop icons. Many of the errors shown were the same, but some were different.

Can anyone tell me how to overcome the following errors/warnings that I've extracted and numbered:

1. Unable to create /home/leslie/.dbus/session-bus

2. x-session-manager[6188]: WARNING: Could not parse desktop file
/home/leslie/.config/autostart/cgmailservice.desktop: Key file does not have key 'Type'
x-session-manager[6188]: WARNING: could not read
/home/leslie/.config/autostart/cgmailservice.desktop

3. (gnome-panel:6345): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24

Is any of them likely to have caused my desktop icons problem?

Thanks for reading this.

EDIT: I opened a terminal. I typed nautilus and pressed Enter. My desktop icons came back. I closed the terminal. The icons disappeared. Although I'd still like to know about the above errors, is there a way I can automate the above process on start-up to get around the disappearing icons?

---

### Post by kpkeerthi on 2009-05-06
GNOME autostarts certain applications & daemons at login. You may want to reset it back to defaults. To do this, open nautilus, and look for a hidden folder **.config**. Open the folder and rename the folder **autostart** to **autostart_backup** and Reboot.

---

### Post by lesliek on 2009-05-06
Thanks for your reply.

I'm sorry, but I don't understand precisely what to do when you say "open nautilus, and look for a hidden folder .config."

---

### Post by kpkeerthi on 2009-05-06
1. Open terminal and enter ```
nautilus ~
```
2. Press Control + h to see hidden files and folders
3. You should now see a folder named **.config**. Double-click on it. Now rename the folder **autostart** to **autostart_backup**
4. Reboot

GNOME should now reset all the required login start up applications to defaults. Hopefully now you desktop icons appear.

---

### Post by lesliek on 2009-05-06
Thank you very much. That seems to have worked.

After rebooting, I followed the first two of your steps again, expecting to find in .config a new folder called autostart, but I didn't. I only found the autostart_backup folder I'd created by renaming the original autostart.

Should there have been a new autostart folder?

---

### Post by kpkeerthi on 2009-05-06
No, unless you have custom startup applications in System -> Preferences -> Startup Applications.

---

### Post by lesliek on 2009-05-06
Thank you very much for that additional information and for your help generally.

---

### Post by kpkeerthi on 2009-05-06
You are welcome. Enjoy Ubuntu!

---


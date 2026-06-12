---
title: "After killing a process no more taskbar and empty desktop"
date: 2010-02-13
forum: Desktop Environments
---

### Post by janvandongen on 2010-02-13
I'm a newby to Linux. I installed Ubuntu 9.10 on an old Dialogue Flybook A33i.
 
Everything worked fine, until I followed someone's advice how to kill a process that was hanginging (something innocent, a game that didn't want to close), seeking a parralel with Windows crtl-shift-esc. The advice was as follows: "ALT + F2 will open the run dialog, then type "xkill" and click on the problematic application."
 
I did that, and the end result is:
I see an empty desktop without icons, and the taskbar has vanished. The only thing I can do is right click the desktop, but that doesn't seem lead to anything useful.
 
What did I try:
--> Alt-F2 does not work so I cannot open a terminal.
--> I tried ctrl-alt-F1 which works, but after login and password I try typing commands but after hitting enter nothing happens.
--> I restarted several times
 
I was so glad I got my first Linux installed, please help me!
 
Be so kind to help in clear steps. In Windows I'm advanced and used to edit the registry by hand, but in Linux I will need it a bit more written out.
 
 
Thanks!

---

### Post by janvandongen on 2010-02-17
Anybody? I would really appreciate your help.
I searched everywhere in this and other forums, but can't find an answer.  ](*,)

---

### Post by nothingspecial on 2010-02-17
What did you kill? I`m wondering weather you killed your panel by mistake.

---

### Post by janvandongen on 2010-02-19
I clicked on the button of the process as it appeared on the taskbar. Thereby it was probably interpreted as attempting to kill the taskbar itself...
 
Do you have any idea what I should do to restore it?
 
Regards,
Jan

---

### Post by Hero of Time on 2010-02-19
Make sure you're not logged in graphically, then switch to a TTY using ctrl+alt+f2. Change directory to ~/.cache/sessions and remove all files there. Log out and switch back to the graphical interface. Log in and you should have everything back.

You can also select a different session from the login screen, e.g. Default Gnome, instead of Last Session.

---

### Post by janvandongen on 2010-02-24
I really appreciate your help. 

I'm an absolute beginner in Linux unfortunately, (advanced in Windows hacking but it doesn't help me at all I notice..).

Could you take me by the hand:
1) How do I log on without letting the graphical environment take control, (which happens by default). Is there a key combonation I use during booting?
2) Switching to TTy means to a terminal I assume, so that seems clear; press ctrl+alt+f2.
3) what is the command for changing directory. cd space and then the string you mentioned, (like in DOS)?

Sorry for the newby level.

Regards,
Jan

------ 

> **Hero of Time said:**
> Make sure you're not logged in graphically, then switch to a TTY using ctrl+alt+f2. Change directory to ~/.cache/sessions and remove all files there. Log out and switch back to the graphical interface. Log in and you should have everything back.

You can also select a different session from the login screen, e.g. Default Gnome, instead of Last Session.

---

### Post by MooPi on 2010-02-24
You can log in normally and use ```
ctrl+alt+F1
``` to get to a command line. then type ```
cd ~/.cache/sessions
``` to get to the proper directory. The previous post recommends you delete all the contents of this directory. Type : ```
ls
``` Then ```
rm "whatever was listed above"
``` this deletes everything in the sessions folder. Now at the prompt  ```
sudo reboot
``` And log back in.

---

### Post by Hero of Time on 2010-02-25
You can use 'rm *' when you are certain you are in the proper forlder. After you've done that, type 'exit' to logout and then ctrl+alt+F7 to switch to the GUI. You don't need to reboot.

Now, if that doesn't solve your problem, try Alt+F2, it should open a run dialogue, and type 'gnome-panel'. That should give you your panels back. If the desktop is still empty, without a wallpaper and icons, and right clicking it doesn't do anything, hit alt+F2 again and type 'nautilus'. It might need a parameter, I don't know as I don't use gnome, but it should give you your desktop back.

---


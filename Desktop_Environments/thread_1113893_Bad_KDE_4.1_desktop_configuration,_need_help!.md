---
title: "Bad KDE 4.1 desktop configuration, need help!"
date: 2009-04-02
forum: Desktop Environments
---

### Post by wizoo on 2009-04-02
I have a problem.

I've recently installed Kubuntu Intrepid, and when I was playing around in the settings manager, when I set the desktop window effects, the desktop wouldn't show. Since then it's just a black screen with the mouse cursor.

Is there a way to access the KDE control center through the console and could I get any instructions on how to reset the display settings to default? 

There's also another minor problem, which is not so vital. If I boot my Kubuntu instal with the splash screen, it freezes while loading. Though, if I remove "quiet splash" from the kernel boot options it loads just fine. Is this just a buggy splash screen or is it something else?

My graphic card: Nvidia Geforce 9600m GT.

---

### Post by wizoo on 2009-04-03
Anybody??

---

### Post by NightwishFan on 2009-04-03
To reset your configuration:

[LIST]
[*]Log out
[*]Press ctrl+alt+f5 (you should see a console)
[*]Log in on console
[*]Type (no quotes) "rm -r .kde"
[*]Reboot
[*]See if it works
[/LIST]

If that doesn't work try:

[LIST]
[*]Log out
[*]Press ctrl+alt+f5 (you should see a console)
[*]Log in on console
[*]Type (no quotes) "rm -r .*"
[*]Reboot
[*]See if it works
[/LIST]

The former should reset your kde configuration, the latter will reset all configuration.


About the splash screen, I have no idea. Try searching for splash screen problems.

---

### Post by Giblet5 on 2009-04-03
The usplash issue is probably a *monitor* problem: your monitor loses sync with the chosen graphics mode that usplash is using. eg, LCD monitors don't like 85hz vertical refresh...

Search around for terms like usplash vesa grub and menu.lst and you'll find the list of VESA resolutions. Start with 640x480, then try others until you're satisfied.

You can alter this from the grub boot menu, btw.

---

### Post by Giblet5 on 2009-04-03
> **NightwishFan said:**
> To reset your configuration:

[LIST]
[*]Log out
[*]Press ctrl+alt+f5 (you should see a console)
[*]Log in on console
[*]Type (no quotes) "rm -r .kde"
[*]Reboot
[*]See if it works
[/LIST]

If that doesn't work try:

[LIST]
[*]Log out
[*]Press ctrl+alt+f5 (you should see a console)
[*]Log in on console
**[*]Type (no quotes) "rm -r .*"**
[*]Reboot
[*]See if it works
[/LIST]

The former should reset your kde configuration, the latter will reset all configuration.


About the splash screen, I have no idea. Try searching for splash screen problems.


I hope the guy doesn't have any email or plugins he hasn't backed up!  :popcorn:

---

### Post by rattking on 2009-04-03
Hi I think the setting for composting is in
.kde/share/config/kwinrc

edit that file with a console text editor
such as 
```
vim ~/.kde/share/config/kwinrc
```

and in the [Compositing] section 
change 
Enabled=true to
Enabled=false

and try to login again from kdm

actually there is not any critical settings in that file so you could just delete it and let kde return to defaults
that will preserve the rest of kde's settings, e-mails, and book-marks 

```
rm ~/.kde/share/config/kwinrc
```

---


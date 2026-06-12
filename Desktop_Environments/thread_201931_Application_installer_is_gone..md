---
title: "Application installer is gone."
date: 2006-06-22
forum: Desktop Environments
---

### Post by minkoo.seo@gmail.com on 2006-06-22
Hi folks.

I've installed Ubuntu Dapper quite recently and having fun with it. But I got two problems:

1) My update-notifier is missing. I've googled and searched this forum and I found that /etc/apt/sources.list should be mode 644 and reinstalling update-manager/update-notifier might help. Unfortunately, my sources.list is 644 mode, and reinstalling them did not help. I also added notifier section in the panel. My update-notifier is running in the background.

So I'd like to ask: Does update notifier appear only when newly added update?


2) During trying to fix update-notifier, I happened to remove application installer/remover application which was located at the end of 'Apps' menu. Could you let me know the name of application so that I can reinstall it?

Sincerely,
Minkoo Seo

---

### Post by bukwirm on 2006-06-22
The update icon only appears in the panel when updates are availible.
For the Add/Remove Programs application, try the package 'gnome-app-install'

---

### Post by johnc4510 on 2006-06-22
1. Notifier icon only appears when there are new updates that have been identified.
2.Open Synaptic: System>Administration>Synaptic Package Mgr.
Scroll down in the window to Update-Manager and Update-Notifier and mark to install

---

### Post by minkoo.seo@gmail.com on 2006-06-22
Thank you for the reply.

But, update manger is located under system->management. Right? (Sorry, I don't know the exct name of the menu cuz I'm using Korean version.)

What I've uninstalled is one that was located at the end of the apps menu(the leftmost menu). Any idea?

Thanks.

[QUOTE=johnc4510]1. Notifier icon only appears when there are new updates that have been identified.
2.Open Synaptic: System>Administration>Synaptic Package Mgr.
Scroll down in the window to Update-Manager and Update-Notifier and mark to install[/QUOTE]

---

### Post by johnc4510 on 2006-06-22
Try this to see if you really removed it. Open:
Applications>Accessories>AlaCarte Menu Editor
Click on Applications and scroll to the bottom and see if Add/Remove is there. If it is, make sure it has a check mark in the box beside it.

---

### Post by minkoo.seo@gmail.com on 2006-06-22
Yes!!! That's what I removed!

There's no Add/Remove in the menu editor :( 

[QUOTE=johnc4510]Try this to see if you really removed it. Open:
Applications>Accessories>AlaCarte Menu Editor
Click on Applications and scroll to the bottom and see if Add/Remove is there. If it is, make sure it has a check mark in the box beside it.[/QUOTE]

---

### Post by johnc4510 on 2006-06-22
Type these commands in terminal:
sudo aptitude update
sudo aptitude install gnome-app-install

---

### Post by minkoo.seo@gmail.com on 2006-06-22
Thank you! Problem solved :-)

p.s. I've never seen a forum where I can get answers as quick as Ubuntu. Now I see why Ubuntu rocks. 

[QUOTE=johnc4510]Type these commands in terminal:
sudo aptitude update
sudo aptitude install gnome-app-install[/QUOTE]

---


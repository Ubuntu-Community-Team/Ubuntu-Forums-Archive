---
title: "No Oxygen theme on sudo'ed GTK applications"
date: 2009-05-10
forum: Desktop Environments
---

### Post by jackhab on 2009-05-10
I'm on Kubuntu 9.04.

When I open a GTK application with root privileges the application has GTK look, when I run it as normal user it has Oxygen theme.

See attached picture. The bigger Wireshark window created by [FONT="Courier New"]sudo wireshark[/FONT] the smaller one by plain [FONT="Courier New"]wireshark[/FONT] command.

Why does it happen?

Thanks.

---

### Post by VCoolio on 2009-05-10
themes you install are stored in ~/.themes and icons in ~/.icons. If you want to use them with root apps move them to /usr/share/themes and /usr/share/icons.

---

### Post by jackhab on 2009-05-10
> **VCoolio said:**
> themes you install are stored in ~/.themes and icons in ~/.icons. If you want to use them with root apps move them to /usr/share/themes and /usr/share/icons.

I don't have neither .themes nor .icons on entire file system.

---

### Post by LinuxGuy1234 on 2009-05-10
sudo uses root's files. gksu and running as a user uses the user's files.

---

### Post by jackhab on 2009-05-11
> **LinuxGuy1234 said:**
> sudo uses root's files. gksu and running as a user uses the user's files.

This is known to me. The question is which files are responsible for selecting application theme.

---

### Post by micio on 2009-05-11
Try to copy the themes and icons files from you home (/home/your_user_name/) to root directory with the same structure.
I use gnome and i have gtk themes and icons in /home/my_user/.themes and .icons, so i copy the content this folder to /root/.themes and /root/.icons (the first time I must create those 2 folders).
In kde I don't remember where they are located, maybe is the same place because we are talking about GTK apps, but if not, try to look into .kde folder.

---

### Post by oobuntoo on 2009-05-17
> **jackhab said:**
> I'm on Kubuntu 9.04.

When I open a GTK application with root privileges the application has GTK look, when I run it as normal user it has Oxygen theme.

See attached picture. The bigger Wireshark window created by [FONT="Courier New"]sudo wireshark[/FONT] the smaller one by plain [FONT="Courier New"]wireshark[/FONT] command.

Why does it happen?

Thanks.

This problem has been around a long time. To get around it do the following.

For KDE 3.5.10 system do:

**sudo ln -s ~/.gtkrc-2.0-kde /root/.gtkrc-2.0**

For KDE 4 system do:

**sudo ln -s ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0**

Use 

**kdesudo systemsettings** 

to change themes for KDE apps that run under root privilege.

---

### Post by jackhab on 2009-05-17
Finally!!! The link trick works. Thanks a lot, oobuntoo.

---

### Post by the_mouse on 2010-02-15
THANK YOU! Has someone filed a bugreport on this? This bug is still present in kubuntu 9.10 and it's pretty easy to fix, so there shouldn't be a problem to do so.

---


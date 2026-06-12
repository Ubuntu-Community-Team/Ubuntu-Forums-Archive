---
title: "Can I run as SU and using the desktop?"
date: 2010-03-27
forum: Desktop Environments
---

### Post by gmushial on 2010-03-27
Is there a way to be "root" and still use the desktop/GUI? It seems that I have to have two modes in being an Ubuntu user: if I'm non-administrative things, then I use the desktop, but as soon as I need to update a conf file, do a chown etc, then I have to move to the command line and SUDO. I have to admit it: the GUI interface is much quicker for me... is there a way to continue to use it, but be SU. What brought this up is: I'd like to set a share for one of the apache directories - from the desktop it's a simple matter of clicking on Shares on a folder's properties and I'm done... unfortunately in this case I don't have permissions (as my normal user self) to share the directory I need. So... now I have to figure out how to talk to samba from the commandline to do the same... this should have been a 15 second job; now I have to browse, google and read to figure this out :-( . Any insight would be appreciated.
TIA, greg
ps. the system in question is 9.10 server

---

### Post by ajgreeny on 2010-03-27
If you are using gnome you can open a gui application with root privileges by using ```
gksudo application-name
```which you can either do in the Alt+F2 run box, or in terminal, or by making a launcher, if there are certain apps you need often

---

### Post by gmushial on 2010-03-27
aj-
Thanks for the reply...  but what I'm trying to do, or, would like to do, is to be able to run the desktop as SU/root. The gksudo business I knew. What I'd like to be able to do is: to be able to go to "places | files " (from the desktop)...  browse the filesystem, and then when I find the directory I'm interested in, "share" it by right clicking on it, clicking on "sharing" and create a share for it, with the privs/attributes I wish...  instead of having to try to create shares from a command line. As much as I'm coming to appreciate Ubuntu, one frustration I'm having is not being able to log in as root and do root things...  having to use sudo to do root things makes everything slower / more time comsuming than necessary.
again, thanks,
greg

---

### Post by louieb on 2010-03-27
[forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

The short of it is -  it against forum policy.

 > ... having to use sudo to do root things makes everything slower / more time comsuming than  necessary.Just my 2 cents worth - I disagree - I can type sudo a lot faster that I can log out - do what ever as root - then log out again - and log back back on to my normal user account.

---

### Post by asmoore82 on 2010-03-28
> **gmushial said:**
> **Can I run as SU and using the desktop?**

The answer is "yes." But...

If you were to ask *can* you strip naked and
attempt to arm wrestle a grizzly bear in the wild...

That answer would be "yes" as well.

For best results, start another thread and ask a more specific question.
Something with "samba" in the title I believe would be in order.

---

### Post by asmoore82 on 2010-03-28
You can adhere to the *sudo* philosophy and still get a single
nautilus "File Browser" window by running this:
```
gksudo nautilus
```

Right-clicking and sharing a folder is *_not_* the same thing as creating a
real samba sharepoint. The right-click method creates a so-called "usershare"
You can view all active usershares in the folder "/var/lib/samba/usershares"

If you would rather edit real samba shares with a GUI instead of the command line,
install the package "system-config-samba" ~ this is Red Hat's samba tool.
It should show up in the menu at "System -> Administration -> Samba"

In general, if you have to `chown` very often it is a good sign that
you are not using a Unix system properly.

---


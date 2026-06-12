---
title: "Switching Users"
date: 2005-04-18
forum: Desktop Environments
---

### Post by mrmoose19 on 2005-04-18
Is there a way to switch users and leave the programs running, as in XP?  If I could make the system do that, I think my family'd fully convert...

---

### Post by shakin on 2005-04-18
[QUOTE=mrmoose19]Is there a way to switch users and leave the programs running, as in XP?  If I could make the system do that, I think my family'd fully convert...[/QUOTE]

I believe there is a Gnome fast-user-switch applet that does what you want. No idea where to get it.

---

### Post by wolovids on 2005-04-18
Here's the [homepage](http://ignore-your.tv/fusa/) for the Gnome Fast User Switch Applet ... enjoy!

---

### Post by mgor on 2005-04-18
program -> system tools -> new login

i've got swedish text so i'm not 100% sure about the translation.

---

### Post by shakin on 2005-04-18
Better yet, from [this thread](http://ubuntuforums.org/showthread.php?t=24392).

Go to Applications -- System Tools -- New Login. You'll get the login screen on the F8 terminal. You can keep adding users and switching between them using ctrl-alt-f7 through ctrl-alt-F? as needed.

---

### Post by wolovids on 2005-04-18
[QUOTE=shakin]Better yet, from [this thread](http://ubuntuforums.org/showthread.php?t=24392).

Go to Applications -- System Tools -- New Login. You'll get the login screen on the F8 terminal. You can keep adding users and switching between them using ctrl-alt-f7 through ctrl-alt-F? as needed.[/QUOTE]
I like the idea of having a user switching applet instead of having the user pressing some three-key combination.  I know my wife would kill me if I told her to hold in ctl-alt-f7 or f8 or ... you get the idea!  

Wife mad = bad  ;-)

---

### Post by Mr Wonka on 2005-04-18
I couldn't find a package of the fast user switching applet so I made one using checkinstall. 

It's available here: [http://www.salienttraits.com/files/fast-user-switching-applet_0.2.1-1_i386.deb](http://www.salienttraits.com/files/fast-user-switching-applet_0.2.1-1_i386.deb)

After you install it you add it to your panel by right clicking on the panel and clicking "add to panel". It's listed as "User Switcher".

It makes things so easy. Though there are a few bugs with various things.
Here: [https://bugzilla.ubuntu.com/show_bug.cgi?id=9895](https://bugzilla.ubuntu.com/show_bug.cgi?id=9895)
and here: [https://bugzilla.ubuntu.com/show_bug.cgi?id=9896](https://bugzilla.ubuntu.com/show_bug.cgi?id=9896)

Hope this helps

---

### Post by mrmoose19 on 2005-04-18
I don't know how indulgent you're all feeling this morning...but could you just kind of walk me through how to install the fast-user-switch applet?  New to Linux and the install file is Greek to me, and I really don't have that much time to sit and hammer it out...lots of hw to still do...thanks! :grin:

---

### Post by Mr Wonka on 2005-04-18
Ok. Say you save it to your desktop. You should type in a console window:

```
sudo dpkg -i /home/%username%/Desktop/%filename%.deb
```

Where %username% is your username and %filename% is the name of the package.

Then just add it to your panel as described above. Each user will have to add it to theirs to utilise it.

Hope this helps.

---

### Post by foxy123 on 2005-04-19
I've got the same problem with KDE. In SuSE KDE has an option Switch User, while in Ubuntu the only option available is Log Out. Even it does not Reboot or Turn Off. I cannot find how to enable it. I'm using Ubuntu with KDE added later. Could it be gdm vs kdm issue?

---

### Post by JamesCape on 2005-05-12
Unfortunately, KDM and GDM have different protocols for applications that wish to use "advanced" features (like creating new sessions). KDE's user-switching stuff requires you be running KDM (just as the fast-user-switch-applet requires you be running GDM).

---

### Post by foxy123 on 2005-05-19
[QUOTE=JamesCape]Unfortunately, KDM and GDM have different protocols for applications that wish to use "advanced" features (like creating new sessions). KDE's user-switching stuff requires you be running KDM (just as the fast-user-switch-applet requires you be running GDM).[/QUOTE]
But gdmflexiserver command works fine in KDE. Is it possible to put it in the logout screen somehow?

---


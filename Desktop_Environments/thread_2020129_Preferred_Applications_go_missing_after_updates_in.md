---
title: "Preferred Applications go missing after updates in 11.10"
date: 2012-07-07
forum: Desktop Environments
---

### Post by stlu on 2012-07-07
Hi,

Today I ran #apt-get upgrade for the first time on a fresh install of xubuntu 11.10, and after all was done, my preferred applications were missing.

Namely:
"Web Browser" - I don't really care, I just pick firefox
"Mail Reader" - I never used it anyway
"Accessories -> File Manager" - It is working, as I can still open folders, drives, etc.  Just this launcher is broken

"Terminal Emulator" - This is what I am most interested in getting back, as I don't know all the details about the environment variables, and I would like to stick with the default.

Can anyone list the default binaries for these 4?  Especially the terminal emulator, since I can't seem to choose between "xfce4-terminal", "x-terminal-emulator" and "xfce4-terminal.wrapper" in /usr/bin when I was prompted to go figure it out, by the dialogue box.  Can anyone tell me which binary is used in the default install?

And is there any way to prevent this from happening, or should I report a bug?

Thanks,

---

### Post by stlu on 2012-07-20
Launchpad.net currently does not accept bugs for Xubuntu.

user "Dice" on Xubuntu IRC says that 11.10 uses an old version of xfce, and plus it is not a LTS version, so no point in reporting a bug.  I did know the web browser was firefox, mail reader was thunderbird, and file manager was thunar.  And Dice told me it is xfce4-terminal that is the correct binary for the terminal, not the other two.

I hope that 12.04 does not have the same problem after updates.

For anyone interested, the affected config files are found under the users home directory when I set the new preferred applications (I found using $ find /home/user/ -mmin -10):
./.local/share/xfce4/helpers/custom-MailReader.desktop
./.local/share/xfce4/helpers/custom-FileManager.desktop
./.local/share/xfce4/helpers/custom-TerminalEmulator.desktop
./.local/share/xfce4/helpers/custom-WebBrowser.desktop

So perhaps keeping a backup copy of these will allow manual restoration after the update alters or removes them. (fingers crossed)

---

### Post by Whovian on 2012-07-20
Stlu I have the 12.04 xubuntu running right now on my machine an those type of problems are not happening so yes the problem is fixed in 12.04 it seems.

---

### Post by protozorq on 2013-01-09
Bug still exists in 12.04 and 12.10.

---


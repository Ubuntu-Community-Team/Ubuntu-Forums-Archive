---
title: "Ubuntu Installation Error HELP!!!!!!!!!!"
date: 2009-02-11
forum: General Help
---

### Post by fernandocra on 2009-02-11
[B][LEFT][FONT="Century Gothic"][COLOR="YellowGreen"][FONT="Century Gothic"]	
help me install ubuntu 8.4 but the uninstall, when we want to install again I get this

[COLOR="Red"]BusyBox V1.1.3 (DEVIO 1:1.1.3-5ubuntu12) Built-in shell (ash) Enet "Help" for a list of built-in comands
(INITRAMFS)[/COLOR]

I installed Ubuntu on a shared partcion not let me install but I get that same
I do not want to install on your hard drive completely, because I have Windows and Linux as it had earlier mind please help[/FONT][/COLOR][/FONT][/LEFT][/B]

---

### Post by fernandocra on 2009-02-11
please help me

---

### Post by the_analyzer on 2009-02-12
I have the same problem. can anyone help us??

---

### Post by Regnulify on 2009-02-12
If you are running vista it is advisable to create your partition in vista first for ubuntu to install into. It is possible that the installer is not seeing an available drive and giving you this error.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by jespdj on 2009-02-12
Sorry, but I don't have a solution for you.

However, I've seen posts before of people who have similar problems. Try searching the forums for "BusyBox" and you might find some useful older posts with more information.

---

### Post by jmszr on 2009-02-12
fernandocra,
             Am I correct that you are installing via Wubi? If so,this should work:

Try The Following Solution: 1) Boot into Windows, Go to "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking (On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do Not hard reboot) and try using Ubuntu now.

You can also go to the windows commandline and run chkdsk/f .

All of this, of course, is if you are using Wubi.

If you are getting "initramfs" on your first boot up with Wubi then I would suggest going to the Wubi forum and search "initramfs on install". Various posts and solutions for that problem are listed there.

---


---
title: "Ubuntu 9.04 - missing shutdown menus"
date: 2009-07-22
forum: Desktop Environments
---

### Post by .kkursor on 2009-07-22
Hello all!
I know that this topic has been discussed for dozens of times, but I have not found the solution for my particular issue and ask for help.
I have received a task to create free-licensed operating system to replace Windows 2000/XP on the computers, on which Windows is not licensed to use. The primary goal is to connect to Windows 2003 terminal servers and to create a vision to the policemen who check software licenses that the computer is a complete workstation (and therefore hide the terminal servers from their sight). I chose Ubuntu as I am using it as the only operating system for two years.
I installed the core system with OpenOffice, Firefox, Skype, nginx (to store scripts, tarballs and Java-based VNC client), VNC for remote support and Tsclient+Rdesktop (patched for russian keyboard layouts). The window manager is the minimal installation of GNOME (gnome-core package, if I am not mistaken). Then I developed two scripts - one to create complete tarball of the root filesystem and /boot partition (sda2 and sda1 respectively) and to prepare a hard drive of the machine and deploy tarball here. And everything seems to work fine - the complete deployment takes about 30 minutes. But on some machines option "Shut Down" from main menu is missing. On some it is present. That is very strange because all machines are deployed using the same tarball (in fact the system is a bit more complex, I may create a machine, fix all bugs (if any), create a tarball of it and install from it).
I will summarize. I have a machine named admin. The system works there perfectly. I create tarballs from it. Then I boot a machine named ar with a pirated Windows 2000 on it from RIPLinux LiveCD/PXE image, download and run my script. It fills first 512 bytes of /dev/sda with zeros, creates 2 partitions (128M for /boot and the rest for /), copies tarballs from the given server, unpacks it, write new hostname to configuration files, installs GRUB and offers to reboot. And it works perfectly, but on some machines there is no shut down entry in System menu. There is a logout entry, but it allows only to log out to gdm (user switching is not possible).
There are two users on machine named "administrator" and "user" (with and without sudo permissions respectively) and gdm logs "user" in automatically without prompting password. When I log in as administrator, there is no "Log out" entry in the menu too. Fast user switch applet also does not allow to shut down or reboot system, at last I purged it away from the system. "gnome-session-save --shutdown-dialog" displays shut down window, and the system can be rebooted or shutted down correctly by user and administrator. I have added it to menu on problematic machines as a temporary solution. When power button is briefly pressed, the system shuts down correctly too. All respective permissions in policy kit are set.
The question is - why did shut down and logout entries disappeared from system menu and how to bring them back?
I've googled all the internet back and forward but found nothing that could help.

I am ready to provide any information you ask.
Thank you very much.
I need your support, please.
Kirill, Moscow, Russian Federation

---


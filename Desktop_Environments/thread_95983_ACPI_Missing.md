---
title: "ACPI Missing"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Travisty on 2005-11-27
I have been using Breezy on my Fujitsu laptop since it was released as a public preview. I have had no problems with it that I couldn't figure out until now. I used to be able to hibernate to computer from Syetem - Logout. I no longer have that option and I want it back due to it's convienence. I do have acpi, acpid, and acpi-support installed. I am not interested in using Suspend2. Any rhoughts on how to fix this?

---

### Post by dcstar on 2005-11-28
[QUOTE=Travisty]I have been using Breezy on my Fujitsu laptop since it was released as a public preview. I have had no problems with it that I couldn't figure out until now. I used to be able to hibernate to computer from Syetem - Logout. I no longer have that option and I want it back due to it's convienence. I do have acpi, acpid, and acpi-support installed. I am not interested in using Suspend2. Any rhoughts on how to fix this?[/QUOTE]
Do you have gnome-power-manger installed?

---

### Post by htoerrin on 2005-11-28
Check out /etc/default/acpi-support

The line
#ACPI_HIBERNATE=true
should be uncommented.

Havard

---

### Post by Travisty on 2005-11-29
I do have gnome-power-manager. It is not fully fuctional either. It won't suspend or hibernate. 
I checked /etc/default. I don't have acpi-support listed in there. I have tried reinstalling acpi-support but it is still not listed in /etc/default. The closest file I have is acpid but there is nothing about hibernate in there.

---

### Post by Travisty on 2005-12-01
I fixed the problem. I had to remove all of my acpi-support. I chose remove completely. Then I re-installed all of the acpi items I removed. Using the comment provided by **htoerrin**, I changed my acpi file, rebooted and I now have all of my previos power down options. The real question becomes how did they get removed? Thanks everyone for you help.

---

### Post by manis on 2005-12-01
HI,
I faced same problem with my notebook ( fujitsu lifebook) when I upgrade to Breezy. My notebook  refuse to shutdown when it suspended or hybrent. So I switch back to hoary. 
Thank a lot for my friend - Travisty for your suggestion. I will migrate to Breezy and try to solve my old problem regarding your opinion.
I hope my problem with Breezy will gone!
tk

---


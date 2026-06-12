---
title: "Restricting Users in Ubuntu 12.04 64bit Desktop"
date: 2012-07-19
forum: Desktop Environments
---

### Post by mmehboobhan on 2012-07-19
Hi all.

I am customizing Ubuntu 12.04 Desktop for a school lab.  So i install gnome classic and made the desktop environment just like Windows using compiz and ubuntu tweak etc.
Now i want to  restrict normal users from following..


[LIST]
[*]Restrict users changing wallpapers & themes
[*]Restrict users adding / deleting system panels.
[*]Restrict users installing / deleting packages.
[*]Restrict users to delete desktop icons.
[*]Restrict to change IP address manually.
[*]Disable USB storage devices.
[/LIST]
Any help in this regard will be highly appreciated.

Thanks in Advance


Khan

---

### Post by ykkhern on 2012-07-24
> **mmehboobhan said:**
> 


[LIST]
[*]Restrict users installing / deleting packages.
[*]Restrict to change IP address manually.
[/LIST]


Just create the USER account with account type "Standard" will do.

> **mmehboobhan said:**
> 


[LIST]
[*]Disable USB storage devices.
[/LIST]


Modify this file "/usr/share/polkit-1/actions/org.freedesktop.udisks.policy", look for the following section:[INDENT]  <action id="org.freedesktop.udisks.filesystem-mount">
    <description>Mount a device</description>
    <description xml:lang="da">Montér en enhed</description>
    <description xml:lang="de">Gerät einhängen</description>
    <description xml:lang="pt_BR">Montar um dispositivo</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <message xml:lang="pt_BR">Autenticação é requerida para montar o dispositivo</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      **[COLOR=Red]<allow_active>yes</allow_active>[/COLOR]**
    </defaults>
  </action>
[/INDENT]Change the line highlighted in red font to:[INDENT]**[COLOR=Red]<allow_active>auth_admin</allow_active>[/COLOR]**[/INDENT]This way, you'll need to provide Administrator password in order to mount the USB drive whenever you plug in any USB Storage device.

---


---
title: "GDM login denied by apparmor"
date: 2011-04-20
forum: Desktop Environments
---

### Post by gnagnibu on 2011-04-20
Hi all!
I've just installed Ubuntu 10.10 on a Toshiba Tecra A3 notebook.
Next, I've joined the pc with likewise-open to our Windows 2000 Active Directory.

AD Domain: SAER
User: SAER\giovanni

The problem is that I can't login trought GDM and /var/log/messages says:

Apr 20 10:08:28 seced10 kernel: [  495.350194] type=1400 audit(1303286908.827:47): apparmor="DENIED" operation="open" parent=1885 profile="/usr/share/gdm/guest-session/Xsession" name="/home/likewise-open/SAER/giovanni/.profile" pid=2389 comm="Xsession" requested_mask="r" denied_mask="r" fsuid=1982858986 ouid=1982858986
Apr 20 10:08:29 seced10 kernel: [  495.684282] Skipping EDID probe due to cached edid
Apr 20 10:08:29 seced10 kernel: [  496.172255] Skipping EDID probe due to cached edid
Apr 20 10:08:30 seced10 kernel: [  497.048222] Skipping EDID probe due to cached edid
Apr 20 10:08:31 seced10 kernel: [  497.540216] Skipping EDID probe due to cached edid
Apr 20 10:08:31 seced10 kernel: [  498.032214] Skipping EDID probe due to cached edid
Apr 20 10:08:32 seced10 kernel: [  498.520219] Skipping EDID probe due to cached edid

After password, GDM restart but I can login in tty

Any ideas?

---

### Post by gnagnibu on 2011-04-20
I've tried to modify /etc/apparmor.d/gdm-guest-session adding:

/home/likewise-open/** rw,

but after login I can see only mouse cursor and wallpaper.

in this case /var/log/messages says nothing

---

### Post by gnagnibu on 2011-04-20
I solved purging GDM and reinstalling ubuntu-desktop package

aptitude purge gdm
aptitude install ubuntu-desktop

I don't like this solution, but it works...

---


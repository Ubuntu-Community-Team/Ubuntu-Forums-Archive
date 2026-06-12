---
title: "You do not appear to have an up to date version of GNOME3."
date: 2012-05-12
forum: Desktop Environments
---

### Post by drpjkurian on 2012-05-12
Hi
I was using Ubuntu Oneric ocelot with gnome shell 3 for few months when precise pangolin was released. I upgraded my OS through update manager. After the upgrade I logged into Gnome shell 3.But to my utter dismay my shell extensions which were installed previously in oneric was not working in precise after upgraing. I went to [https://extensions.gnome.org](https://extensions.gnome.org) to solve the issue but I was greeted with the message [COLOR="Black"]*"You do not appear to have an up to date version of GNOME3. You won't be able to install extensions from here. See the about page for more information.*[/COLOR]"

**I solved this through reinstalling the Gnome shell through software center **

---

### Post by grahammechanical on 2012-05-12
I get the same message but then I am not using Gnome 3 shell at all. I do have gnome 3.2 desktop environment (DE).

That website talks about Gnome 3 but does not explain that its actually Gnome 3 shell under discussion and not simply Gnome 3.

So, this issue is due to newer Gnome shell extensions being incompatibile with older versions of the Gnome 3 shell.

Just so we know that there are Gnome issues due to development by the Gnome organization.

Regards.

---

### Post by drpjkurian on 2012-05-15
Hope most of them did not face this problem  of gnome shell extensions after upgrade.

---

### Post by markbl on 2012-05-15
If you upgrade your ubuntu gnome-shell moves from v3.2 to v3.4. You really are far better off deleting all your extensions and installing them again.

Just "rm -rf ~/.local/share/gnome-shell/extensions" then restart gnome-shell (log out/in or alt+f2 then "r"). Then go to [http://extensions.gnome.org](http://extensions.gnome.org) and click to install. Only takes you a few minutes and ensures you get up to date versions.

---


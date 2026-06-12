---
title: "LightDM Login Cancel Button \ Custom Script?"
date: 2012-12-07
forum: Desktop Environments
---

### Post by Kirk Schnable on 2012-12-07
Good afternoon,

I am currently working on perfecting my Xubuntu 12.04 lab image, and we have noticed a somewhat troubling bug with the LightDM GTK Greeter.

The bug appears to be well documented on Launchpad, but it seems that other than releasing a C patch and committing some code, it doesn't look like this has really been fixed in Precise repositories.

Some folks have said that installing the Quantal package version fixes the issue, but I found that doing so seriously broke LightDM on my test machine.

I would like to either fix this issue by installing a package (prefer to avoid compiling one, as this will be a mass scale deployment) or by creating a custom button on the LightDM greeter screen which kills\restarts the process, thus effectively canceling the failed authentication.

Anybody have any input on this?

Here are the relevant Launchpad bugs:
[https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/983152](https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/983152)
[https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/990315](https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/990315)
[https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/974610](https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/974610)

Thanks,
Kirk

---

### Post by Kirk Schnable on 2012-12-13
For the information of anyone interested, what I ended up doing was scrapping my original login screen and getting rid of LightDM GTK Greeter altogether.

I changed /etc/lightdm/lightdm.conf and made my greeter lightdm-kde-greeter.  I spent a bit of time making a custom theme for it, and am now satisfied with how it looks.  Not really a fix, more of a workaround, but just letting any future readers know that the option exists.

---


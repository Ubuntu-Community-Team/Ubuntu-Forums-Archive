---
title: "desktop effects &amp; Beryl problem"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by Dod_basim on 2007-05-14
hey

i have no idea why but when i reboot my computer i got a blank white screen and X server crashed. after using Ctrl+Alt+Backspace and run the Failsafe gnome i know it's a Beryl error so i have removed it with synaptic.
Now my ubuntu boot and everything is okay.
But
if i try to enable the desktop effects i get the same white screen.

what is wrong? i want to use beryl or at list desktop effects. Thanks

Please help, thanks.

---

### Post by lungdart on 2007-05-14
Did beryl work fine before hand?

What were you doing before this started happening? Updates? Changing conf files?

What graphics card do you have, and what drivers are installed with it?

I also assume since you can "enable desktop effects" that you are using Feisty.

I would remove any graphics drivers I have installed through the restricted drivers manager, and then reinstall them, and re-enable desktop effects. and rebooted or restart X.

If that doesn't work, I would try re-installing beryl through synaptic. and then doing a "complete removal" instead of just removing them, as this gets rid of config files as well.

Good luck

---

### Post by Dod_basim on 2007-05-14
> **lungdart said:**
> Did beryl work fine before hand?

What were you doing before this started happening? Updates? Changing conf files?

What graphics card do you have, and what drivers are installed with it?

I also assume since you can "enable desktop effects" that you are using Feisty.

I would remove any graphics drivers I have installed through the restricted drivers manager, and then reinstall them, and re-enable desktop effects. and rebooted or restart X.

If that doesn't work, I would try re-installing beryl through synaptic. and then doing a "complete removal" instead of just removing them, as this gets rid of config files as well.

Good luck

Thanks!
problem solved! yeah i did some xorg.conf newbie mistakes. thanks god i made back file.
Yeah

---


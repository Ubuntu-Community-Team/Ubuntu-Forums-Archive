---
title: "How can I disable lightdm in Ubuntu 12.04"
date: 2012-12-12
forum: Desktop Environments
---

### Post by Leo Simon on 2012-12-12
I need to be able to boot into console mode, from where I launch fvwm.   It used to be easy to do this, by setting

GRUB_CMDLINE_LINUX_DEFAULT="text"

in /etc/default/grub, then updating grub.   But then, in order to deal with ubuntu's sound problems I follows the instructions in

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

which ran a number of updates.     Since doing this, I now an unable to avoid being booted into lightdm's gui screen.    I read that this was a bug, and that the bug had been fixed, but my version of lightdm (1.2.1) is apparently the most recent one.  I tried to remove lightdm as some threads suggest with

sudo update-rc.d -f lightdm remove

but this simply hung my machine.

so I had to use recovery mode to get back.

Could anybody suggest something please?
How could it possibly be so hard to do such a primitive thing as avoid a gui?   Ubuntu seems to want to be more like windows every new release....

Thanks for any advice!

---

### Post by Cheesemill on 2012-12-12
```
 echo  "manual" | sudo tee -a /etc/init/lightdm.override
```

---

### Post by Leo Simon on 2012-12-12
Thanks for the quick response.   I should have posted that I'd tried the override route.    lightdm.override exists and says manual, but it doesn't override the gui for some reason.   

I've also tried editing /etc/init/lightdm.conf, and commenting out the stanza that begins with"start on".   This is ignored.
Also, the script clearly says that if /proc/cmdline contains the word "text" then to quit.    /proc/cmdline *does* contain the word "text" but it doesn't quit.

The only conclusion I can draw is that the startup script is not even looking at /etc/init/lightdm.conf.    Is this possible?

---

### Post by Leo Simon on 2012-12-13
I finally solved this problem.    After the patch described above was installed, lightdm.conf was not being read at all.    Rather gdm.conf was calling lightdm! I copied into gdm.conf the lines in lightdm.conf that checked cmdline.conf for the word "text" and bailed if these words were found.     Then everything worked the way it should.

But what a crazy patch!!!   Why would anybody set things up this way???

---


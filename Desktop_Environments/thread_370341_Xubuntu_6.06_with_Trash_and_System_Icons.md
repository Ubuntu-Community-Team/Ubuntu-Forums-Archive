---
title: "Xubuntu 6.06 with Trash and System Icons?"
date: 2007-02-25
forum: Desktop Environments
---

### Post by Linux_Zoo on 2007-02-25
I've just installed Xubuntu 6.06 on my mother's old PC, for her home use.  

The default install does not include desktop icons like "home directory" or trash.  I've enable the file/launcher behaviour, but there are no default system icons.

From the reading I've done, it looks like trash and system icons are only available in the very latest version of xfdesktop, xfce and Thunar.  I've tried to update using the Package Manager.  It tells me that I have the latest of everything, despite the fact that later versions of each application exist if you go to their websites.  

Can anyone help?  

Thanks.

---

### Post by kerry_s on 2007-02-25
Dapper is already frozen for long term support. The next step up is edgy 6.10, which has what you need plus there's a repo to move it to the latest 4.4.0.
-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)
You'll need internet, with this 1 disk you can install any of the ?ubuntu desktop versions and then some.

---

### Post by mcduck on 2007-02-25
Software for Ubuntu versions usually doesn't change during the lifetime of the version to keep the system as stable as possible. New software versions are usually added only for security reasons, not to add new features.

The XFCE4 in Ubuntu 6.10 has those desktop icons you want, 6.06 will probably never get them.

---

### Post by Linux_Zoo on 2007-02-25
Thanks all.  Kerry, do I just burn the iso to a CD, then use it to boot the computer, or is there more involved?  Do I need to install 6.10 first, then use the CD?  Thanks.

---

### Post by kerry_s on 2007-02-25
> **Linux_Zoo said:**
> Thanks all.  Kerry, do I just burn the iso to a CD, then use it to boot the computer, or is there more involved?  Do I need to install 6.10 first, then use the CD?  Thanks.

Just burn the iso and boot it. That is the net installer, it installs straight from the net, so you will be up to date when finished installing. There will be a point in the install were it will ask you what you want to install, use the arrow keys to move down to xubuntu-desktop, press the space bar to select it and tab to continue with the install. With that 1 disk you can install anything ubuntu, you won't have to download and burn anything else.

---

### Post by Linux_Zoo on 2007-02-25
Any idea  how many megs it will download for the install?  I'm on a fixed plan and am due to run out this month.

---

### Post by kerry_s on 2007-02-26
> **Linux_Zoo said:**
> Any idea  how many megs it will download for the install?  I'm on a fixed plan and am due to run out this month.

Ohh, that hurts, it would be around 700mb just like if you downloaded the regular iso. I wouldn't reccommend if your fixed or on dial up.

Wait, i just remembered reading about a dapper backport on the mepis forum, let me look that up and get back to you.

---

### Post by kerry_s on 2007-02-26
Okay, i got it, there are repo's for 4.4.0 in dapper. You just need to add them to your list.

Press> alt+F2
type

gksu mousepad /etc/apt/sources.list

add this to the bottom->

deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) dapper xfce-4-4-0

close and save

press> alt+F2
type

gksu synaptic

click on>  reload
then> mark all upgrades
then> apply

That should get you the current xfce4. I use the same version in edgy using his repo so it should work just as well. Here's his site in case you want to take a look.-> [http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy](http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy)

---

### Post by Linux_Zoo on 2007-02-26
Worked really well, thanks!

---


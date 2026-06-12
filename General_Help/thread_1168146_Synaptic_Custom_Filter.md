---
title: "Synaptic Custom Filter?"
date: 2009-05-23
forum: General Help
---

### Post by Hartless on 2009-05-23
Is there a way to make a custom filter in synaptic to show only the programs installed manually? How would i go about doing that?

Thanks, 
Hartless

---

### Post by 67GTA on 2009-05-23
If you mean installed manually by downloading and installing a deb file, then it will already show you. Select the status button on the lower left side, and look under "Installed (local or obsolete)".

---

### Post by Hartless on 2009-05-24
No i mean programs installed using apt-get or synaptic after the base system was installed

---

### Post by 67GTA on 2009-05-24
Not sure of an easy way to do that. Any package that has been installed will be listed in /var/log/dkpg.log, but it is messy. It keeps a history of dpkg activity.

---

### Post by 67GTA on 2009-05-24
I remember this being discussed a while back on the debian developers irc channel, but I think the idea died.

---

### Post by Hartless on 2009-05-25
Well i wanted to do this so when i reinstall different types of linux, i know what to install to get my system back. My machine is due to switch distributions of linux soon.

---

### Post by 67GTA on 2009-05-25
Different distrobutions use different package naming methods, so it won't work very well if you move to a non Debian based distro. Debian based distros also don't always have the same versions. Your best bet would be to make a list with ```
dpkg -l > packages.txt
``` This will make a file called "packages" in your home folder. This will list every installed package. You will have to reference this against your new distro's packages. If you are moving to another Debian based distro with the same package base/versions, you can use ```
dpkg --get-selections > package.list
``` which will make a file that you can transfer to another installation and install the listed packages with ```
dpkg --set-selections < package.list
```

---

### Post by drs305 on 2009-05-25
Synaptic also now has the capability of creating a list of installed packages. Open Synaptic and from the main menu select "File, Save Markings". Save the list and on the new machine/installation use "File, Read Markings" to import the package list.

---

### Post by Hartless on 2009-05-28
This works great, but when i install it on the new distro, all the ubuntu base system packages will be installed also. Ill look around for a way.

Hartless

---

### Post by drs305 on 2009-05-28
> **Hartless said:**
> This works great, but when i install it on the new distro, all the ubuntu base system packages will be installed also. Ill look around for a way.

Hartless

You could probably make a list via the dpkg,log or apt term.log. They list the installs including the date. You could edit the file to start at a given time/date (after the initial install, for instance), and then run one of these to extract the added package names:
```

sudo cat /var/log/dpkg.log | grep " installed" | awk -F" " 'print{$4}'
sudo cat /var/log/apt/term.log | grep "Setting up" | awk -F" " '{print $3}'

```

Just some food for thought.

---


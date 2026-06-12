---
title: "Gnome 2 permissions problems with scripts"
date: 2011-07-22
forum: Desktop Environments
---

### Post by Alistair George on 2011-07-22
Hi I have just had to reinstall Linux. Now I cant seem to run many scripts, even though I have checked several scripts and the permissions are the same; some run, some dont, with the previous installation all ran fine:

As administrator, only some of my scripts work (.gnome2/nautilus-scripts). 
EG this works:

    cd $NAUTILUS_SCRIPT_CURRENT_URI
    exec gnome-terminal


but this doesnt; does not even bring up the root user password dialog:


    cd $NAUTILUS_SCRIPT_CURRENT_URI
    sudo gnome-terminal


This one brings up the pw dialog, but does not instantiate nautilus with root or admin:

    foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
    sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI

Anything I could try please?

---

### Post by doas777 on 2011-07-23
just use gksu in place of sudo. when invoked, it brings up its own prompt.

but it is much easier to install [nautilus-gksu]("http://www.ubuntugeek.com/nautilus-gksu-gksu-extension-for-nautilus-allows-you-to-open-files-with-administration-privileges.html")

---

### Post by Alistair George on 2011-07-23
> **doas777 said:**
> just use gksu in place of sudo. when invoked, it brings up its own prompt.

but it is much easier to install [nautilus-gksu]("http://www.ubuntugeek.com/nautilus-gksu-gksu-extension-for-nautilus-allows-you-to-open-files-with-administration-privileges.html")
Unfortunately, this does not sort out the scripts of which there are many. Id prefer to find out whats causing the problem and sort it out correctly.
For example, before I could click the Scripts within Nautilus and execute one of many scripts, now it does not work.
Thanks,
Alistair.

---

### Post by doas777 on 2011-07-23
then make sure you replace your sudo's with gksu's, if you plan on executing somthing as root without being in a terminal.

---

### Post by Alistair George on 2011-07-23
> **doas777 said:**
> then make sure you replace your sudo's with gksu's, if you plan on executing somthing as root without being in a terminal.

Well I did that, and GKSU did not make any different. Sorry about being pedantic, its unusual that the scripts _did_ work, now dont.

---


---
title: "Closing laptop brings up command line"
date: 2005-09-12
forum: Desktop Environments
---

### Post by Tiny Grasshopper on 2005-09-12
I have Ubuntu running on my laptop. When I close the cover, while its on, it would leave gnome and enter the command line and I dont know how to get back to the GUI. How do I get back to gnome in that situation or stop that from happening?

---

### Post by Tiede on 2005-09-12
[QUOTE=Tiny Grasshopper]I have Ubuntu running on my laptop. When I close the cover, while its on, it would leave gnome and enter the command line and I dont know how to get back to the GUI. How do I get back to gnome in that situation or stop that from happening?[/QUOTE]
 try Ctrl+Alt+F7 maybe that'll work...
I dunno how to stop it from happening (yet). I did not have this problem with Tuxed, my tiny laptop.

---

### Post by Hairy_Palms on 2005-09-12
lol i have the exact opposite problem, when i close the lid nothing happens and the screen stays on.
if your at the commandline just type startx should bring back the desktop

---

### Post by rusi_pathan on 2005-09-12
See these for clues...

/etc/acpi/lid.sh
/usr/share/acpi-support/screenblank

---

### Post by Tiny Grasshopper on 2005-09-12
Thanks. Ctrl+Alt+F7 worked.

---

### Post by Hairy_Palms on 2005-09-12
anyone know how i can make my laptop turn the screen off when i close the lid?
i had a look at those two files but i couldnt figure out what i would need to change to make it work,
its a dell inspirion 5160. as a stopgap measure ive made a desktop shortcut to run "xset dpms force off" which turns the screen off but id rather like a moreelegant solution if its possible.

---

### Post by rusi_pathan on 2005-09-12
Back up '/usr/share/acpi-support/screenblank' and then edit the file to make it look like this...

#!/bin/sh
xset dpms force off

It is called by '/etc/acpi/lid.sh' which runs everytime you close your lid.

---

### Post by Hairy_Palms on 2005-09-12
hmm it already has that inside the screenblank file, i can only assume for some reason lid.sh isnt working.
heres my lid .sh file
> #!/bin/sh

. /usr/share/acpi-support/power-funcs

getXuser;

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        . /usr/share/acpi-support/screenblank
        echo `fgconsole` > $LIDSTATE
else
        grep -q off-line /proc/acpi/ac_adapter/*/state
        if [ $? = 1 ]
        then
                su - $user -c "xscreensaver-command -unthrottle"
        fi
        chvt `cat $LIDSTATE`
        su - $user -c "xscreensaver-command -deactivate"
fi
 chvt `cat $LIDSTATE`
chvt 7
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

this is really confuseing me, as it used to turn off the screen in both windows and suse

---


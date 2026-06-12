---
title: "booting without 'x'"
date: 2011-05-10
forum: Desktop Environments
---

### Post by israelc on 2011-05-10
can I start ubuntu 11/04 in monitor only. If yes how can I login, and use some administrations without 'X'
Shall be grateful for any help:)

---

### Post by Jose Catre-Vandis on 2011-05-10
If you don't need to do it a lot, press e when your grub menu comes up, arrow down to the vmlinuz line and remove all the options back to and including quiet splash. Type a 3. Press CTRL+X and should should boot up to the command line login

**[EDIT - see below]**

**[COLOR="Sienna"]Don't put a 3, put "text" (no quotes)[/COLOR]**

**[End of EDIT]**

---

### Post by Krytarik on 2011-05-10
*Jose Catre-Vandis's* suggestion only disables the Plymouth boot splash and makes the output during the boot process visible.

See here on how to boot into the CLI instead of running GDM:
[http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)

And yes, you can of course log in there and work on the command line.

Greetings.

---

### Post by sisco311 on 2011-05-10
> **Krytarik said:**
> 
See here on how to boot into the CLI instead of running GDM:
[http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)


That method does not work in Natty.

@OP: 

You can disable GDM with the following command:
```
echo "manual" | sudo tee -a /etc/init/gdm.override
```

The splash screen can cause some problems, so I would suggest you to disable it. Edit the /etc/default/grub file and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="quiet"**. Then generate a new Grub2 config file:```
sudo update-grub
```

If you want to start an X session from the virtual console, simply run:
```
startx
```
or start GDM:
```
sudo service gdm start
```


If you want to re-enable GDM, then simply remove the .override file:
```
sudo rm /etc/init/gdm.override
```

---

### Post by Krytarik on 2011-05-10
> **sisco311 said:**
> That method does not work in Natty.

Ok, I didn't know that until now.
Thanks for dropping by! :-)

---

### Post by Jose Catre-Vandis on 2011-05-11
> **Krytarik said:**
> *Jose Catre-Vandis's* suggestion only disables the Plymouth boot splash and makes the output during the boot process visible.

See here on how to boot into the CLI instead of running GDM:
[http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)

And yes, you can of course log in there and work on the command line.

Greetings.

Agreed, my mistake. What I should have said is "text" (no quotes) instead of 3 :)

---

### Post by Krytarik on 2011-05-11
> **Jose Catre-Vandis said:**
> Agreed, my mistake. What I should have said is "text" (no quotes) instead of 3 :)
No matter, since it eventually turned out that were both wrong, apparently. ;-)

---


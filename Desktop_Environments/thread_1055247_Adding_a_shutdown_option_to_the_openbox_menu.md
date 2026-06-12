---
title: "Adding a shutdown option to the openbox menu"
date: 2009-01-30
forum: Desktop Environments
---

### Post by Major_Kong on 2009-01-30
I got from this guide - [http://urukrama.wordpress.com/openbox-guide/#shutdown2](http://urukrama.wordpress.com/openbox-guide/#shutdown2) - the following tips:
> To shutdown the computer with gdm-control, use the following command:

	gdm-control --shutdown && openbox --exit

To restart, use this command:

	gdm-control --reboot && openbox --exit

And to suspend, use the following line:

	gdm-control --suspend

And they work just fine, but not if i run them from the openbox menu (adding a menu item that executes "gdm-control --reboot && openbox --exit" ).

Any solutions ?

---

### Post by Major_Kong on 2009-01-31
None ?

---

### Post by Major_Kong on 2009-02-01
Okay... so how do most users running openbox shutdown ?

---

### Post by Major_Kong on 2009-02-02
Was looking for a more "elegant" solution, but i just made 2 scripts and added items to the menu to execute them.

---

### Post by Hooya on 2009-02-02
I added a line to the sudoers file to allow "sudo shutdown -h now" without having to enter in a password.  Then you just execute that commande from the menu.

I'm running Fluxbox, but the principle should be the same for openbox.

I don't know what qualifies as "elegant".  If it works it works.

The other option is to have those commands run inside of a terminal.  Something like
"x-terminal-emulator -t shutdown -e insert_shutdown_command_here"

Adjust for the proper syntax because I'm too lazy to make sure it's right...

---

### Post by Major_Kong on 2009-02-02
The "gdm-control --shutdown && openbox --exit" and "gdm-control --reboot && openbox --exit" commands do not require administrative privileges. The problem was that openbox menu doesn't seem to support the "&&".


PS: But thanks anyway, you gave me the solution to another problem. :D

---

### Post by urukrama on 2009-02-02
> **Major_Kong said:**
> The "gdm-control --shutdown && openbox --exit" and "gdm-control --reboot && openbox --exit" commands do not require administrative privileges. The problem was that openbox menu doesn't seem to support the "&&".

That is indeed the problem. You could circumvent this by editing the menu.xml file (rather than using obmenu) and use the following syntax:

```
<item label="**Menu entry title**">
     <action name="Execute">
        <execute>**command 1**</execute>
     </action>
     <action name="Execute">
        <execute>**command 2**</execute>
     </action>
</item>

```

That should work with gdm-control too, though I haven't tested it (this computer doesn't have GDM installed).

The same applies for the keybindings & mousebindings in the rc.xml.

I guess I should add this to my guide...

EDIT: I use [this system]("http://urukrama.wordpress.com/2007/12/03/confirm-to-shut-down-reboot-or-log-out-in-openbox/") to log out and shut down.

---

### Post by Major_Kong on 2009-02-03
> **urukrama said:**
> That is indeed the problem. You could circumvent this by editing the menu.xml file (rather than using obmenu) and use the following syntax:

```
<item label="**Menu entry title**">
     <action name="Execute">
        <execute>**command 1**</execute>
     </action>
     <action name="Execute">
        <execute>**command 2**</execute>
     </action>
</item>

```

That should work with gdm-control too, though I haven't tested it (this computer doesn't have GDM installed).

The same applies for the keybindings & mousebindings in the rc.xml.

I guess I should add this to my guide...

EDIT: I use [this system]("http://urukrama.wordpress.com/2007/12/03/confirm-to-shut-down-reboot-or-log-out-in-openbox/") to log out and shut down.

Hmm... nice. But alas, i'm lazy, i'll just keep using the scripts for now.

---

### Post by urukrama on 2009-02-03
> **Major_Kong said:**
> Hmm... nice. But alas, i'm lazy, i'll just keep using the scripts for now.

As you wish. :) But now you know how to solve the problem if you want to do something else along these lines in the future.

---

### Post by Major_Kong on 2009-02-03
> **urukrama said:**
> As you wish. :) But now you know how to solve the problem if you want to do something else along these lines in the future.

Yeah, thanks. :D

---

### Post by Jelloir on 2009-07-20
I know this is reviving a pretty old thread but I worked out how to add a menu entry for reboot/shutdown using obmenu and google bought me to this thread so I figured I would reply in case others stumple across it also. 

Add an entry as follows:

```
x-terminal-emulator -e sh -c "gdm-control --shutdown && openbox --exit"
```

reboot should be obvious enough to work out.

Obviously add a Label and action is "execute" but this worked fine for me on Debian Sid.

Cheers

James

---

### Post by ~sHyLoCk~ on 2009-07-20
```
<item label="Shutdown">
     <action name="Execute">
        <execute>shutdown -h now</execute>
     </action>
</item>
```

---


---
title: "GDM won't start after boot &quot;single user&quot;"
date: 2010-02-20
forum: Desktop Environments
---

### Post by SaintDanBert on 2010-02-20
I'm running Ubuntu Karmic and did a "single user boot"
[list]
[*]at the GRUB-2 menu, pressed 'e' to edit
[*]added " single" at the end of the **linux ...** record
[*]press **control-X** to boot the workstation
[/list]

chug ... chug ... chug ...
and I get a login prompt where I login and do the work I wanted.
When I was finished, I typed **shutdown -r now**.

chug ... chug ... chug ...
the GRUB-2 menu appears and I select my preferred boot option.
chug ... chug ... chug ...
I get the login pronpt instead of a GDM start.

Before you grab your flame throwers asking about "the work I wanted" I worked strictly with the [highlight]showkey[/highlight] command and console keystrokes. I didn't install anything or edit any config files. I get this behavior from all of the available GRUB-2 menu options.

Can anyone help me sort out what happened and how to fix it?
~~~ 8d;-< Dan

---

### Post by Hero of Time on 2010-02-20
Without knowing what a certain paramater means, how do you expect to get what you want? The parameter 'single' is used when you boot to recovery. Single doesn't mean single user for the GUI, but really, single user, aka, root only.
See [http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html) for more info.

It might also be useful if you tell us WHAT you did. Either you somehow disabled GDM, or set the boot option permanently.

---

### Post by SaintDanBert on 2010-02-20
> **Hero of Time said:**
> Without knowing what a certain paramater means, how do you expect to get what you want? The parameter 'single' is used when you boot to recovery. Single doesn't mean single user for the GUI, but really, single user, aka, root only.
...

I wanted "root only" that is pretty "single user" to me ... at least that is what we called it years ago.  **I got what I wanted** when I added 'single' to the GRUB-2 record. I needed linux running. I needed a working shell. I didn't need a lot of running services ... so that my **showkey** typing did not have many things to interact with.

> 
See [http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html) for more info.

It might also be useful if you tell us WHAT you did. Either you somehow disabled GDM, or set the boot option permanently.


I wanted to collect all of the scancodes from my laptop. I needed to press buttons, see the codes, and have nothing much happen because there were no other services running to catch the keys and buttons.

Does this 'splain what is going on enough to turn off [down] the flame?

~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-02-20
[color=blue]An update but not completely back to normal.[/color]

I have no idea how this happened, but at some point a program replace my **/etc/fstab** and scrambled with file systems were mounted where.
I fixed that!

[color=blue]Now I have a new-and-improved problem.[/color]

[list=1]
[*]I cannot login through GDM -- no typing appears in the password text box.
[*]I cannot launch a console login -- CTRL-ALT-F2 does not respond
[*]I cannot use the tap-keyboard to login -- I think tap-keys wonder around and become X11-input-keys
[*]If I boot **root only** and then **startx** nothing that I type does anything -- I launch an xterm or konsole and nothing happens.
[/list]

It seems that something that I did while running [highlight]showkey[/highlight] corrupted my X11 keyboard input. Pointer input and navigation work fine.

~~~ Dan 0;-/

---

### Post by Hero of Time on 2010-02-21
I thought you didn't know what you were doing, I was wrong, sorry.

To get raw key codes, why didn't you use xev instead? That one picks up more keys, like shift and ctrl. You could also use a live environment in case you are afraid of breaking your current install.

As for the keyboard failure, it appears that your system doesn't pick up your keyboard at all. Or it does pick it up, but sends them to a TTY, instead of the GUI (if GDM runs on TTY7, it get send there, behind your GDM).

Do you remember what settings you had for keyboard in X11? Did you let it stay on 'Use system default', or did you select a specific layout? If you have it set for default, then running 'dpkg-reconfigure console-setup' as root might get you your keyboard back in X11.
In case you have an xorg.conf file, check that one as well. Also check with aptitude if you have 'xserver-xorg-input-kbd' still installed. You may need to reinstall it.

---


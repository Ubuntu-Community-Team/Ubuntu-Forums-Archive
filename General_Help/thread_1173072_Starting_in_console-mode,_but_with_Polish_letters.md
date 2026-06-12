---
title: "Starting in console-mode, but with Polish letters"
date: 2009-05-29
forum: General Help
---

### Post by borysj on 2009-05-29
Hello,

I installed Xubuntu on my Asus EEE 901. Everything works very nicely. However, I mainly use EEE as a mobile electronic typewriter, so all I need is a text-editing program. In order to minimize startup and shutdown time, it would be cool to work without XFCE and simply use nano in the console-mode.

My questions:

1) What config files do I need to edit so Xubuntu starts without XFCE and goes to text-mode as quick as possible, without loading any additional stuff?

2) I am Polish so I would like to use Polish keyboard layout and Polish letters when working with nano. This layout is installed in XFCE, everything work fine, but I would like to "keep" it even without the graphical interface.

Thanks for your help.

---

### Post by Keith_Beef on 2009-05-29
> **borysj said:**
> Hello,

I installed Xubuntu on my Asus EEE 901. Everything works very nicely. However, I mainly use EEE as a mobile electronic typewriter, so all I need is a text-editing program. In order to minimize startup and shutdown time, it would be cool to work without XFCE and simply use nano in the console-mode.

My questions:

1) What config files do I need to edit so Xubuntu starts without XFCE and goes to text-mode as quick as possible, without loading any additional stuff?

2) I am Polish so I would like to use Polish keyboard layout and Polish letters when working with nano. This layout is installed in XFCE, everything work fine, but I would like to "keep" it even without the graphical interface.

Thanks for your help.

If you are using GRUB to load Linux, then you probably need to edit your GRUB configuration to load the Polish keymap.

I have not needed to change GRUB for years (probably I have not touched it for about four years)... so my memory is a little rusty.

There is a prompt to press a certain key before GRUB loads the default image; probably the "e" key (in the same position in the Polish as in the US layout). At this point, you can look in the command line for "keymap=us". If you do, change the "us" to "pl". I *think* that this is the correct abbreviation for the polish keymap...

---


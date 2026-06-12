---
title: "xfce ubuntu keymapping not saving"
date: 2014-05-07
forum: Desktop Environments
---

### Post by tyler40 on 2014-05-07
Hello!

Let me preface this by stating that I am running xfce ubuntu with crouton on an Acer c720 Chromebook.

I seem to be having a trouble with key mappings.  I've tried ```
xmodmap -e "keycode 74 = XF86AudioMute"
```  which works, but when I log out of ubuntu and restart it, the new keybindings I set are gone.

Is there anyway to fix this from happening?

---

### Post by SonnyE on 2014-05-07
For customizing my own keys, I followed the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=1979757](http://ubuntuforums.org/showthread.php?t=1979757)

I wanted a compose key = menu key in Lubuntu, but Lubuntu kept forgetting my setting or overwriting it on startup, so this is what I did:

This is the line I added to /home/[user]/.config/lxsession/Lubuntu/autostart
@/usr/local/bin/setcompose

This is the script I wrote for setcompose (and I had to make the file executable using chmod)
#!/bin/bash
sleep 5s
setxkbmap -option compose:menu

If you use that method with an xmodmap command, of course it would only apply after starting a desktop environment where you've put it into some sort of autostart file or autostart list.

For instructions specific to XFCE on that, see: [https://wiki.xfce.org/faq#is_it_possible_to_use_media_keys_in_the_shortcut_editor](https://wiki.xfce.org/faq#is_it_possible_to_use_media_keys_in_the_shortcut_editor)

For more general instructions (that include mention of XFCE): [http://askubuntu.com/questions/54157/how-do-i-set-xmodmap-on-login](http://askubuntu.com/questions/54157/how-do-i-set-xmodmap-on-login)

If you want your keyboard modifications to apply all the time, no matter what desktop environment (or none,) writing a udev rule that makes Linux recognize your type of keyboard is the way to go, but that's something harder to do that's mostly done by Arch users.

---


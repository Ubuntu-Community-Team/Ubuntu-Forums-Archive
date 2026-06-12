---
title: "Ubuntu 8.10 upgrade --&gt; xserver forgetting that my keyboard and mouse exist"
date: 2008-12-21
forum: Desktop Environments
---

### Post by professorbell on 2008-12-21
Right, so I used the network upgrade to Ubuntu 8.10 install went mostly smoothly. After the install I booted, but xserver crashed. from tty1, i checked the logs and found that xserver had not been updated with the kernel, so I reinstalled xserver and booted and the login for the gui poped up and looked fine.

The problem: I can see the gui, but the mouse and keyboard don't seem to be recognized by xserver. i ran "less /etc/x11/xorg.conf" and found no keyboard listed, but i don't know how to edit the configuration or do a simpler operation that would solve the problem. (yes, i have tried reconfiguring xserver-xorg, did not help...) 

apparently this is not a unique problem, but have not found anybody with exactly my situation as yet, so any help or a link to a solution would be greatly appreciated.

Brian

---

### Post by stinedvd on 2008-12-21
I have the same problem.  I have been running 8.10 for a few months on a Gateway tablet M285-E and ran recommended updates two days ago and since then at the GDM login screen I have no mouse or keyboard inputs.  I do see a "error setting MTRR" in /var/log/gdm, but I don't know if that is the problem or if it is related.  If anyone has any ideas, pleas let me know.  Thanks.

---

### Post by Monteaup on 2009-01-16
Same Problem here. I did a dpkg-reconfigure xserver-xorg. But where are the options for the Videocard, Mouse and Monitor gone? Keyboard is the only thing I can reconfigure.

---

### Post by Favux on 2009-01-16
Hi everyone,

With the move to Intrepid Ubuntu introduced HAL (hardware abstraction layer).  This allows cool things like hot plugging.  HAL is suppose to run your keyboard and mouse, so there aren't any xorg.conf settings.  There should be .fdi files somewhere to support your keyboard and mouse.  If you updated from Hardy the settings should still be in xorg.conf but commented out.

If you need the keyboard and mouse settings, etc. you have to have either backed up xorg.conf in Hardy or earlier or find an xorg.conf for your machine somewhere.  The alternative would be to go back to Hardy, back up xorg.conf and then re-upgrade.

HAL also presents a special problem for tablet pc users.  It only supports stylus.  If you have eraser or touch you have to revert to xorg.conf.  HAL also breaks single key key bindings, so if you rotate your tablet with a single key (with key binding to your rotation script) on the bezel you have to reactivate the keyboard section in xorg.conf to get your single key press rotation back.

Hope this helps.

---


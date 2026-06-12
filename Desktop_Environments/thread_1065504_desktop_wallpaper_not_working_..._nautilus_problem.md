---
title: "desktop wallpaper not working ... nautilus problem"
date: 2009-02-09
forum: Desktop Environments
---

### Post by bpedman on 2009-02-09
So, when I log in I have no desktop wallpaper, just blackness

I have found other people with the same problem. They have said to make sure that in gconf apps/nautilus/preferences->show_desktop is checked. I went in and it is already checked. 

I actually unchecked it, killed any instances of nautilus, rechecked it, and started nautilus again but I got nothin...

I finally uninstalled nautilus...after I did this I rebooted and when I logged in I had my wallpaper back...just no icons for the Desktop

I re-installed nautilus, but I am right back to where I began

I am using 8.10 intrepid...any thoughts on what would be causing this issue?

Thanks

---

### Post by Shazaam on 2009-02-10
Is there anything in /usr/share/backgrounds?

---

### Post by bpedman on 2009-02-11
got it working...did some more searching and found another posting here [http://ubuntuforums.org/showthread.php?t=820252](http://ubuntuforums.org/showthread.php?t=820252) that solved the problem

in gconf-editor went to desktop/gnome/background and selected draw_background ... somehow it was not selected

---


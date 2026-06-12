---
title: "load nvidia-settings automatically"
date: 2005-04-14
forum: Desktop Environments
---

### Post by bigbadb on 2005-04-14
Hi

I have the nvidia driver and nvidia-settings installed but I just can't get it to load automatically when x starts.

I followed the instruction to edit the xinitrc file found at /etc/X11/xinit/xinitrc
and added the line "nvidia-settings --load-config-only &"
                        

This did not work so i created a .xinitrc file in my home directory and put this in it

nvidia-settings --load-config-only &
        . /etc/X11/xinit/xinitrc

This does not work either.

However when log into gnome and type nvidia-settings --load-config-only
the settings i want are applied.

This is driving me crazy as i am probaly overlooking something stupid. 
I would be grateful for any suggestions

Thank you

---


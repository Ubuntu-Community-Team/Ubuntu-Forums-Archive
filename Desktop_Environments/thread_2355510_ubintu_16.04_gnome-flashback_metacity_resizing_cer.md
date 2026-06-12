---
title: "ubintu 16.04 gnome-flashback metacity resizing certain windows"
date: 2017-03-13
forum: Desktop Environments
---

### Post by jerryferry on 2017-03-13
I'm a regular user of gnome flashback on a machine with nvidia gtx 650 with twin monitors. After a new installation of 16.04, (ran 14.04 for a few years) ran into a problem of being unable to resize certain windows. Catfish file search being one in particular, I only found a solution after hours of searching. I'd like to share it with other user users of gnome-flashback metacity users. I wish I could attribute this to the original user that solved this but I've forgotten.


create a file with..
gksu gedit  ~/.config/gtk-3.0/gtk.css 
and place this in it..

.window-frame {
    margin: 10px;
}

---


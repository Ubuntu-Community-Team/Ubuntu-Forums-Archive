---
title: "Lock Google Gadgets to specific workspace"
date: 2010-02-28
forum: Desktop Environments
---

### Post by frankonearth on 2010-02-28
Hi,

Is it possible to lock the Google Gadgets application to a specific workspace?

I launch Google Gadgets on a blank workspace and would like to keep them there but when I switch to another workspace they show up on that workspace.

In a nutshell, I'm trying to have one workspace that just has a bunch of gadgets on it (news, clock, weather) --- when I switch I don't want the gadgets to come with me.

BTW, I'm new to ubuntu --- it's awesome so far :)

Thanks,
Frank

---

### Post by peterum on 2010-07-31
did u find a resolution yet? i want the same thing..

---

### Post by lightspd on 2010-10-13
Was trying to figure this one out myself and thought I would share the answer I found.
install devilspie ( sudo apt-get install devilspie)
mkdir ~/.devilspie
vi ~/.devilspie/ggl-gtk.ds
add the following:

(if
(is (application_name) "ggl-gtk") - or ggl-qt, whatever you use.
(begin
(set_workspace 3) - whatever workspace you want.
)
)

setup devilspie to start on startup and run google gadgets.

---


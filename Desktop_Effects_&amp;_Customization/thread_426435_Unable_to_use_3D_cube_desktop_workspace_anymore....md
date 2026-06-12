---
title: "Unable to use 3D cube desktop workspace anymore..."
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by ThaiNguyenVu on 2007-04-28
hello everyone!
I'm new to Ubuntu, and I feel it great. But I have a problem so I think some body can help me.
I'm enabled Desktop Effects and it works perfectly. But yesterday, the 3D cube desktop workspace didn't work anymore after my Ubuntu OS update some packages from server. Now I can't move to others desktop workspace with 3D effects with Ctrl + Alt + arrow keys.

Your support is greatly appreciated

Please help me :)

---

### Post by Spin Doctor on 2007-04-28
From synaptic. Install the following package:

[B]gnome-compiz-manager

[/B]After installing, go to:

[B]System > Perferences > GL Desktop

[/B]Select the workspace tab, and enable "cube and rotation", and select how many workspaces you want.

That should work I think =)

---

### Post by AWCADDET on 2007-04-28
That works perfectly, i can't thank you enough. I also had that problem you see :D

---

### Post by Spin Doctor on 2007-04-28
That is great! I see that was your first post on the forum! Welcome aboard! =)

---

### Post by ThaiNguyenVu on 2007-04-28
WOW!!!.  Spin Doctor, Thank you so much for your consideration.

Please help me in showing me the problem of window border and title, it's only white color when I maximize the window. Thanks a lot.

Screenshot of problem:

[IMG]http://img214.imageshack.us/img214/1187/screenshotob7.png[/IMG]

---

### Post by the8thstar on 2007-04-28
It doesn't work for me. Whenever I'm trying to set the options, nothing changes.

---

### Post by Spin Doctor on 2007-05-01
> **ThaiNguyenVu said:**
> 
Please help me in showing me the problem of window border and title, it's only white color when I maximize the window. Thanks a lot.


Try changing the window decoration option, under the configuration tab. Either turn off or on metacity. 

If that does not work. I am sorry. I dont know how to fix it since it is probably hardware / driver related and you have to mess with the xorg.conf

---

### Post by dirtydaman on 2008-06-16
yo spin docter i cant see 3D cube either but i cant find the package gnome-compiz-manager

---

### Post by Spin Doctor on 2008-06-26
> **dirtydaman said:**
> yo spin docter i cant see 3D cube either but i cant find the package gnome-compiz-manager

Hi there,

I believe it is now called```
compizconfig-settings-manager
```Try it out...

---


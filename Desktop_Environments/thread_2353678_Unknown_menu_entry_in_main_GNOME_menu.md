---
title: "Unknown menu entry in main GNOME menu"
date: 2017-02-24
forum: Desktop Environments
---

### Post by broly93 on 2017-02-24
I'm using gnome-flashback with Ubuntu 16.04, and in the main GNOME menu, there is an entry, under "Places", that is named after my computer, that doesn't seem to do anything. It can't be removed with Alacarte, so I guess it's in the source code. I thought it might have something to do with dual monitors or mounted drives, but that doesn't seem to be the case. I can't find any documentation on it. Does anyone know what it is, or what it's supposed to do?
Here is a screen shot: [https://postimg.org/image/s8ieusbs1/](https://postimg.org/image/s8ieusbs1/)

---

### Post by vasa1 on 2017-02-24
> **broly93 said:**
> I'm using gnome-flashback with Ubuntu 16.04, and in the main GNOME menu, there is an entry, under "Places", that is named after my computer, that doesn't seem to do anything. It can't be removed with Alacarte, so I guess it's in the source code. I thought it might have something to do with dual monitors or mounted drives, but that doesn't seem to be the case. I can't find any documentation on it. Does anyone know what it is, or what it's supposed to do?
Here is a screen shot: [https://postimg.org/image/s8ieusbs1/](https://postimg.org/image/s8ieusbs1/)
In your image, there's an arrow to the right-hand of "Places". Hover on that or click on it. It should expand to show the various devices seen by the system. Show us what you see preferably by using the paper-clip icon to attach the image rather than posting a link.

---

### Post by broly93 on 2017-02-24
[IMG]https://s16.postimg.org/3s090bb1h/gnome_menu.png[/IMG]

Thanks for the reply. It's not the "Places" entry that is the problem - "Places" works just as you said it would. It's the entry under that labeled "Computer" (my login for that session is "Computer" - if you login as another user, that entry is labeled whatever the username is). Hovering over that entry just brings up an empty box with nothing in it, like the image shows. I've yet to figure out what it is, or if it is a bug. I've not found any documentation or bug reports describing it, and I've tried things like dual monitors or mounted drives - it just seems to be a box of nothing.

---

### Post by broly93 on 2017-02-26
> **vasa1 said:**
> In your image, there's an arrow to the right-hand  of "Places". Hover on that or click on it. It should expand to show the  various devices seen by the system. Show us what you see preferably by  using the paper-clip icon to attach the image rather than posting a  link.

Bumping
Again, this has to do with the entry that appears between "Places" and "Switch User". You can see in the image the entry opens a small, empty box. This entry always takes the name of the user - in my case "Computer". If my username was "Apple" the entry would appear as "Apple".
I have gone thru the source code for GNOME Main Menu and haven't come up with anything.
Anyone have an idea what this entry is - does it have a use I am not aware of, is it a bug?

---

### Post by Frogs Hair on 2017-02-27
If the Alacarte menu editor is installed try removing the check next to the unwanted item.

---


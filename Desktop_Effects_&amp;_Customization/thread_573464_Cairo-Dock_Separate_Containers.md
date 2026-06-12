---
title: "Cairo-Dock Separate Containers"
date: 2007-10-11
forum: Desktop Effects &amp; Customization
---

### Post by blazercist on 2007-10-11
Anyone know how to get separate containers for the Launchers and Applications ?

I want one container on the left for launchers and then a separate free standing container on the right for the currently open applications.

I've seen it on the BerliOS site in the screenshots section, I just have no idea how to do it.

---

### Post by blazercist on 2007-10-17
Bumpzor.

---

### Post by fabounet on 2007-10-19
well it's quite tricky since it's not a real feature ;-)
you just create a new launcher, in which you specify a container's name that doesn't exist yet.
When you apply, the container will be created, and since no icon point to it, it will be considered like a main dock. you can then place it anywhere. But its position will not be saved.
Then you can just edit all our launchers and place them in this new container. In the main container, there will only be applications and applets.

---

### Post by az_s_za on 2007-11-19
I would like to do this as well, but was unable to follow the guide (above).

The only way I am able to add new launchers is with the drag-and-drop method.  If I right-click the dock and select "add a launcher", the new launcher does not appear.

I have no idea how to add a new container, empty or otherwise???

---

### Post by az_s_za on 2007-11-19
I've just worked out a way to make the launchers, applications and appelets look different, although they are still on the same dock...

I specify hard sizes in the minimum and maximum size windows for each.  For example I force my launchers to be 48 pixels (when small) by specifying 48 as the max and min sizes.  Then I make the applications 30 pixels in the same way.  I don't use visible appelets.  This way my "applications" icons look like they are a small system tray next to the launchers.

Even if I could choose, I'd prefer this to them being in a seperate container.

---


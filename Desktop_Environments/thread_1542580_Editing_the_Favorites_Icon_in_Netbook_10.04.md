---
title: "Editing the Favorites Icon in Netbook 10.04"
date: 2010-07-30
forum: Desktop Environments
---

### Post by Gaygerbil on 2010-07-30
How do I do it? I want to change the Favorites icon in Ubuntu Netbook Remix 10.04, the icon is ugly and doesn't match my theme.

There has to be a way.

---

### Post by Gaygerbil on 2010-07-31
Bumping for response.

---

### Post by Gaygerbil on 2010-08-01
Bump.

---

### Post by kerry_s on 2010-08-01
you mean the star?

---

### Post by Gaygerbil on 2010-08-01
> **kerry_s said:**
> you mean the star?

Yes....the star.

---

### Post by Gaygerbil on 2010-08-01
Haha I figured it out, the icon is located here if you're using the humanity set like me:

'file:///usr/share/icons/Humanity/emblems/48'

What you have to do is give yourself permission to edit this folder first by doing this in your terminal:

sudo chown -R 'username':'username' 'file path'

'username' being your username mine for example is bewbman

'file path' being where you want to have root permission this was:

/usr/share/icons/Humanity/emblems/48 for me

After that you can see the favorites icon for yourself it's called emblem-favorite.svg, it's a 48X48 icon. So you're going to have to get a svg icon that's 48X48 to replace it. If anyone's feeling brave replace it with a bigger icon and see how it goes haha.(just make sure to back up the original either way)

After you get the svg icon you want rename it in a folder 'emblem-favorite' and replace it.

If you are not using the humanity theme like me just click on your file system and search 'favorite' to find it. (Which is what I did to find the icon).

Thanks for all the helps guise!

;)

Thread is solved, someone tell me how to set threads as solved though...<__<

[http://i31.tinypic.com/23jn0ia.png]("http://i31.tinypic.com/23jn0ia.png")

---

### Post by kerry_s on 2010-08-01
you shouldn't have changed the file permissions. all you had to do was edit it as root. you could have used alt+f2 to launch a root nautilus or create a launcher in the menu.

the actual path is /usr/share/icons/Humanity/actions/48/help-about.svg
all the rest are links there.

---

### Post by kerry_s on 2010-08-01
ohh, thank you by the way. been looking for that icon, i now have it set for the add button.

---

### Post by Gaygerbil on 2010-08-01
Sweet didn't know about the root manager, will use from now on. :>

---

### Post by horse@pples on 2010-08-02
Sorry to be a nit here but this is exactly the sort of thing that drives people away from Linux. Changing an icon should be easy peasy and never involve terminals or roots or hunting down individual locations for each icon. There should be an 'icons' tab right there next to the 'background' and 'themes' tabs IMO. Changing icons oughta be a simple way of customizing a new users desktop.
 
Isn't there an "Icon Manager" proggie I can get from the Ubuntu download center? Something that allows the user to see current icons & their locations, change icons, change icon size, maybe allow for animated icons, do a preview with accept/revert to previous. Seems like it'd be fairly simple and I'm sure lots of folks would find it useful.
 
Personally, I don't like icons much so I've been trying to figure out a way to *simply* get rid of most of them for the past several days. No luck so far.
 
Any thoughts would be muchly appreciated.

---

### Post by kerry_s on 2010-08-02
you can't even do that in windows. to change each & every icon is just to much trouble to program.

> Personally, I don't like icons much so I've been trying to figure out a way to simply get rid of most of them for the past several days. No luck so far.

Any thoughts would be muchly appreciated.

i don't think so, especially with everything moving to a touch screen type set up.

---

### Post by Gaygerbil on 2010-08-02
You can actually remove all the icons on the desktop in netbook, if you go to System -> Admin -> Startup Applications

Then uncheck Netbook Launcher, you can also just get rid of Netbook launcher completely by doing this:

sudo apt-get remove netbook-launcher

You can get netbook-launcher again from the Synaptic Package Manager if you decide you want it. But you don't really need to remove it first just take it off start up apps and see how you like it.

That will get rid of all your desktop icons however. :>

---


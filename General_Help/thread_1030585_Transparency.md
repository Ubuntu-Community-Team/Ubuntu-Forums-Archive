---
title: "Transparency"
date: 2009-01-04
forum: General Help
---

### Post by Andy06 on 2009-01-04
How do I make normal windows and dialog boxes completely transparent apart from their contents.
Right now I'm using the opacity, brightness and saturation plug in for compiz to make the overall window slightly transparent. The opacity plugin (Separate from the one mentioned above) does not work at all (or I'm not configuring it right).

Basically I want the window background to be completely transparent and only the contents to show. Also preferably Firefox should be completely opaque, I tried doing this but failed.

Any help is appreciated.

Thanks

---

### Post by Forlong on 2009-01-04
Not possible for now, if the theme *and* the application doesn't support it.

---

### Post by Andy06 on 2009-01-04
How about the attached picture. I saved it from somewhere online (don't remember where). The terminal seems to be transparent.

Would using the opacity plug in help? I cannot work out how it functions. Even after seemingly configuring it right, I cannot seem to notice any changes. The opacity, brightness and saturation plug in on the other hand works well but I'm still trying to open every normal window at 90% opacity except firefox which I want at 100% opacity. These two seem to conflict since ubuntu regards firefox as a normal window too I think.

Any suggestions on which filter I should use and what values? (Window ID, Type, Name, Class?)

Thanks a lot

---

### Post by semi_fiction on 2009-01-04
You can change the transparency in the terminal by opening a terminal window and going to Edit->Profile Preferences (Or Edit->Current Profile before Ubuntu 8.10), Clicking the Background tab Then clicking Transparent Background (Or Solid Color before 8.10, I think), then adjusting the transparency slider.

---

### Post by Forlong on 2009-01-05
Yup, the Gnome-Terminal is pretty much the only GNOME application that supports real transparency. No need to tweak anything with Compiz (it just needs to running).

---

### Post by Andy06 on 2009-01-05
Ok thanks a lot guys.

I also managed to get all the other windows transparent via compiz and successfully excluded firefox.

Thanks again

---


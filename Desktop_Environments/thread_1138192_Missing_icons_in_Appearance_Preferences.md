---
title: "Missing icons in Appearance Preferences"
date: 2009-04-26
forum: Desktop Environments
---

### Post by thin-King on 2009-04-26
This is a clean install of Jaunty and I was downloading icons and themes when the icons for the default GNOME and Tangerine icon sets went missing. Have a look...

[[IMG]http://img147.imageshack.us/img147/6956/missingicons.th.png[/IMG]](http://img147.imageshack.us/my.php?image=missingicons.png)

The icon sets still work but their 'avatars' aren't showing correctly in the preferences pane. Logging out, rebooting, and switching users doesn't change anything. 

Was thinking it might have to do with one of the config files in the home directory or maybe rebuilding the icon cache but I've been searching and can't remember how to resolve this.

TIA

---

### Post by rolandixor on 2009-04-26
same here. I can't find a solution, tho I'm sure there is one, as I've had this problem before and glanced a post that had a solution, but can't seem to find it now :)

---

### Post by thin_king on 2009-04-28
Yeah I'm pretty sure there's a fix too since I've also seen this before, I think when the Tango icons first came out. I seem to remember something about an older icon set screwing up the default fallback icons and having to change a config file to restore them. Does that ring a bell? Did you install any older icon sets? I always install incons and themes manually into usr/share/icons and themes folders for all users. Don't know if that has any bearing on this.

Any help appreciated folks...

---

### Post by thin_king on 2009-04-28
Alright so now I have the GNOME and Tangerine icon set avatars back in the appearance preferences pane but now the icons themselves aren't showing up. This happened when I was eliminating some older themes I had downloaded. So it looks like it could be a theme related issue. The other thought that crossed my mind was that it could be related to permissions.


[[IMG]http://img513.imageshack.us/img513/5010/noicons2.th.png[/IMG]](http://img513.imageshack.us/my.php?image=noicons2.png)

---

### Post by thin_king on 2009-04-28
More random weirdness, all of the window borders show up black in the appearance preferences.

[[IMG]http://img232.imageshack.us/img232/9880/blackborders.th.png[/IMG]](http://img232.imageshack.us/my.php?image=blackborders.png)

---

### Post by thin_king on 2009-04-28
Looking more and more like a theme problem. The black window borders were solved by deleting a dark theme called Tactile. Still haven't got the GNOME or Tangerine icons back. 

It's a real shame that there's so much discontinuity and breakage between versions that you can't even download some nice older themes without running into stupid problems.

---

### Post by thin_king on 2009-04-28
And finally, the last two theme culprits were Darkilouche and Pharago. All back to normal now once those were deleted. So folks, the moral of the story is be careful with older themes!

Themes for the blacklist: Tactile, Darkilouche, Pharago

and probably quite a few more out there...

---

### Post by rolandixor on 2009-04-28
I do happen to have some old icon themes installed. I think this may be the cause indeed. I'll try to fix that part and see if it solves the problem, though I think it may be GTK+ themes too.

---

### Post by rolandixor on 2009-04-28
I think we could put together a nice black list of themes and the versions that support them, ways to get them working if possible etc.

I can provide a place to host them on my site.

---


---
title: "Disable Quick Find feature in Nautilus"
date: 2009-04-06
forum: General Help
---

### Post by Ryback on 2009-04-06
Whenever I start typing in any nautilus window (and firefox, which is why I'm asking this question) nautilus brings up a "Quick Find" bar and starts displaying and searching for that text.  I find it quite annoying - does anyone know how I can switch it off?

I took a look through the configuration settings for Nautilus but couldn't see anything obvious.

Thanks :)

---

### Post by jo4hnc on 2009-04-06
In Firefox, Make sure that the "Search for Text When I start Typing" box isn't checked. Check in Firefox Preferences, click on Advanced and look under the General tab. I'm not sure about Nautilus.

j

---

### Post by Ryback on 2009-04-07
Is that option in firefox related to the firefox find feature (CTRL+F) or the nautilus one? The firefox find feature I don't have a problem with.  It's the nautilus "Quick Find" that pops up and annoys me while I'm in firefox that I'm trying to disable.

---

### Post by jo4hnc on 2009-04-07
Here's a guy who was upset that it went away. Hopefully it'll point you in the right direction.

[http://ubuntuforums.org/showthread.php?t=980346](http://ubuntuforums.org/showthread.php?t=980346)

Found using a search of the forum. It's a good idea to check that way first.

---

### Post by Ryback on 2009-04-07
Thanks :) I did use the search function, and found that post.  Looks like that was caused by a different application misbehaving (SCIM) and interfering with nautilus "behind the scenes".  I found other similar posts too, but nothing on how I can actually configure nautilus to change it's behaviour.  I'm not too keen on deliberately breaking nautilus using SCIM as it could break other functionality further on down the line...

---

### Post by jo4hnc on 2009-04-07
Hi again. On my machine, under System>Preferences there is a SCIM configuration tool (SCIM Input Method Setup). You might look in there to see if you can set it up to your liking. Look at Panel>GTK.

---

### Post by Ryback on 2009-04-07
Actually I just realised this IS different from the quick find feature in nautilus - I thought they were actually the same thing.  So your original suggestion for "search for text when I start typing" in firefox removes the problem there.  So my original question was ill-posed in the first place.  Thanks for taking the time to look into this.

---

### Post by jo4hnc on 2009-04-07
You're welcome.

---


---
title: "Terminal No Longer Affected by Profiles"
date: 2012-06-29
forum: Desktop Environments
---

### Post by bay3rs on 2012-06-29
I think it's gnome terminal, whatever the default that comes with Ubuntu is.  I'm using version 12 and it has the icon "Terminal" as the application name.

I had a terminal profile set up with all my preferences and that worked fine for a couple of days.  I'd click on the icon marked "Terminal" and the terminal would launch with my settings.  (I had created a profile called term01, configured that to my liking and set it to be the default.)

Then yesterday I decided to manually adjust my terminal's size by dragging the corner with my mouse.

That seems to broken the program.  Now when I launch a new terminal by clicking on the icon, my custom profile is ignored.   

I can open the menu item Terminal and click on number 3 say, and that works, but if I open the Terminal menu item, click on Profiles, and manually set it to Default or term01, nothing happens.

---

### Post by rajan on 2012-07-03
I'm still using 10.04, but I think it might be the same still. In my terminal profiles window, there's an option for "Profile used when launching a new terminal:" and in that drop-down box your term01 should be there. If it's the "Default" profile, that's why you're not getting the right profile. 

Also, if you really want to make sure your profile is doing ok, check out:

```
username@computer:~$ ls .gconf/apps/gnome-terminal/profiles/
Default  %gconf.xml

```

As you can see, I don't have any other profiles besides "Default." If you don't see term01 there, something probably deleted it. I've never heard or seen a profile get deleted, although if you log in as a different user, you will not have access to the same profiles. This includes root, so if you have superuser privileges, you won't get term01.

---


---
title: "Human List"
date: 2008-03-07
forum: Desktop Environments
---

### Post by WamBamBoozle on 2008-03-07
The real problem here is that the UI for "Login Window Preferences" does't make it clear that I have to restart GDM for this to work. At least I think thats the real bug. I restarted GDM and everything started working as advertised so, if I could, I'd withdraw the help request, which ran originally as:

I have my "Login Window Preferences" set so that on the "Local" tab I've selected the theme "Random from selected". The themes selected are

	 "Happy Gnome with Browser"
	 "Human List"

I have photos set for the users of my desktop. Once upon a time both of the above themes would present a menu of login ids along with their pictures, just as it is supposed to do. But it no longer displays their pictures. I log in by knowing my username/password just like in 1973. Nothing is displayed. There is nothing selectable in the area where the list of users should appear. How do I fix this?

In the "Users" tab I have the "Include all users from /etc/passwd" checked.

This is different from #144325 "[Gutsy] Face browser missing faces" in that *nothing* is displayed in the user menu. My install, like this bug, is the Gutsy upgrade from Fiesty.

It sounds rather like bug #126702 "user images not shown when logging back in" except that has a misleading title as the face browser is simply broken.

I thought it might be a dup of Bug #153837 "gdm shows empty face browser" but alas the cause for that one was traced to ubuntustudio-gdm-theme -- I do not have that installed.

---


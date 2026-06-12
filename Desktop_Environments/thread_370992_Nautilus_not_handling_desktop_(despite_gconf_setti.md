---
title: "Nautilus not handling desktop (despite gconf settings)"
date: 2007-02-26
forum: Desktop Environments
---

### Post by ahawks on 2007-02-26
I left my laptop off over the weekend, and was greeted by this odd behavior when I got in this morning.  Nautilus is not (properly) handling my desktop. First thing I checked was the gconf settings, logged out and back in, rebooted, and still no luck.

With Beryl as the window manager, it doesn't render the wallpaper or icons, or handle clicks.

With Metacity as the window manager, it renders wallpaper, but doesn't receive right-clicks or display icons. 

Any ideas?

Below is my nautilus preferences from gconf.  Notice the show_desktop=true

```
$ gconftool-2 -R /apps/nautilus/preferences
 show_image_thumbnails = local_only
 side_pane_view = NautilusPlacesSidebar
 enable_delete = true
 start_with_status_bar = true
 desktop_font = Sans 10
 click_policy = double
 theme = default
 confirm_trash = true
 background_filename = 
 navigation_window_saved_geometry = 774x706+0+239
 start_with_sidebar = true
 background_color = #5BA7CF
 navigation_window_saved_maximized = false
 side_pane_background_color = #ffffff
 start_with_location_bar = true
 desktop_is_home_dir = false
 preview_sound = local_only
 thumbnail_limit = 5242880
 directory_limit = -1
 start_with_toolbar = true
 show_directory_item_counts = local_only
 show_icon_text = local_only
 date_format = locale
 side_pane_background_set = false
 default_folder_viewer = icon_view
 background_set = false
 no_ubuntu_spatial = true
 executable_text_activation = ask
 **show_desktop = true**
 sort_directories_first = true
 always_use_browser = true
 sidebar_width = 146
 search_bar_type = search_by_text
 show_advanced_permissions = false
 side_pane_background_filename = 
 always_use_location_entry = true

```

---

### Post by ComplexNumber on 2007-02-26
have a look at apps/nautilus/desktop. are any of the icons clicked on? i'm pretty certan thats not the reason, buty i just want to eliminate the obvious. i've had that same problem before, but i can't remember how i resolved it.

can you give me a printout of apps/metacity/general?

---

### Post by ahawks on 2007-02-26
I always keep those unchecked (show Home, show trash, show computer, whatever else).  But have icons in ~/Desktop that should be shown. 

To test, I checked them all and restarted nautilus and still see nothing.

More info:
$ nautilus --version
Gnome nautilus 2.16.1
(Edgy)

---

### Post by ComplexNumber on 2007-02-26
ok, just in case something has been deleted, go to synaptic and select "reinstall" for nautilus. 
it should be a nautilus problem because thats what draws the desktop. your problem does seem odd.

---

### Post by ahawks on 2007-02-26
I reinstalled nautilus, same behavior.

---

### Post by ahawks on 2007-02-26
Anyone know of a way to get nautilus to dump out a log or anything?

/var/log/messages has normal loading information for gconfd, but no errors/warnings.

I tried strace nautilus and got nothing extraordinary.

---

### Post by ComplexNumber on 2007-02-26
> **ahawks said:**
> Anyone know of a way to get nautilus to dump out a log or anything?

/var/log/messages has normal loading information for gconfd, but no errors/warnings.

I tried strace nautilus and got nothing extraordinary.
install nautilus-dbg. its the debugging package for nautilus.

---

### Post by ahawks on 2007-02-26
Well for whatever reason, installing nautilus-dbg actually *fixed* the problem.  Bazaar.

---

### Post by ahawks on 2007-02-26
Possibly unrelated, but kind of interesting:

After it suddenly worked, I rotated my desktop (beryl) and got this odd/cool behavior:
[http://www.youtube.com/watch?v=2ISjd9dvsU4](http://www.youtube.com/watch?v=2ISjd9dvsU4)

And then realized I probably had the Desktop set as "sticky".  I went into my beryl prefs and sure enough, i was setting the window attribute for t:Desktop:0  in initial viewport, meaning that Desktop would be sticky.

I disabled that and everything seems to be normal.  I don't think that would explain the odd behavior from Metacity though.

---

### Post by Dylan666 on 2007-07-30
> **ahawks said:**
> Well for whatever reason, installing nautilus-dbg actually *fixed* the problem.  Bazaar.

What file did you download? What version? How did you install it?

---

### Post by ahawks on 2007-07-30
I have no idea by now what the problem or solution was that I was talking about... that was at least one major version of Ubuntu ago, and I've stopped using Beryl/compiz.  Sorry.

---


---
title: "Recommended Way to Bring Back All System Tray Icons in Ubuntu 16"
date: 2016-05-02
forum: Desktop Environments
---

### Post by dannymichel on 2016-05-02
What's the recommended way to bring back all system tray icons(whitelist) in Ubuntu 16 as separate icons not included in a dropdown?

---

### Post by mc4man on 2016-05-02
> **dannymichel said:**
> What's the recommended way to bring back all system tray icons(whitelist) in Ubuntu 16 as separate icons not included in a dropdown?
you may want to put your query into some sort of context/example as on the face it makes no sense..
systray/application  icons are separate icons per app  (no dropdown there) & work by clicking on to expose options (certainly a dropdown there

---

### Post by dannymichel on 2016-05-04
Notice skype and foobar on the top right system tray?
I had to install an app that allowed me to see them because Ubuntu hides them by default. I dont like how that app puts them in a dropdown. I'd rather something modify the default hiding behavior Ubuntu has for some really really odd reason has implemented.

---

### Post by QDR06VV9 on 2016-05-04
> **dannymichel said:**
> Notice skype and foobar on the top right system tray?
I had to install an app that allowed me to see them because Ubuntu hides them by default. I dont like how that app puts them in a dropdown. I'd rather something modify the default hiding behavior Ubuntu has for some really really odd reason has implemented.

Hi dannymichel could you in future just use the Attachment option for posting screenshots or big images in the post as they are hard on those with sight impairments and have low bandwidth caps.
Thanks :)

---

### Post by dannymichel on 2016-05-04
> **runrickus said:**
> Hi dannymichel could you in future just use the Attachment option for posting screenshots or big images in the post as they are hard on those with sight impairments and have low bandwidth caps.
Thanks :)

Sure - I used both for that reason, but no problem

---

### Post by QDR06VV9 on 2016-05-04
Thank You!;)

---

### Post by mc4man on 2016-05-04
Ubuntu moved to application indicators a couple of years ago & for the most part apps have created them in lieu of their systray icons.
I probably wouldn't expect that from wine programs & a few others.

In that case to get individual icons you'd need to re-enable systray icons in the unity source & re-build the packages.
The change in source is quite simple, change 1 line of code & disable 1 compile time test. this is the patch I use here to do such in 16.04 - 
```
--- unity-7.4.0+16.04.20160415.1.orig/tests/CMakeLists.txt
+++ unity-7.4.0+16.04.20160415.1/tests/CMakeLists.txt
@@ -251,7 +251,6 @@ if (ENABLE_X_SUPPORT)
                  test_panel_menu_view.cpp
                  test_panel_service.cpp
                  test_panel_style.cpp
-                 test_panel_tray.cpp
                  test_panel_view.cpp
                  test_places_group.cpp
                  test_preview_player.cpp
--- unity-7.4.0+16.04.20160415.1.orig/panel/PanelTray.cpp
+++ unity-7.4.0+16.04.20160415.1/panel/PanelTray.cpp
@@ -133,7 +133,7 @@
   glib::String res_name;
   na_tray_child_get_wm_class(icon, &res_name, &res_class);
 
-  bool accept = FilterTray(title.Str(), res_name.Str(), res_class.Str());
+  bool accept = true;
 
   if (accept)
   {
```

Building unity locally is possible however it tends to fail a number of tests somewhat randomly, plus the build folder goes to around 4GB due to pre-compiled headers. A little bit of a pita, myself just let launchpad deal with this for me

---

### Post by dannymichel on 2016-05-04
> **mc4man said:**
> Ubuntu moved to application indicators a couple of years ago & for the most part apps have created them in lieu of their systray icons.
I probably wouldn't expect that from wine programs & a few others.

In that case to get individual icons you'd need to re-enable systray icons in the unity source & re-build the packages.
The change in source is quite simple, change 1 line of code & disable 1 compile time test. this is the patch I use here to do such in 16.04 - 
```
--- unity-7.4.0+16.04.20160415.1.orig/tests/CMakeLists.txt
+++ unity-7.4.0+16.04.20160415.1/tests/CMakeLists.txt
@@ -251,7 +251,6 @@ if (ENABLE_X_SUPPORT)
                  test_panel_menu_view.cpp
                  test_panel_service.cpp
                  test_panel_style.cpp
-                 test_panel_tray.cpp
                  test_panel_view.cpp
                  test_places_group.cpp
                  test_preview_player.cpp
--- unity-7.4.0+16.04.20160415.1.orig/panel/PanelTray.cpp
+++ unity-7.4.0+16.04.20160415.1/panel/PanelTray.cpp
@@ -133,7 +133,7 @@
   glib::String res_name;
   na_tray_child_get_wm_class(icon, &res_name, &res_class);
 
-  bool accept = FilterTray(title.Str(), res_name.Str(), res_class.Str());
+  bool accept = true;
 
   if (accept)
   {
```

Building unity locally is possible however it tends to fail a number of tests somewhat randomly, plus the build folder goes to around 4GB due to pre-compiled headers. A little bit of a pita, myself just let launchpad deal with this for me
Wow, that's a heck of a lot to do.

---

### Post by wildmanne39 on 2016-05-04
Please use thumbnails or Url's when posting images because many people have slow internet conections and loading pages with large images is very difficult for them.

---

### Post by jim_deadlock on 2016-05-06
You should try Gnome Shell, it has a beautiful way of showing those icons on a small auto-hide tray at the bottom of the screen. The rest of it is very elegant too (yes, I'm biased).

---


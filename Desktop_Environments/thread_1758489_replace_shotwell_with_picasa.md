---
title: "replace shotwell with picasa"
date: 2011-05-14
forum: Desktop Environments
---

### Post by cybergalvez on 2011-05-14
I use picasa for photo management, how do i make it show up in the the dash shortcuts in place of shotwell? Where are these shortcuts configured? where is the default photo management program configured?

---

### Post by mc4man on 2011-05-14
If you want it to show up in the dash (large icons), I don't remember seeing any way as a user.

There is no entry for this in 'Preferred Applications', otherwise you'd just change there.

Edit: just noticed that default 'photo' is a fix me, so Atm shotwell is specified in the source as the default, may just have to change that to "picasa", giving a test run

Those icons work also work from a 'fallback' list, so if for instance shotwell was un-installed the next available (installed) in the list would take it's place
So if rebuilding the unity source picasa was added to the list and shotwell un-installed it would show up (post 6
[http://ubuntuforums.org/showthread.php?t=1744591](http://ubuntuforums.org/showthread.php?t=1744591)

Otherwise you could just add picasa to the launcher, make default ect.
some ideas on if need be
[http://ubuntuforums.org/showthread.php?t=1746081&page=2](http://ubuntuforums.org/showthread.php?t=1746081&page=2)

---

### Post by mc4man on 2011-05-14
Edit: missed your post in that thread - 
Off hand I forget what source file it was in - that was a beta 2 install that I just relaced the other day

If wishing I'll take a look thru the source - I rebuild unity here on my laptop to increase the size to max windows and change 1 other small thing.
(The 75% cutoff is ok on my desktop, for this laptop I prefer a bit higher (use .0875

---

### Post by mgmiller on 2011-05-14
See if this works..
Open your home folder
click on Edit > Preferences
go to the Media tab
Set the drop down next to Photos: to Picasa
close and see what happens (maybe log off and back in?)

---

### Post by mc4man on 2011-05-14
Pretty simple if you re-build (I'd do as ubuntu packages, 3 built, 2 installed, I up the version to keep from updating so this build was
unity 3.8.12-0ubuntu1+nmu1

You actually don't have to remove shotwell - because ATM, for photos the default can't be determined so shotwell is defined directly
As long as you can open p1casa properly this will do nicely

I'd make 2 simple changes to src/PlacesHomeView.cpp, then picasa will automatically show up in dash, and if desired when removed then shotwell will become the new one
 The diff on unity 3.8.12 (probably the same for 3.8.10
```
--- unity-3.8.12.orig/src/PlacesHomeView.cpp
+++ unity-3.8.12/src/PlacesHomeView.cpp
@@ -150,7 +150,8 @@
   _browser_alternatives.push_back("epiphany-browser");
   _browser_alternatives.push_back("midori");
   
-  _photo_alternatives.push_back("shotwell");
+  _photo_alternatives.push_back("picasa");
+  _photo_alternatives.push_back("shotwell");
   _photo_alternatives.push_back("f-spot");
   _photo_alternatives.push_back("gthumb");
   _photo_alternatives.push_back("gwenview");
@@ -290,7 +291,7 @@
 
   // Photos
   // FIXME: Need to figure out the default
-  CreateShortcutFromExec ("shotwell", _("View Photos"), _photo_alternatives);
+  CreateShortcutFromExec ("picasa", _("View Photos"), _photo_alternatives);
```

To show the source file as is after editing - 
  ```

  _photo_alternatives.push_back("picasa");
  _photo_alternatives.push_back("shotwell");
  _photo_alternatives.push_back("f-spot");
  _photo_alternatives.push_back("gthumb");
  _photo_alternatives.push_back("gwenview");
  _photo_alternatives.push_back("eog");


```
and then  - 
```
// Photos
  // FIXME: Need to figure out the default
  CreateShortcutFromExec ("picasa", _("View Photos"), _photo_alternatives);


```


If interested the size before max window
```

--- unity-3.8.12.orig/src/PluginAdapter.cpp
+++ unity-3.8.12/src/PluginAdapter.cpp
@@ -23,7 +23,7 @@
 PluginAdapter * PluginAdapter::_default = 0;
 
 #define MAXIMIZABLE (CompWindowActionMaximizeHorzMask & CompWindowActionMaximizeVertMask & CompWindowActionResizeMask)
-#define COVERAGE_AREA_BEFORE_AUTOMAXIMIZE 0.75
+#define COVERAGE_AREA_BEFORE_AUTOMAXIMIZE 0.875
 


```

---

### Post by Gnome3Crazy on 2011-05-14
ugh...You Need WINDOWS For Picasa You Know...:confused:

---

### Post by Atermoon on 2011-05-14
> **Gnome3Crazy said:**
> ugh...You Need WINDOWS For Picasa You Know...:confused:

Uhm... No, you don't.

---

### Post by cybergalvez on 2011-05-14
> **mgmiller said:**
> See if this works..
Open your home folder
click on Edit > Preferences
go to the Media tab
Set the drop down next to Photos: to Picasa
close and see what happens (maybe log off and back in?)

Well I cheated, I made a shell script in my bin folder called shotwell that points to picasa. Its cheating, but it seems to work pretty well

---


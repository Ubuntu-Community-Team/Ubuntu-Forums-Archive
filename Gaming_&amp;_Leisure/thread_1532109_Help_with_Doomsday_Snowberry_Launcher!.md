---
title: "Help with Doomsday Snowberry Launcher!"
date: 2010-07-16
forum: Gaming &amp; Leisure
---

### Post by Darkjackal on 2010-07-16
I recently got doomsday, I installed it with cmake and such and was excited to finally lauch snowberry. Now, my excitement comes to a grinding halt as soon as I click on the play button and snowberry just quits....I cant explain why, just quits and doesnt launch doom. I looked at the command line and it just says Command Launch followed by Notify Launch and then Command Quit. No explanation no errors nothing. Snowberry just feels the need to launch and then terminate and I have no idea why...Im still really new to using ubuntu and any help at all would be greatly appreciated!

```
:~/deng-1.9.0/snowberry$ python snowberry.py
Module init in example.plugin
Example init called!

Notify: tab-selected
  Selection = tab-summary

Notify: addontab-selected
  Selection = example-bundle

Notify: example-bundle-tab-selected
  Selection = example-bundle-subpage

Notify: collection-box-tab-selected
  Selection = collection-box-part1-bundle

Notify: example2-bundle-tab-selected
  Selection = example2-bundle-preferences

Notify: populating-area
  Area id = general-options

Notify: pref-tab-selected
  Selection = addon-paths

Notify: populating-area
  Area id = game-options

Notify: populating-area
  Area id = display-options

Notify: populating-area
  Area id = graphics-options

Notify: populating-area
  Area id = sound-options

Notify: populating-area
  Area id = input-options

Notify: populating-area
  Area id = developer-options

Notify: populating-area
  Area id = addons-options

Notify: populating-area
  Area id = example-bundle

Notify: populating-area
  Area id = example-bundle-subpage

Notify: populating-area
  Area id = example10-bundle

Notify: populating-area
  Area id = example3-bundle

Notify: populating-area
  Area id = example4-bundle

Notify: populating-area
  Area id = example5-bundle

Notify: populating-area
  Area id = example6-bundle

Notify: populating-area
  Area id = example7-bundle

Notify: populating-area
  Area id = example8-bundle

Notify: populating-area
  Area id = example9-bundle

Notify: populating-area
  Area id = example-pk3

Notify: populating-area
  Area id = collection-box

Notify: populating-area
  Area id = collection-box-part1-bundle

Notify: populating-area
  Area id = collection-box-part2-bundle

Notify: populating-area
  Area id = collection-box-part3-bundle

Notify: populating-area
  Area id = example2-bundle

Notify: populating-area
  Area id = example2-bundle-preferences

Notify: populating-area
  Area id = example2-bundle-selections

Notify: preparing-windows

(python:13206): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 15

(python:13206): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 15

(python:13206): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 15

(python:13206): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 15

(python:13206): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 15

Notify: language-changed

Notify: profile-updated
  Profile = doom2
  Hidden = False

Notify: profile-updated
  Profile = doom1
  Hidden = False

Notify: profile-updated
  Profile = defaults
  Hidden = False

Notify: active-profile-changed

Notify: init-done

Command: play

Notify: launching

Command: quit

Notify: quit

```

---

### Post by Darkjackal on 2010-07-16
Ok, so I discovered the command: quit was just the frontend closing itself down, but still no explanation as to why it wont launch the game. Would maybe a re install help? Or are the wad files bad? Any ideas at all?

---

### Post by afrodeity on 2010-08-08
I'm stuck on this step:

```

You are free to install the Doomsday Engine and Snowberry where you like, but Snowberry's configuration files need to be modified so that Snowberry knows where the doomsday binary is located. The .conf file with the binary's location can be placed in any of Snowberry's conf folders. For example, you could create the following mydoomsday.conf and put it in your personal Snowberry home folder: ~/.snowberry/conf/mydoomsday.conf:

configure doomsday (
  binary: /usr/local/bin/doomsday
  base: /usr/local/share/deng
)

```

I have deng installed but can't find it on the system.

---

### Post by afrodeity on 2010-08-08
I think you need to make sure that latest python-wx is installed.

Check this tutorial

[http://indlovu.wordpress.com/2010/08/08/playing-doom-legacy-on-ubuntu-lucid/](http://indlovu.wordpress.com/2010/08/08/playing-doom-legacy-on-ubuntu-lucid/)

---


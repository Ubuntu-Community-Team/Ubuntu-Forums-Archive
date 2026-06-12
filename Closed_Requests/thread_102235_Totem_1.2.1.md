---
title: "Totem 1.2.1"
date: 2005-12-11
forum: Closed Requests
---

### Post by quinnman on 2005-12-11
New features:
* New Ukrainian (uk) help files
* Use filters in the Open file dialogues
* Support turning off the screensaver when gnome-screensaver is used
* Scroll to the current file in the playlist when starting to play it
* Add ability to play back DVDs and VCDs from .iso and .bin/.cue files
* Add a menu item for switching angles on DVDs
* Play file from the beginning when double-clicking on it in the playlist
* Make CD drives with blank CDs in them unsensitive in the Play Disc menu
* Don't add backup files to the playlist

Bug fixes:
* Avoid weird startes when using the "Toggle fullscreen mode" shortcut
* Fix drag'n'drop on the playlist itself not working
* Parse Shoucast playlists in .m3u files properly
* Stop the currently playing song when loading a media, and playing this media fails
* Set the play/pause buttons' tooltips according to the image
* Fix possible crashes on startup when the widget creation functions cannot be found
* Use N/A instead of '0' when the bitrate or the number of frames per second isn't available in the property window
* Fix a possible crash on startup in the Mozilla plugin
* Fix possible i18n problems with the Nautilus properties window and the Mozilla plugin
* Fix a memory leak in the Mozilla plugin
* Fix a crasher when running the Mozilla plugin in a debug build
* Allow compiling the Mozilla plugin against xulrunner
* Fix duplicate access key in the display preferences
* Fix wrong accesskeys for the saturation and hue sliders
* Show the video properties again when a stream has video
* Move Totem's remote socket to TMPDIR
* Make libmusicbrainz optional
* Build with newer versions of D-Bus

GStreamer:
* Fix an access to invalid memory when getting metadata from a file

xine-lib:
* Avoid playback stopping when seeking forward in DVDs
* Get the xine-lib version at run-time

It would be nice to have this in backports. Of when it will be prepared for Dapper.

---

### Post by jdong on 2005-12-12
In Dapper; awaiting build tests.

---

### Post by jdong on 2005-12-12
Build sent off.

---


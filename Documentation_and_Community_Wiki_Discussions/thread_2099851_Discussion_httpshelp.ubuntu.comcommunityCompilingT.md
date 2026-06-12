---
title: "Discussion: https://help.ubuntu.com/community/CompilingTransmission"
date: 2012-12-30
forum: Documentation and Community Wiki Discussions
---

### Post by andrew.46 on 2012-12-30
This thread is intended for discussion of the following:

CompilingTransmission
[https://help.ubuntu.com/community/CompilingTransmission](https://help.ubuntu.com/community/CompilingTransmission)

Please use the thread for discussion on any good points, problems and suggestions for additions to the page. It is a wiki so please feel free to jump in and make any changes yourself, that is what a wiki is for :)

---

### Post by andrew.46 on 2012-12-31
To get things off to a good start I have updated the wiki page to cover Quantal Quetzal, libevent 2.0.21-stable and Transmission 2.75. Why upgrade from the repository 2.61? Well, the following is the changelog since 2.61:

```

**[COLOR="Red"]Transmission 2.75 (2012/12/13)[/COLOR]**

Mac

    Fix crash on non-English localizations 
[B][COLOR="Red"]
Transmission 2.74 (2012/12/10)[/COLOR][/B]

All tickets closed by this release
All Platforms

    Fix a bug that prevented IPv6 addresses from being saved in dht.dat
    Better handling of magnet links that contain 'tr.x=' parameters
    Add filtering of addresses used for uTP peer connections
    Fix detection of whether or not a peer supports uTP connections 

Mac

    Auto-grouping won't apply until torrents are demagnetized
    Tweak the inspector's and add window's file lists to avoid auto-hiding scrollbars overlapping the priority controls
    Fix potential crash when downloading and seeding complete at the same time
    Fix bug where stopped torrents might start when waking the computer from sleep 

Web Client

    Fix a multi-file selection bug
    Fix bug where the upload and download arrows and rates would not appear for downloading torrents
    Fix bug when displaying the tracker list 

**[COLOR="Red"]Transmission 2.73 (2012/10/18)[/COLOR]**

All tickets closed by this release
Mac

    Fix crash on non-English localizations 

**[COLOR="Red"]Transmission 2.72 (2012/10/16)[/COLOR]**

All tickets closed by this release
All Platforms

    Fix crash when adding magnet links with malformed webseeds
    Fix handling of magnet links' webseed URLs that contain whitespace
    Fix remaining time estimates of magnet links that have webseeds
    Show the webseed count in the torrent list when downloading from webseeds 

Mac

    When possible allow automatic switching to the integrated GPU on dual-GPU machines
    Include seeding-complete transfers in the badged count on the Dock icon 

GTK+

    When adding torrents by URL from the clipboard, handle whitespace in the link 

Qt

    Fix dialog memory leaks 

Web Client

    Minor interface fixes 

**[COLOR="Red"]Transmission 2.71 (2012/09/26)[/COLOR]**

All tickets closed by this release
Mac

    Fix crasher on 10.6 Snow Leopard 

**[COLOR="Red"]Transmission 2.70 (2012/09/25)[/COLOR]**

All tickets closed by this release
All Platforms

    Improved speed with the µTP protocol
    Fix bug that caused some incoming encrypted peer connections to fail
    Fix bugs with the speed limit scheduler
    Fix crasher with magnet links 

Mac

    Notification Center support on Mountain Lion
    Torrent files can be previewed with Quick Look in the Finder
    Add an option to remove transfers when seeding completes
    Fix displaying the Web Client with Bonjour
    Fix bugs with Time Machine exclusions
    Other minor interface tweaks and bug fixes
    Removed Simplified Chinese localization because of lack of localizer 

GTK+

    Require GTK+ 3.4 

Qt

    Control speed limit from the icon tray
    Improved behavior when clicking on torrents in the torrent list
    Fix bug where torrent files were not deleted
    Fix bug with unicode characters in the default location 

Web Client

    The file inspector tab displays files nested under directories
    Improved scrolling on iPad
    Fix incorrectly rendered characters
    Fix bug involving attempts to post notifications without permission 

```

Pretty convincing?

---

### Post by andrew.46 on 2013-01-27
Transmission 2.76 has been released and I have updated the wiki appropriately. Changes in this version:

```

Transmission 2.76 (2013/01/08)

All tickets closed by this release
All Platforms

    Better error logging when user-provided scripts can't be executed
    The "Time Remaining" property wasn't set for torrents with webseeds but no peers
    Fix rare error that created a directory name "$HOME" 

GTK+ Client

    Fix sort-by-age regression introduced in 2.74
    The "Edit Trackers" window didn't resize properly due to a 2.70 regression
    Raise the main window when presenting it from an App Indicator 

Qt Client

    Add magnet link support to transmission-qt.desktop
    Fix notification area bug that inhibited logouts & desktop hibernation
    Use the "video" icon when the torrent is an mkv or mp4 file
    Toggling the "Append '.part' to incomplete files' names" had no effect
    Fix display of the torrent name in the Torrent Options dialog
    Fix cursor point bug in the filterbar's entry field
    Fix crash when adding a magnet link when Transmission was only visible in the system tray
    Fix free-memory-read error on shutdown 

Daemon

    Better watchdir support
    Documentation fixes in transmission-remote's manpage 

Web Client

    Fix indentation of the torrent list and toolbar buttons on mobile devices 

CLI

    If the Download directory doesn't exist, try to create it instead of exiting 

```

Hope somebody is reading this, feed back has been a little low :(

---

### Post by dhicom on 2013-02-05
Hello.

Thank you for your effort creating the nice tutorial.
If I may add, could you please add another way for installing Transmission just for web based only. Mostly, many people using Transmission to gain smallest foot print of the computer resource, like me. :D

I try your instruction, with small adjustment to disabling the gtk and other gui which I don't need them. I just want my headless Transmission, accessing from any browser, however, I failed. Some parameter like --disable-gtk isn't working after ./configure

Any suggestion would be appreciate..

Another thing, if you don't mind I am being little bit greedy, can you add another way like performing upgrade, rather than new compiling. Many peoples will use the old one and like to upgrade. However, you haven't write the "upgrade" tutorial. Just my though.

Thanks.

---

### Post by andrew.46 on 2013-02-15
> **dhicom said:**
> If I may add, could you please add another way for installing Transmission just for web based only. Mostly, many people using Transmission to gain smallest foot print of the computer resource, like me. :D

I try your instruction, with small adjustment to disabling the gtk and other gui which I don't need them. I just want my headless Transmission, accessing from any browser, however, I failed. Some parameter like --disable-gtk isn't working after ./configure

Any suggestion would be appreciate..

Looks like what you are after may very well be:

```

./configure **[COLOR="Red"]--without-gtk[/COLOR]**

```

Perhaps look at rtorrent for a truly light client?

> Another thing, if you don't mind I am being little bit greedy, can you add another way like performing upgrade, rather than new compiling. Many peoples will use the old one and like to upgrade. However, you haven't write the "upgrade" tutorial. Just my though.

I guess I could add a note concerning this, although since it is a wiki you could do this yourself :). No escaping the recompiling of Transmission itself though...

Thanks very much for your thoughts and questions regarding this wiki page!

---

### Post by dhicom on 2013-02-22
Thanks for the tip, sir. Appreciated.

Along with the version 2.77, I try the trick and its worked. :)

---

### Post by andrew.46 on 2013-02-22
Great news, glad it has all worked out:)

---


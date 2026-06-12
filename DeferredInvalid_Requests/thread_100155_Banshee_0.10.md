---
title: "Banshee 0.10"
date: 2005-12-07
forum: Deferred/Invalid Requests
---

### Post by vassie on 2005-12-07
**New Features**

  [LIST]
[*] Completely rewritten and much smarter import backend
[*] iPod Syncing is enabled again and is much improved now it is implemented through the new DAP framework
[*] Experimental GStreamer 0.10 playback support (Ripping/Transcoding port not yet complete)
[*] MimeType detection through GStreamer and Gnome VFS for importing
[*] Interface updates and minor polish; Icon Theme support for most icons
[*] Monodoc API Documentation for some namespaces
[*] New French translation Stephane Raimbault
[*] Imported items show up in library view only if there is no active search or new items match the search [/LIST]  **Important Notes**

  1. Experimental GStreamer 0.10 support has been added. Currently only the playback backend has been ported to the new GStreamer API. Transcoding and Ripping/CD support have not been ported yet. If you would like to test the GStreamer 0.10 playback backend, pass --with-gstreamer-0-10 to configure. 
 2. Multimedia keys support was disabled for this release after some re-thinking of how this should be handled. We feel it's unsafe to steal key-grabs in such a large program for such a small task. This support should really be implemented in a separate process. 
  **Major Bug Fixes**

  [LIST]
[*] Progress reporting and import logic and stability is very much improved (fixes [#314965]("http://bugzilla.gnome.org/show_bug.cgi?id=314965") (*[http://bugzilla.gnome.org/show_bug.cgi?id=314965](http://bugzilla.gnome.org/show_bug.cgi?id=314965)*), [#318330]("http://bugzilla.gnome.org/show_bug.cgi?id=318330") (*[http://bugzilla.gnome.org/show_bug.cgi?id=318330](http://bugzilla.gnome.org/show_bug.cgi?id=318330)*))
[*] Library view updates while importing an Audio CD ([#316132]("http://bugzilla.gnome.org/show_bug.cgi?id=316132") (*[http://bugzilla.gnome.org/show_bug.cgi?id=316132](http://bugzilla.gnome.org/show_bug.cgi?id=316132)*))
[*] Search now works properly while importing ([#316102]("http://bugzilla.gnome.org/show_bug.cgi?id=316102") (*[http://bugzilla.gnome.org/show_bug.cgi?id=316102](http://bugzilla.gnome.org/show_bug.cgi?id=316102)*))
[*] Banshee should no longer crash if searching at startup ([#323202]("http://bugzilla.gnome.org/show_bug.cgi?id=323202") (*[http://bugzilla.gnome.org/show_bug.cgi?id=323202](http://bugzilla.gnome.org/show_bug.cgi?id=323202)*)) [/LIST] 
Thanks
Ben

---

### Post by XQC on 2005-12-07
I also want Banshee 0.10 to hit the backports.
But probably it's not possible because a new version of mono is required...

---

### Post by sjoeboo on 2005-12-07
yeah, untill mono is backported, banshee etc won't be. 

in the mean time, there is an "unoffical" repo to get mono/banshee etc from (current mono, banshee might be current or close, at the very least you'll have the mono to build the current release)

deb [http://packages.filefind.net/](http://packages.filefind.net/) ubuntu-breezy dotnet p2p

---

### Post by arpunk on 2005-12-07
Yea, we all been waiting for the mono backport :P, hope we can get monodevelop backported too.

---

### Post by XQC on 2005-12-09
[quote=sjoeboo]
deb [http://packages.filefind.net/]("http://packages.filefind.net/") ubuntu-breezy dotnet p2p[/quote]
Banshee 0.10 is now available in this repo.

Edit:
I can't confirm the "improved iPod syncing", Banshee didn't manage to transfer one song to the ipod without a crash.
Also it hangs very often by searching something in the library, so I have to kill it.

---

### Post by akurashy on 2005-12-12
banshee have to much dependencies imho, its taking me a while to grab everything =/

---

### Post by charlieg on 2005-12-13
[quote="XQC"]Also it hangs very often by searching something in the library, so I have to kill it.[/quote]

Seems to work perfectly for me.  I noticed that some parts of the mono upgrade were optional - perhaps you've not done that?

---

### Post by XQC on 2005-12-14
[quote=charlieg]Seems to work perfectly for me.  I noticed that some parts of the mono upgrade were optional - perhaps you've not done that?[/quote]
Oh yes, I've done that.

Perhaps it's because of the issue that Banshee can't handle very large libraries very well... I once tested it with a ~200 tracks library and all was fine. But with about 10000 files it has its problems.
Also Banshee needs about 45 seconds to load the library (and my computer is by no means outdated).

Still not the best player around, especially when comparing to windows apps, but I'm confident that Banshee will be a superb player in one year.

---

### Post by eduardgrebe on 2005-12-18
[QUOTE=sjoeboo]yeah, untill mono is backported, banshee etc won't be. 

in the mean time, there is an "unoffical" repo to get mono/banshee etc from (current mono, banshee might be current or close, at the very least you'll have the mono to build the current release)

deb [http://packages.filefind.net/](http://packages.filefind.net/) ubuntu-breezy dotnet p2p[/QUOTE]

Does anyone know where these or similar breezy PPC packages can be found? Thanks.

---

### Post by myke on 2005-12-27
I'd love to have banshee to use with my ipod but it's quite buggy it seems.  I used the suggestions above to upgrade to .10.2 and every time I try to sync, banshee just blinks off.   It recognizes the ipod fine and lets me add songs for syncing but when I actually try to do so ... it cuts off every time.  I have all dependencies and even recommendations installed just fine ... I don't know what else to do.  I hate having to log off and back to XP just for the ipod.  It's quite annoying.

---

### Post by shu on 2005-12-28
I had several talks with abock, banshee's author and we haven't found the reason why banshee crashes. It works ok in other systems than ubuntu. The segfault happens in the "native" code, so it's mono and it's libraries that crashes, not banshee itself. 

:???:

---

### Post by eduardgrebe on 2005-12-28
[QUOTE=myke]I'd love to have banshee to use with my ipod but it's quite buggy it seems.  I used the suggestions above to upgrade to .10.2 and every time I try to sync, banshee just blinks off.   It recognizes the ipod fine and lets me add songs for syncing but when I actually try to do so ... it cuts off every time.  I have all dependencies and even recommendations installed just fine ... I don't know what else to do.  I hate having to log off and back to XP just for the ipod.  It's quite annoying.[/QUOTE]

Use different software to control the ipod in the mean time. For example, gtkpod works well. It's available in synaptic.

---


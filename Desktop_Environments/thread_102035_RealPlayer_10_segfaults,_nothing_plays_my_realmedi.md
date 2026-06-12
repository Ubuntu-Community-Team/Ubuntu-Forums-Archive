---
title: "RealPlayer 10 segfaults, nothing plays my realmedia stream"
date: 2005-12-11
forum: Desktop Environments
---

### Post by kest on 2005-12-11
I had a faint memory of having got RealPlayer to work in Hoary so I downloaded the binary installer (why can't they distribute as a tarball?!) from real.com and used it to install the program to /opt/RealPlayer. It seemed to install fine but now I get this when I try to run "realplay" (the shell script symlinked in /usr/bin):
> /usr/bin/realplay: line 75: 10948 Segmentation fault      $REALPLAYBIN "$@"
and when running /opt/RealPlayer/realplay.bin itself:
> ** (realplay.bin:11254): WARNING **: HXPlayer: Error 0x80004005: "A general error has occurred."

** ERROR **: Could not create helix engine. You must run:
export HELIX_LIBS=<path to your helix libs>

aborting...
Aborted
Apparently HELIX_LIBS is supposed to point to where lib/libgtkhx.so is. The realplay script points it to /opt/RealPlayer. I get the the same segfault when I point it to /usr/lib/helix/player, where a libgtkhx.so was installed by the Synaptic installation of Helix Player.

When I open up Helix player and try to play a realmedia stream I'm supposed to watch, it resizes itself as if to show the clip, shows the right running time and name but fails with the message
> Error

Connection to server has been lost. You may be experiencing network problems. (rtsp://ra.yle.fi:554/opintoradio/cern/a99001slt1.rm)
Googling with the error message only gave me a mailing list post that said Helix Player won't work with ldap in the hosts section of nsswitch.conf, and I don't have it there either. VLC Player fails silently when opening the stream (shows the file name for a while and then doesn't do anything). The same stream works with just about anything on my Windows box. I seem to have Helix and realmedia plugins for Firefox (according to about: plugins), but accessing the stream in Firefox only ever gets to "connected to server" and does nohing. However, it seems that the plugin playing that is mplayerplug-in, which also claims to handle realmedia, though only up to version 9.

Sorry for the long post. I really have no idea what's wrong. Does anyone have an idea? :???:

---


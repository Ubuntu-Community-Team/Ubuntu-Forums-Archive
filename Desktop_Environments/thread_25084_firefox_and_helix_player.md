---
title: "firefox and helix player"
date: 2005-04-09
forum: Desktop Environments
---

### Post by fsman on 2005-04-09
I regularly use the bbc.co.uk site. it uses realplayer for the video and audio.
In mandrake I could download helix and the real codecs and video/audio would play in the browser.

I have downloaded Helix and installed the real-codec rpm in usr/lib/real - so the helix can play real files.

problem is that unlike mandrake, in ubuntu firefox doesn't seem to load helix. Any ideas?

PS - I recommend the bbc website

---

### Post by joshmachine on 2005-04-09
have you checked that the plugins have been copied to the correct places?

i.e. are they in ~/.mozilla/plugins
or 
/usr/lib/mozilla/plugins

If they aren't you can symlink them into either.  
It should be obvious in the installation directory which are the plugins (for realplayer10 there is a "mozilla/plugins" directory, not sure about the helix distro through.

If they are there, what do you get when you type "about:plugins"

in your location bar?

---

### Post by fsman on 2005-04-09
I'm almost there.

[http://plugindoc.mozdev.org/linux.html](http://plugindoc.mozdev.org/linux.html)

---

### Post by fsman on 2005-04-09
gave up.

actually installing real player was easy see...



[http://www.elyps.de/guide.html#realplayer](http://www.elyps.de/guide.html#realplayer)

the important part is in english, so don't mind the .de

---

### Post by p!=f on 2005-04-09
Did you install Helix from sources or using Ubuntu package?

---

### Post by fsman on 2005-04-09
I used synaptic to install helix.
I used the guide in the above post to install real-player

---


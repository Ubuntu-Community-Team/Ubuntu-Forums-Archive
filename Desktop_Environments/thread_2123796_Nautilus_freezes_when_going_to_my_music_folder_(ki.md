---
title: "Nautilus freezes when going to my music folder (killall command required)"
date: 2013-03-09
forum: Desktop Environments
---

### Post by KBD20 on 2013-03-09
Since my last hardware upgrade (and rsyncing across),
My music folder has started to cause nautilus to lock up (causing me to use the killall command and restarting nautilus). 
And I know this is probably not a too many files/folders issue, since when I run nautilus as root, this does not happen; terminal has mentioned some thumbnail files being corrupt or unreadable so this seems to be a thumbnail issue.
Is there a way to delete the thumbnails? (this issue is recursive since some thumbnails are further levels down in the file structure)

Thanks,

Edit: The issue is resolved after upgrading to 13.04

---

### Post by ManamiVixen on 2013-03-09
[http://mygeekopinions.blogspot.com/2011/06/how-to-remove-nautilus-thumbnail-cache.html](http://mygeekopinions.blogspot.com/2011/06/how-to-remove-nautilus-thumbnail-cache.html)
Try that, it tells you how to delete the thumbnail cache. :) Hope that helps!

---

### Post by KBD20 on 2013-03-09
Thanks for the link,
It didn't seem to help though.
upon starting nautilus in terminal it did give the following error output.

> Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory



and this is what I get when entering one of my music folders (just showing one to give a general idea).

> (nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Comma%20King%20-%20Smile%20Through%20The%20Stars.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Daydream%20Anatomy%20-%20=AsymmetricGrind=%20(original%20mix).flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Daydream%20Anatomy%20-%20=AsymmetricGrind=%20(Remastered).flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/NWFA%20-%20A%20Lighthouse%20Waits.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/NWFA%20-%20With%20All%20Clarity.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Redshirt%20Theory%20-%2001%20-%20I%20Think%20It's%20Gonna%20Rain.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Redshirt%20Theory%20-%2002%20Rattled%20Snake.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Redshirt%20Theory%20-%2003%20San%20Diego%20(radio%20edit).flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Redshirt%20Theory%20-%2004%20The%20Redshirt%20Anthem.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Tendril.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Testudo%20-%20Pillium.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/Testudo%20-%20Who%20Will%20Be%20There.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Error creating thumbnail for file:///home/kane/Music/beat_hazard_ultra_ost_flac/%7BX-FaCtOr%7D%20-%20X1%20-%2001%20Enigma.flac: Unrecognized image file format

(nautilus:13625): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/flac: Unrecognized image file format



I had been getting this on other files too, I also couldn’t seem to find the image it was drawing off of as well.
I'm not sure why cache clearing didn't work though.

Thanks,

---

### Post by fiodev on 2013-03-09
turn off the file manager plugin in gedit prefrences plugins

---

### Post by KBD20 on 2013-03-09
I found that since I didn&#8217;t have samba installed ,that what was causing the error, it now no longer shows up.
The music directory still freezes up though;
Where can I find the gedit preferences for the file manager?

---

### Post by KBD20 on 2013-04-30
After upgrading to 13.04 this issue seems to be resolved.

---


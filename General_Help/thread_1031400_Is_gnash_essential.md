---
title: "Is gnash essential?"
date: 2009-01-05
forum: General Help
---

### Post by Odyssey1942 on 2009-01-05
I am not sure where to post this, so please move it if appropriiate.

I am looking at my system monitor. At the moment, I have a large number of firefox windows open, with ff using cpu resources within a range of 18-31% (this while I am just looking at the sys mon and not doing any lookups or searches, etc, i.e., not actively working the ff windows).

gtk=gnash utilizes between approximately a combined (there are several instances of gtk-gnash listed) minumum of 30% and ranging up to 60%. 

The description of gnash is:
"free SWF movie player  
Gnash is a free Flash movie player, which works either standalone, or as plugin for Firefox/Mozilla or Konqueror. Currently it is in a alpha state. The plugins are under heavy development at this time.
Gnash supports the majority of Flash opcodes up to SWF version 7, and a wide sampling of ActionScript classes for SWF version 8.5. All the core ones are implemented, and many of the newer ones work, but may be missing some of their methods.
Included in the Gnash is an XML based messaging system, as specified in the Flash specification. This lets a flash movie communicate over a TCP/IP socket, and parse the incoming XML message. This lets a movie be a remote control for other devices or applications.
This package includes the standalone GTK+-based OpenGL player.
Homepage: http://www.gnu.org/software/gnash/"

Is this a critical component? Is the very high CPU usage a result of my many ff windows open? If I remove gnash, what would happen?

Is there a resource anywhere that lists the essential processes?

---

### Post by mcduck on 2009-01-05
No, it's not essential but if you wish to be able to see flash content on web pages you need to have either Gnash or Adobe's flash plugin installed.

Anyway, using a lot of CPU power is quite normal for flash applications, most likely the usage will drop as soon as you close any pages with flash content.

---

### Post by Odyssey1942 on 2009-01-05
How much of an impact does additional RAM have on this, if any?

---

### Post by mcduck on 2009-01-05
None. Flash just happens to be quite CPU-intensive, and badly done flash movies/advertisements can use ridiculous amounts of CPU power. Amount of RAM has nothing to do with it.

Gnash is still quite new, you could try if the Adobe's flash plugin works better for you. But the best solution really is to use Adblock+ or some other Firefox extension that allows you to block flash advertisements, that way you will at least only suffer from the slowdown caused by flash content you *want* to see. :)

---

### Post by wolfen69 on 2009-01-05
if you decide to go with adobe flash (which is better imo), [here]("http://get.adobe.com/flashplayer/") is the link. download the .deb for ubuntu and click to install. but remember to remove gnash first. and yes, flash content can use alot of resources. just the way it is.

---


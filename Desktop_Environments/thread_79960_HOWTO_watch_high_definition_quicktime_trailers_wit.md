---
title: "HOWTO: watch high definition quicktime trailers with firefox+mplayer/vlc"
date: 2005-10-21
forum: Desktop Environments
---

### Post by 3david on 2005-10-21
As you may have noticed, apple are now using .mov files as buttons in the high definition trailers pages, this messes up the mplayer mozilla plugin,
I wrote a greasemonkey script that changes these to normal links:

   [http://www.userscripts.org/scripts/show/1993](http://www.userscripts.org/scripts/show/1993)

(for those who don't know greasemonkey is a firefox extension that allows you to change webpages using javascript: [https://addons.mozilla.org/extensions/moreinfo.php?id=748](https://addons.mozilla.org/extensions/moreinfo.php?id=748))

so these are the steps:

1. install greasemonkey and the "Apple Buttons Fix" greasemonkey script
2. install mplayer and the mozilla-plugin (using one of the Howto threads, i can't remember which)
3. install vlc (since mplayer doesn't support the audio codec of some of the hd trailers)

now go to one of the hd trailers in apple, those who are supported by mplayer will have no problem playing within firefox, the others won't play but the mplayer plugin will download them to /tmp/mplay????
just run "vlc /tmp/mplay???"
(run ls -s /tmp/mplay* and see which one is the right size)


I know this isn't perfect, but it works.

---

### Post by elias4444 on 2005-11-27
I tried your instructions, but everytime I hit one of apple's high definition movie trailer pages, the script run, but my whole system locks up (like it did before without the script). Any ideas?

---

### Post by !nkubus on 2006-06-26
The same appear here, the system is completely freezing like it was before I install the script :(

---


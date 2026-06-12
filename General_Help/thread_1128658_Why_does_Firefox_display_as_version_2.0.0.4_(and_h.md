---
title: "Why does Firefox display as version 2.0.0.4 (and how to install v 3?)"
date: 2009-04-17
forum: General Help
---

### Post by papachungo13 on 2009-04-17
Hi

Forgive if this question has been asked/answered before, but I would like to install v3 of Firefox and not getting what I expected.

Synaptic Package Manager indicates that I already have Firefox 3.0.0.8 installed, however when I check the version it displays 2.0.0.4.

How do I get version 3?

I'm using Ubuntu 8.10

Thanks.

---

### Post by mikewhatever on 2009-04-17
Have you tried reinstalling? Version 2.0.0.4 is not in Intrepid's repositories, I really wonder where it came from.

---

### Post by trlkly on 2009-04-17
You probably already have it, it's just the link in the menu is wrong. But let's check.

Open a terminal, and type in firefox. Check the version of the program that comes up. If it is still 2.0.0.4, then we still have a problem. If it's the right one, then all you need to do is edit the Link's properties to say "firefox %u"

If it's the wrong one, then make sure firefox-2 is uninstalled in Synaptic. Reinstall firefox and firefox-3.0.

If you have problems with Firefox after doing this, then you may have to completely remove the last two packages, and then install them again. This will, unfortunately, clear your bookmarks, and most, if not all, of your plugins.

---

### Post by papachungo13 on 2009-04-17
> **trlkly said:**
> You probably already have it, it's just the link in the menu is wrong. But let's check.

Open a terminal, and type in firefox. Check the version of the program that comes up. If it is still 2.0.0.4, then we still have a problem. If it's the right one, then all you need to do is edit the Link's properties to say "firefox %u"

If it's the wrong one, then make sure firefox-2 is uninstalled in Synaptic. Reinstall firefox and firefox-3.0.

If you have problems with Firefox after doing this, then you may have to completely remove the last two packages, and then install them again. This will, unfortunately, clear your bookmarks, and most, if not all, of your plugins.

Running firefox from terminal opened 2.0.0.4.

Completely uninstalled firefox 3 and components with Synaptic.  There was no trace/mention of FF2.  Restarted and found no links to FF 2 or 3.  Reinstalled FF3 from Synaptic and FF2 returned with all bookmarks customizations etc.  Not sure if I should have also mentioned that my setup is coming from 6.10 up through to 8.10.  I don't know how relevant that is, but just in case (though when I ran 6.10, FF was at 1.x).

---

### Post by Amerinidiot1231 on 2009-04-17
You could try going to the Firefox/Mozilla website and downloading the .deb from there, maybe something with synaptic is off.

---

### Post by trlkly on 2009-04-18
Sorry I didn't get back to you last night. Getting a .deb package will work (don't know about updates), but there may be a more important underlying problem.

You may still have repos from an earlier version of Ubuntu. Check you /etc/apt/sources.list, and make sure there are no references to other versions. If so, try to find the appropriate intrepid equivalent for those lines. (if you need help with that part, I'd start another topic)

Hope that made sense...

---

### Post by bendib on 2009-04-19
Ok, here's what you do to install v3 over 2 so this does not happen again...
1. download v3 from firefox.com
2. hit alt F2 and type sudo nautilus /usr/lib and check the run in terminal box.
3. find the firefox-2.0.0.7 or similar folder. Don't touch the fooling folder called firefox.
4. Copy the contents of the main folder inside the tarball you downloaded to that folder, first making a backup. If you have two different versions, back up and fill them both with this data. Be sure not to simply copy the folder inside the tarball, but the contents of this folder. 
5. Use firefox 3! Enjoy!

But be careful, don't rename the folders. Doing so will cripple firefox, unless you rename them back to their original state.

---


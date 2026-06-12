---
title: "Animated Backgrounds - Fedora Style Solution"
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by e30power on 2007-11-14
[http://koji.fedoraproject.org/koji/buildinfo?buildID=24050](http://koji.fedoraproject.org/koji/buildinfo?buildID=24050)

Looking at this entry, it seems that this patch was made:
* Thu Aug 16 2007 Matthias Clasen <mclasen at redhat dot com> - 2.19.90-2
- Port Soerens background patch to the appearance capplet
 
Looking here:
[http://fedoraproject.org/wiki/Interviews/MairinDuffy](http://fedoraproject.org/wiki/Interviews/MairinDuffy)
we can see that fedora allows the backgrounds to change simply by dragging the .xml file into the background applet (in gnome-control-center)

"The animated backgrounds feature, which was written by Søren Sandmann, actually made it into Fedora 7 but we didn't ship any backgrounds that utilized it then. If you're still using Fedora 7 and would like a preview of the feature, you can make your own by creating an XML file using the format documented here ([http://www.redhat.com/archives/fedora-art-list/2007-August/msg00170.html](http://www.redhat.com/archives/fedora-art-list/2007-August/msg00170.html)), writing out the filepaths of the images you'd like to use in the file. Then, you can click and drag the xml file onto the Background Preferences window (as if it was a new image you were adding) to take a look"

All of this to say that we can probably have backgrounds that change according to the time of day if we can port the appearance-capplet from fedora to ubuntu, and that will let us drag and drop .xml files like you can in fedora.

Am I way off base here, or is this really a simple gnome-control-center upgrade that needs to be done from here?
[http://koji.fedoraproject.org/koji/packageinfo?packageID=194](http://koji.fedoraproject.org/koji/packageinfo?packageID=194)

---


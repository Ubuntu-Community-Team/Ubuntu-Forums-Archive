---
title: "MIME types don't seem to be setup properly..."
date: 2014-07-31
forum: Desktop Environments
---

### Post by vuarnet on 2014-07-31
I'm looking for some guidance to a problem that I noticed with a new installation... I downloaded a file in Firefox, and then clicked it from the downloads menu, and nothing happened. I opened my Firefox preferences to look to make sure I had MIME types setup, and sure enough, a lot of them are missing. 

So if I download say ubuntu-server-14.04-amd64.iso.torrent and click on it in FF, I get a "launch application" dialog and I manually selected deluge from /usr/bin/deluge-gtk, but when I continue... nothing happens. The torrent never opens in Deluge. Same happens with video files or text file or apparently any sort of file. Same happens whether I select "Open with" directly or "Save" and *then* open the file by clicking it from the downloads drop-down.

I installed gnome via gnome-core metapackage, not gnome/gnome-desktop or UbuntuGNOME distro. I started with a server ISO and built up from there (because I needed the alt installer). I fear I am missing some package that is responsible for this behavior... but I'm not sure what it is.

Any guidance would be greatly appreciated! Thanks in advance!

EDIT: If I open Nautilus and open the file there, it opens just fine in Deluge or whatever other respective program would be associated with the filetype... so I think it's something up with Firefox specifically...

---

### Post by vuarnet on 2014-07-31
I feel stupid. It was the apparmor profile I set for FF. I set it to complain and tried again and it worked. So I'm just going to go without this functionality. Marking thread as "solved" since I would prefer the extra security over the functionality, and don't want to manually edit the apparmor profile. Thanks

---


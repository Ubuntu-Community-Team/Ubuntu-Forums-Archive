---
title: "RSS'ify your gnome pictures screensaver"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by sseremeth on 2007-10-28
So I spent a ton of time looking for something that would allow me to pull RSS photo feeds onto my desktop for use with my Gnome Screensaver.  I ended up hacking up [bashpodder]("http://lincgeek.org/bashpodder/") to roll my own.  Props to Linc for the original.

The script takes a config file which consists of the URL to the feed you want to subscribe to and the xsl file which pulls out the URLs to the photos themselves from the feed.  Currently RSS feeds/xsl transformations from Gallery, Picasaweb, and Flickr have been tested.  When it runs, it checks the feed against files previously downloaded and only downloads the new stuff.  It could be run from cron or perhaps when you log in.  I suggest running it by hand the first time to make sure it is doing what you expect.

Prerequisite pkg: libwww-perl (I used GET instead of wget - long story)

To install:
```
$tar -xzvf rss_photos.*.tar.gz
```

Edit rss_photos.sh and change the values of CONF_FILE and LOG_FILE to a permanent location.  Create the CONF_FILE you just specified.

#  Lines in CONF_FILE should be of the pipe-delimited format:
#    <URL to RSS feed>|<XSL file to transform the feed and pull out the images>
#    e.g.
# http://api.flickr.com/services/feeds/photos_public.gne?id=YOURIDHERE&lang=en-us&format=atom|parse_flickr_enclosure.xsl

Obviously, you will need to enable the "Pictures Folder" screen saver in Gnome for this to work - the script simply grabs photos for the screen saver.

Any questions, drop me a line or respond to this post.

Be well - 

Steve

P.S.  If you end up using this, please reply to this post so I can know it was a worthwhile endeavor (or if I can do some features/bug fixes to help other folks).

---------------
New rev 12/7/07 - v.011 - changelog:
* adds local paths as potential image sources
* also does pruning (limiting number of matches) on local source paths
* requires jhead for local images (for identifying datestamps in EXIF headers)

Will probably do a total rewrite for next rev.

---

### Post by brucealdridge on 2007-10-31
just tested and setup via cron. 
i like it.
i get the screensaver with the benefit of the downloaded files :)

-bruce

---

### Post by orliville on 2007-11-13
This may be exactly what I've been looking for my DIY digital picture frame.  This seems much simpler than what I've seen so far.  Thanks for your work!

---

### Post by sradhakrishna on 2007-12-03
Guess I've found what I've been looking for some time now. :)

Am gonna try it out on my photo frame. Will update on how it went. 

Thanks much for all the effort!!! =D>

Regards,
Radha.

---

### Post by sradhakrishna on 2007-12-04
Dude! This stuff is ammazing. Got everything I ever wanted into my digital photo frame.

One small request. Was wondering if I could use the same mechanism to pull out photos from a shared folder on a different computer in my home network. Can you please suggest how I could do it?? In other words, how can I generate a RSS feed with the pics in pictures folder on my pc??

Thanks a lot once again for this stuff.

Regards,
Radha.

---

### Post by weblordpepe on 2007-12-04
Well you can mount remote folders by using SSHFS. You could mount a remote folder to a local location on your computer. And tell the screensaver to look there for pictures.

I do a similar thing to get VLC to open videos stored on a remote machine.

---

### Post by sseremeth on 2007-12-04
Hang tight.  I'm going to add a feature or two.  I am thinking:

- add a prune feature that only keeps the number of photos in the mix you specify
- ability to add "local" photos - incl. those mounted in various ways

Will try to do this tonight.

Steve

---------------------------
New tarfile at the top of this thread for grabbing files in local dirs.  If you have stuff on your local network, just mount the shares (using samba, nfs, etc.) and point to local paths.  Warning: if you make it look at a lot of files it will run for a _long_ time the first time as it runs jhead against all local files at least once.  And yes, that means if you want to use local drives, please make sure you have jhead installed.

---

### Post by sseremeth on 2007-12-04
Radha - 

What OS are you running on your other system?  Presumably if it is windows or MacOS, you could use a samba mount for the local feature I'll setup - or NFS if it is a Linux/UNIX box.  If you have questions about any of that, let me know.

Steve

---


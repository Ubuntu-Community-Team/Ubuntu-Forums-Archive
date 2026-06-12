---
title: "Server 10.04 (headless)"
date: 2013-03-22
forum: Desktop Environments
---

### Post by Bevlar on 2013-03-22
Hi,

I currently have a stable server running Subsonic and Transmission Daemon. I use ssh for CLI access.

I am looking for a way to manage the downloaded files. They currently end up in a seeding folder which subsonic monitors and adds to the web interface. This setup means that all media is in one folder and is very disorganized at the Subsonic end.

As my collection grows I will need to add drives for storage and move the data around.

My initial thought is to install a front end and use xrdp to access it as required. This would need to shutdown the xserver upon disconnection to free up the memory it uses.

As the front end is purely for file management (move/rename/delete junk) I am open to suggestions. If anybody has a better solution I'm all ears.

Thanks for reading.

---

### Post by tgalati4 on 2013-03-22
```
apt-cache search content management system
```

Brings up several hits.  Drupal is probably too heavy for what you want.  Perhaps writing a custom Django CMS might work.  You would have to learn another framework.  gnump3d is a perl-based webserver that handles audio files, but could be extended for video files.  It gets slow after 10,000 tracks since it uses a flat-file index that has to be scanned when searching.  Rhythmbox on a headless server and run the cli clients or remotely run the graphical frontend.  This means installing xorg on the server so you can serve up the graphcial pages remotely.  Rhythmbox has a DAAP plug-in so other DAAP clients and see the indexed file shares.

---


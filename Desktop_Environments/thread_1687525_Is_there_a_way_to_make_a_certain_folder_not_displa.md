---
title: "Is there a way to make a certain folder not display thumbnails?"
date: 2011-02-14
forum: Desktop Environments
---

### Post by x300 on 2011-02-14
I have a WebDAV server at home with at folder that I want to mount on my Ubuntu computer at work over the Internet. Everything works fine if I just use dav://user@server:port in Nautilus so I tried adding it to fstab (using davfs2) and managed to get it to mount fine.

The problem is that when mounted using fstab Nautilus thinks that it is a lokal folder and downloads images and movies to create thumbnails/previews, something that it doesn't do when just using dav://. This uses a lot of bandwith everytime I'm trying to access a folder with any media. I'm wondering if there is any way to exclude my entire /media/nas folder from showing thumbnails?

---

### Post by x300 on 2011-02-16
Come on, someone's got to know if it is possible or not?

---

### Post by Krytarik on 2011-02-16
I subscribed to your thread after your first post, actually hoping that someone comes up with a solution.

But imo it's not possible (currently) to make a file browser handle folders individually. But you could of course use another file browser to access your remote location, e.g. Thunar.

---


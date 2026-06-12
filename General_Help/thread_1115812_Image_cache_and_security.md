---
title: "Image cache and security"
date: 2009-04-04
forum: General Help
---

### Post by cavedog on 2009-04-04
I'm moving towards a paperless file system for my bills and such, scanning them as I get them for reference and then shredding the paper copy.  I have been trying out several image viewers: GQView, gThumb, Ristretto and Mirage in addition to the standard viewer in Gnome (Ubuntu 8.04 LTS).  I've set up a TrueCrypt container to hold these pdf and jpg files, but I'm concerned that there may be thumbnails or some sort of copy, or some record of the files saved somewhere on the hard drive.  These images and pdf's have very sensitive information on them, and I want to be knowledgeable about the risks with this paperless concept.

What image program provides the best security for this, (no stored filenames/paths/thumbnails/etc). 

What steps do I need to take, if any, to implement a secure environment?

---

### Post by cariboo on 2009-04-04
Thumbnails are stored in ~/.thumbnails in your home directory, check to see if the images are showing up there.

Jim

---

### Post by cavedog on 2009-04-04
> **cariboo907 said:**
> Thumbnails are stored in ~/.thumbnails in your home directory, check to see if the images are showing up there.

Jim


Is there a way to not generate thumbnails so I don't have these spread all over the system.  I found a couple of other places where thumbnails get generated.  A couple of the programs I mentioned in my original post put thumbnails where you indicated, and in other places.

---


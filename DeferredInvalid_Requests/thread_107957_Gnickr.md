---
title: "Gnickr"
date: 2005-12-24
forum: Deferred/Invalid Requests
---

### Post by dexae on 2005-12-24
[FONT=Arial][SIZE=2][ Gnickr]("http://gnickr.sourceforge.net") allows you to manage photos on your Flickr site as if they were local files on your Gnome desktop.
 
Supported operations
    * Uploading
    * Renaming photos and photo sets
    * Deleting photos
    * Arranging photos in photo sets
    * Efficient uploading (scales photos to 1024*768)

Planned
    * Creation/deletion of photosets
    * Toggling privacy options on photos
    * Rotating photos
    * Editing photo descriptions
    * Integrate authorization process in to Nautilus


 
**Requirements**
This application requires GTK+ version 2.2.x.  Other dependencies include:
 gnome-python >= 2.12.13 (Or patched ersion from Gnickr's site) gnome imaging library (PIL) [/SIZE][/FONT]

---

### Post by jdong on 2006-01-02
Does not comply with Backports policy.

---

### Post by brainkilla on 2006-01-05
No need to backport anything - there's a breezy package on gnickr download page, and also an updated python-gnome2 package which gnickr requires. Works great...

---

### Post by Tripmonkey_uk on 2006-01-18
Tried this out with the patched version of gnome-python & it seems to work very well.

Couple of things to watch out for though..
Spelling mistake on the installer screen (cat instead of can lol).
Had to run the authorization program twice. The first time it authorized in the web browser but the program wouldn't complete & end for some reason. Could have been me trying to rush?
Instead of just restarting Nautilus with pkill nautilus, u might have to restart the computer fully. Wouldn't work for me until I did.
Crashed out (& re-started) Nautilus when I tried to download a single photo from the site. Not sure if the programs supposed to download anyway or if it's planned for in the future as it doesn't state so on the site, but it **did** get the picture onto my desktop.
Won't display a couple of jpegs that I have on the site. It turned out that these weren't photo's but saved pictures that I put together on a Windows system with the Gimp (I think it was the Gimp I used?).
There's no creation/deletion of photosets yet but this has been planned for & is stated on the homepage. U can always upload the photo's to the default Unsorted folder anyway though.

There are some good things as well..
If u save the main page as a bookmark in Nautilus, it then allows u 1 click access to your Flickr photo's from the Gnome taskbar in Places/flickr (bookmark can be edited & the flickr name changed to whatever u want).
Everything went fine when I uploaded 29 new photo's. Simple drag & drop worked pretty fast & with no problems.

Impressed enough to look forward to the next version anyway :D

---

### Post by vladdythephotogeek on 2006-06-22
Greetings everyone!
I need some help getting this thing to work. I'm also quite the N
I'm trying to run gnickr with gnome 2.14 and it's not at all working. I have made sure that the other dependencies are met and they are. (at least I believe).

I type in "flickr:///" into the location bar on nautilus and it takes me to my home folder and/or crashes. So: I'm thinking I either have something not installed that I should or, it isn't working with a more advanced release 2.14 of gnome or gnome2-python2.1.4 intead of x.x.3.

Can anyone help?

Warmest Regards,
Paul

---


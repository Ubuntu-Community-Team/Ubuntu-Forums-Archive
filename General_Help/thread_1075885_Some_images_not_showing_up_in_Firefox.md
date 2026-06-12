---
title: "Some images not showing up in Firefox"
date: 2009-02-20
forum: General Help
---

### Post by blueshiftoverwatch on 2009-02-20
I've noticed for awhile now that when I go onto some websites such as Flickr many of the images on certain Flickr pages don't show up. But others do.

I'll use the EFF's Flickr page as an example:
[http://flickr.com/photos/hughelectronic/](http://flickr.com/photos/hughelectronic/)

I go onto there and the only image I see is the page logo at the top. With the black silhouette cartoon guy and the yellow background. 

As far as the images all I see is the image caption in bolded text and some of the stuff underneath the space where the image is supposed to be such as it's copyright status and date of upload.

But oddly enough I've only encountered this problem on the Linux version of Firefox. It works fine on the Windows XP and Mac OSX versions of Firefox. And even in the Galeon web browser under Ubuntu.

If I go to the Flickr page of one of the images from that page posted above the image doesn't show up at all:
[http://flickr.com/photos/hughelectronic/3201566757/](http://flickr.com/photos/hughelectronic/3201566757/)

But when I got a friend to send me the example image's actual location it shows up:
[http://farm4.static.flickr.com/3101/3201566757_559ec13fde_m.jpg](http://farm4.static.flickr.com/3101/3201566757_559ec13fde_m.jpg)

Has anyone else encountered this problem or know what is happening and how to fix it?

---

### Post by dcstar on 2009-02-20
> **blueshiftoverwatch said:**
> I've noticed for awhile now that when I go onto some websites such as Flickr many of the images on certain Flickr pages don't show up. But others do.

I'll use the EFF's Flickr page as an example:
[http://flickr.com/photos/hughelectronic/](http://flickr.com/photos/hughelectronic/)
.......
Has anyone else encountered this problem or know what is happening and how to fix it?

Works fine on my FF, do you have any page blocker add-ons etc installed?

---

### Post by blueshiftoverwatch on 2009-02-20
> **dcstar said:**
> Works fine on my FF, do you have any page blocker add-ons etc installed?
I use NoScript, but I enabled all JavaScript for Flickr and that didn't accomplish anything. Other than that I have eight other extensions installed but none of them have to do with blocking ads or anything of the like.

---

### Post by blueshiftoverwatch on 2009-03-01
I found the solution. I must have accidentally right clicked on an image from Flickr and hit "block images from example.com" accidentally in the content menu. But it's easy to undo:

Just go to the "Edit" button in Firefox's menubar, than "Preferences", than select "Content" from the tabbed interface. Make sure that a checkbox titled "Load images automatically" is checked. Than click on the "Exceptions" button to the right of load images automatically and make sure that the site that list images you don't want blocked isn't on the list. If it is than just remove it.

---


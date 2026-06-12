---
title: "[SOLVED] Digikam flickr export problem"
date: 2007-06-24
forum: Desktop Environments
---

### Post by velvetGreen on 2007-06-24
Hi,

When I try to upload a photo to flickr I get the following error pop-up: 

Error Occured: Invalid signature
We can not proceed further.

Am I the only one with this or what's going on? I am running kubuntu feisty 7.04 with Digikam version: 2:0.9.2-1~ach0feisty1 and Kipi plugins: 0.1.3-5~ach0feisty1

---

### Post by velvetGreen on 2007-06-30
I noticed today that digikam and kipi-plugins had been updated so I also upgraded them to their newest versions. 

However, when trying to export images to flickr, after authorization (which I have to do every time) I still get the same error popup after failed to upload a photo:

Error Occured: Invalid signature
We can not proceed further

Kipi-plugins are now version 0.1.5 and Digikam 0.9.2 (newest as of writing this).

One strange thing though: when granting authorization for kipi-plugins flickr export, flickr announces:

You have successfully authorized the application FlickrUploadr.

I find this odd as I don't have that installed and am fairly sure that's just an API or something.

---

### Post by velvetGreen on 2007-07-06
I've been wrestling with this annoyance for over a week and just finished reading kde-imaging mailing lists: no mention of Invalid Signature bug.

On accessing the plugin for the first time the user is taken through the process of obtaining a token. Which is used for authentication purposes.

I know this has to do something with the authentication process as for some reason, flickr export plugin wants to confirm my authentication every freaking time at flickr site when try to export photos. That is, I always get this popup ([http://www.kipi-plugins.org/drupalimages/plugins/flickrexport-signup.png](http://www.kipi-plugins.org/drupalimages/plugins/flickrexport-signup.png)) and never this, as I should after the authentication has succeeded: ([http://www.kipi-plugins.org/drupalimages/plugins/flickrexport-continue.png](http://www.kipi-plugins.org/drupalimages/plugins/flickrexport-continue.png))

Flickr page do say I have given write permissions to FlickrUploadr but digikam can't seem to realize that.

And here's something more: I have some older pictures back from the year 2003 that are altered for web usage and contain no EXIF data. I tried to upload these and behold: no problems what so ever. But when I clean EXIF data from pics taken with my Nikon D70 and even save them for we usage, I just can't upload them and get that Invalid Signature error?!

I have tried to change the default browser to see if it interferes with authentication somehow. Permissions are also checked.

Here's an example picture straight from my camera I can't upload: [http://koti.mbnet.fi/fork/kuvat/dsc_1066.jpg](http://koti.mbnet.fi/fork/kuvat/dsc_1066.jpg) (1,5 mb)
And here's that one web image I can upload just fine: [http://koti.mbnet.fi/fork/kuvat/otto_009.jpg](http://koti.mbnet.fi/fork/kuvat/otto_009.jpg) (24 kb)  

So I just can't figure out what's wrong with the authentication... official docs ([http://www.kipi-plugins.org/drupal/?q=node/13](http://www.kipi-plugins.org/drupal/?q=node/13)), google and kde-imaging doesn't know anything.

---

### Post by velvetGreen on 2007-08-05
I think I solved this, the upload now works. Problem was that in my camera (Nikon D70) has a setting that enables to store comments as exif data. I have set it to read (c) [www.address.com/here](www.address.com/here)

It seems to be that digikam's tagging system (or flickr upload plugin) doesn't like comment tags that contain a () / or .

Strange thing is that when removed the exif comment using digikam's tools, that didn't make a difference, but I had to clean the field using exiv2 command.

Thanks for all your help guys!

---


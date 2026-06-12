---
title: "Images for some sites don't appear in firefox (Solved)"
date: 2005-11-10
forum: Desktop Environments
---

### Post by the~jester on 2005-11-10
Not sure if i am in the right section or not. This is a new install of Ubuntu on a Sony Vaio VGN-FS570

I noticed some issues the other night with firefox and images. Images from sites don't appear in firefox, If I got a site like [www.ilovebacon.com](www.ilovebacon.com) I can see the images of the website but if I go to another site, [www.dumbassdaily.com](www.dumbassdaily.com) I do not see any images at all on the site.  Also when making a purchase on Amazon I did not have a button to continue to the next page after enter some information to confirm the purchase. Anyone have any ideas?

thx
jester

---

### Post by Kapre on 2005-11-10
[QUOTE=the~jester]Not sure if i am in the right section or not. This is a new install of Ubuntu on a Sony Vaio VGN-FS570

I noticed some issues the other night with firefox and images. Images from sites don't appear in firefox, If I got a site like [www.ilovebacon.com](www.ilovebacon.com) I can see the images of the website but if I go to another site, [www.dumbassdaily.com](www.dumbassdaily.com) I do not see any images at all on the site.  Also when making a purchase on Amazon I did not have a button to continue to the next page after enter some information to confirm the purchase. Anyone have any ideas?

thx
jester[/QUOTE]

jester - I just checked the website you've listed and both appeared fine (images loaded). Maybe you need to also load the User Agent Switcher. This is an extension in Firefox that you can download. This will enable you to view pages made for IE or Netscape.

K

---

### Post by aysiu on 2005-11-10
[QUOTE=the~jester]Nbut if I go to another site, [www.dumbassdaily.com](www.dumbassdaily.com) I do not see any images at all on the site.[/QUOTE] Works fine for my Firefox. I didn't use User Agent Switcher, either.

Maybe your profile's corrupt. Try renaming /home/thejester/.mozilla to /home/thejester/.mozilla_backup.
Note: **rename** does not mean copy. It means **rename**. Then reopen Firefox.

---

### Post by the~jester on 2005-11-10
I tried moving the mozilla profile, and still the same behavior happens. If I right click on the location where an image is and select view image, then I am able to download the image in a new window and see it. 

I would attach some screenshots but apperanlty I am not able to access that function either. I will try and upload them from another pc

******
From a windoze box using firefox 1.0.6 I was able to upload the images also I didn't have a button for manage attachments on the ubuntu laptop.

---

### Post by the~jester on 2005-11-10
Well that seem to do the trick. I did as you said and moved the profile to another file and restarted the browser and the same issue was happening... I contiuned to browse sites, when clicking on a like shutdown the browser I was working in as well as browsers in other workspaces.. I started it backup, the default start page appeared. I immediately went to dumbass daily and taadaa, images were appearing.. Thanks for the help

jester

---


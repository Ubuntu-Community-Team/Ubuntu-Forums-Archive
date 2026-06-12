---
title: "No previews in nautilus - how to solve it?"
date: 2010-03-14
forum: Desktop Environments
---

### Post by keforex on 2010-03-14
In Nautilus->Edit->Preferences->Preview everything is set to Always and the size for previews is set to any files under 100Mb of size.

Still I can't see any previews. I am trying to look at the icons inside \usr\share\icons but all I get is a little icon that looks like piece of paper with an analog clock on it.

I gotta see the images without having to open image viewer every time.

How?

---

### Post by keforex on 2010-03-14
I found the solution:

Change the permissions on the \.thumbnails folder from root to user and all thumbnail previews are back.

---

### Post by loneowais on 2010-05-10
Same problem here... But it happens only when I select the Preview Other type of files...

Permissions are fine... the problem persists.

---

### Post by hariks0 on 2010-05-10
You can use Ubuntu Tweak to clear all the thumbnail cache, which may solve your problem.

---


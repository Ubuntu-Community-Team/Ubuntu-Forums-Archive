---
title: "Video file thumbnails in Lubuntu"
date: 2012-06-08
forum: Desktop Environments
---

### Post by Gannin on 2012-06-08
I installed Lubuntu and noticed there were no video file thumbnails in the file manager, pcmanfm.  I did some poking around and it looked like some people were saying because of some changes in Gnome 3, pcmanfm wasn't able to create video thumbnails anymore.

So, I installed nautalis, using it with the --no-desktop option, but it also wouldn't give me any video thumbnails.  Is there some way I can get video thumbnails within Lubuntu with either pcmanfm or nautalis?  Thanks.

---

### Post by MG&amp;TL on 2012-06-08
> **Gannin said:**
> I installed Lubuntu and noticed there were no video file thumbnails in the file manager, pcmanfm.  I did some poking around and it looked like some people were saying because of some changes in Gnome 3, pcmanfm wasn't able to create video thumbnails anymore.

So, I installed nautalis, using it with the --no-desktop option, but it also wouldn't give me any video thumbnails.  Is there some way I can get video thumbnails within Lubuntu with either pcmanfm or nautalis?  Thanks.

I think it's a bug, rather than a change, as it should be possible in Gnome 3.

However, both PCManFM and Nautilus have a Gnome3 backend, so I'm afraid you're out of luck. What version are you using of Lubuntu?

---

### Post by Gannin on 2012-06-08
I'm using Lubuntu 12.04.  I know that in Ubuntu 12.04 with Unity, video thumbnails work, but I prefer the interface of Lubuntu.  Is there some package that can be installed to get this working?  Or are video thumbnails in general just not going to work in Lubuntu?

---

### Post by Rex Bouwense on 2012-06-08
This is interesting.  Some of my thumbnails work and some do not and I am using Lubuntu 12.04.  I'm not sure what is going on.

---

### Post by Gannin on 2012-06-08
I should add that not even my good old .ogv / .ogg video thumbnails are working, when they should really be the first to work.

---

### Post by Rex Bouwense on 2012-06-21
Just thought of something and perhaps it may be answer to your question.  Go to PCManFM->Preferences->Display.  Adjust the Do not generate thumbnails exceeding size to whatever you want it to be.  I had to play with that a while back to get thumbnails to generate.

---

### Post by Gannin on 2012-06-21
I actually did try that before making my original post and it didn't do anything for me.  I appreciate the suggestion though.

---

### Post by Rex Bouwense on 2012-06-21
Sorry.  When I remembered that, I changed it upwards and all of my thumbnails are now visable.  I did have to adjust it about 5 Mbs (5500 Kbs exactly) to view some of the thumbnails of the larger pictures.

I just realized that you are talking about videos and I'm giving you answers for pictures.  Probably not the same.

---

### Post by Gannin on 2012-06-21
I think I set it to about a gig or so just to be safe, but no results.

I think what I'll probably do is instead of going with Lubuntu, I'll just go with regular Ubuntu, considering it's still good to be familiar with Unity because that's what the majority of people are using, and then I'll install OpenBox along side it and maybe use the XFCE panel and Thunar along with that.

---

### Post by Rex Bouwense on 2012-06-21
Hate to lose you, but a man's got to do what a man's got to do:popcorn:

---

### Post by Lyfang on 2012-11-02
Hi, try to install ffmpegthumbnailer and follow the instructions here: [Thumbnails for video files missing]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1064089")

---


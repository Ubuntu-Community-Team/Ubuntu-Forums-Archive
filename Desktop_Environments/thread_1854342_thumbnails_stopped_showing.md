---
title: "thumbnails stopped showing"
date: 2011-10-04
forum: Desktop Environments
---

### Post by gogolink on 2011-10-04
A couple of days ago all of a sudden (as far as I can tell) my picture- and video-files do no longer show as pictures either on my desktop, or in Nautilus' "Icon View."  All I see are the generic thumbnails for the respective file types -- which really affects my ability to quickly browse the contents of a picture folder.

I'm on 10.10.  I'm not aware of any changes I made that might have caused this.

Any ideas?

---

### Post by ~!geek!~ on 2011-10-04
> **gogolink said:**
> A couple of days ago all of a sudden (as far as I can tell) my picture- and video-files do no longer show as pictures either on my desktop, or in Nautilus' &quot;Icon View.&quot;  All I see are the generic thumbnails for the respective file types -- which really affects my ability to quickly browse the contents of a picture folder.

I'm on 10.10.  I'm not aware of any changes I made that might have caused this.

Any ideas?

 Did you try preference settings in nautilus!! Edit->Preferences->Preview 
Change the configurations, if they are not set as you want!

---

### Post by gogolink on 2011-10-04
Thank you, that was it.  I feel a bit embarrassed now: I *had* actually changed the preference settings to 'Preview: Show Thumbnails - Never' in order to speed up Nautilus; had forgotten about it.  Now that I reversed that, the thumbnails show again.

---

### Post by Krytarik on 2011-10-04
> **gogolink said:**
> I *had* actually changed the preference settings to 'Preview: Show Thumbnails - Never' in order to speed up Nautilus; had forgotten about it.
You could try Thunar, or even PCManFM, both are way faster than Nautilus in generating/showing image thumbnails, and therefore don't *lock up* the browser window during that process. Both are in the official repos, see for yourself which fits your personal needs/taste better. :P

Greetings.

---

### Post by gogolink on 2011-10-04
Thanks, Krytarik, for your suggestions; I installed Thunar and quite like it -- though I will not immediately use it as my primary file manager, as I use Dropbox and it seems a bit complicated to get the icon overlays and context menu entries integrated into Thunar.  (I found this post: [http://softwarebakery.com/maato/thunar-dropbox.html]("http://softwarebakery.com/maato/thunar-dropbox.html"), but I'm not used to building from tar balls.)

I used PCManFM in the past, but missed some functionality and don't love its looks.

---

### Post by Krytarik on 2011-10-04
> **gogolink said:**
> I used PCManFM in the past, but missed some functionality and don't love its looks.
Yeah, me neither, at least reg. the looks part :P , but upon comparing the features earlier when I did my previous post, I didn't notice too much of a difference. Moreover, PCManFM has at least a search feature included, which is missing completely in Thunar, not even the most basic one, like in Nautilus; was really stunned when I noticed that a while back when I first tried Thunar. But yes, I still prefer Thunar over PCManFM, too. However, I, too, don't use it as my main file browser, but at least when I'm going for the "/usr/share/icons" directory. ;-)

---

### Post by Rgibbons on 2011-12-01
I had the same problem with missing thumbnails for my folders and files. Switching to 2D solved my issue.

---


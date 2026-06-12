---
title: "Icon View in File Select Dialogue Box"
date: 2011-04-23
forum: Desktop Environments
---

### Post by wgilthorpe on 2011-04-23
Is there any way to make the file selector dialogue box in Ubuntu show icons instead of a list or detail view?  I have been trying to convince people to use Ubuntu instead of windows, but this seems to be a deal breaker for most of them.  When uploading pictures to the web or facebook it is very difficult to navigate pictues in the file browser window with the little bitty thumbnails beside the file name.  If there is no way to do this how would I recommend this idea for Ubuntu and to whom would I submit it?  Any info would be greatly appreciated.

---

### Post by mig1964 on 2011-08-24
Funny that something so minor can be so important but I'm having the exact same problem with my wife, who is asking for me to put Windows back on her machine simply for want of thumbnails in the file selection dialog.  Yes, for uploading photos to Facebook.

---

### Post by cbstryker on 2011-08-30
Ok, this is awesome. I almost started a new thread about this exact same thing. My wife was trying to upload images to her blog yesterday and the exact same issue came up and in her frustration remarked "it's because of your stupid linux"! After a brief moment contemplating divorce (just kidding) I admitted I didn't know how to display thumbnails in the file select window.

For myself I've always found it annoying but it never took me more than 2 seconds to fire up a Nautilus session to match up the thumbnails to the filenames I wanted. 

However, there MUST be a way to do this. Perhaps a completely different file manager is needed?

---

### Post by mcduck on 2011-08-30
> **cbstryker said:**
> Ok, this is awesome. I almost started a new thread about this exact same thing. My wife was trying to upload images to her blog yesterday and the exact same issue came up and in her frustration remarked "it's because of your stupid linux"! After a brief moment contemplating divorce (just kidding) I admitted I didn't know how to display thumbnails in the file select window.

For myself I've always found it annoying but it never took me more than 2 seconds to fire up a Nautilus session to match up the thumbnails to the filenames I wanted. 

However, there MUST be a way to do this. Perhaps a completely different file manager is needed?

It's not a exactly question of file manager, even while the file selection dialog might look like it would be related to Nautilus it's not part of the file manager but instead a feature of the toolkit, GTK2. So to change that you'd need to use programs that are based on different toolkit that has a different file selection dialog.

As an interesting note, the GTK2's file selection dialog *does* support showing a preview for images, but the program that initiates the dialogs must ask for the preview. Firefox doesn't, as you often need to select other files than images and preview only makes sense for image files. 

Anyway, to get a different file selection dialog you'd have to use some web browser that uses some other toolkit than GTK2. Opera comes to mind... (of course there are many ways to handle the file selections easily without having to rely on icons/preview in the file selection dialog, but making people change their ways is often quite hopeless...)

---

### Post by cbstryker on 2011-08-30
> **mcduck said:**
> It's not a exactly question of file manager, even while the file selection dialog might look like it would be related to Nautilus it's not part of the file manager but instead a feature of the toolkit, GTK2. So to change that you'd need to use programs that are based on different toolkit that has a different file selection dialog.

As an interesting note, the GTK2's file selection dialog *does* support showing a preview for images, but the program that initiates the dialogs must ask for the preview. Firefox doesn't, as you often need to select other files than images and preview only makes sense for image files. 

Anyway, to get a different file selection dialog you'd have to use some web browser that uses some other toolkit than GTK2. Opera comes to mind... (of course there are many ways to handle the file selections easily without having to rely on icons/preview in the file selection dialog, but making people change their ways is often quite hopeless...)

Ya I learned just now that it's not the file manager than handles it. Incidently in my search I've come across some other discussions on other threads that discuss the exact same issue. The best solution seems to involve using a wrapper to handle the file preview request. The original posters explain it much better, so I'll post the links:

[http://forums.debian.net/viewtopic.php?f=10&t=68588](http://forums.debian.net/viewtopic.php?f=10&t=68588)[http://forums.debian.net/viewtopic.php?f=10&t=68588]("http://forums.debian.net/viewtopic.php?f=10&t=68588")

[http://forums.linuxmint.com/viewtopic.php?f=55&t=2248](http://forums.linuxmint.com/viewtopic.php?f=55&t=2248)[http://forums.linuxmint.com/viewtopic.php?f=55&t=2248]("http://forums.linuxmint.com/viewtopic.php?f=55&t=2248")

---


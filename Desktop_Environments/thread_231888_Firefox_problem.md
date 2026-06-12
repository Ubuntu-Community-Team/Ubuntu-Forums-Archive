---
title: "Firefox problem"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Megatog615 on 2006-08-07
Now, for some reason, when I try to view flash movies with Firefox, it will play for about 3 seconds, then stop. Then, if I click any link on the page, or anything in the browser, it freezes, and I have to kill the process in order to close it.

---

### Post by simonn on 2006-08-07
start firefox from the command line 

```

$ firefox

```

And view some flash movies. Do any error messages appear?

---

### Post by Megatog615 on 2006-08-08
Nope. Everything in flash movies works except for the play feature. If I view a YouTube video, it plays for 3 seconds, and then stops playing. I can then move the progress bar/etc.
It freezes when I click on anything clickable in the browser, only after the video has stopped.

---

### Post by Pionner on 2006-08-08
Same here. Deleting the ~/.firefox directory fix the problem. Maybe some extension is causing the problem?

---

### Post by Megatog615 on 2006-08-08
Didn't solve it for me.

---

### Post by simonn on 2006-08-08
How did you install flash?

---

### Post by Megatog615 on 2006-08-09
I don't remember, was a long time ago. I believe I did it through the official installer. It has worked fine up until a few days ago.

---

### Post by Megatog615 on 2006-08-10
For example, if I were to play a youtube movie, it only plays for 3 seconds, then mysteriously stops playing, and all other elements of the flash continue. I can move the seek bar/etc, but if I do anything outside the flash video, it locks up Firefox.

---

### Post by simonn on 2006-08-10
Personnaly, I would remove the version of flash you have installed and install flashplugin-nonfree using synaptic.

---

### Post by shawnrgr on 2006-08-10
also you might want to give swiftfox a try. it fixed ALOT of issues i had with firefox.

---

### Post by Megatog615 on 2006-08-10
I'm not sure how to remove flash, but I removed libflashblahblah.so and flashplayer.so from /usr/lib/firefox/plugins/.

I then installed flashplugin-nonfree, and still have the same problem.

---


---
title: "mouse pointer size"
date: 2019-01-16
forum: Desktop Environments
---

### Post by jgw on 2019-01-16
I am having a mouse size problem.  I cannot change the size of my mouse in ubuntu.  It just doesn't work.  

Then I noticed that when I am in either firefox OR chrome, and the pointer is on either's pages,  my mouse goes from redglass to black and shrinks to about 40% of my normal mouse (teeny).  Before is found out it does it in chrome I thought that it was a firefox problem but they have no idea.  Since the problem is in both programs I tend to believe this might be an ubuntu problem.  I also suspect that it may have something to do with the fact that I am running with a 3840x2150 resolution (using a k4 tv for a monitor).  

Any thoughts would be appreciated - thank you..............

---

### Post by Dennis N on 2019-01-16
_Suggestions:_
First, change default cursor to redglass with command:
**sudo update-alternatives --config x-cursor-theme**
(redglass should also be selected in Tweaks > Appearance > Cursor)
redglass is resizable. Set the size in Settings > Universal Access > Cursor Size
If it continues to change between sizes, there is another thing to try:
Add this line to the file **~/.Xresources** to set cursor size (if this file doesn't exist, create it).
**Xcursor.size: 48**
redglass size can be any of 12, 16, 24, 32, or 48

---

### Post by jgw on 2019-01-16
Thank you for the reply!

I did the sudo update-alternatives............  and, now, I can change my mouse pointer size!  I also tried the .Xresources to see if it had anything to do with the pointer in Firefox or Chrome but no cigar there (mouse pointer still goes down in size and changes color to black).    I should add that I had the setting the size in settings thing on a couple of machines and the one I am using, right now, has a resolution of 1920x1080 and it works here and suspect it will on the tv one too.

I will eventually reboot and then, perhaps? Still, progress!!!!!

Thanks again!

---

### Post by Dennis N on 2019-01-16
You would at least need to log out and log back in to be sure these changes take effect. Reboot would work too, of course.

---

### Post by jgw on 2019-01-19
I went to the firefox forum and asked the same question (teeny mouse pointer in firefox).  The answer, from another user, was that he thought it was a bug and its been reported.  I didn't check to make sure but I think he was right.  I will mark this one as solved as I can, now, change my mouse size outside of the browser and I will just have to wait I guess.  I have set my mouse to show me where it is (with the control key as per tweak) which helps.

Thanks again for the help!!!

---

### Post by Dennis N on 2019-01-19
Cursor theme changing back to default theme (DMZ-Black) outside the browser window usually means your default cursor theme is not set to the cursor you select in Tweaks. Please post output of:

```
update-alternatives --query x-cursor-theme
```

Normally, this isn't necessary in newer Ubuntu versions. The cursor theme from Tweaks and (optional) size from Universal Access are enough to get it set.

---


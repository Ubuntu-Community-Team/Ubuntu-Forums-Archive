---
title: "A strange problem with jpeg images"
date: 2009-02-13
forum: Desktop Environments
---

### Post by Mman_ on 2009-02-13
Ok, here's a strange one.

I have all my jpeg photos in subfolders under /media/Storage/Graphics/Pictures/

I also have symlink "Pictures" in my home dir linking to the Pictures 
directory on Storage disk (Pictures -> /media/Storage/Graphics/Pictures)

Now when I open nautilus and browse to the /media/Storage/Graphics/Pictures/[subdir]/ most of the .jpg images show thumbnails, but some don't. Those which do not show the thumb have an icon with lots of zeros and ones.

When I browse to /home/[myuser]/Pictures not a single .jpg image thumbnail is visible. Only zeros-and-ones icons.

All the other image formats show thumbnails normally.

So I'd like to get my thumbs back and working.
All the help appreciated.

Thanks in advance =)

---

### Post by SteveDee on 2009-02-13
While I can't reproduce exactly what you have, I hope this may help.

I have a load of jpeg files of various sizes in a directory. I create a link to that directory. In "icon view" all of these .jpg files show thumbnails whether accessed direct or via the link.

Now in Nautilus I go to Edit > Preferences > Preview > Other Previewable Files and set "Local Files Only" and "100k". When I view the directory direct I still see thumbnails for all files (not sure why), but via the link I only see thumbnails for small files, and see icons to the larger files.

Although my file icons don't show 0s and 1s, I think that may just depend upon desktop settings/themes.

Suggest you play around with some of these settings.

---

### Post by Mman_ on 2009-02-13
Thanks for the tip.

However it did not help. I had my size limits at 10Mb. Tried to play with the values though.

What I found out was that when I browse nautilus through any symlink in my system, jpegs "inside" the symlink fail to display thumbnails.

Other thing that might be related to this: When I open some jpeg "inside" a symlink in the image viewer (eog), eog fails to "see" any other jpeg images in that directory. Eog then disables the arrow buttons used to move to the next and previous images inside the same dir. The same happens when I run eog from shell.

---

### Post by SteveDee on 2009-02-13
From what you said I wondered if Permissions for the symlink were somehow more restricted than those on the real directory. But when I try to 'close down' Permissions for the symlink, the real directory Permissions also change in step.

...Oh well, good luck with this one!

---

### Post by Mman_ on 2009-02-18
I'm still having this problem. If anyone has ANY ideas, please share them.

I have tried to reinstall all the packages that I found from synaptic by searching for mime and jpg/jpeg, but it did not help.

I also found out that if I rename a .jpg file to .jpeg nautilus generates the thumbnail. When I rename the file back to .jpg the thumb stays. So in theory I could get all the .jpg thumbs visible by renaming them twice but I don't really like the idea, as it doesn't solve the real problem.

---

### Post by Mman_ on 2009-02-26
I'm not certain what exactly caused my problem, but I managed to track it to the /home/user/.gconf/apps/nautilus/preferences/%gconf.xml -file.

I didn't bother to start tracking which setting was responsible for this so I simply removed the file and the problem went away =)

---


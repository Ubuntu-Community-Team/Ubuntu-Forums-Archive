---
title: "Installed Blender 3d 2.42a --&gt; No icons!"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Senesence on 2006-07-28
I downloaded and extracted the "Linux i386 2.3.2, dynamic, FFMPEG, Python 2.4 (10.0 MB)" package from the main blender download page here: [http://www.blender.org/cms/Blender.31.0.html](http://www.blender.org/cms/Blender.31.0.html)

What happened was: the package got extracted to the desktop as a folder, and in that folder there was the binary executable which worked like a charm.

But there was no Blender icon for the executable, and also I had no idea where to put the folder so that I could have Blender 3d show up in the applications section.

I would have done this through synaptic, which I think would have put everything in the right place icons and all, but searching through synaptic only showed a 2.41 version of blender, so I had to go manually for the latest 2.42.

Is there a way to install the latest version of blender just as it would be installed through synaptic with all the bells and whistles?

---

### Post by MrSmith on 2006-07-28
You should find a Blender icon here:
/usr/share/icons/gnome/16x16/mimetypes/

It will be called:
gnome-mime-application-x-blender.png

This is what I use for Blender 2.42

Hope this helps,
MrSmith

---

### Post by Senesence on 2006-07-28
Ughh, that is one ugly icon. Are there any more?

Something along the lines of the one for windows.

How can I find all blender icons available on my system. Just typing blender in search doesn't bring out any icons.

---

### Post by MrSmith on 2006-07-28
You might check out this tutorial and create an icon you like.

[http://www.gimp.org/tutorials/Creating_Icons/](http://www.gimp.org/tutorials/Creating_Icons/)

I think all the Blender icons available look about the same, just different sizes.

MrSmith

---

### Post by Senesence on 2006-07-29
I see what you mean. I used the "locate blender" command in terminal and as you said all the blender icons are the same.

I'm just looking for the default icon like on windows, but it's not in there.

If I installed blender through synaptic all of those default icons would probably be present.

How come the latest version of blender is unavailable through synaptic? All they have is the previous version 2.41, but blender 2.42 has been out for some time now. How slow is the update cycle on synaptic?

---

### Post by xenon2000 on 2006-08-03
> **Senesence said:**
> 
How come the latest version of blender is unavailable through synaptic? All they have is the previous version 2.41, but blender 2.42 has been out for some time now. How slow is the update cycle on synaptic?

Must be very slow to get things into the repositories because Bluefish editor had a big bug fix update version 1.0.5 in Feb 2006 and Ubuntu 6.06 repositories still only have 1.0.4

I really wish there was a repository with up to date packages. Such as the latest stable Apache, PHP, MySQL, Blender, SSH, web dev, etc....

---

### Post by paris_m_ on 2006-08-31
Try to read this thread: [http://www.blender3d.org/forum/viewtopic.php?t=9285]("http://www.blender3d.org/forum/viewtopic.php?t=9285")

Someone has created a 2.42a deb package for dapper

---

### Post by xenon2000 on 2006-08-31
> **paris_m_ said:**
> Try to read this thread: [http://www.blender3d.org/forum/viewtopic.php?t=9285]("http://www.blender3d.org/forum/viewtopic.php?t=9285")

Someone has created a 2.42a deb package for dapper

Note to those interested in the 2.42a deb package in that thread. It's not just a simple download 1 .deb and install. It depends on many dev packages that you will also have to download as well as others not in his folder for download.

But if you follow the entire thread, it will work for you. It did for me. But I am still hoping that a 2.42a version becomes available in a repository.

---


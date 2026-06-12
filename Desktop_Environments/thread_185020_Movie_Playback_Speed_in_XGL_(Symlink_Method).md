---
title: "Movie Playback Speed in XGL (Symlink Method)"
date: 2006-05-30
forum: Desktop Environments
---

### Post by DarthMandeep on 2006-05-30
I apologize in advance if this has been covered before, or if this was obvious to everyone but myself. I'd also like to apologize in advance for spelling and gramatical mistakes.

I haven't noticed any posts mentioning this, so I figured I'd make a new thread so people who might find this useful can actually find it. People who are using GDM to start XGL should stop reading now, as this post is of no use to them and I wouldn't want to waste anyones time. Here's hoping this thread is not a waste of time for other folks.  ;) 

If you're like me you prefer to start XGL via the symlink method instead of using GDM to load it. This method starts XGL by changing the /etc/X11/X symlink to point to /usr/bin/Xgl instead of /usr/bin/Xorg. Then you can use "startx" to load XGL and compiz and your panel and whatnot, the way everyone started their X server back in the 90's.

The problem with this is that folks who are using GDM can append options to their XGL configuration that greatly improve video playback, allowing them to watch movies in fullscreen without issues, while we can't.

To make use of those options I tried several things, this is what worked for me.

Remove your /etc/X11/X symlink, and open your text editor. Copy the following into it, the smile icon you see is supposed to be a ": p" with no space in between.

#!/bin/sh
/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo

Save the file as /etc/X11/xgl
Make the file executable with "chmod a+x /etc/X11/xgl"
Then create a new symlink called /etc/X11/X that points to that file. It seems /etc/X11/X has to be a symlink or startx will complain.

Now when you type startx, you'll load XGL like you did when you had /etc/X11/X linked to /usr/bin/Xgl, except now you've got the options needed to improve fullscreen video playback just like your GDM-using friends.

Once you've loaded X and started gmplayer you should have no problems with video, as long as you also make use of the gl2 renderer and maybe the frame-drop option for HD vids.

Yes, this is very simple and basic. But I'm not very bright and could not figure this out before now. I'm hoping this will help someone else who isn't very bright and also doesn't like GDM :) 

Let me know if this has been of any use, or if this even works on systems other than mine.

---

### Post by FedeXX on 2006-07-11
Thank you, but that doesn't works... even without any option added in the script, X doesn't start...it only gives a strange screen with an "X" mouse cursor in the middle...and nothing more. So seems impossible to link X to a script.

I'm a KDM user, there's no way to set this option like a gdm one? I really want to see fullscreen videos on my Xgl :P

---

### Post by DarthMandeep on 2006-07-16
This isn't really for any *dm, just for folks who run X from the command line by typing "startx".

For KDM you've got to add the options to your kdmrc file, I did a quick search and got this: [http://ubuntuforums.org/showthread.php?p=845077](http://ubuntuforums.org/showthread.php?p=845077)

Hope that helps.

---


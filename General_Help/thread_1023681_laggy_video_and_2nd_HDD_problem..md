---
title: "laggy video and 2nd HDD problem."
date: 2008-12-28
forum: General Help
---

### Post by nibon on 2008-12-28
First problem: Laggy video
when I play something in vlc, it looks okay, sounds okay, when I fullscreen it the sound is still okay but the video turns all laggy / really old webcam framerate.

I have updated my ATI Radeon 9800 PRO drivers via EnvyNG

Second problem: my 2nd HDD
I have movies, music, pics, other media on my 2nd HDD. When I log in I have audacious autostarting with my playlist up, however I can't just press a song there and expect it to play, I have to open nautilus first and enter the HDD, then my songs get playable, same goes for my wallpaper, the .jpeg is in the 2nd HDD. the wallpaper is the standard brown one 'til I enter it, then it changes to the one I've set it to.

---

### Post by laceration on 2008-12-28
As to #1.  Linux video drivers are just not that good yet.  They do not utilize the gpu and put a strain on your cpu.  A way to improve playback would be to shut down anything that is using up cpu.  Maybe another app such as mplayer or totem would work better?
Much better drivers are appearing in beta for Nvidia and are on the drawing board for ATI, so we have smoother days ahead.;)

---

### Post by nibon on 2008-12-28
the video playback used to work perfectly other times i've used ubuntu with severals apps running in the background. Weird...

I'll try the other programs and return with results.

EDIT:
They both worked even worse. Mplayer had about 5 FPS in fullscreen and totem couldn't even play the video, just audio.

---

### Post by -kg- on 2008-12-28
And for your second problem:

> I have movies, music, pics, other media on my 2nd HDD. When I log in I have audacious autostarting with my playlist up, however I can't just press a song there and expect it to play, I have to open nautilus first and enter the HDD, then my songs get playable, same goes for my wallpaper, the .jpeg is in the 2nd HDD. the wallpaper is the standard brown one 'til I enter it, then it changes to the one I've set it to.

You'll need to add that partition to your fstab configuration file.  See [How To Fstab]("http://ubuntuforums.org/showthread.php?t=283131") for more information.

---

### Post by nibon on 2008-12-29
FIRST PROBLEM SOLVED!

I had to open vlc and go into the Video options, change output module a couple of times. OpenGL option works fine, not 100% but about 98% maybe... absolutely fine.
Thanks for trying to help anyways.


-kg- Thanks, I'll look into that.

---


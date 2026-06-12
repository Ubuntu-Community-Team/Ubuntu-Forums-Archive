---
title: "stella full screen"
date: 2007-11-16
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-11-16
Hello everyone. I recently got my 32 inch lcd tv working as a monitor and have installed stella (atari). Well it works great but when I hit alt+enter for fullscreen, it gives me a blue screen, then once again and its back to windowed. The res is 640x480...any way to fix this?

---

### Post by hikaricore on 2007-11-16
Well I'm guessing your tv doesn't support 640x480.
Mine works only a certain resolutions from 800x600 up to 1366x768 (1360x768 truely).

You may have to find a resolution that your tv supports and see if it's possible to run Stella at that res.
I'm not personally familar with Stella, so someone else will have to point out where the config files are/if this is possible.

---

### Post by hikaricore on 2007-11-16
I tracked down Stella and found something that might interest you.

The version of Stella in the repos is **2.2**.

The current version (to the best of my knowledge) is **2.4**

From this version's changelog:

> What's New in This Release:

Added new video sub-system where fullscreen and windowed modes are treated
differently. Windowed modes now use '-zoom_tia' and '-zoom_ui' arguments,
while fullscreen modes can be specified by resolution using the new
'-fullres' argument.

· Widescreen video modes are now supported; Stella will simply center the
image with surrounding black borders.

So you may want to test out the new version.  ^_^

Best of luck,

--Aaron

---

### Post by Ripfox on 2007-11-16
Thanks Aaron I did read that somewhere, but ignored that it was the new version...hence the confusion! I will try that, thanks again.

On a related note, I am using the ATI Legacy tv out how to on these forums, and it works BUT, it claims that it will do 800x600 on the tv...but all i can get is 640x480. When I test 800x600, it fails and reverts. Any clue?

---

### Post by Ripfox on 2007-11-16
Confirmed...it does do fullscreen in the new version. Really slow though, and Mrs. Pacman froze my pc + reverted my session to XFCE from Gnome. Nasty!

---

### Post by hikaricore on 2007-11-17
Make sure you are running in the correct mode, the new version (i think) has both sdl and opengl and I'm sure one defaults.  I don't know if the previous version had these.  Other than that it may just be the resolution that's again the issue.  >.<  The higher the resolution the more graphical data needs to be processes and rendered for video output.  Same reason games will run slower at higher res if you didn't already know.  Not saying you didn't just throwing it out there.  ^_^

---


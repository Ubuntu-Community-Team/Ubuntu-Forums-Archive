---
title: "fluxbox and no sound in Flash and some other applications"
date: 2009-01-15
forum: Desktop Environments
---

### Post by oooooops on 2009-01-15
I've used both KDE and Gnome in the past.  I decided to try something lighter and was giving fluxbox a chance.  I am running on Intrepid.

I have fluxbox installed and most things are working great for me.  I do have some sound in fluxbox.  For instance when I am working in a terminal I can get sound.  VLC seems to have sound.  However I can not get flash (v10) to give sound from Firefox.  Nor can I get the application Exaile to output sound.  

After numerous searches/etc the answers seemed to be one of the following
1) Run Pulseaudio
2) Run the gnome-settings-daemon alongside Pulse
3) Install flashplugingnonfree-extrasound (for a flash fix)

I tried all of the above.  In neither case can I get sound from Flash and/or Exaile.  

Can anyone point me to a solution and/or some steps to try to troubleshoot these issue(s)?

---

### Post by oooooops on 2009-01-15
Well apparently I have gone completely crazy.  

I now have sound in both Exaile and Flash.

The only thing I changed is in Exaile I changed the Playback Sink (sync) to use "automatic" and now I magically have sound in both Exaile and Flash.

I do see the gnome-settings-daemon running by doing a ps.  I suspect that is being caused by my usage of nm-applet as I have not switched to either wifi radar and/or wicd yet.

This thread is now for mocking me for being crazy.

---


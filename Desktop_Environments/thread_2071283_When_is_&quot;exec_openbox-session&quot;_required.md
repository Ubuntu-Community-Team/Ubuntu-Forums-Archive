---
title: "When is &quot;exec openbox-session&quot; required?"
date: 2012-10-15
forum: Desktop Environments
---

### Post by PeterTaps on 2012-10-15
Folks,

I have to install openbox on a clean Ubuntu that does not have any GUI yet.

The steps I had written down were:
$ sudo apt-get install xorg
$ sudo apt-get install openbox
$ vi ~/.xinitrc and create a line "exec openbox-session"
$ startx

I accidentally missed the step of creating ~/.xinitrc file and just ran the final step "startx." What I noticed was that openbox did start to run. I am a bit confused. How is openbox running even though I did not specify "exec openbox-session" in .xinitrc? If this step was not mandatory, when is it needed?

Thank you in advance for your help.

Regards,
Peter

---


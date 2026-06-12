---
title: "Beryl / XGL for ATi Cards"
date: 2006-10-21
forum: Desktop Environments
---

### Post by ikehack on 2006-10-21
Hello Ubuntu forums.

   For the past several weeks I have been playing around with the installation of Beryl / XGL. I have done many tutorials from several sites, forums (including this one), and Wikis but all have failed. 

   About 20 minutes ago my X crashed, and wouldnt come back so I had to reconfigure it. Once I completed the reconfiguration Beryl was running. How it was I don't know. To see if it was stable and finally working, and if it boots on its own I restarted the computer. It never came back. 

   Beryl-manager runs in the corner and it says that Beryl is the window manager but there are no effects.

   Please Ubnutu Forms. I want to play with Beryl / XGL but I can't! :(

---

### Post by HanZo on 2006-10-21
I suggest you post the output of the following commands:

fglrxinfo
glxinfo | grep direct

then get a session with xgl loaded (if you get it to load) and try to launch beryl from the X-terminal 

I've been fighting a lot too with beryl, I get xgl to run, I get dri with the fglrx driver (on a radeon9200 card). but beryl does not wan to run.
if I start it from terminal it gives me the following output:

```
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```
now I wonder... what is this *GLX_EXT_texture_from_pixmap* thing?

---

### Post by ikehack on 2006-10-21
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 PRO Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by HanZo on 2006-10-22
hmm... looks like you've got the proprietary driver running... so xgl should work. how do you launch xgl? sh script associated with a session, i.e. by selecting the appropriate xgl session at login? have you got xgl running? otherwise you could have the same proble as I have... although I haven't figured out yet what my problem exactly is...

---


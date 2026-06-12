---
title: "How to make the window flame effect in 7.10"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by Dapman01 on 2007-10-22
I saw in a youtube video that when a guy got out of a window there was a flame effect from the bottom of the screen up.  Is there any way to enable that in 7.10

---

### Post by badactress on 2007-10-22
You need to install the compizconfig settings manager (search in Synaptic Package Manager for it), which will appear in your System->Preferences menu as "Advanced Desktop Effects Settings".

Click "Animations" from there, and select "Burn" as the Close Animation. 

:)

---

### Post by Dapman01 on 2007-10-22
> **badactress said:**
> You need to install the compizconfig settings manager (search in Synaptic Package Manager for it), which will appear in your System->Preferences menu as "Advanced Desktop Effects Settings".

Click "Animations" from there, and select "Burn" as the Close Animation. 

:)
what do I put in the options of 
WIndows match 
options

---

### Post by badactress on 2007-10-23
Hi, Sorry.. I didn't explain that too well..

You don't want to add a new animation, just change the existing one which applies to main application windows. By default on my Gutsy, it's the top entry & says:

GLIDE 2      200      ((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)

Just double-click anywhere on this line & change the close effect to Burn.

The other two lines change the close effects of menus/pop-up help boxes, and dialog boxes. You can play around with them too, but I found it's really annoying to have menus & pop-up-help set to burn as your screen is constantly bursting into flames!!

Hope this helps :)



> **Dapman01 said:**
> what do I put in the options of 
WIndows match 
options

---

### Post by alex13cp on 2007-10-23
hi

---

### Post by Sandlizardz on 2008-07-06
[**http://www.youtube.com/watch?v=BQ0RSKjJNaU**]("http://www.youtube.com/watch?v=BQ0RSKjJNaU")

I made a quick video tutorial and put it on youtube for others...the video quality was recorded at the highest quality but you know after uploading to youtube they reduce it. So there it is.

---


---
title: "Separate X Screens Setup"
date: 2008-12-06
forum: General Help
---

### Post by jdralphs on 2008-12-06
I recently purchased another 19" LCD monitor for my Ubuntu machine. I am running an older Nvidia GeForce FX 5200 with VGA and DVI ports and am using the restricted Nvidia drivers with Ubuntu 8.10.

After fumbling around a while, I got the two monitors working using nvidia-settings and have them under Separate X Screens.  However I seem to be having 2 problems:

1.  If I try to start an application from the GNOME panel on my second screen prior to starting an application on the first screen, gnome-panel hangs and the application does not start.

2.  I would like to be able to use the two screens as seperate workspaces, so when I tell GNOME to send a window to Workspace Right, it goes to Workspace Right.

Any ideas?

Thanks,

Jason

---

### Post by jdralphs on 2008-12-07
Any takers?

---

### Post by Ng Oon-Ee on 2008-12-08
Sorry, can't help on the first problem, but I myself have been looking for information on the 2nd and I can confidently say that its not possible currently to have applications sent from one x-screen to another. There used to be code to do that via a virtual network, but it was buggy, slow, and never finished I think, I only saw oblique references to it in years-old listings.

The explanations I saw stated that since separate x-screens are separate x-servers, moving an app would not just move its appearance but most of its workings. For example, if you click on a link in one x-screen, and firefox is running on another, the app will try and open another instance of firefox (generating an error). This is because to the x-server you're currently on, there is no firefox running. It has no awareness of it at all.

So I think if you want to move apps, its better that you use twinview or enable xinerama. Search around, there's guides on both. Also, the search function would have meant you didn't need to start this post at all, I think, because this subforum isn't really the right area for it (try hardware and laptops).

---

### Post by jdralphs on 2008-12-09
Thanks, your post confirmed my suspicions (and fears) on how separate x screens worked.  I'll play around with Twin View.

---


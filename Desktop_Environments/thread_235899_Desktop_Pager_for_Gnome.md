---
title: "Desktop Pager for Gnome"
date: 2006-08-13
forum: Desktop Environments
---

### Post by mtpadilla on 2006-08-13
Hi All. Just wondering if anyone could please recommend a pager to select virtual desktops for Gnome, but that can be positioned somewhere on the main part of the desktop (as opposed to lying in the panel, as the panel applet pager does). I've found other pagers that do this (ex. fbpager), but they all seem to be for other DEs/WMs, not Gnome...

Thank you!!!

---

### Post by ardchoille on 2006-08-13
fbpager is in the universe repo. Does it not work for you? fbpager sits on a part of the desktop, not in the fluxbox panel.

---

### Post by maniacmusician on 2006-08-13
he wants one for Gnome, not fluxbox. 

I don't really know of any, sorry

---

### Post by ardchoille on 2006-08-13
A pager is a pager, it's just another app. It's ok to run kde apps in gnome and gnome apps in kde, so I am guessing it is ok to run fluxbox apps in gnome. I once ran a WindowMaker dockapp that was a pager and it worked fine in gnome.

---

### Post by mtpadilla on 2006-08-17
> **ardchoille said:**
> A pager is a pager, it's just another app. It's ok to run kde apps in gnome and gnome apps in kde, so I am guessing it is ok to run fluxbox apps in gnome. I once ran a WindowMaker dockapp that was a pager and it worked fine in gnome.

Thanks or the comments folks.

Ardchiolle, do you recall what that app was?

I've tried fbpager before and the problem is that for some reason, when running it under Gnome, it does not show the silhouette of the windows in each of the workspaces; it only shows a blank screen. It also doesn't highlight which workspace is active. I'm guessing this isn't the normal behaviour when using it in Fluxbox, so apparently it doesn't work well under Gnome...

Wow...so apparently the only pager available for Gnome is this applet in the panel that we cannot detach to a more useful location!? Sad.....

---

### Post by ardchoille on 2006-08-17
> **mtpadilla said:**
> Thanks or the comments folks.

Ardchiolle, do you recall what that app was?

I've tried fbpager before and the problem is that for some reason, when running it under Gnome, it does not show the silhouette of the windows in each of the workspaces; it only shows a blank screen. It also doesn't highlight which workspace is active. I'm guessing this isn't the normal behaviour when using it in Fluxbox, so apparently it doesn't work well under Gnome...

Wow...so apparently the only pager available for Gnome is this applet in the panel that we cannot detach to a more useful location!? Sad.....

Looking in Synaptic, I see bbpager, fbpager, kpager, and more. Open Synaptic and do a search for "pager" and you'll find a bunch of them. I don't remember what the pager name was, but it was a pager that window maker users use, I had to compile it as a dockapp because it wasn't in the repos.

---

### Post by mtpadilla on 2006-08-18
Yep, I see them also and they're for Blackbox, Fluxbox, and KDE. The first two don't operate correctly under Gnome (in my experience), and the KDE one is just well.....take a look and you'll see what's wrong with it (a big windown around the pager doesn't make for economical usage of desktop space). I'll search more for the windowmaker app you mention...cheers!

---

### Post by ButteBlues on 2006-08-18
Why not use Compiz or Expocity to get an Expose-like effect instead?

---

### Post by Genican1 on 2006-10-19
the kde pager works in gnome, but it's not exactly pretty.  i'm not sure what you mean about the big window around it...  here's a pic...

---

### Post by mtpadilla on 2006-10-19
> **Genican1 said:**
> the kde pager works in gnome, but it's not exactly pretty.  i'm not sure what you mean about the big window around it...  here's a pic...

Hi Genican1...thank you for the post. Yeah, I wasn't very clear but I was referring to the border around KDE pager. It gets the job done, I suppose, but definitely not an elegant application or efficient use of desktop real estate.

I don't know why there's nothing like fbpager for gnome...ugh. Oh well.

---

### Post by mtpadilla on 2006-10-28
Hi Folks...just a follow up for those interested. I've since found the gdesklets app LTPager, which is very nice and comes close to what I was originally looking for. Thanks again to everyone and their helpful comments!

Best.

---

### Post by BuffaloX on 2007-01-15
Has anyone found out how to change the color of the gnome pager, or can it only be grey?
Or alternatively found a customizable pager with alpha blending?
I tried to look in the source code for the pagers for gdesklet, but they all include the same pager object, which has no configuration options for color or alpha, that I can find.

---


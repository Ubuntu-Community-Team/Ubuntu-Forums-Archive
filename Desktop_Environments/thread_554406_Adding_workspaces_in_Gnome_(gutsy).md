---
title: "Adding workspaces in Gnome (gutsy)"
date: 2007-09-18
forum: Desktop Environments
---

### Post by charles_elwood on 2007-09-18
Trying gutsy on a spare box, and having a look at the latest gnome. I go looking for a way to get the 4 desktops I'm used to. Right click on the workspace switcher -> preferences as has previously worked and as described here and in the gnome manual, but no sign of the spinner for the number of workspaces. WTF?

And while I'm at it, is it possible to use the mousewheel on the desktop to switch workspaces? I'm sure this used to be be possible.

Please resist the temptation to use add this to the Gnome vs <Insert desktop environment here> flamewar.

---

### Post by ivelasco on 2007-09-19
Maybe [THIS]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") is what are you looking for

---

### Post by Wolki on 2007-09-19
> **charles_elwood said:**
> Trying gutsy on a spare box, and having a look at the latest gnome. I go looking for a way to get the 4 desktops I'm used to. Right click on the workspace switcher -> preferences as has previously worked and as described here and in the gnome manual, but no sign of the spinner for the number of workspaces. WTF?

Maybe some compiz related thing? I'd recommend trying it with metacity.

> And while I'm at it, is it possible to use the mousewheel on the desktop to switch workspaces? I'm sure this used to be be possible.

I don't think this was ever possible in gnome. You can mousewheel over the workspace switcher panel applet though, which I consider better anyway - it's always in the same location, and you're less likely to switch workspaces by accident, then having a maximized window in the way of getting back to the previous workspace.

Switching like this doesn't seem to work in compiz though (yet another reason for metacity...), there is a 'switch workspaces on desktop scroll' plugin for it though; you might need to install extra plugins.

---

### Post by sgornick on 2007-09-20
Thanks to ivelasco for the link to Forlong's Blog.

First need to install compizconfig-settings-manager,
then 
  System -> Preferences -> Advanced Desktop Effects Settings

Then click on
  General Options,
then select Desktop Size tab.

  Horizontal Virtual Size (set to 2)
  Vertical Virtual Size (set to 2)

You then end up with 2X2.

---

### Post by charles_elwood on 2007-09-21
> **Wolki said:**
> 
Switching like this doesn't seem to work in compiz though (yet another reason for metacity...), there is a 'switch workspaces on desktop scroll' plugin for it though; 

Well that's a nail on the head. I still can't work out how to change the number of workspaces, yet on my fesity ubuntustudio box, gnome+beryl is easily beaten to my will. Grmbl.

---

### Post by Michal77 on 2007-09-23
HI,
If you use desktop effects in Gusty and want to change settings (including number of workspaces) you have to install: gnome-compiz-manager (is in repos, so you can use easily Synaptic). Them go to System>Preferences>GL Desktop. There is more options. 
Good luck!

---

### Post by charles_elwood on 2007-09-23
Oh I managed to get it configured the way I like it eventually. But yeah, gnome-compiz-manager is a bit nasty to use. It just feels counterintuitive. Maybe I'm used to the (non-kubuntu) kde settings manager, I don't know. 

I confess to missing ivelasco's post the first time I read through the replies here, and the link he posted contains many answers.

It seems that in the rush to embrace the eye candy and performace advantages of compiz usability has taken a back seat, and I have a feeling that no-one asked the most important question: *How can I explain this to my mother?*

---

### Post by thatonefatguy on 2007-10-01
I have the exactly same issue, rather had the same issue.
What i did was turn the desktop effects off completely and right clicked on the workspaces went to prefs and the "number of workspaces" was there.
I changed it to 4 and turned my effects on and it worked fine.
It also allowed me to use my scroll wheel to switch through workspaces.

---


---
title: "Black widget backgrounds with the Adwaita theme under Gnome"
date: 2014-02-03
forum: Desktop Environments
---

### Post by mjumbewu on 2014-02-03
Certain windows show up for me with a black background while using the Adwawita theme. Other themes seem to use the right background colors. Even more odd, when I take a screenshot of what's happening (see attached), sometimes the black area shows up as transparent! Trust me, it's black on my screen.

Transparent background: [ATTACH=CONFIG]250047[/ATTACH]
(I took a screenshot of the screenshot so that you could see what I'm talking about)

Black background: [ATTACH=CONFIG]250046[/ATTACH]

Here's what my settings are in Gnome tweak tool, for reference: [ATTACH=CONFIG]250048[/ATTACH]

I'm using Ubuntu 13.10 with Gnome 3 from the gnome3-team repo. This has been happening for me for a couple months now. I tried purging and reinstalling the gnome-themes-standard and light-themes packages to no avail. Any assistance with how to fix this would be appreciated.

Thanks,
- Mjumbe

---

### Post by yamcsha on 2014-10-04
solution: Disable overlay scroll

---

### Post by tareko on 2014-10-31
> **yamcsha said:**
> solution: Disable overlay scroll

Thank you! This solution worked for me.

Here are the instructions, from [http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars](http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars)

```
gsettings reset com.canonical.desktop.interface scrollbar-mode
```

tarek : )

---


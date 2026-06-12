---
title: "fiesty-to-gutsy no raise on click"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by tentative on 2007-10-19
I had compiz set up nicely in Fiesty. I have an ATI Radeon 9200 so it's fully supported. No problems at all. Only thing is, I like to have the settings for window management set up so that the only way to raise a window from behind another is to click the titlebar or Alt+click. This was working fine in the old version of Ubuntu but since upgrading to Gutsy this no longer works. The only way I can raise the window now is to turn on "raise on click" or just to live with not being able to Alt+click. 

I tried installing a compiz manager via
sudo aptitude install compizconfig-settings-manager

I tried modifying the General Options -> Actions -> General -> Raise Window to <Alt>Button1

But when I close the settings manager and re-open it. The settings have changed back to default. 

Am I missing something?

---

### Post by tentative on 2007-10-21
Nevermind, I just used gconf-editor to solve the problem.

---

### Post by TrioTorus on 2007-12-02
So, what setting did you change in gconf-editor? I got the exact same problem.

---

### Post by TrioTorus on 2007-12-02
Never mind, I found it. It's in:
/apps/metacity/general/raise_on_click
(I turned it off)

---


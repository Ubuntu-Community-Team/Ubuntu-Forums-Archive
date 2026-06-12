---
title: "How to get Solid Color Transparency for Panel?"
date: 2010-12-23
forum: Desktop Environments
---

### Post by frustratednerd on 2010-12-23
In GNOME, I know you can do this by right-clicking the panel, clicking properties, then going to the Background tab and selecting "Solid Color" and then full transparency.

But in Xubuntu, there's no option for this. How would I achieve the same effect on Xubuntu?

---

### Post by cherylfoster on 2010-12-23
The steps to get solid colour transparency for the panel are given below.
1. First you have to take care of easiest of Gnome.
2. Check the Solid colour button.
3. Slide the Style bar to the left until it is as transparent as you like.
4. Click Close.

---

### Post by frustratednerd on 2010-12-23
Thanks for your reply.

I don't understand your first step though. What does "First you have to take care of easiest of Gnome." mean? Are you saying that I should install GNOME?

---

### Post by hhh on 2010-12-23
I think it's a joke, ignore it. You need to enable compositing or the panel won't have a transparency option. Settings>Window Manager Tweaks>Compositor. Then right-click a panel, choose Customize Panel...

-edit- If you are using Compiz, you'll already have compositing enabled and can ignore that step.

---

### Post by frustratednerd on 2010-12-23
@hhh: Thanks for your reply.

I do indeed have Compiz enabled. However, when I go into the Panel properties, there is no "Background" option (and thus no "Solid color" option either)...only an option to adjust the transparency. The provided transparency control does not achieve the effect I am looking for.

I am looking to get something like this:

[http://www.quicktweaks.com/wp-content/uploads/2008/09/screenshot-2.png](http://www.quicktweaks.com/wp-content/uploads/2008/09/screenshot-2.png)

---

### Post by x1a4 on 2010-12-23
You can't set a background colour for the Xfce4 panel (yet).  However, you can set a background image.  If the image is a solid colour it amounts to the same thing as changing the colour of the panel.  [This]("http://xubuntu.wordpress.com/2007/10/12/howto-set-a-background-image-for-your-panel/") is a good guide on how to set a panel's background image in Xubuntu.

---

### Post by frustratednerd on 2010-12-23
I guess setting a background image will have to do for now. Thanks for the link, x1a4.

---


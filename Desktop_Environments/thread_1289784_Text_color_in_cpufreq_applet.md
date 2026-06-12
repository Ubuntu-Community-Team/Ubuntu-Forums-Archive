---
title: "Text color in cpufreq applet"
date: 2009-10-12
forum: Desktop Environments
---

### Post by grturner on 2009-10-12
what is the best way to change the color of the text in the cpufreq applet? I've installed a darker theme and where all the text in menus are white. cpufreq applet is keeping it's text black.

I'm running ubuntu intrepid.

---

### Post by mcduck on 2009-10-13
You could try this, it will change all panel applet colors:

Create a file called ".gtkrc-2.0" inside your home directory, and past the following code into that file:

```
style "panel"
{
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
```

After tyhat log out and back again, and all applets in your panels should now use the text color defined in that file.

---

### Post by grturner on 2009-10-13
no luck.

---

### Post by mcduck on 2009-10-14
That's strange, since it definitely works on all my Ubuntu computers...

---


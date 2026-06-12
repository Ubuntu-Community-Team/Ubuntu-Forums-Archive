---
title: "Tooltips color in Ubuntu 11.10"
date: 2011-10-07
forum: Desktop Environments
---

### Post by kakalos12 on 2011-10-07
Hello. I've just installed Ubuntu 11.10 and I have difficulty reading the tooltips when coding with eclipse. That's annoying. I can't find how to change the tooltips color in ubuntu 11.10. Please help me .

---

### Post by sam-k on 2011-10-15
I also struggled with this in 11.10. In 11.04, you can fix the problem with Ubuntu's appearance configuration dialog, but the theme color options are now gone.

To fix your problem with Eclipse in 11.10, you need to modify the /usr/share/themes/Ambiance/gtk-2.0/gtkrc file. In the gtk-color-scheme string at the very top of the file, change the tooltip_bg_color and selected_fg_color entries and add a tooltip_fg_color entry.

Hope this helps.

---

### Post by bilderbuchi on 2011-10-17
thanks, that works nicely. in my case, I just had to set ```
tooltip_bg_color:#7f7f7f
``` and it looked good.

---

### Post by victor.pillac on 2011-12-01
Hi, I created a script to do this, see [here]("http://victorpillac.wordpress.com/2011/12/01/fix-tooltips-color-in-ubuntu-11-10/").
Cheers

---

### Post by rick333 on 2011-12-13
Your script changed the color values appropriately, and then I changed from Ambiance to Radiance and back again, but I still have a problem with Eclipse that occurs in at least 3 different places. 

1. If I select a file in the file explorer, I get a dark orange background and a light text. Fine. But if I then click on the content of a file in the editor, the selected file's background becomes a very light gradient gray, and I can no longer read it.

2. Bigger problem. If I CTL-SHIFT-T to search for a file, the dialog uses the same light foreground and light gray gradient -- can't read it. If I mouse-click to select an item, the orange background is used, which I can easily read. This same problem occurs when using code completion (which I use all the time). Also resolves when I mouse-click to select an item.

I don't understand the meanings of all the different color types in the gtk config files, and I don't know how they are mapped in Eclipse -- not a good recipe for figuring this out. Has anyone solved the above problems. Ubuntu 11.10 is (nearly) completely great, but this one hitch is really quite annoying.

Any help would be greatly appreciated. Thanks.

Rick

---

### Post by tilusnet on 2012-01-26
I have been suffering for the last hour+ for the same reason. I have no idea where the light grey background comes from.


> **rick333 said:**
> Your script changed the color values appropriately, and then I changed from Ambiance to Radiance and back again, but I still have a problem with Eclipse that occurs in at least 3 different places. 

1. If I select a file in the file explorer, I get a dark orange background and a light text. Fine. But if I then click on the content of a file in the editor, the selected file's background becomes a very light gradient gray, and I can no longer read it.

2. Bigger problem. If I CTL-SHIFT-T to search for a file, the dialog uses the same light foreground and light gray gradient -- can't read it. If I mouse-click to select an item, the orange background is used, which I can easily read. This same problem occurs when using code completion (which I use all the time). Also resolves when I mouse-click to select an item.

I don't understand the meanings of all the different color types in the gtk config files, and I don't know how they are mapped in Eclipse -- not a good recipe for figuring this out. Has anyone solved the above problems. Ubuntu 11.10 is (nearly) completely great, but this one hitch is really quite annoying.

Any help would be greatly appreciated. Thanks.

Rick

---

### Post by bilderbuchi on 2012-01-27
for what it's worth, after messing around with them files and stuff like that, I found an easier way to correct the problem for Eclipse here: [http://askubuntu.com/a/85034/11069](http://askubuntu.com/a/85034/11069)

For CDT do the following:
  Window>Preferences>C/C++>Editor: Appearance Color Options>Source Hover Background
  Uncheck System Default, and select a color.
  Unfortunately there's no Eclipse-wide setting that I know of. Pretty  lame. You shouldn't have to set stuff like that for every perspective.

---

### Post by tilusnet on 2012-01-27
...and searching on I came across 

[http://askubuntu.com/questions/62421/eclipse-content-assist-popup-is-unreadable-on-ambiance-radiance-theme](http://askubuntu.com/questions/62421/eclipse-content-assist-popup-is-unreadable-on-ambiance-radiance-theme)

which inspired me and have it FIXED!:

[LIST=1]
[*]Open your gtkrc file, e.g. /usr/share/themes/Ambiance/gtk-2.0/gtkrc
[*]In your style "default" section change/add

base[ACTIVE]      = shade(0.5, "#F2F1F0")

[/LIST]

This will make the background a dark grey shade. 
The first parameter influences the tone; the nearer to 1.0, the lighter the colour.
Tweak the colour at your will.

---


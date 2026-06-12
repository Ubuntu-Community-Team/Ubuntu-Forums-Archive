---
title: "Glass GNOME panel"
date: 2010-02-21
forum: Desktop Environments
---

### Post by heywtf on 2010-02-21
I am trying to glass up my GNOME panel.

The easy option seems to select panel properties and set the right background image, but I'm ending up with this situation (see screenshot) where some parts of the panel are glass and some still use the system theme.

[http://img28.imageshack.us/img28/5288/glassgonewrong.png](http://img28.imageshack.us/img28/5288/glassgonewrong.png)

Is there an easy solution to this?

Failing that, what other ways can I glassify panels?

Thanks.

---

### Post by chewearn on 2010-02-21
True opacity of GNOME panel is a long standing unfixed wish list.  Alternative is to use compiz "Opacity, Brightness and Saturation" plug-in to make the panel partially opaque, but it's not a true fix.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=147775&stc=1&d=1266772716[/IMG]

---

### Post by mcduck on 2010-02-21
That's because the GTK theme you are using is defining a background image to the panel and panel applets. Any panel theming in the GTK theme will override whatever you try to set directly from the panel's options.

The only way to fix that is to edit the GTK theme and remove any panel-related stuff from it. Quite many themes have a separate panel.rc file that handles the panel's theme, if that's the case you can simply delete or rename that file. Otherwise you'll just have to read through the main theme.rc file to find the relevant sections.

(you might also want to enable scaling for panel background image, that can be done through gconf-editor, just browse to apps/panel/toplevels/*your_panel*/background and enabling "scale" or "stretch", depending which one fits your situation best...)

---

### Post by moongia on 2010-02-21
this worked for me.

---

### Post by heywtf on 2010-02-21
> **mcduck said:**
> That's because the GTK theme you are using is defining a background image to the panel and panel applets. Any panel theming in the GTK theme will override whatever you try to set directly from the panel's options.

The only way to fix that is to edit the GTK theme and remove any panel-related stuff from it. Quite many themes have a separate panel.rc file that handles the panel's theme, if that's the case you can simply delete or rename that file. Otherwise you'll just have to read through the main theme.rc file to find the relevant sections.

(you might also want to enable scaling for panel background image, that can be done through gconf-editor, just browse to apps/panel/toplevels/*your_panel*/background and enabling &quot;scale&quot; or &quot;stretch&quot;, depending which one fits your situation best...)

 Heh, I just spent the last 10 minutes removing any panel related information from a test theme to see what would happen. Then I come back to this thread to find that someone's suggested doing just that. Thanks! It worked nicely. 

 Incidentally, scale/stretch has solved a different (albeit minor) problem I was having, so thanks for that too.

---

### Post by IcarianVX on 2010-03-01
Removing the panel.rc worked for me.  However, I still have 2 little panels (audio and network status) that STILL have the background.  Any idea where I should look for those?

Thanks.

---

### Post by stinkeye on 2010-03-01
Try renaming panel-bg.png in the theme your using in your ~/.themes folder.

---


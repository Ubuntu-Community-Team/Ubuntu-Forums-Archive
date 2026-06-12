---
title: "Problems with XGL and Beryl."
date: 2007-02-16
forum: Desktop Environments
---

### Post by Scooter7 on 2007-02-16
Hi, I'm having various problems with XGL and Beryl. I'm using Kubuntu 6.10. My XGL problems being:

The only option on the Log out menu is 'End Session'. This only is true in XGL, in a normal KDE session everything else is there too. I've tried the various suggestions in the  beryl wiki, with no luck.

In the 'Monitor and Display' section of System Settings, it says that something could not be started, and that my KDE install could be corrupt; I don't remember the exact words. Like the first problem, this only occurs in the XGL session.

My last items aren't really problems, just questions of the linux newb. :p   

One, how do I change Beryl themes? And two, what's my 'super key'? Coming from a Windows-only background, I've never heard of that.

---

### Post by shareMenaPeace on 2007-02-16
Hi, 
for error messages you can look in 

System -> Administration -> System Log


When you run beryl-manager from console you can see the beryl task icon and rightclick choose emerald theme manager to change themes.

I dont understand super key - where do you need this?

---

### Post by Scooter7 on 2007-02-16
I know how to access the theme manager, I'm just unable to change the theme.   I've done it once, by clicking on a theme then restarting the beryl window manager, but now it doesn't work.   As for the super-key, it's for enabling things such as the water effect.

I'll look in my error log, and post back here with the results.   Or do you want to know the error message from my system settings panel?   I'll check that too.

-EDIT-

Here's the error:

> The module Monitor and Display could not be loaded.

The diagnostics is:

Possible reasons:

	* An error occured during your last KDE ugrade leaving an orphaned control module
        * You have old third party modules lying around.

Check these points carefully and try to remove the module mentioned in the error message.   If this fails, consider contacting your distributor or packager.

Also, xgl doesn't run very well in my preferred resolution (1280x1024).   It's very slow, and the video is choppy.

---


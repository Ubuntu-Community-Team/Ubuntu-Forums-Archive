---
title: "Can't disable Window Decorations plugin after upgrade to Karmic"
date: 2009-10-29
forum: Desktop Environments
---

### Post by foxmajik on 2009-10-29
Hello,

I just upgraded to 9.10 (which seems to have gone smoothly).

After the upgrade I went into compizconfig settings manager to disable the Window Decorations plugin (I don't want window decorations since I'm using the Grid plugin and keyboard input to manage windows and the decorations waste screen space).

However when I uncheck the box to disable the plugin "Window Decorations," it re-checks itself.

Why is there a check box if it's just going to re-check itself?

How do I really disable the plugin?

Thanks in advance.

---

### Post by Alain2 on 2009-11-03
I second that question... ? Is there a setting to change in gconf-editor or somewhere else to allow deactivation of this plugin (and actually others that have the same issue) ?

---

### Post by foxmajik on 2009-11-03
> **Alain2 said:**
> I second that question... ? Is there a setting to change in gconf-editor or somewhere else to allow deactivation of this plugin (and actually others that have the same issue) ?

I even tried setting Compiz's plugins to manual management and manually disabling the plugin, but it just puts itself back into the "enabled" list as soon as the preferences panel is closed.

The only way I've found to disable window decorations to forcefully crash the window decorator, but that sucks because then I have some windows I can't close.

---

### Post by arkashkin on 2009-11-19
This page has a solution for you:
[http://intipadi.com/linux/gain-space-by-removing-the-maximized-windows-titlebar-linux-w-compiz-or-maximus.html]("http://intipadi.com/linux/gain-space-by-removing-the-maximized-windows-titlebar-linux-w-compiz-or-maximus.html")

---

### Post by foxmajik on 2009-11-19
> **arkashkin said:**
> This page has a solution for you:
[http://intipadi.com/linux/gain-space-by-removing-the-maximized-windows-titlebar-linux-w-compiz-or-maximus.html]("http://intipadi.com/linux/gain-space-by-removing-the-maximized-windows-titlebar-linux-w-compiz-or-maximus.html")

Thank you!

That did, in fact, fix my problem.

All I had to do is change "Decoration windows" from "any" to "none".

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136863&stc=1&d=1258665039[/IMG]

---


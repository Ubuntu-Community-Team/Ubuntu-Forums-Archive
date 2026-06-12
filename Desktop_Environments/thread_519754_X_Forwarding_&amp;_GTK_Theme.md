---
title: "X Forwarding &amp; GTK Theme"
date: 2007-08-07
forum: Desktop Environments
---

### Post by Bogaurd on 2007-08-07
Hi there,
I have X forwarding working correctly on my machine, and am able to connect it remotely with no problems.

The remote machine I am using is also an Ubuntu machine - I want to know how I can make the x11 forwarded apps use the GTK theme that I have enabled on the machine I am working from - at the moment they seem to have no theme, and don't look so great.

Is this possible to do?

Thanks :)

---

### Post by Bogaurd on 2007-08-11
Is this not possible? :confused:

---

### Post by akadruid on 2007-10-25
You need to have your local theme on the remote machine

If you downloaded the theme off the web, download to the remote machine in the exact same way and it should work.

If you customized your theme, follow these steps:

[LIST]
[*]On your local machine, check your theme is saved (System / Preferences / Themes, Save Theme).

[*]Open ~/.themes/ and you should see a folder with the name you saved your theme with(e.g. My Theme). Inside that there should be a file called My Theme, and possibly a bunch of other folders and files.  Copy everything from there into the folder to the /usr/share/themes on the remote machine (just straight into that folder, not into a My Theme folder).

[*]Change your local theme to something else and back again.
[/LIST]

hope that helps

---

### Post by akadruid on 2007-10-25
Sorry I just realised I was using local and remote the other way round in my explanation.

For local, I meant the machine you are sitting at, where the applications are displayed.  For remote, I meant the machine that is running the applications

---


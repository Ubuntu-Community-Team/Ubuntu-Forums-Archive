---
title: "XFCE4 Workspace Switching broken"
date: 2006-10-08
forum: Desktop Environments
---

### Post by elemental0125 on 2006-10-08
I'm using the latest version of XFCE4 on edgy, and after rebooting today I found that I can't switch workspaces properly.

I've got XFCE4 setup with six workspaces and so that I can switch workspace using Alt-F1 through Alt-F6, which has worked for me since I installed Dapper back when, and since I switched to edgy (pretty much as soon as I could), until today.

Today, after I rebooted, Alt-F1 still switches to Workspace one, but Alt-F2 goes to five, and Alt-F3 goes to six, Alt-F4,5,6 does nothing.

I've gone through the settings and it's all setup correctly as far as I can tell. Restarting has no effect, neither does reinstalling XFCE4. I've destroyed and recreated all the workspaces to no avail. I've tried different key mappings. Even if there are only two workspaces Alt-F2 still won't switch to workspace two.

Any ideas?

---

### Post by john.nicholls on 2006-10-08
Do you have the Pager installed? If so, can you switch desktops using that?

John

---

### Post by elemental0125 on 2006-10-09
Yup, the pager works without a problem. Switching to Left/Right Workspace works without a problem. But neither of those are adequate substitutions for being able to switch directly to the right workspace quickly, and ideally without having to take hands off the keyboard.

---

### Post by john.nicholls on 2006-10-10
Have you tried the default workspace switching shortcut, Ctrl-F1, Ctrl-F2, etc?

I haven't switched to Edgy, but I believe the current version of Xfce is different to the one in Dapper. Could you revert to the Dapper version of Xfce to see if that still works?

I'm inclined to think that something's gone wrong in the Edgy Xfce version, and that you should lodge a bug report in Ubuntu. I wouldn't lodge a bug report with Xfce at this stage, as they are unhappy about Ubuntu using experimental versions of their software instead of waiting for the official 4.4 release.

John

---

### Post by john.nicholls on 2006-10-10
Your problem was the subject of some talk on the Xfce discussion forum today. The significant comment from the developer Olivier Fourdan is:

"If you are talking about Ctrl+Fn shortcuts to switch workspaces, then yes, it's a bug that has been fixed last Saturday (10/06) and yet to be included in Xubuntu package. I've created a Lauchpad report for that, it's #64918."

John

---

### Post by elemental0125 on 2006-10-10
Yeah, I suspected it was a bug in the XFCE packages - it sounds like they're making some changes to parts of the key handing code. The discussions about Alt-Tab for window switching and some of the bug filed on that seem to point in that direction.

Ah well, it isn't the end of the world - guess I'll just wait for a new package. I can deal with the annoyance for a time.

---


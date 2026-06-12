---
title: "Always on Visible Workspace does not work"
date: 2014-03-07
forum: Desktop Environments
---

### Post by beniamin-kalinowski on 2014-03-07
As I stated in the title, Always on Visible Workspace does not work.
It used to, but I think that plugging another monitor (via HDMI) changed some options and now, after unplugging this option does not work.
I've found [http://gregcor.com/2011/05/07/fix-dual-monitors-in-gnome-3-aka-my-workspaces-are-broken/](http://gregcor.com/2011/05/07/fix-dual-monitors-in-gnome-3-aka-my-workspaces-are-broken/) but I don't have desktop/gnome/shell config, so there was no help.

Do you have some ideas what might have happened?

Edit:
Description:    Ubuntu 13.10

Edit2:
Move to other workspace makes current window dissapear - so I suppose it exists in some other (virtual?) workspace, that actually doesn't exist. So I think something in wrong with workspaces (!).

---

### Post by phidia on 2014-03-08
I'm not sure if [this]("http://askubuntu.com/questions/339250/how-to-automatically-set-always-on-visible-workspace-for-windows-on-particular") will help or not but check the links in the sidebar there because there might be an answer in those.

---

### Post by beniamin-kalinowski on 2014-03-08
Well, in my case it does not work at all. I check "Always on top" and it works great. I check "Always on visible workspace" and it doesn't work when I move to the other workspace.

From what I've found out: Move to another workspace does not work neither. It simply makes the current window dissapear. So I suppose that Unity/Gnome doesn't recognize workspaces correctly. How is it possible?

But Ctrl+Shift+Right/Left/Up/Down works all right. It moves window to other workspace. So I suppose the application that moves by "Ctrl+Shift+Right/Left/Up/Down" has a proper settings while window manager does not.

---


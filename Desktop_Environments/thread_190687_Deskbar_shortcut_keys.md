---
title: "Deskbar shortcut keys"
date: 2006-06-06
forum: Desktop Environments
---

### Post by underwater on 2006-06-06
What syntax do you use if you want to configure it to use Ctrl or the windows key and space to give it focus?  Shortcuts like WindowsKey+Space or Ctrl+Space

If you enter the wrong syntax for a shortcut key something like

<Super_L>space

from then on space alone will access the deskbar.  You have to set the  shortcut back to something OK and then reload the whole deskbar.

Thanks in advance

---

### Post by smilelover on 2006-06-13
I can't believe they didn't implement setting the shortcut by actually pressing it. Is this some kind of joke?...in 2006 in a distro that calls itself user-friendly and aims to be "enterprise" :rolleyes:

---

### Post by jgoguen on 2006-06-13
When was this said?  I see a question about how to manually input a shortcut combination, which when involving the Super key is a perfectly valid question since the Super key is the *only* key that doesn't seem to work like the others.  AFAIK no distro has this working right yet.  Nowhere did I see anyone saying that you can't input other shortcut combinations.

---

### Post by nemik on 2008-02-18
I'd also like to know this. It broke in Gutsy. Past Ubuntu versions could do this without a problem.

Actually I just figured it out, open gconf-editor in terminal and find the keybinding  you want to assign. In there put "<Mod4><Hyper>space" then it works fine.

---


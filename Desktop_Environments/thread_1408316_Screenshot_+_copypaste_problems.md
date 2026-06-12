---
title: "Screenshot + copy/paste problems"
date: 2010-02-16
forum: Desktop Environments
---

### Post by sloom22 on 2010-02-16
I'm running Ubuntu 9.10. I would like to be able to copy and paste the screen like in Windows - press the Print Screen button ("PrtSc"), the screen gets copied to the keyboard, with Ctrl-V you can paste it into any application.

This does not work, I think for two reasons.

1) When I press PrtSc, it runs gnome-screenshot, opening a window. I don't want this window, I just want the picture on the clipboard! Worse, on my laptop PrtSc is right next to Backspace, so I always press PrtSc by accident, popping up the screenshot window when I don't even want a screenshot. If this just overwrote the clipboard, I think it would be less of a problem.

Potential solution: Is there a replacement application for gnome-screenshot which just runs in the background, writes to the clipboard automatically, and doesn't pop up windows?

2) There's an option in the gnome-screenshot window to write to the clipboard. (What I want.) But if I choose it and then close gnome-screenshot, what's on the clipboard gets lost! This seems to be general X-Windows behavior and is very annoying, since the user has to keep in mind the state of 3 things (copy-to program, copy-from program, clipboard) simultaneously!

Potential solution: The clipboard application runs continually in the background.

Does anyone know of a screenshot program, or a (hidden?) option in gnome-screenshot, which does these things?

---

### Post by lovinglinux on 2010-02-16
[http://ubuntuforums.org/showpost.php?p=567113&postcount=13](http://ubuntuforums.org/showpost.php?p=567113&postcount=13)

Once you choose the best command for your needs from that thread, you can create a launcher on your panel with the selected command.

---


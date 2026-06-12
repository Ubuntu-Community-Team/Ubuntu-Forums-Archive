---
title: "How to stop Ubuntu Screenshot from taking over Game Screenshots?"
date: 2008-11-11
forum: Gaming &amp; Leisure
---

### Post by Laibcoms on 2008-11-11
I can't find how to disable or prevent the default Ubuntu Screenshot from taking over the screenshot feature of Games.  Anyone knows how?

No, I don't use/have/enabled the compiz screenshot module, it is Ubuntu's screenshot app that is kicking in when I'm pressing PrintScreen while playing games.

Thanks for any info.

---

### Post by MikeyUbun2 on 2008-11-11
Go to System>Preferences>Keyboard Shortcuts then goto the desktop section and find take a screenshot then click the key combo and press backspace to clear it you can do this to take screenshot of current window out to the same way if alt print is causing you problems

---

### Post by Grishka on 2008-11-11
run gconf-editor and change the keybinding in /apps/metacity/global_keybindings/run_command_screenshot.

---

### Post by Laibcoms on 2008-11-23
Thanks thanks.

I tried using CTRL or Shift as modifier before I tried changing the default keybindings.  It seems to work, it uses the application's own screenshot method and not metacity's screenshot.

^_^

---


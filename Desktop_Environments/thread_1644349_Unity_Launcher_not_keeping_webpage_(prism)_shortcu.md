---
title: "Unity Launcher not keeping webpage (prism) shortcuts"
date: 2010-12-13
forum: Desktop Environments
---

### Post by jingaling on 2010-12-13
HI Guys,

I have recently upgraded my netbook from 10.04 LTS desktop to 10.10 netbook as I really like the new unity feature.

Anyway, I have a couple of prism shortcuts that I use for both my personal and work webmail (both are google apps). When I open them I select them to stay in launcher so they are always accessible. Problem is - as soon as I reboot my machine the prism shortcuts disappear from the Unity launcher. All my other shortcuts like chrome, file browser, open office etc all stay...it's just the prism shortcuts.

Has anyone else found the same problem? I have searched the forums and can't find anything.

Jing

PS Just in case any of you don't know, prism is a tool that lets you create a shortcut to any webpage, with a custom icon and a cut-down version of your browser (i.e. no tool bars cluttering the page) so the shortcut almost works like it's own application.

---

### Post by ubugaru on 2010-12-28
i noticed yesterday that within gconf, unity is set to use chromium by default.

you need to access gconf-editor via sudo

then go to 'desktop/unity/launcher' there is a setting 'webapp_use_chromium' uncheck this for prism.
I don't know that this is what you need but i know it exists.

;)

---


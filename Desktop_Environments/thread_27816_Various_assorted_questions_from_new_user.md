---
title: "Various assorted questions from new user"
date: 2005-04-17
forum: Desktop Environments
---

### Post by epb613 on 2005-04-17
A bunch of assorted questions:

1. I installed kde-desktop after installing Ubuntu. I'm tidying up now and I wanted to know if there's a way (or rather which packages do I remove) to remove Gnome.

2. I love Kaffeine player. I'm having one problem: I can't play shoutcasts with it. They work fine in XMMS, but Kaffeine says it's missing the plugin. For example, when I type the following location under play URL it doesn't work: [http://broadcast.umbc.edu:8000/wmbc-lofi](http://broadcast.umbc.edu:8000/wmbc-lofi) (The website is wmbc.umbc.edu.)

3. Is there a way/program to enable widows key hotkeys. For example, I want to make it so that windows key + d shows the desktop.

4. This one is really important. Can I make it so that only the programs in the current workspace show up minimized on the bottom of the screen. This is how it works by default in GNOME.

Thanks so much if anyone can help with any of these issues.

---

### Post by bored2k on 2005-04-17
1) [http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster](http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster) 
You can use debfoster to wipe Gnome from your box.

---

### Post by Morgoth on 2005-04-18
3) Kde will allow you to use the windows key in a hotkey assignment now.  I use it to bring up my file manager the same as in windows (" windows key" e ), but I am not sure how you would get it to show the desktop.  Go to the Control Centre -> Regional & Accessibility -> Keyboard Shortcuts.  Click on the Command Shortcuts tab and then you can select an application and set the hotkey combo you want to open it.  You could try playing around in there and see if there is a way to show the desktop.

---

### Post by philipacamaniac on 2005-04-18
2. I just tried that URL, and it works in Kaffeine. Have you installed the [w32codecs](http://ubuntuforums.org/showpost.php?p=134199&postcount=2)  package? XMMS uses its own codec system, while Kaffeine by default uses xine. The w32codecs should provide most of your multimedia needs.

4. Right click your taskbar and choose "Configure Panel...". Select the Taskbar icon on the right, then uncheck the box "Show windows from all desktops"

EDIT: 3. Goto Control Center --> Regional & Access. --> Keyboard Shortcuts. On the Shortcut Schemes tab, change the "Current Scheme" to "Windows Scheme (With Win Key)". Or, keep the current scheme and just modify some of the shortcuts to use the Win key. You can set Panel --> Toggle Showing Desktop to Win+D.

---

### Post by epb613 on 2005-04-18
Wow! Quick accurate replies. Thank you guys so much!!!

philipacamaniac, I did have w32codecs installed, but I clicked to have it reinstalled and after doing so, not only did the shoutcasts work fine but so did other things which 
I forget to mention in my original post.

Again, thank you guys so much!

---


---
title: "Music Player shortcut issue"
date: 2005-11-27
forum: Desktop Environments
---

### Post by rado_london on 2005-11-27
Hi 
I have HP Pavilion DV4145EA. All shortcut keys work perfectly. But I have a problem. When I press My Music player shortcut it says.
```
Couldn't execute command: rhythmbox
Verify that this command exists.
```

This is probably because I uninstalled rhythmbox. My question is?
How can set it up when I press this function key to load Amarok or Beep media player?

Thanks in advance
Radoslav

---

### Post by towsonu2003 on 2005-11-28
this may work, but wont choose the music player... under system>preferences>keyboard shortcut>sounds, click to where it says launch music player and click your button. click close and give it a try...

---

### Post by rado_london on 2005-11-28
I did it. It starts a music player, but it is trying to start rhythbox. I would like to start amarok intead of rhythmbox.
Do you have any ideas of how to do this?

---

### Post by Merlintrix on 2006-07-18
> **rado_london said:**
> Hi 
I have HP Pavilion DV4145EA. All shortcut keys work perfectly. But I have a problem. When I press My Music player shortcut it says.
```
Couldn't execute command: rhythmbox
Verify that this command exists.
```

This is probably because I uninstalled rhythmbox. My question is?
How can set it up when I press this function key to load Amarok or Beep media player?

Thanks in advance
Radoslav

Have u tried using gconf-editor?
U'll have to modify apps --> metacity --> global_keybindings and apps --> metacity --> keybinding_commands

---

### Post by aldegaz on 2006-08-02
I have the same problem, and going to metacity -> keybinding_commands doesnt let you change it, just to add a keyboard "combo" like alt+something to get the application, but nothing about changing the keyboard launcher

any ideas?

---

### Post by aldegaz on 2006-08-02
I have the same problem, and going to metacity -> keybinding_commands doesnt let you change it, just to add a keyboard "combo" like alt+something to get the application, but nothing about changing the keyboard launcher

any ideas?

---

### Post by hikaricore on 2006-08-21
> **rado_london said:**
> Hi 
I have HP Pavilion DV4145EA. All shortcut keys work perfectly. But I have a problem. When I press My Music player shortcut it says.
```
Couldn't execute command: rhythmbox
Verify that this command exists.
```

This is probably because I uninstalled rhythmbox. My question is?
How can set it up when I press this function key to load Amarok or Beep media player?

Thanks in advance
Radoslav


FIXED!

sudo gedit /usr/bin/rhythmbox

"type in the command that launches your music player and save the file"

sudo chmod +x /usr/bin/rhythmbox

"then hit the button you use to launch a music player"

YOU WIN!

---


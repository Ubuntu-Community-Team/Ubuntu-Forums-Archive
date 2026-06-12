---
title: "gnome-terminal question"
date: 2005-12-09
forum: Desktop Environments
---

### Post by gilgongo on 2005-12-09
I'm trying to start gnome-terminal so that executes an SSH session. I've tried variations on the following, but the best I can do is launch two terminals, one of which has the correct commands sent to it, but none of the desired settings (like geometry), and other other just seems to be a default with nothing.

The string I'm trying is:

```
gnome-terminal --working-directory=%f  --window-with-profile=ServerName --geometry=80x24 --command="ssh -i $HOME/.ssh/id_rsa username@myserver.com"
```

Can anyone give me any clues?

Thanks.

---

### Post by somnoliento on 2005-12-09
Did you try making the command part of the terminal profile? On the second tab of the profile preferences, there should be a text field where you can enter a command, which will be executed every time a terminal with that profile is started.

---

### Post by gilgongo on 2005-12-09
Wahooo! I didn't know about the profiles thing - thanks! :p 

Now all I need to do is work out why I get this error message in the terminal just before I get asked for my SSH password:

Warning: Identity file $HOME/.ssh/id_rsa not accessible: No such file or directory.

It doesn't seem to affect anything, but it's just annoying. Odd.

---


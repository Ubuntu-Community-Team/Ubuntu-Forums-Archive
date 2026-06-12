---
title: "Alt + Tab has stopped working since Dapper upgrade..."
date: 2006-06-24
forum: Desktop Environments
---

### Post by Rebajas on 2006-06-24
Hiya,

Since my upgrade to Dapper my Alt + Tab has stopped working.

Any ideas how this can be rectified?

Tony.

---

### Post by rai4shu2 on 2006-06-24
Double-check your "Window Management" settings in the Preferences / Keyboard Shortcuts.

---

### Post by Rebajas on 2006-06-24
I have done so and although the heading is there, there are no options underneath and no little arrow to toggle them.

Weird.

---

### Post by rai4shu2 on 2006-06-24
Very strange. Try using the "gconf-editor" and checking this value:

/apps/metacity/global_keybindings/switch_windows

---

### Post by aysiu on 2006-06-24
Can you create a new user and see if the new user encounters the same problem? That way you can know immediately whether it's a system problem or a user configuration problem.

---

### Post by Rebajas on 2006-06-24
Thanks for your help, there are no settings under global_keybindings though.

I have also noticed that when I try to run Update Manager I get the message:
Only one software management tool is allowed to run at the same time

I haven't got anything open :) It must be running itself.

---

### Post by Rebajas on 2006-06-24
Hiya Aysiu,

I created a new user and the problem didn't go away. I have also noticed that Alt + F4 no longer works either :(

Cheers.

---

### Post by aysiu on 2006-06-24
This is weird and bad.

I guess I didn't need to tell you that.

Can you try this? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` and then Control-Alt-Backspace and log back in again...?

---

### Post by Rebajas on 2006-06-25
Excellent - that seems to have fixed it.

Thanks alot.

Tony.

P.S: My signiture has never been so apt - I don't reckon I'll ever upgrade again at this rate ;)

---

### Post by jlchannel on 2006-11-04
I had the similar problem in Ubuntu 6.10. I tried as suggested but no luck :(

---

### Post by viocudinti on 2006-11-08
I have a similar (but not identical) issue. I've tried creating a new user and alt-tab and other alt-* keys are working. But I'm now trying to fix my current user. 
I've tried setting the shortcut for switch window and when i press alt-tab i get : <Alt><Mod2><Tab> ... what is mod2 ?

---

### Post by allyson on 2007-03-21
I'm also getting alt+Mod2+tab when trying to set alt+tab after it mysteriously stopped working. I have no idea what it is, nor how to fix it. Any help would be appreciated! Thanks :) For me, though, it isn't a dapper upgrade. My keyboard settings randomly got reset back to defaults yesterday within what had been a very stable edgy. I tried to solve it (maybe not the best thing!) by upgrading to feisty. Feisty seems stable, but it hasn't solved my alt+tab problem. Annoying, as alt+tab was working yesterday morning, but not yesterday afternoon. I had been having some problems using the Fn+CRT/LCD key combination, but not sure why that would break all other key combinations!

---

### Post by viocudinti on 2007-03-22
xmodmap /usr/share/xmodmap/xmodmap.us-101 (or the right one for you)

... i think this fixed this issue for me (but not sure, don't remember exactly)
If that works, add it to your session startup and provide feedback here.

---


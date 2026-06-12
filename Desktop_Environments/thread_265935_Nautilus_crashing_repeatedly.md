---
title: "Nautilus crashing repeatedly"
date: 2006-09-26
forum: Desktop Environments
---

### Post by taser on 2006-09-26
I'm having a rather annoying problem with Nautilus.

I opened it to move some files from the Desktop to my home folder, and it crashed on me, with a dialog box saying:
[I]
The application "nautilus" has quit unexpectedly.

You can inform the developers of what happened to help them fix it. Or you can restart the application right now.
Buttons: Restart Application; Close; Inform Developers
[/I]

I used Bug Buddy to inform the developers of the bug, then re-opened Nautilus. It stayed open for about 5 seconds or so, then the same dialog box shows up. If I click on either the Restart Application or Close button, the Nautilus window shuts down, automatically reopens, then shows the dialog above after 5 seconds.

Is there anything that I can do? I debated uninstalling Nautilus through Synaptic, but the dependencies include gnome-base, which I assume is the window manager, and I'm afraid I might be unable to make it back to a usable environment afterwards.

Any help is appreciated. Thanks in advance!

---

### Post by mingotta on 2006-10-29
I have the same problem. Tried different solutions I found by googling around but couldn't solve it.

---

### Post by solotransit on 2006-12-10
i have the same problem. its a bit dissapointing for me because i didnt expect this to happen with linux, especially with such a basic, fundamental part of the operating system. 


i cannot browse any files at the moment. i will try a reboot. sounds like a windows solution. "im not sure so ill just reboot and hope it goes away"

ill try a "killall nautilus" first.

Edit after reboot:

ok, i tried killall nautilus, and it did nothing, same effect as pushing either close or restart buttons (they do the same thing in this case, reopen a file browser window, soonafter another message box)

i rebooted, my desktop didnt load. as in no background, no icons. i opened a file browser, and found i could navigate folders other than my desktop and home folder. i open my desktop in the file browser window and note (looking past the error box) that the icon for a .swf file is a clock or timer, the one that is shown while preview thumbnails for images/videos etc are loaded. it was stuck on this. i moved the file to its own seperate folder, and start "nautilus" in the terminal. everything works fine. 

conclusion:
nautilus has a problem getting a thumbnail preview for some .swf files. 

solution for the time being:
isolate the file from commonly used folders. 
i had no noticable issues using nautilus and just ignoring the message box.


i hope this helps everyone with the same problem :) maybe a developer could consider a feild to specify which file types previews are generated for. good luck everyone!

---


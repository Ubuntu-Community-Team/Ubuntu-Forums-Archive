---
title: "Set Taskbar to auto-hide, will not show up again..."
date: 2010-06-08
forum: Desktop Environments
---

### Post by curryking1 on 2010-06-08
Hi,

I just set my taskbar to 'auto-hide' in a Gnome desktop environment...

And... when I mouse to the bottom area where it is supposed to be (I can see the little strip indicating that it's 'there,' just obviously not responding)... there is no response...

I deleted my other taskbar... so... I don't know what I'm supposed to do to change the setting back to normal...

Not a fun bug :(

Something that probably should be fixed... I guess...

I just updated Ubuntu 10.04 today before I made the change, so my stuff is up to date.

On x64.

Arggh.... why can't the super key just open the taskbar by default... that's really lame... >.>

---

### Post by Breambutt on 2010-06-08
Alt+F2

/apps/panel/toplevels/top_panel_screen0

Fiddle around with the settings.

You might have some sort of an invisible layer on top of it, possibly due to a bug or something else. I had this when recording full screen desktop video and the callback area of my auto-hiding dock was 1 pixel.

---

### Post by curryking1 on 2010-06-08
Thanks for the prompt response.

I copy and pasted that into the GUI that came up after pressing Alt-F2, but it did not do anything.

I don't think I have an /apps folder right at the top of my filesystem, so I'm not sure what that is trying to access?

I guess that may be the problem, being only a pixel tall. I can't right click the taskbar to modify any attributes there unfortunately.

How can I just create a new taskbar for now?

Is there something I can do from gconf-editor to fix this?

Edit -

Oh my God...

You have to scroll to the bottom left pixel of the screen...

T_T

T_T

Why, Ubuntu, just why...

At least now I know... thanks for the help, cheers.

---

### Post by original_jamingrit on 2010-06-08
Ack, I think he intended to say Alt F2, then type in ```
gconf-editor
```, then look in the path described as /apps/panel/toplevels/top_panel_screen0.

This should give you configuration options.

---

### Post by curryking1 on 2010-06-08
I see, I will remember that section now haha.

Thanks for the help.

---

### Post by Breambutt on 2010-06-08
Hoho.

Yeah, well, you know, that's just like... your opinion, man.

Poop happens. I have a habit of revising my sentence structures and accidentally erasing vital parts.

---


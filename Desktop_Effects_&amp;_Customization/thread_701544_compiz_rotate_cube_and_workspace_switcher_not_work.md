---
title: "compiz rotate cube and workspace switcher not working together"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by blakboy on 2008-02-19
running gutsy 64 with desktop effects enabled with cube rotation...

now when I change workspaces using <ctrl><alt><L/Rarrow> the workspace switcher doesn't register a change in the workspace (it stays on WS 1).

I have 4 workspaces in the workspace switcher, when trying to use this to change the workspace the system freezes.

I dont even have to use cube rotation I can use <ctrl><alt><down arrow> then <L/Rarrow> which brings the panoramic WS switcher into effect. and the problem still occurs

Anyone got any ideas?

thanks

---

### Post by Don_Shifty on 2008-02-21
i have the same question... any answer would be helpful!
thanks

---

### Post by j3frea on 2008-06-11
Hi, I had the same problem when I stumbled upon this post. I thought perhaps I should explain how I fixed it...

I began by ensuring that no windows were open on any other workspaces then:

System -> Preferences -> Advanced Desktop Effects Settings

- General Options
 - Desktop Size
I set Horizontal "Virtual Size", "Vertical Virtual Size" and "Number of Desktops" all to "1".
I then exited the manager (I'm not sure whether that did anything special but that's what I did...)
The workspace switcher then only showed 1 workspace.
I then went back to those settings and set "Horizontal Virtual Size" to "4". 'Cause that's how many I use...

Hope this helps...

---

### Post by suggsjc on 2008-06-20
I just did exactly what j3frea said, and I still only have one workspace.  None of the <ctl>-<alt>-[up,down,left,right] do anything.

Any ideas?  FWIW, I had been running xfce for a bit, but changed for this session.

Edit: I also just moved to a newer kernel...are there any modules that I need to recompile?

---


---
title: "Unpleasant Screen Switching Behavior, Please Help"
date: 2009-05-30
forum: General Help
---

### Post by e64462 on 2009-05-30
Semester just ended, so I decided to update to Jaunty... good news, everything works great... sort of...

My laptop is an X61 tablet that i frequently attach to an external monitor (as in daily). Only two modes are necessary for my purposes: either the whole desktop on the external monitor with max resolution, or the whole desktop on the laptop's monitor with max resolution (with the alternative monitor being switched off in both cases). All this nonsense involving cloned Desktops is worthless for my purposes. Unfortunately, the default behavior on jaunty is to cycle through the numerous screen combinations, with each fn+f7 keypress. This is mostly just annoying... 

I tried using an acpi script i wrote for Intrepid, the problem is that the fn+f7 keypress event activates both my script, and the screen cycling process (which didn't cause too much trouble, because as it turns out, my script doesn't work on Jaunty)

In short, I'd like to do one of two things, either disable the default script altogether (so that i can implement my own), or change the behavior so that only two screen combinations are possible.

If you're confused on the screen combinations im referring to the cycling follows this process, roughly...
1. LCD ON, Res 1024x768   and   Ext Mon OFF
2. LCD ON, Res 1024x768   and   Ext Mon ON, Res 1024x768
3. LCD OFF   and   Ext Mon ON, Res 1980x1080

(so i guess i just want to disable option 2 in the default script)

If anyone could tell me where this script is located / how to edit it, that would be pretty sweet...

Thanks in advance,
Nick

---


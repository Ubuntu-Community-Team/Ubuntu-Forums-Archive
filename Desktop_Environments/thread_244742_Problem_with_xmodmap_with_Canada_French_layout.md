---
title: "Problem with xmodmap with Canada French layout"
date: 2006-08-26
forum: Desktop Environments
---

### Post by crazymonkey on 2006-08-26
I have read several threads about the shift+backspace restarting x problem related to xgl/compiz and i have a similar problem.

I use the US English layout without a problem but when i switch my layout to Canada French (Legacy) as soon as i start typing è, à or other characters with accent followed by backspace my x session restart.

This problem has started after i tried to install and run xgl/compiz (which didnt work). Now i dont use xgl/compiz and i'm stuck with xmodmap -e keycode 22=BackSpace BackSpace Terminate_Server in my startup programs and i cant remove it. When i kill xmodmap in the Sessions utility i can type in CaFr without problems.

Any suggestions on how to remove that line from my startup session?

---

### Post by crazymonkey on 2006-09-11
I finally reinstalled my whole computer and that solved the problem...

---


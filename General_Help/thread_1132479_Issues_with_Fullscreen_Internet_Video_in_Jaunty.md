---
title: "Issues with Fullscreen Internet Video in Jaunty"
date: 2009-04-21
forum: General Help
---

### Post by Funnyguts on 2009-04-21
Ever since I upgraded to Jaunty a few days ago, I have been unable to watch video in Firefox in fullscreen. Each time I click the fullscreen button, the video flickers up to take the whole screen, then instantly disappears and returns to the normal, in-page screen. This only happens on Google Video, Youtube, or any other video site that uses Flash to display the video. Any suggestions as to how to fix this or do I just have to deal with flash?

---

### Post by Alka-Seltzer PLUS on 2009-05-15
Hola !
If you have compiz enabled maybe this will be useful ( solved the problem right now )

*gconftool --type=bool --set /apps/compiz/plugins/workarounds/allscreens/options/legacy_fullscreen false*
 [I] gconftool --type=bool --set /apps/compiz/general/screen0/options/unredirect_fullscreen_windows false

let me know :D
[/I]

---

### Post by kthari85 on 2009-05-28
:( it does't works ....

---

### Post by Yellow Pasque on 2009-05-28
I suggest starting FF from the terminal to see any error output Flash throws.

Also, see if right-clicking on Flash and unchecking "hardware acceleration" makes a difference. Of course, without hardware acceleration, full-screen Flash needs a lot of CPU, but it might point you in the right direction.

---


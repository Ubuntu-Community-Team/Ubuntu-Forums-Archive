---
title: "Cursor Themes installation problems - inconsistent application"
date: 2009-01-01
forum: General Help
---

### Post by zachthejones on 2009-01-01
I like playing with my desktop theme, and wanted to try out some new cursor (mouse) themes. So I went to gnome-look.org and downloaded a few. But here's the problem I'm running into (and this happened when I was running Hardy as well) is that the new cursor theme is applied sporadically. Like when I'm in a OpenOffice document or in firefox. But other than that, I might as well not have it installed or running.

I did a complete restart after installing the mouse theme, but the issue persists.

---

### Post by fooman on 2009-01-01
i have had similar problems in the past...heres how i fixed it:

go to system > preferences > appearance > customize button > pointer tab...choose the default pointer.  close that box and the appearance preferences box.

open your home folder (places > home folder).  in the toolbar click "view" and put a check next to "show hidden files".  find the .icons folder and open it.

inside you should see a folder for the cursor theme you installed....right click on that folder and choose "move to trash".

reinstall your cursor theme and see if it works....hope that helps.

---

### Post by zachthejones on 2009-01-01
thanks for the suggestion. I tried that with the same result. It's weird, in Hardy I could install cursor themes correctly in Kubuntu, but I had the same issue in Ubuntu. Any other suggestions?

---

### Post by zachthejones on 2009-01-02
okay - I think I figured out the issue. Compiz is messing with my pointer. I switched the window manager to Metacity and the pointer/cursor worked fine across the desktop and windows. How can I get Compiz to recognize the new mouse theme?

---

### Post by DeviousLearning on 2009-01-03
I'm having the exact same problem. Right now, about five different cursor themes show up. Some appear when I click on something, others in certain windows like firefox. It's really annoying. 

I also found the same thing as zachthejones. When I switch to metacity, the issue goes away and one consistent mouse theme is applied (the one selected under appearance).

Any help would be greatly appreciated.

---

### Post by le singe on 2009-01-22
If you go into CompizConfig Settings Manager, under General Options, and type in the mouse theme you want to use exactly how it is called in the "Cursor theme" box, that should do it.

I had a similar problem where changing my cursor under the appearances settings no longer did anything, and come to think of it, it was about when I switched from Metacity to Emerald window manager.  Hope this helps, if you're still looking for a fix.

---

### Post by zachthejones on 2009-01-22
le singe - thanks man! that totally fixed the problem! I just typed in the name of the cursor theme exactly as it was under the regular theme window and it worked just fine!

---

### Post by KhaaL on 2010-04-27
sorry for bringing up an old thread, but it's relevant to my problem. I don't seem to find the option to find "Cursor theme" under general settings in cssm 0.8.2, is that option taken out?

---

### Post by zachthejones on 2010-04-27
um, I just checked and tried it out using the field "Default Icon" under CCSM's General Options. After logging out and back in my new cursor theme is working across the board, at least thus far...

They may have just re-named the field, not sure though. This is what seemed to work on my installation...

---

### Post by KhaaL on 2010-04-29
ah, well that didnt help in my case. I'm using Comixcursors and i've tried typing in both ComixCursors-Black-Small and the full path with no luck.

---

### Post by zachthejones on 2010-04-29
sad. that sucks - I'm using a comix cursors one as well and it's working perfectly here. Not sure what else to check - are you using Ubuntu or Kubuntu? are you using the fusion-icon to help manage Compiz?

---


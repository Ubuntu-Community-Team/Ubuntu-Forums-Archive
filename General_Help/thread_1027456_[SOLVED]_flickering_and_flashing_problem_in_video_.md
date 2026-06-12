---
title: "[SOLVED] flickering and flashing problem in video programs!problem solved!"
date: 2009-01-01
forum: General Help
---

### Post by maidenfan1961 on 2009-01-01
ok! i hope this helps people in the future that has this problem! since i installed the latest version of ubuntu (ubuntu 8.10) everytime i played video files using helix,totem and vlc, the videos would have extreme flickering flashing and very brief blanking.
at first,i fixed the problem in vlc by going to the video settings and setting the video output module to X11,but i still kept having the same problem with the other video programs such as helix and totem!
well i finally fixed the problem,and as is the case with most problems like this the solution is actually so simple i actually feel stupid for not seeing it!lol
anyway for anyone else that is having this problem with flickering and flashing video programs,all you do is go to system preferences,appearance and simply turn off visual effects!
it is really that simple! all my video programs now work as though i never had the problem at all!
i hope that helps ubuntu users that have had similar problems with this!
thanks for letting me share this solution,and good luck!

---

### Post by maidenfan1961 on 2009-01-01
i will also add that whenever you want to use compiz fusion or any other program that requires video effects,to turn your video effects back on being that it is pretty obvious that you cant run video programs side by side with visual effects programs!
hopefully developers will fix this issue in future upgrades. hint, hint.
but we just have to settle with this solution in the meantime!

---

### Post by leveliv on 2009-01-01
Thread Tools > Mark as Solved
Instead of "Problem Solved"

---

### Post by zika on 2009-01-01
without need to turn compiz off:
System->Preferences->Multimedia_Systems_Selector->Video->X_Window_System_(no xv)
[for flash: right-click->choose_video_output_to_x11_(not_xv)]

---


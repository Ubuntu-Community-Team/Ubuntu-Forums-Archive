---
title: "Video/Visualization problem Intrepid"
date: 2009-01-07
forum: General Help
---

### Post by aschwerin.moses on 2009-01-07
I've just installed 8.10. Im having issues with video playback and visualization. When i play a movie or just music in totem or any player, the video is just black, when i move the window around i can see the video/visualization. Full screen does the same and i have to keep moving the window and finally it shows the video/visualization... i had no issues with 8.04.. please help..

i have intel 865 mobo and graphic card is integrated...

---

### Post by mssever on 2009-01-07
> **aschwerin.moses said:**
> I've just installed 8.10. Im having issues with video playback and visualization. When i play a movie or just music in totem or any player, the video is just black, when i move the window around i can see the video/visualization. Full screen does the same and i have to keep moving the window and finally it shows the video/visualization... i had no issues with 8.04.. please help..

i have intel 865 mobo and graphic card is integrated...
Compiz might be at fault. To test if it is, type ```
metacity --replace &
``` to switch from Compiz to Metacity. Then see if it still happens. You can make the change permanent through the Appearance tool.

---

### Post by aschwerin.moses on 2009-01-07
> **mssever said:**
> Compiz might be at fault. To test if it is, type ```
metacity --replace &
``` to switch from Compiz to Metacity. Then see if it still happens. You can make the change permanent through the Appearance tool.

Yes... that's working.. but i want to use Compiz :confused:

---

### Post by mssever on 2009-01-07
If things work in Metacity but not Compiz, I don't think there's much you can do but maybe file a bug report with Compiz and wait for a new version. Probably Compiz, your video driver, and your video card don't get along for some reason.

---

### Post by aschwerin.moses on 2009-01-08
:( :( :( .. now that is sad.. really there is'nt anything that can be done

---


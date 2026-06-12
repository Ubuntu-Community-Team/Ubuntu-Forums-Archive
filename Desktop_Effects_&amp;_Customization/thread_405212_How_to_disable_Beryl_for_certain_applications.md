---
title: "How to disable Beryl for certain applications?"
date: 2007-04-09
forum: Desktop Effects &amp; Customization
---

### Post by HunterK on 2007-04-09
Hey guys, my first post here.  I really love Ubuntu + Beryl.  I have it working great with my NVIDA 6800gt card.  (Antialiasing and everything.)  It's just that some applications, I have found, dont work all that well with beryl.

NES Emulator: Sound is choppy when beryl is activated.

Google Earth: Choppy scrolling, zooming, etc, when beryl is activated.

Is there any way to disable beryl only for certain applications or windows? (Sort of like disabling visual styles in windows by using the properties tab of the shortcut.)

Or, maybe you guys have a solution for choppy sound in applications under beryl? hehehe :) 

Thanks is advance!
Ken

---

### Post by Gallardo Spyder on 2007-04-10
Right click on the Beryl Icon in your task bar..

You will see an option called - Select Window Manager.  Select Metacity or any other than Beryl if you have multiple installed (you will at least have Beryl and the Standard).

That will immediately disable Beryl - and you can use whatever you like.  Once you are done you can reselect Beryl.

You could also write a script and launch that with your problematic programs - which would start and stop it automatically - but the above method is pretty quick and easy.

---

### Post by HunterK on 2007-04-10
Thanks, for the info.  I've been doing that for now.  I'll look into the script thing.  I didnt know if there was a way to tell beryl "Hey dont process this application when it runs."

---

### Post by vatechtigger on 2007-04-10
I know what you are saying but I don't believe you can have Beryl render everything but just one application. Its all or nothing. It would probably take more horsepower to unrender just one application (almost like a virtual machine)

---

### Post by toorima on 2007-04-10
DISPLAY=:0 googleearth will make googleearth work with beryl activated.

---


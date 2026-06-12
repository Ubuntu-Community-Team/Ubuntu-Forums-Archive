---
title: "Skydome Randomizer"
date: 2008-02-25
forum: Desktop Effects &amp; Customization
---

### Post by Akovia on 2008-02-25
HI,
Well I have my compiz-fusion up and running nicely now. I am running a transparent cube with the skydome plugin and noticed how hard it was to pick an image as the effect is so cool on lots of wallpapers. So I though it would be even better if the image could be randomized.

I poked around a bit but have not found any solution yet and wondered if I could get some input from some pros on how hard it would be to make a script to do just that, and if it would be worth the trouble. I think I understand the basic concept on how it could be done and wondered if another randomizing wallpaper script could be hacked  for this purpose, or if it's something that would have to be built from scratch.

I would appreciate any input.

Akovia

---

### Post by DaymItzJack on 2008-02-25
The best way I could think of doing a script would be:

Have a list of images in a folder and make a script to change a random image to the file name "currentskydome" and then just set that one as your skydome, once that image changes next time, your skydome should change.

Does it have to be random or is in a cycle ok? (I might attempt this once I get home from school tomorrow.)

---

### Post by DaymItzJack on 2008-02-25
Actually a smarter way would be using:

dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/cube/screen0/skydome_image org.freedesktop.compiz.set string:"/path/to/new/image"

---

### Post by Akovia on 2008-02-26
Sweet!,
If I understand it right, that is the actual command to load the new image right? If that is right, I just need to find a randomizing script to use it with.

Personally I have about 100 wallpapers I want to go through so cycling would be fine but randomizing without repeating would be optimal. In a perfect situation I would have it change every hour (cron job?), scanning a directory to see if there are new wallpapers, and some sort of lax rules to prevent duplication as much as possible.

Thanks a ton for the help. There seems to be limited info on the dbus command so that is very helpful indeed. I am gonna try to snoop around for a host script if I get some time today.

Cheers,
Ako

---


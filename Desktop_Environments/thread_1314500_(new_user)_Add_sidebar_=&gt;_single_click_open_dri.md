---
title: "(new user) Add sidebar =&gt; single click open drive"
date: 2009-11-04
forum: Desktop Environments
---

### Post by dragonetti on 2009-11-04
I'm just a 5 weeks ubuntu user, in that time I managed to install and configure ubuntu to my taste (configure wine and get the adobe CS4 working, only photoshop, dreamweaver and fireworks though, got my 2 shared folders from 2 different NAS drives correctly mounted, setup a Virtual box with Windows XP working correctly including networking etc...)

Only one thing drives my up the wall....I want a sidebar on the left side of my screen and I want make it display my mounted drives. And to make things even more difficult, I want to single click on a mounted drive on that sidepanel so the contents of that clicked drive gets displayed...

I tried:
- add a panel in ubuntu (right click > new panel > add to panel "disk mounter"
- adesklet
- screenlet

None of the above makes it possible to add a panel on which i can single-click to open a mounted drive.

Thank you in advance.

---

### Post by grizato on 2009-11-04
right click on panel > Properties position= left. That takes care of another part of the problem.

I don't know how to get the other one!;)

---

### Post by onyxwolf on 2009-11-04
This is a little long winded, but I'm keeping in mind your experience with Ubuntu, so stay with me. Go to the places menu and you should see a launcher for your mounted drive (probably right below the computer launcher). Click on it to open the file browser (Should be Nautilus which I did this with). Right below the back and forward buttons (upper-left) there should be a button that should be a paper and pencil (if you hover over it'll say something like toggle between button and text-based location bar); beside that will be location buttons (by default if there is a text bar just hit the paper button and it will display the location buttons); the last button should be your mounted drive (may say 4GB Media). Grab unto that button (just like windows just have to hold down left mouse button) and drag it to the panel where you want it on. This creates a launcher to the mounted location /media/disk (if it is a thumb drive)  (This is were a thumb drive mounts to by default. When that particular mounted drive isn't there and you click on the launcher it will come up with the error "Could not open location 'file:///media/disk'". So that same launcher should work if its a thumb drive or a usb hdd (Will keep the same name as the media you used to create it {shows when you hover over it}, but just right click on the launcher and click properties to edit that). Unless you have both plugged in at once!

---

### Post by dragonetti on 2009-11-05
@onyxwolf

Thank you!

That did the trick! Although it doesnt't show text (only the default icon).
This is definitely the way I wanted it. (sidebar + mounted drive + single click!)

Again thank you!

---

### Post by onyxwolf on 2009-11-05
Glad I could help and the text (name and description) only show if you hover over the launcher.

---


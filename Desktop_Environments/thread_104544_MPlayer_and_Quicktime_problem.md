---
title: "MPlayer and Quicktime problem"
date: 2005-12-16
forum: Desktop Environments
---

### Post by pioni on 2005-12-16
I've installed MPlayer and QuickTime support with Automatix to a fresh install of Breezy and it's working fine except for one thing. For some reason MPlayer keeps on opening new windows again and again when I try to watch QuickTime trailers in apple.com (examples: [Da Vinci Code]("http://www.apple.com/trailers/sony_pictures/da_vinci_code/") or [X3]("http://www.apple.com/trailers/fox/x3/")). Is there anything I can do to prevent this? If I'm quick enough to close all opening MPlayer windows and select the trailer size (small/medium/large) from the page, the opening page shows the selected trailer just fine. It's the HD trailer labels below those size selections that cause MPlayer to act annoyingly.

---

### Post by pioni on 2005-12-17
Has anyone else noticed the problem? I tried to look at MPlayer settings, but there are none that, in my opinion, are of help in this case. Please try the examples above and tell me whether MPlayer works on your computer or not.

---

### Post by TrinitronX on 2005-12-17
I looked at the actual source code for the pages, and it's perfectly normal.  There are 6 different .mov files that you can select from.  The small, medium, and large links go to different pages which embed the movie file in the page, and the other HD links actually embed their .mov  files in the first (main) page.  I noticed that when I clicked on these, you can see the mplayer controls show in the small space where the link image is, and another window pops up with the actual video... because it would be hard to see such a large movie in what little space those small link images are :p.  Think of it as a feature :)

---

### Post by pioni on 2005-12-17
But do these three HD videos play automatically on your computer, I mean the ones that have very small MPlayer controls on the page? The problem is that on Windows the controls are not shown, but there are simple 720 etc. buttons for opening the trailer in a new window, whereas in Ubuntu all three trailers open and play automatically and the page shows small MPlayer controls instead of the resolution buttons. It's very annoying on a slow computer that isn't capable of showing HD trailers anyway to have to close the opening HD trailers several times, since MPlayer does not understand that I don't want to see the HD trailers nor play them automatically.

---

### Post by TrinitronX on 2005-12-17
no... the hd trailers do not automatically play for me.  Only when I click on their links.  What browser are you using?

---

### Post by pioni on 2005-12-17
[QUOTE=TrinitronX]no... the hd trailers do not automatically play for me.  Only when I click on their links.  What browser are you using?[/QUOTE]
I'm using Firefox 1.07 that came with Breezy. Opera and Konqueror do not play movies at all, because Opera is missing the required plugins and Konqueror is complaining it can't find ALSA or something (it tries two or three alternatives and then quits/crashes).

It'd be just fine if only the HD trailers were not played automatically. I don't care if the buttons are not shown correctly, but now it always opens three trailers when I load the page for the first time and then reopens the trailers until I click stop on those mini-controls.

---

### Post by pioni on 2005-12-17
Adding autostart=0 to ~/.mplayer/mplayerplug-in.conf seems to solve the problem with automatic play. The buttons are not shown, but I can live with it as long as these MPlayer windows do not pop up.

Now the three small MPlayer controls say they are buffering. Does this mean that MPlayer is still loading three HD trailers as long as I stay on the page? :confused:

---

### Post by pioni on 2005-12-17
Answering to myself...
[QUOTE=pioni]Now the three small MPlayer controls say they are buffering. Does this mean that MPlayer is still loading three HD trailers as long as I stay on the page? :confused:[/QUOTE]
Yes it does. After a couple of minutes the small MPlayer control changed to "Download complete". I guess I can live with this now, because MPlayer does not open the huge HD trailers and play them automatically anymore. Bandwidth is free, so I don't care...

---


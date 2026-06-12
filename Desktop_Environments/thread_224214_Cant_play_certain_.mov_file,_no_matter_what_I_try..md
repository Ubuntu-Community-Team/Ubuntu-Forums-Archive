---
title: "Cant play certain .mov file, no matter what I try."
date: 2006-07-27
forum: Desktop Environments
---

### Post by jcapote on 2006-07-27
My dapper system has prevoiusly been able to play 99% of all the media i've thrown at it, except for this one elusive movie: [Rails 15 minute demo]("http://media.rubyonrails.org/video/rails_take2_with_sound.mov"). Here are the following media players tested:

totem (gstreamer): Crashes instantly.
mplayer (full output [here]("http://pastebin.com/758414")): I hear "Here we go" then crashes (great timing!).
xine-ui: I hear the presentation, but see nothing.
vlc: Crashes instantly.


Anyone else have any luck? I have all the restricted formats working and configured (I can see everything else)

---

### Post by Lord Illidan on 2006-07-27
Downloading it right now.. Streaming it in Konqueror seemed to work. Using mplayer in kmplayer.
I am wgetting it right now to test on my normal players, see how it goes.

---

### Post by jcapote on 2006-07-27
Just finished restarting my laptop, and reproduced all the same results :-(

---

### Post by Lord Illidan on 2006-07-27
VLC didn't work..sound worked, video not.
Same for Xine.
Mplayer worked though, sound and video. Have you installed the w32codecs?

---

### Post by jcapote on 2006-07-27
I actually just updated to the latest version of w32 codecs,

capotej@zen:~/Desktop$ dpkg -l | grep w32
ii  w32codecs                              20060611-0.0  win32 binary codecs

---

### Post by jcapote on 2006-07-27
FIXED! I started messing around with mplayer's command line options, and I found that if you play it with -vo x11, it appears to work!

---

### Post by DrMeers on 2008-07-02
I stumbled across this thread by googling "*ubuntu hardy crash play mov file*" -- and it just so happens that I was also trying to play the .movs from the *RubyOnRails* site ([http://www.rubyonrails.com/screencasts]("http://www.rubyonrails.com/screencasts"))! There must be something unusual about them -- they crashed the system (blue-screen, restart session) with every player I tried.

The **mplayer -vo x11** works for me also -- thanks. 

But it doesn't sound like a long-term solution -- the instability needs to be fixed in the players, libraries or OS, wherever it lies... anyone have any ideas?

---


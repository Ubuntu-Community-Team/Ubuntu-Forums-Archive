---
title: "Video problems"
date: 2009-02-16
forum: General Help
---

### Post by Gizenshya on 2009-02-16
I can't view the videos on this site: [http://www.theonion.com/content/video/breaking_news_series_of](http://www.theonion.com/content/video/breaking_news_series_of)

They are hilarious, but the flash or java or whatever video player is just a white box.  The rest of everything is OK.  It seems to load (with a progression bar)... but then just turns white and does nothing.  It works fine with windows.  Am I missing somekind of plugin?

---

### Post by dcstar on 2009-02-16
> **Gizenshya said:**
> I can't view the videos on this site: [http://www.theonion.com/content/video/breaking_news_series_of](http://www.theonion.com/content/video/breaking_news_series_of)

They are hilarious, but the flash or java or whatever video player is just a white box.  The rest of everything is OK.  It seems to load (with a progression bar)... but then just turns white and does nothing.  It works fine with windows.  Am I missing somekind of plugin?

Install the **ubuntu-restricted-extras** package.

---

### Post by Gizenshya on 2009-02-16
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.

```

:(

---

### Post by Crafty Kisses on 2009-02-16
Try refreshing the page a couple of times and see if you have the problem.

---

### Post by Gizenshya on 2009-02-16
I've refreshed, restarted... tried different browsers. is the video working for you guys?

I'm on firefox atm.

---

### Post by sunkenpirate on 2009-02-17
Same thing here. I load the page, the video starts playing, with the progress bar and everything. It plays for about 10-12 seconds, and then hangs. The buttons and progress bar become unresponsive.

When I switch the tab, and come back to this one, or if I minimize and then maximize firefox, I see a blank black rectangle in place of the video, and the buttons and the progress bar are also missing.

Here's the information about my system, I have the ubuntu-restricted-extras package installed, and also have flash plugin 10, I have firefox 3, and also, this problem happens only for stumblevideo, the flash video works fine for youtube.. Bizarre.

---

### Post by Darkshade on 2009-02-17
Lol The Onion :D Hilarious stuff!

/On topic:
Are you able to watch flash videos at all? (like youtube for example). Try installing the package **flashplugin-nonfree**, if you're unable to see flash at all that should solve it.

Good luck!

---

### Post by sunkenpirate on 2009-02-19
Actually, at first, I could see youtube videos. But now , the problem has spread and I cannot see any flash video for more than 10 seconds.
I do have flashplugin-nonfree installed, as well as vlc multimedia plugin and mplayer plugin for firefox installed, both separately, and at the same time.

---

### Post by Gizenshya on 2009-02-19
My specs (program-wise) are the same as sunkenpirate's. (I'm using 64-bit flash 10, btw)  I can also watch youtube videos... but not without some issues.  For instance, about half the time, where the video is (for youtube), the audio plays.. but there isn't anything visual (video, player, etc.). Its just a white box... but if I refresh a couple times, it usually comes back eventually.  If not, I have to restart firefox...and occasionally the computer.  But the onion hasn't worked at all for me (always a white box... doesn't even try to play.  the only sign oflife is when the player first 'loads').

---

### Post by shamimkhaliq on 2009-03-21
i think there's a flash issue because there are so many posts about flash in browser problems. to stop the crashing problem i uninstalled all the flash plugins and installed the adobe one because i'd read the problem was caused by adobe not sharing their source code so it's hard for anyone but adobe to write good flash programs. then i had the "works fine for a couple of hours then starts sticking minutes into a movie" problem. so i'm thinking of setting edit>preferences>applications to "download file" hoping i'll be able to watch streaming media okay once it's saved to disk. wish me luck and tell me if you come up with something.

---

### Post by shamimkhaliq on 2009-03-21
omg, that solved it! if flash is making your browser crash, try using adobe's flash plugin, if flash is sticking in your browser, then edit>preferences>set swf & spl to "download file"

---


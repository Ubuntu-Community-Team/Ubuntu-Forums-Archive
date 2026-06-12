---
title: "Unity bar - no indication that Chromium is open"
date: 2011-07-25
forum: Desktop Environments
---

### Post by TBABill on 2011-07-25
I drug my Chromium launcher from "applications" to the Unity bar, placing it right below Firefox. It works fine as far as launching Chromium, but it gives absolutely no indication that the browser is actually open (no triangle to the left to show it's open or to the right to show it's the active window). If I open more than one instance of it, there is no "windows" view of both to pick from. I can't remember what that function is called, but it's when it shows you all the active windows of the program to pick from if you have more than one open.

I couldn't find any other posts on this topic, but if there's a known fix I'd appreciate the help. Still searching on my end via Google and the forum.

---

### Post by TBABill on 2011-07-25
Here's a screenshot showing Chromium open but no indication of it being open in the Unity bar.

---

### Post by mc4man on 2011-07-25
> but if there's a known fix
Not really, can't say I've seen this here or posted. Sometimes though things go south with natty and can be hard to 'fix'

So things I might try - 
Close chromium, remove the launcher icon (right click, uncheck) **then log out and back in.**
Try starting chromium in various ways - if the icon shows up in the launcher as active then r. click on it and enable the keep option. If it doesn't show as active then close out without pinning and try the next

Alt+F2, then start typing in chromium-browser, when the icon shows up d. click on

Open nautilus, browse to /usr/share/applications and d. click on the "Chromium Web Browser" icon

If neither of the above produces an active icon - (single command
```
mkdir -p ~/.local/share/applications && \
cp /usr/share/applications/chromium-browser.desktop ~/.local/share/applications/
```
Then 
```
chmod u+x ~/.local/share/applications/chromium-browser.desktop
```

```
 nautilus ~/.local/share/applications
```

D. click on icon and see...

---

### Post by TBABill on 2011-07-26
I'll give it a shot this evening after work. I didn't think it mattered much until I ran top in a terminal and saw a couple instances of Chromium open but it was not in any of the work spaces. Thanks for the suggestions. I'll try them all and see if they fix the problem. If they do, then it's off to Launchpad to report it.

---

### Post by malspa on 2011-07-26
@TBABill: Those indicators are working here with my Chromium item on the launcher. Using Natty. What you're seeing, is it only happening with the Chromium icon, or with other apps as well? Just curious.

---

### Post by malspa on 2011-07-26
> **TBABill said:**
> I drug my Chromium launcher from "applications" to the Unity bar, placing it right below Firefox.

The way I put the Chromium item into the Unity launcher, instead of dragging it from "applications," I started Chromium, and when its icon showed up in the launcher, I right-clicked on the icon and clicked on "Keep In Launcher." Wondering if it makes a difference if you do it that way.

---

### Post by TBABill on 2011-07-26
Hmmm....not sure if I even tried launching Chromium and then pinning to the Unity bar. I just opened all applications, grabbed it and dropped it on the bar. It could be that the simplest of methods like you mentioned is the easiest fix. It shouldn't behave that way and that'd surely be a bug to report, but at least I could show both ways and how one way works and one does not. Thanks for suggesting....the obvious eluded me!
 
All other apps are working fine. What I haven't tried is to see if the others I dragged to it are behaving the same. I added terminal, Sudoku and a few others. Quick to check and if that's all it takes to get it working it's only a minute or two of time.
 
Thanks again! I'll give it a go when I'm back on my machine this evening.

---

### Post by TBABill on 2011-07-26
Ok, so this is a known bug and was reported to Launchpad [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/772063](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/772063) I have added my own comment to confirm it exists and to show it via screenshot by linking back to the forum.

---


---
title: "Login goes to blank screen, then back to login screen"
date: 2007-09-30
forum: Desktop Environments
---

### Post by HoberShort on 2007-09-30
Heya folks, got a little problem.

All of a sudden today, when I boot up my Kubuntu version of Fawn I get the login screen just fine, but when I put in my username and password, things get hairy. The screen goes black like it normally does for a moment, before popping up the KDE loading screen. Except now it just stays black for a bit, then drops me back to my login screen. 

Console logins work just fine, and it seems to be some kind of error that only happens via graphical login.

Before I shut down last time, I was downloading a file with KTorrent, and it gave me an error about a failure writing to some cache. Sorry I can't give more details, but that's the best I remember it. (If anyone knows where ktorrent keeps its error logs, I'm all ears. The man page is too large for a console login.) 

After that error, I restarted the download, and it said it was Stalled. So I rebooted, and now I can't log in.

I'm using the public releases for everything, so it can't be an issue with KDE 4 (because I don't use it), but I'm sort of at a loss as to where to look. 

I'd be glad to answer any questions I can, and thank you folks working this forum for your well-educated time. And sorry if this has been answered before: it's a tricky one to describe in a search query, and "blank screen" turns up quite a host of results.

---

### Post by Soarer on 2007-09-30
Is it possible that your disk is full?

---

### Post by HoberShort on 2007-09-30
Hole in one. Running a df -h showed 100% disk usage.

After deleting a gig and a half of ephemera, the problem has changed. After entering my username/password, now it gives me a Konsole window on top of the login screen background, which is different from my desktop wallpaper. It would seem to be the screen that usually has the KDE loading animations, except nothing ever loads.

The Konsole window sits there, without any sort of window management. There is no bar at the top of the window with the familiar minimize/maximize/close buttons, and there doesn't seem to be any way to move it. I can run various commands, and even open a browser window, but none have title bars, and alt+tabbing does nothing. 

KDE seems to be choking somewhere.

---

### Post by Soarer on 2007-09-30
Can't help with KDE I'm afraid, I use Gnome. I would be thinking about re-installing the desktop (not the whole OS) as it sounds like something has become corrupt. It may be just your settings though, which will be in your home directory. Try renaming whatever directory KDE uses for settings and re-logging in. I think it will rebuild the defaults, and if it borks you always have the old settings for backup.

---

### Post by HoberShort on 2007-09-30
Hmm, moving the KDE config files didn't change anything. It just recreates the .kde directory and populates it with files. 

Could it be that the KDE files themselves, not the config files, are corrupt? If so, I suppose I'll have to somehow reinstall those. Or perhaps nuke and reinstall.

Hmm, actually, I'm going to go see if I can't download an install disk and see if that has some manner of repair/reinstall function.

Thanks again, Soarer.

Update: I just flattened the install and am reinstalling. May this thread die quietly.

---

### Post by Eothred on 2007-11-19
Thank you, I had the exact same problem (hopefully, moving my music from the home-directory now which were on 100%, and then I will try to re-login). For the second problem you are mentioning, this I think I recognize. I believe you have chosen the failsafe option in your login. Chose normal login method and I think you should be fine (don't remember where the option is, but it's hidden somewhere in the login menu). This solved the exact same problem for me anyway.

Edit: didn't see your last edit. Anyway, could be nice for other people popping into the thread to know what the solution is...

---


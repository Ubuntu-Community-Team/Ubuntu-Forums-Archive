---
title: "Search in &quot;Applications&quot; and &quot;Files and Folders&quot; no longer works"
date: 2011-09-29
forum: Desktop Environments
---

### Post by snr89 on 2011-09-29
Hi guys,

So I'm relatively new to Linux, have only played around and learning the terminal.

I was trying to remove the recent documents as Unity doesn't really have a GUI feature (not that I know of anyway?) to do that.

So upon googling and trying various things, I most likely used more than one suggestion, and removed or over-wrote or disabled zeitgeists activity.sqlite

Basically, the issue right now is when I open up Applications or Files and Folders, the search bar is there but it is not accessible either by clicking or by any typing.

Any help would be appreciated and apologies for the newb question. I've been searching on how to rectify the problem including redownloading application-place for unity and file-place for unity from the software center and also tried to remove and reinstall zeitgeist to no avail (or if that should fix it..if someone can give me a hand on that that would be great). I just don't want to try to use anymore poorly chosen suggestions because clearly I don't know which suggestions to follow! lol.

---

### Post by Copper Bezel on 2011-09-29
Yeah, the search depends on Zeitgeist. Those lenses essentially *are* Recent Documents in another form.

activity.sqlite is a user config file, not a system file, so it won't be affected by uninstalling and reinstalling the software (unless you use the "completely remove" option or --purge from the command line.) If you erase it, Zeitgeist actually should replace it the next time it runs. In fact, that should be true of the whole ~/.local/share/zeitgeist directory.

---

### Post by stinkeye on 2011-09-29
> **snr89 said:**
> Hi guys,
I was trying to remove the recent documents as Unity doesn't really have a GUI feature (not that I know of anyway?) to do that.


With the use of 
[**_[COLOR="DarkRed"]Activity Log Manager[/COLOR]_**]("http://www.omgubuntu.co.uk/2011/05/activity-log-manager-for-zeitgeist-lets-you-blacklist-files-and-apps-delete-your-history-more/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29")
you can manage what zeitgeist logs.

---

### Post by snr89 on 2011-10-01
Aah okay, thanks for the explanation on how to manage logs.. will do that from now on.

However, would you guys have any suggestion on what I could do to fix my problem of the "search" in applications and files not opening??

---

### Post by Krytarik on 2011-10-01
> **snr89 said:**
> However, would you guys have any suggestion on what I could do to fix my problem of the "search" in applications and files not opening??
Have you already tried *Copper Bezel*'s suggestion!?

---


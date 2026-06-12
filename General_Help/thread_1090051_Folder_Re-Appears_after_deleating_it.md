---
title: "Folder Re-Appears after deleating it"
date: 2009-03-07
forum: General Help
---

### Post by xXNI4NI on 2009-03-07
As aforementioned a folder of mine continues to re-appear. It was a music folder that cut/pasted into a more appropriate location but it seems that it is tied somehow. I am running songbird (love it btw) and do not believe it is directly affecting the restoration because i have removed the folder while it was closed, open songbird and played the songs that correspond w/ it (also the song's path is to the cut/pasted path not ~/Desktop). It is not being "restored" by the recycle bin because there are about 9 copies of the folder in there :o any help would be appreciated thank you.

---

### Post by kaibob on 2009-03-07
I believe the folder is created by Ubuntu. You can disable this feature by opening */etc/xdg/user-dirs.conf* and changing *enabled=True* to *enabled=False.*

If you just want to edit the behavior, look at /home/user/.config/user-dirs.dirs

---

### Post by xXNI4NI on 2009-03-07
Ok I did what was asked, I guess it is just sit and wait now. I'll give it about an hour if it doesn't re-appear I'll mark as solved and send you my praise :)
btw to be able to save I had to do the above steps via 'sudo nautilus' permission was denied otherwise.

---

### Post by xXNI4NI on 2009-03-07
I just saw your edit and I am looking at the document right now but due to my lack of experience I have no idea what I'm looking at or even begin to edit. I'm guessing it will be in the line "XDG_DESKTOP_DIR="$HOME/Desktop" but I would not know how to format it to my needs....however this sounds like a generic change to all folders being deleted on the desktop, but I have only had this occurrence happen one despite other folder deletions made on the desktop so I don't know if this is exactly the solution or not?

---

### Post by xXNI4NI on 2009-03-07
not solved

---

### Post by kaibob on 2009-03-07
Glad that worked.

---

### Post by xXNI4NI on 2009-03-07
AHH it just re-appeared can you please walk me through your steps mentioned earlier. *sigh

---

### Post by kaibob on 2009-03-07
* Double check the file /etc/xdg/user-dirs.conf to make sure that it shows enabled=False.

* Check the "Sessions Preferences" applet (system > Preferences > Sessions) to make sure that "Users folders update" is not present. 

* I assume you rebooted.

That's all I know. Maybe another application is creating the folder. Perhaps someone else will have a suggestion.

---

### Post by xXNI4NI on 2009-03-07
Unfortunately I did not reboot for the last attempt.
The Option under Sessions was marked and I removed
Double Checked the file (everything was a go)
and then rebooted
it is removed and I am standing bye
I will give it the full hour now to be sure thanks in advance

---

### Post by xXNI4NI on 2009-03-09
to follow up I gave it ample time to see if all the above worked and they indeed did thank you very much, most definitely solved now. :)

---

### Post by kaibob on 2009-03-10
> **xXNI4NI said:**
> to follow up I gave it ample time to see if all the above worked and they indeed did thank you very much, most definitely solved now. :)
Glad to hear that it's really fixed this time. Just in case someone else has the same issue, it appears that unchecking "Users folders update" in "Sessions Preferences" was what worked?

---

### Post by xXNI4NI on 2009-03-10
yes indeed followed by a reboot of course :)

---


---
title: "So, has anone sent a bug report on cd burn through Nautalus?"
date: 2005-12-13
forum: General Help
---

### Post by ed_d on 2005-12-13
If not, how can I? I and a few others I know have run into the issue of trying to burn a CD from naualus, and it keeps asking to insert a cd-r, even though one is in the burner already. Let me know where to submit the bug, if not done already.
Thanks,
Ed

---

### Post by az on 2005-12-13
I have had this problem if there is anther application (like gnomebaker) running.  I think they both try to share HAL, or something.

If this is not the issue (or even if it is, I guess) the package to file the bug against is
nautilus-cd-burner

and you should file it in bugzilla

bugzilla.ubuntu.com

Check to see if there is already a similar bug filed.

You do not have to be an expert to file a bug, but be descriptive so that the bug is easy to understand.  Describe how you can reproduce the bug.

Most likely it will be maked "Need Info" after it has been received and follow up on the instructions you will be given to help track down and fix the bug.

Keep this thread up-to-date, too to help others participate in squashing this bug.

---

### Post by 5-HT on 2005-12-13
Hi,

Azz gave some great advice on how to submit a bug repor amongst other things in his post.

I'm just wondering if you've been able to burn a cd using nautilus?

If not, there is a quick fix for the meantime:
```

Applications > system tools > configuration editor > apps > nautilus-cd-burner

```
and select "burnproof".

Hopefully, that will get rid of the "Please insert CD" dialogue.

HTH

---

### Post by ed_d on 2005-12-13
K, ticked on "burnproof" tried to burn with nothing running, no joy. I think I will try again after I log out and back in again to see if fixes.

---

### Post by John Jason Jordan on 2005-12-13
[QUOTE=ed_d]K, ticked on "burnproof" tried to burn with nothing running, no joy. I think I will try again after I log out and back in again to see if fixes.[/QUOTE]
One thing I discovered is that Nautilus has only one error message. If anything is wrong it just says there is no blank media in the drive. For example, I selected my entire MP3 collection intending to burn them to a DVD. I selected enough to total about 4 Gb and told it to burn it to the DVD in the drive. Little did I know that Nautilus Burn window ignores the file selection. It will burn whatever is in the window, not just what you select. And that was too much to fit, so I got "insert a blank CD in the drive." Over and over until I figured it out.

But then even worse things happened. Figuring that I'd have to remove the extras from the burn window I selected all but about 4 Gb worth and started to delete them, only to stop just before hitting the OK button. You see, from previous experience, I knew that Nautilus uses the same icon for the file itself and for a shortcut to the file. Plus, there was no indication when I put the files in the burn window whether Nautilus had copied them there or moved them there. If I hit OK it was entirely possible that I would inadvertently delete the entire collection. And I had no backups -- that was what I was trying to accomplish by burning them to DVDs.

So I decided to copy them back to the folder where I got them from. I reasoned that if the file was already there I could just let it overwrite. I selected all but about 4 Gb of the files and went to copy them. Sure enough, on the very first one I got an error message that the file was already there. I told it to skip that file. But then it popped up again for the next file. It appeared I would have to hit the skip button for each file -- 301 of them. There was no Skip All button. 

However, there was a Copy All button. "OK," I thought, "I'll just let them be overwritten -- no harm in that, right?" I hit the Copy All button, at which point Nautilus proceeded to DELETE about 280 of my collection. No backups. About 14 Gb gone forever.

That was the point when I banned Nautilus from my computer. Now I use Konqueror.

Anyway, if it says there is no media it may actually be something else that is wrong.

---

### Post by ed_d on 2005-12-29
Well, I did get a note back from bugzilla, and that nautilus is fixed in dapper. I also discovered something on my home system. When I reloaded a time back, I removed just the cdrom, but kept my dvd-r in. Well, now I can burn in nautilus. I am wondering if having 2 cds is confusing nautilus. All I can say is I am happy now that it works. Will have to try the same thing here at work.

---


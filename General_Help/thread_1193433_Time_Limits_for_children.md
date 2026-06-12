---
title: "Time Limits for children??"
date: 2009-06-21
forum: General Help
---

### Post by markwilliams666 on 2009-06-21
Is there a way I can easily (Linux Dummie here) restrict the time my 6 year old spends on his laptop? I could do with one of the many free Parental Control packages available for windows but as he's running Ubuntu, I don't know of a way to do it.

I want to set him a daily limit of one hour.

Any help would be gratefully received.

---

### Post by nateperson on 2009-06-21
Check out this thread,
[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

There might be something here that can do what you need.

---

### Post by SuperSonic4 on 2009-06-21
On his laptop or on the internet?

If it's the former you could issue a ```
sudo shutdown -hPt 3600
``` or change -t 3600 to one hour afterwards. You could make it into a script and put it into ~/.config/autostart to start on boot.

For the latter you can use the router to change time

---

### Post by michy99 on 2009-06-21
Check out this thread on Timekeepr

[http://ubuntuforums.org/showthread.php?t=887769](http://ubuntuforums.org/showthread.php?t=887769)

---


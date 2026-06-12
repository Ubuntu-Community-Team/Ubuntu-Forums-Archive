---
title: "Evolution data server?"
date: 2009-03-20
forum: General Help
---

### Post by WhiskyChris on 2009-03-20
I've recently installed conky and one of the things it shows me is the cpu usage. I'm running Ubuntu 8.10 on a dual core (2 * 1.86GHz) dell laptop and one of the cpus seems to be working overtime at 100% (and has been since I logged in > 1hours ago.

I had a look in top and the culprit was evolution-data- something so I looked it up with ps and found it to be the following command for evolution data server:

```
/usr/lib/evolution/evolution-data-server-2.24 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=23
```

Can someone help me understand what this process is, if I need it, and why it is being so intensive? Thanks!

PS. I see this is something to do with the calendar in evolution which I know is integrated with the gnome desktop. I don't have many items in the calendar but one thing I am using is a couple of ics webcalendars (public holidays) - is this anything to do with it?

---

### Post by WhiskyChris on 2009-03-20
Just having another look and I noticed that I had set evolution to work offline (as I'm still having email issues... a different problem I'm happy to leave for a different day!) but this obviously didn't agree with the web calendars. CPU usage is back to normal now, though I'm still not really sure why denying access to the internet would cause the full and continued use of a cpu, surely even trying to reconnect to an unavailable resource continually shouldn't cause this due to waiting for some sort of time out before testing the resource again?

Oh well, I've sorted it now, even if I didn't really understand what was happening!

---


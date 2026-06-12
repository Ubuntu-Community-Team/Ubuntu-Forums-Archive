---
title: "self-starting audio stream that shouldn't"
date: 2009-05-23
forum: General Help
---

### Post by 1fastbullet on 2009-05-23
Good Morning.

I am trying to understand and defeat whatever would allow or make a radio station stream start on its own.

**Backgound**: I frequently let a radio station run (stream) over night on my machine and, on the weekends, I usually begin the mornings listening to a different radio station stream.
The stream I allow to run over night is an AM station from Dallas, Texas. The stream I listen to on the weekends is an FM station out of Houston.
It is important to note that I have always started these streams manually and that I have never intentionally used Cron or any other device to start these streams.

**Issue**: For a number of weeks, the Houston station has been starting itself at 7:14 in the morning. This does not occur every day, but it happens frequently. I awake to find the Houston FM station running on top of the Dallas AM station I allowed to run over night. Following the nights when I do not manually start either stream, I often awake to find the Houston FM station has started itself.
Going into the system monitor>processes, I have noticed that each time this Houston radio stream was running, Totem was also actively using resources. But there was never an open window or tab to indicate that Totem was active. I could stop, end or kill Totem and it would effectively stop the stream from running. If the other stream, the AM station from Dallas was running when I killed Totem, the Dallas stream continued to run. In other words, stopping Totem only killed the unwanted stream and left the intentionally run stream to run.

**Steps taken**: As I stated, I have never used Cron. I do not believe Cron is/was the problem. However, I completely un-installed Cron from this machine, solely to eliminate any possible chance that it could be the cause. Uninstalling Cron (as expected) has not prevented the Houston radio station stream from starting itself and , I believe, eliminates it from consideration.
Because the Houston continued to self start after having un-installed Chron, my next effort was to completely uninstall Totem. As I stated, above, each time I found the Houston stream to be running, I also found Totem to be active. I honestly expected to have no further problem with the Houston station after un-installing Totem. I was wrong.

Currently, with both Cron and Totem un-installed, the Houston radio stream still self starts. It now starts within Firefox. It seems that, like an intelligent virus, this thing has migrated from Totem to Firefox.

The only thing I know to do now is go into Firefox's about:config options and try to find what is responsible for this. The biggest problem I face is, I do not know what to look for.

As a final note, I should probably mention that I also have a Firefox add-on called SpeedDial installed on this machine. I have a dozen frequently used sites attached to this SpeedDial app, including both radio station streams. I have not removed the Houston radio station from Speed dial (yet) because I do not think it would be the only site which would self start, if SpeedDial were the root cause. I may be wrong, and maybe I should remove the station from SpeedDial or disable SpeedDial. I do not know.

There is (obviously) something responsible for the starting of this radio stream but I cannot seem to find it. Any help with this mystery will be greatly appreciated.

**Update:** As I stated in my previous post, I have un-installed Totem from my machine. An interesting side effect of having un-installed Totem is that, for the first time, when this Houston radio station tried to self-start yesterday, I got an indication that it was trying to start. The indication came in the form of the screen splash I have attached. By clicking the cancel button, I was able to prevent the stream from opening, but I still do not know what is responsible for it trying to start.

This morning the stream self-started without warning. Once it began, I went to system monitor>processes and found no indication that it was running. Obviously, the stream was again playing through Firefox today, and when I quit and then re-opened Firefox, the stream was effectively stopped. The second attachment is a screen shot of the system monitor, as I found it, when the stream had started itself.

---

### Post by KhurramM on 2009-05-23
It might be a trojan or some type of virus.

What actually happens is that u install or use some software from an unidentifed or hacking site or a virus infected source from a fault causing site. This is my guess only. There might be

What I would do in such a case: It will be better that u reinstall your OS, to remove this issue, permanently.

If u use auto login, remove it.

---


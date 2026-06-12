---
title: "Fresh install 9.04, nVidia 180 = hang"
date: 2009-06-21
forum: General Help
---

### Post by UranUtan on 2009-06-21
Hi,

I just did a fresh install of Ubuntu 9.04 x64. Update Manager is run after install so I assume the system is perfectly up to date.

Admin, Hardware Drivers downloaded nVidia driver #180. My graphic chip is 9300i (integrated in the Asus P5N7A-VM board). This driver is probably bad, the screen hung up after about 5 minutes (or after a low number of mouse movements ?) Pushing Reset button is the only way to restart.

I then downgraded the NVidia drivers to #173. This time no more hang up. But now the windows content is not redrawn. On any application with a scrollbar, as soon as the scrollbar move down and up again, the window content is displayed with lines and unreadable gibberish content. Minimize / Restore, Resize, Maximize ,etc. Any action that redraw the Window refresh the content which become readable as normal. And of course another scroll and the issue appears again.

Also Gedit has lost its graphical element: empty toolabr, empty menu and the content area display nothing. Close / Open Gedit several times, and sometimes it could display something. Or a resize could fix the display.

In other words, the new re-install of Ubuntu 9.04 x64 fixes a fea issues I had before (audio codec) but add new wierd graphical issues. Hope you have a solution.

Thanks in advance.

---


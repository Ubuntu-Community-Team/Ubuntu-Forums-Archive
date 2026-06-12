---
title: "Gnome-panel crash"
date: 2005-06-28
forum: Desktop Environments
---

### Post by EcliptuX on 2005-06-28
Hi,

For the second time, my gnome-panel crash and all my application icons, drawers... disappears ](*,)

I had this error message just after the crash :

[img]http://img181.echo.cx/img181/4011/errorgnomepanel4ca.png[/img]

I am borred to redo all my configuration every time (2 hours !!!).
So, I am looking for the cause of this crash, and the way to restore my application icons, drawers etc.... too.

I try to find the directory where are store my panel configuration (icons, drawers...)
I have found this one : /home/ecliptux/.gnome2/panel2.d/default/launchers
Inside, I have this :
 ```
[ecliptux]@[~/.gnome2/panel2.d/default/launchers]$ ll
total 104
-rwx------  1 ecliptux ecliptux 242 2005-06-22 19:39 bar-0040e14cce.desktop
-rwx------  1 ecliptux ecliptux 212 2005-06-28 16:44 blah-0022a14345.desktop
-rwx------  1 ecliptux ecliptux 206 2005-06-22 19:43 curly-004c40ac74.desktop
-rwx------  1 ecliptux ecliptux 282 2005-06-22 19:41 curly-007df0b70c.desktop
-rwx------  1 ecliptux ecliptux 257 2005-06-22 19:35 eek-0040ae40e2.desktop
-rwx------  1 ecliptux ecliptux 193 2005-06-22 19:57 eek-00ea758180.desktop
-rwx------  1 ecliptux ecliptux 249 2005-06-22 19:55 eek-00f3583283.desktop
-rwx------  1 ecliptux ecliptux 248 2005-06-22 19:49 foo-0031b2d267.desktop
-rwx------  1 ecliptux ecliptux 284 2005-06-22 19:40 foo-005015f7dc.desktop
-rwx------  1 ecliptux ecliptux 249 2005-06-22 19:54 foo-007cfd738c.desktop
-rwx------  1 ecliptux ecliptux 231 2005-06-22 19:38 foo-00c822139e.desktop
-rwx------  1 ecliptux ecliptux 216 2005-06-22 19:44 frobate-004cbabd43.desktop
-rwx------  1 ecliptux ecliptux 227 2005-06-28 18:36 greasy-002d70e82f.desktop
-rwx------  1 ecliptux ecliptux 197 2005-06-22 20:21 greasy-0033b18a20.desktop
-rwx------  1 ecliptux ecliptux 192 2005-06-28 18:37 greasy-00348ff048.desktop
-rwx------  1 ecliptux ecliptux 216 2005-06-22 19:46 hadjaha-00aa9371e4.desktop
-rwx------  1 ecliptux ecliptux 283 2005-06-22 19:47 hadjaha-00e0975305.desktop
-rwx------  1 ecliptux ecliptux 248 2005-06-22 19:53 hammer-00177501fe.desktop
-rwx------  1 ecliptux ecliptux 219 2005-06-22 19:42 hammer-003803626d.desktop
-rwx------  1 ecliptux ecliptux 210 2005-06-22 19:50 hammer-00436f9f45.desktop
-rwx------  1 ecliptux ecliptux 206 2005-06-22 19:49 hammer-008411c8f5.desktop
-rwx------  1 ecliptux ecliptux 214 2005-06-28 15:57 hammer-0089ca130f.desktop
-rwx------  1 ecliptux ecliptux 271 2005-06-22 19:50 hammer-00e2e8b4e8.desktop
-rwx------  1 ecliptux ecliptux 219 2005-06-28 18:37 larry-005f7e2970.desktop
-rwx------  1 ecliptux ecliptux 234 2005-06-22 19:35 moe-00c30e3a8c.desktop
-rwx------  1 ecliptux ecliptux 216 2005-06-22 19:42 moe-00dad166f5.desktop

``` 

I told to myself : "Yes!!!!! All my configuration was store there and I should repair my gnome-panel"
But unfortunately, I don't know how to repair it :(

So if you know why my configuration disappear or how to restore it, please, help me !!!:roll:

Thanks a lot :)

---


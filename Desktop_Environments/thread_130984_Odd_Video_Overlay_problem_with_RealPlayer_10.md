---
title: "Odd Video Overlay problem with RealPlayer 10"
date: 2006-02-15
forum: Desktop Environments
---

### Post by Solon on 2006-02-15
OK, I have an odd problem, I searched the board for solutions but didn't see any. I installed Realplayer using the binary from the Real site, and it installed with no problems. As far as I can tell, the plugin(Firefox 1.0.7) seems to work flawlessly except for one problem, that also is consistant with the standalone player as well. That problem is the fact that the video doesn't draw onto the screen consistantly. OK, for embedded video on webpages, for example on C-SPAN, you see the real logo drawn twice, and the controls, then the buffer green indicator overdraws the video section, it hits 99%, then the video starts playing. The audio is perfect, however the video fails to draw at all, the Real logo as mentioned above doesn't disappear, and neither does the buffer indicator. I did another test by right clicking on the video section, the little "play, pause, stop" menu pops up, but doesn't disappear after you select an option on it.

OK, that gives you an idea of the problem, for the standalone player, it is practically the same, except for the fact that you can resize the window, and that brings about an odd problem. OK, I started a local *.rm file with real player(totem plays it perfectly), anyways, I get a black screen, and the audio plays fine, so I tried resizing it. When I shrink the window, the video starts playing fine, except for the fact that its small as all hell, so I tried stretching it, and what happens is that the window border draws in the video section, and the video stays playing in the top left hand corner, and stretches out, like it should, but doesn't overdraw or update anything but the upper corner. I know this sounds odd, but this problem simply has me stumped. As far as I can tell, this problem is isolated to Realplayer, all my other players(Totem, Mplayer, VLC) play videos just fine. I have no other video problems but this, so I have no clue as to what is wrong.

Here's a screenshot, apparently the screenshot utility cannot capture the video at all on Realplayer, just imagine a that the upper black corner square is where the video is playing.

[[IMG]http://img106.imageshack.us/img106/5811/screenshot23lh.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshot23lh.png)

My Specs are:
OS: Ubuntu 5.10(Breezy Badger)
CPU: AMD AthalonXP 1.25 GHz
GPU: Nvidia Geforce4 MX4000 AGP 8X 128MB
Sound: SB LIVE!

---

### Post by Houman on 2006-12-31
hi there;

I know this was posted a long time ago. But I had the same problem and this is pretty much the only thread that posted the same issue (and no solution). I also had realplayer with video but no audio and the strange video overlay problem but I seem to have fixed this problem and I thought I'd post the solution in case someone else needed it.


All I had to do in Realplayer was go to: Tool-> Preferences -> Hardware: UNcheck the "Use XVideo" option, restart realplayer and it should work hopefully.

regards
Houman

---


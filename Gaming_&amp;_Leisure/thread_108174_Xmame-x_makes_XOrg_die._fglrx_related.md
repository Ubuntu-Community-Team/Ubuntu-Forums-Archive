---
title: "Xmame-x makes XOrg die. fglrx related?"
date: 2005-12-25
forum: Gaming &amp; Leisure
---

### Post by The Warlock on 2005-12-25
Okay, so I've tried the xmame packages inside Breezy Universe (0.83) as well as the more up-to-date packages for Debian Sid (0.101). I'm using xmame-x because I don't like the SDL package (it doesn't run well for some reason and has other problems). Now. Before I started using the fglrx drivers for my video card, xmame worked perfectly. But now, when I start up xmame, my screen goes blank. Everything is still running, and I can hear the game's sound ("this is street fighter alpha 3!", etc) but the screen is dead and nothing I do can bring it back; I need to CTRL-ALT-BACKSPACE to restart X. This happens even if I just start xmame without loading a real game. It happens before it shows the message that it's loading the games. 

What do I do?! Is there any way to fix this? I'm going crazy here!

EDIT: And please don't tell me to use the ati driver instead of fglrx. I need 3D acceleration for other games.

---

### Post by wargames on 2005-12-26
I thought the xmame in breezy universe was version 0.86. Anyway, I tried using the xmame-x also with my ATI fglrx, and it always gave me a blank black screen and then nothing. The only solution I found that worked was to use the xmame-sdl package. I've got it running at full screen and it seems to be ok.

Here is a link to my post on what I did to get it running:
[http://www.ubuntuforums.org/showthread.php?t=104222&highlight=xmame](http://www.ubuntuforums.org/showthread.php?t=104222&highlight=xmame)

The steps are at the bottom of the post.

Don't know if this will help, but it's the only solution I could come up with.

---


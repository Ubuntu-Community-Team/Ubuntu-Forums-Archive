---
title: "Cursor has vanished since upgrade to 11.10"
date: 2012-02-08
forum: Desktop Environments
---

### Post by Jonners59 on 2012-02-08
I upgraded my PC to 11.10 - 64-bit and since then I have lost the  cursor.  Well not literally, I just can not see it.  It appears in some  parts of the screen and when I pass over some of the "switches" on  windows they change shade, but otherwise, it ain't there to see....

It is directly wired in to the mouse socket, not even a USB, not that it  makes any difference.  The video card is a ATI Tech Inc. RS690 Radeon X1200 series

Any help please?

---

### Post by leonhartxian on 2012-02-08
howto delete this XD

---

### Post by leonhartxian on 2012-02-08
we have the same problem too
i use wubi installation
i got a black screen..after applying nomodeset...the window appear but as you mention there is no cursor
what i did is reinstall and viola! i have the cursor...but the screen issue is still there

---

### Post by Jonners59 on 2012-02-09
leonhartxian thanks for the input.

The wubi is quite a different install and it sounds like yours was on the boot screen, this is in the actual desktop.  I have seen bug reports and I also saw a solution for n-videa drives (it was a small addition to the xorg.conf file), but I have not installed a card in this machine, it is using the video build on the motherboard, a Radion.

Maybe the nomodeset is the answer.  Not sure how I can change that.  Don't want to do a new install.?!?!?!?!?!?!?!?!

Any other ideas folks

---

### Post by Jonners59 on 2012-03-13
Fixed by following this:
  	 	 	 	 	 	   [COLOR=#222222][FONT=Ubuntu Mono, Ubuntu Beta Mono A, monospace][SIZE=2]sudo apt-get --reinstall install humanity-icon-theme gnome-icon-theme[/SIZE][/FONT][/COLOR] [COLOR=#333333][FONT=Ubuntu Beta, UbuntuBeta, Ubuntu, B, serif][SIZE=2]If your icons are still not fixed you can also try[/SIZE][/FONT][/COLOR]
 [COLOR=#222222][FONT=Ubuntu Mono, Ubuntu Beta Mono A, monospace][SIZE=2]sudo apt-get --reinstall install gnome-icon-theme-full[/SIZE][/FONT][/COLOR] [COLOR=#333333][FONT=Ubuntu Beta, UbuntuBeta, Ubuntu, B, serif][SIZE=2]You can also try removing/moving [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT=Ubuntu Mono, Ubuntu Beta Mono A, monospace][SIZE=2]~/.icons[/SIZE][/FONT][/COLOR]

Also look at changing the Theme to Radienze

---


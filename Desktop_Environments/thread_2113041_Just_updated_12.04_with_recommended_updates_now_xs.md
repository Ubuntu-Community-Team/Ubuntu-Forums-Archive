---
title: "Just updated 12.04 with recommended updates now xserver won't start at all"
date: 2013-02-06
forum: Desktop Environments
---

### Post by myrrdinoftheforest on 2013-02-06
So after the update, Ubuntu will only start in tty1.  I've tried startx, I've tried sudo start lightdm, I've even tried getting the repository to reinstall fglrx legacy. Nothing has worked. I got desperate and from my laptop downloaded the Ubuntu boot repair cd and ran it's repairs on my desktop, it then gave me a URL     	 	 	 	 	 	   [http://paste2.org/p/2832157](http://paste2.org/p/2832157)
 
If anyone can help me at all any help would be greatly appreciated :)

---

### Post by myrrdinoftheforest on 2013-02-06
Ok, so I figured it out but for the benifit of others here was the fix:

when in the tty1 console, completely remove the proprietary ATI drivers using:

sudo sh /usr/share/ati/fglrx-uninstall.sh 
 sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

Then reboot... it was that simple... the last 2 hours I've been spending on this boiled down to these two lines of code :-P

---

### Post by myrrdinoftheforest on 2013-02-06
So, another update, after rebooting somehow my original profile got corrupted and when I tried to login, it looped me back to the log in screen. Not sure what caused this, but I just logged in as guest, created another admin profile, then deleted the old one. Required a little extra work but a far cry better than reinstalling. On a side note, anyone have any idea how I can unlock the music and picture files from the original profile so the newly created profile can own them and use them?

---


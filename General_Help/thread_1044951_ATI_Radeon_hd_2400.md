---
title: "ATI Radeon hd 2400"
date: 2009-01-19
forum: General Help
---

### Post by Syroth on 2009-01-19
Hello all, 

I have googled and looked through these forums but have not found anything useful, just to throw that out there, so that is why im posting. Of course if this has already been covered please link me.

My friend just put on ubuntu 8.10, he has a Dell Inspiron 530 , the wireless is a broadcom BCM4328 . 

The issue is two fold, First, his display works, but it seems like ubuntu thinks his monitor is four times as big as it is, and it shows the top left quater of the screen. As in , the view is super zoomed. 

From what i can tell via google, the latest fglrx drivers should resolve the issue, but then i come to the problem that his wireless doesnt work either , and i cant get a wired connection to his computer. So, i need help in downloading and installing either driver. If i can see properly then i can use synaptic to install the wireless, or something. Or if i have the wireless working i can use a cmd line and apt-get the video drivers,

Im not sure how to do either off hand and i have been hunting a while so i figure posting will help resolve the issue the quickest and with most ease. I'm not a guru or anything but im not new to ubuntu either, and any help will be greatly appreciated  thanks!

---

### Post by Yellow Pasque on 2009-01-20
Press Ctrl+Alt+F1 to get to a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf
```
Now you should see a section like the following. Add the Subsection Display part if it's not there. The key is to use the Virtual option like shown below (with the resolution you want) to fix the super-size desktop.
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		**Virtual	1680	1050**
		Modes		"1680x1050@60"	
	EndSubSection
EndSection
```
If you're not comfortable with nano, use a LiveCD to fix your xorg.conf. The change won't take effect until you restart the X server.

---


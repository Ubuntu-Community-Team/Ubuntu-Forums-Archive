---
title: "refresh rate"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Sophotect on 2005-10-25
i installed ubuntu and i want to increase my refresh rate but i only get one option (60hz). 
Any help is appreciated

---

### Post by darius_underhill on 2005-10-25
[QUOTE=Sophotect]i installed ubuntu and i want to increase my refresh rate but i only get one option (60hz). 
Any help is appreciated[/QUOTE]

im having the same problem with my laptop.  But when I used to have hoary installed i can set it to 70... help please!

---

### Post by SickTwist on 2005-10-25
The problem is that Ubuntu cannot detect the horizontal and vertical sync frequencies that your monitors use. This consists of two ranges that are highly dependant on the monitor that you are using (if you enter the wrong range, it could mess up the monitor). Ubuntu uses a smaller, more conservative range that is less likely to damage a monitor but results in a slower refresh rate.

The fix is to edit /etc/X11/xorg.conf. Open a terminal and type this:
```

sudo gedit /etc/X11/xorg.conf

```
Find the monitor section. It starts with

**Section "Monitor"**

and ends with

**EndSection**

Add the following two lines anywhere inside the monitor section:
[B][INDENT]HorizSync       30-82
VertRefresh     50-85[/INDENT][/B]
[COLOR="Red"]Important[/COLOR]: The ranges above (30-82 and 50-85) are specific to my monitor. You need to find out what your monitor's horizontal sync and vertical refresh rates are. This might be in the manual that came with your monitor/laptop. You may have to search google with your monitor's manufacturer and model number or you might have to look on the website of your monitor manufacturer to see if it is listed there (or available as a download). I cannot stress this enough:
[B]
[COLOR="Red"]If you do not use the correct numbers you risk damaging your monitor.[/COLOR][/B]

Once you have added these two lines, save the file and restart X. (ALT+CTRL+BACKSPACE does the trick). Your monitor will now use the highest refresh rate that it can for your current resolution. If it is still too low, you can make it go higher by using a lower resolution (ask if you need help with that).

---

### Post by ezze66 on 2007-10-12
hi there!
thanks for your advise. it helped.
i changed my xorg.conf with the specifications of my monitor
Syncmaster 591s

just one more question.
how can i see at what rate my monitor is really working at?
when i try to change the resolution to 1024x768 the only refresh rate available is 61 Hz
at 800x600 the only refresh rate available is 86Hz

---

### Post by gcbzzzz on 2007-10-13
Since my Feisty install, every front end tool to detect monitor refresh rate fail.

I just installed Gutsby, and things got worse. Now i have 3 tools in the System menu to choose from, and all of them screws my refresh rate.

I have a Philips 109B. In windows it's automatically detected as such. Under ubuntu it used to have the settings detected correctly, besides the model, until Feisty.

Now, it detects the resolution allright, but limits me to really low refresh rates. In windows, i can get 1600x1200@75Hz.

+ System > Preferences > Screen Resolution (NOTE: menu names may not be accurate since i'm translating from memory, using other language now)
It shows me only all resolutions my board is capable, even the wide screen ones. But any resolution besides 1280x1204 only allows 65Hz.

+ System > Preferences > Monitor Settings (I do not recall having this tool in Feisty. Also, in Gutsy, the name is not translated, still in English).
This one opens with a warning about my monitor not being in the database.
When i try to send the ddccontrol output by email, it generates lots of errors. But i sent anyway. Doubt most users will manage to capture the output with that message. Let alone that it does not mention you root access, also it has 3 commands colapsed in one line.

+ System > Administration > Screens
New in Gutsy. This one at least allow me to select a monitor from a list. I select, choose resolution, exit. and after a reboot, bang, i`m again with a "generic" monitor selected and 60Hz...

This is all the same if i write my xorg.conf by hand. Any way to completely remove those automatic monitor detections?

---


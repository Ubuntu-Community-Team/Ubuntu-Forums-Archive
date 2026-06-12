---
title: "Font bug?? I don't know what to do"
date: 2009-06-08
forum: General Help
---

### Post by s4stevo on 2009-06-08
I was looking at ubuntu and I liked everything I saw so I installed it on my desktop to try it out. After installing it everything works fine but all the letters are messed up. I'm not sure how to describe it other than it looking like the pixels are messed up or something. I tried changing the font and restarting my desktop several times. None of this worked so I don't know what to do...

---

### Post by Pork_Samichez on 2009-06-08
If you right click on the desktop, assuming you're using gnome, and select "change desktop background"  there will be a tab called Fonts which gives you options for setting the font rendering for LCD screens or CRT screens.  Did this help?

---

### Post by s4stevo on 2009-06-08
No it didn't help anything else?

---

### Post by Pork_Samichez on 2009-06-08
Are you using an LCD screen or CRT?  It might be configured with the wrong resolution.  Have you installed any graphics cards drivers for NVIDIA or ATI aka proprietary hardware drivers?

---

### Post by YldGuy on 2009-06-08
> **s4stevo said:**
> I was looking at ubuntu and I liked everything I saw so I installed it on my desktop to try it out. After installing it everything works fine but all the letters are messed up. I'm not sure how to describe it other than it looking like the pixels are messed up or something. I tried changing the font and restarting my desktop several times. None of this worked so I don't know what to do...

A screenshot would help us to see what exactly are you talking about.

---

### Post by s4stevo on 2009-06-08
I took a screen shot how do i put it on here for you to look at? and its a crt

---

### Post by cariboo on 2009-06-08
Click the new reply button, then go to the advanced editor, scroll down and you will see a Manage Attachments button, click that.

---

### Post by s4stevo on 2009-06-08
ok I uploaded a screen shot

---

### Post by YldGuy on 2009-06-09
looking at the screenshot, it seems the 'a', 'b', 'n' and 'p' letters in firefox are distorted. The 'PM' looks like it has a distorted 'P'. Which font did you use btw? I suspect a corrupt font. OR does it happen with every font you use?

---

### Post by QIII on 2009-06-09
Try this . . .

Go to System -> Preferences -> Appearance.  Click the Fonts tab.

Try changing the Application Font to something vanilla like Sans (if it's not already set there) and see if that helps.

Also, try changing the font in Firefox.  Edit -> Preferences -> Content.  Look for Fonts and Colors.  Set it to something vanilla like serif.

---

### Post by s4stevo on 2009-06-09
yeah the font is messed up everywhere I just used firefox to show a bunch of letters at once since I was already on that page

---

### Post by YldGuy on 2009-06-09
what about the vanilla fonts that comes shipped with ubuntu? i think its more of a corrupt font.

---

### Post by Zoandar on 2009-09-29
Hi,
I was reading this because I am having little black boxes replace certain letters running Ubuntu 9.04 on my Sony VAIO PCG-R505DL notebook. The font starts out clear, then slowly the letter "e" will start to get a gray box behind it. Eventually the box turns darker to complete black, and then other additional letters will catch the "contagion". It is happening both on the LCD screen and on the attached external VGA-cable connected CRT, which is echoing the same screen. 

However, I tried your suggestion and switched to "Sans" font for each setting, with Window Title set to Bold Sans, and all the little boxes instantly disappeared! Thanks!!!

However, as I was typing this, the corruption returned. So I am not sure whether maybe a restart will help. 

I should mention that before I started this Ubuntu project, I was working on creating a copy of the "Ultimate Boot Disc for Windows" and through a lot of research when that didn't work on the notebook, I learned about the Intel 830M family of graphics processor using what Intel's update website calls "manufacturer-specific drivers". Sony hasn't updated them since 2003, and Intel advises NOT to try to use a generic driver for this notebook. 

I was able to learn how to extract the notebook's current drivers and swap them for the newer Intel 8.xxx drivers supplied with the ISO-making software for that boot disk, and that allows the disk to run on this notebook. So I suspect the underlying cause of this problem discussed here will be the same one. That being, the driver in use is the wrong driver for this notebook's graphics card.

I found some information on how to edit the Samba.conf file to try to help, but I can't figure out how to do that. When I edit the file and try to save it, I am told I don't have permission. ( Permissions on WinXP were one of the factors driving me to Linux.) If you could tell me how to circumvent that issue, I would appreciate it! I have 2 things I want to try that I found here on the forum, but each requires such an edit and the files won't let me edit them. I have been looking for a post on how to edit a conf file, but couldn't find one. 

Zoandar

---

### Post by FunkyRes on 2009-09-29
Another possibility is a corrupt font cache.

Try the following:

/usr/bin/fc-cache
sudo /usr/bin/fc-cache

Log out and log back in.

---


---
title: "Screen Display (Dash menu) Whats going on?"
date: 2014-08-15
forum: Desktop Environments
---

### Post by Richard Carlson on 2014-08-15
I've posted this now for several months with no response or indication this problem is universal. The dash menu on the left side of my laptop screen changes from the initialized state in Screen1 to the view shown in screen2 after about 10 seconds. I cannot see the whole menu bar as seen in screen1. What is the problem here? Is this a software or hardware issue?  This laptop uses a generic Intel video driver chipset ( which is installed . . . v1.06 I believe is the latest. This is one problem that makes me want to completely dump Gnome altogether. Any help would be appreciated. 


Rich

---

### Post by WB0HYQ on 2014-08-15
It almost looks as if your screen resolution changes to a slightly lower value in picture 2.  Check what your resolution is before the change and afterwards.

Bill

---

### Post by Joeb on 2014-08-15
If you go into the settings screen and go to displays, does the resolution shown match what your monitor is supposed to be?  It's hard to tell because the two pictures are not from the same distance and angle, but with the way it extends off the bottom of the screen it looks like it thinks there are more pixels.  Also, have you created an x.org file or are you using the defaults?

---

### Post by Richard Carlson on 2014-08-16
Laptop screen size is 15"
Aspect Ratio is 16:10
Resolution: 1280 X 800 (16:10)

This is what my laptop says on both screens (i.e. screen1 and screen2)for both of my photo's I submitted as attachments. The Menu bar (dash)  is way over magnified in size as seen in  screen2. This 1280 x 800  is the default display for this Gateway Laptop. Drives me nuts when half of the menu (dash) disappears from view off the bottom of the screen out of view. If it would stay the same size as in SCREEN1 that would be the appropriate way for it to act in my opinion. Something tells me it's a software issue that needs to be addressed. I guess I could just run 'KDE' in its place and that would solve this issue but I think I'd prefer Gnome because of it's simplistic approach and noncluttered workspace. 

Rich

---

### Post by Richard Carlson on 2014-08-16
I formatted my laptop drive last night and installed Mageia 4.1 Gnome. Here comes the rub. I don't have this dash menu-bar issue with Mageia. Why?  Maybe I'm the only person with this laptop that has this issue. Strange as it may seem this is where it will all stay for now. I've posted this issue for some time now in the forums and still no resolution to this issue. It baffles me how some distro's can have specific problems which may be hardware or software related and others not so. I only hope some of the developers read some of these posts and understand the frustrations some of us feel out here. Thanks for all the responses. BTW I had Fedora 20 Gnome on this laptop months ago. . . it too had this problem and was also experienced by another individual who had this issue. Have they fixed this problem there? Can't say. . . I'll have to wait to Fedora 21 comes out. Time to move on. 

Thanks for the help. 

Rich

---

### Post by Joeb on 2014-08-16
I'm glad it's working for you with Mageia. It still sounds like the wrong resolution for your display. Is Mageia also reporting 1280x800? From what you describe, it sounds like the correct resolution came up in Ubuntu and Fedora and then changed for some reason. Since you don't have it installed anymore, it won't be possible to troubleshoot it further.  If you install Fedora 21 and the problem is still there, verify that the display on the laptop actually is physcally 1280x800 and even if the display setting says it is 1280x800, reset it to that.  It sounds like that for some reason, the window manager is getting confused.

Anyway, I'm glad you now have a functioning Gnome desktop.

---

### Post by Richard Carlson on 2014-08-19
Fedora 20 has the same issue. . . come to find out it's this crappy Intel chipset 965GM  used for the video on this  cheap laptop. I installed the latest Intel drivers and still the same issue. So I opted to just install KDE over Gnome and run KDE instead. No big deal. . . . I'll never again buy a laptop especially with any Intel video chipsets in them again. I'll get one with a nvidia or ati video card instead and deal with their issues. Might have to pay more but we will see. . . actually my desktop system is what I really prefer for all my computer work. 

Thanks for all the help. 

Rich):P):P

---


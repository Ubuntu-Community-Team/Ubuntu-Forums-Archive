---
title: "Font issue on Dell Dimension 4550.."
date: 2006-09-15
forum: Desktop Environments
---

### Post by WipeOut on 2006-09-15
Hi,

I have just setup Ubuntu 6.06 for the first time on my Dell Dimension 4550 PC.. There seems to be an issue with the fonts or something and also the resolutions I can set the screen to..

The font issue is that in certain areas the font is HUGE.. For example when logging in.. As I enter my name in the name box each letters are massive and so all you see are thick lines.. Then once its going through the login process and shows that startup box that says things like "Window Manager" and "Nautilus", the text on there is huge too..

Then the resolution issue.. I have an ATI rage pro ultra card.. When I looked in device manager the only thing that looks like it relates to the graphics card says "vga16fb.0".. Not sure what thats all about.. I would like to get at least 1024x768 resolution but right now all I can get is 640x480 or 800x600..

Af anyone can point me in the right direction to resolve these issues I would be greatful..

---

### Post by xmas1888 on 2007-04-06
Yeah, this is a problem that is happening regularly with me with the past couple of versions of Ubuntu. With Dapper, updating the graphics driver to the proprietary nvidia one fixed it for me, but now with feisty that's not happening. Someone said that changing the font size number in the human.xml file in /usr/share/gdm/themes/Human will fix the login font problem. This font issue also appears on the login options screen, which someone said they fixed in GTK, but not sure what they changed, trying to find that out. Actually had this happen in openSUSE with the ALL the menus and icon fonts. Trying to figure this out so I can actually use openSUSE as well as ubuntu.

---


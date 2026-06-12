---
title: "Seperate X, Multi head, Different Window Managers in Xfce."
date: 2011-07-16
forum: Desktop Environments
---

### Post by Kashi Commodore on 2011-07-16
OK. What I'm trying to achieve here is a dual monitor (multi head?) setup with separate X sessions on each. Each X screen would have a different window manager/DE but they share one keyboard and mouse. I'm hoping to use Xfce (or maybe KDE) on one screen and another (dunno which) WE on the other smaller screen (Openbox?)

I have installed Xubuntu successfully, and it recognizes my dual screens. I installed the proprietary NVidia driver and enabled 'Separate X' in the settings, which also works just fine. I am left with two seemingly separate Xfce sessions, one in each screen, that I cannot drag windows between and have separate wallpaper. I can set up separate panels for each screen etc. This works.

My xorg.conf file has 2 screen sections, 2 device sections, and 2 montior sections, with 1 'Serverlayout'. Switching to using 2 'Serverlayouts' left me with one blank screen.

When I login via GDM, it has one login box on the main screen. The wallpaper here is the same on both screens. Switching to using XDM meant I had one blank screen at login, and no way to choose my session - and it promptly logs into Xfce dual-head quite nicely.

What I'm asking here is:

[LIST=1]
[*]How do I get from here to separate window managers? Have Xfce only use the main screen, and get Openbox or something on my second screen?
[*]Do I need to have 2 separate login prompts? If so, thats fine..... as long as I can still share one KB/Mouse between em :)
[*]I know I cannot move windows between screens in this setup, but can I share a clipboard?
[*]Is any particular WM/DE incompatible with this setup? I know KDE seems to have shaky multihead support (cannot run 2 KDE's at the same time, I read) and Gnomes multi head setup seems to be under debate now everyone switched to Unity/Gnome 3 (which I hate - hence Xfce) - In short, is there anything to avoid?
[*]What happens when I switch to a console (CTRL ALT F1) - will I be able to see what I'm doing on the single screen? (Obviously, I know consoles won't multi head)
[/LIST]
Without trying to sound sarcastic, I do NOT want TwinView/Xinerama - I've tried these sucessfully but that thats not what I'm aiming for. Thanks! I also need to use only one keyboard and mouse - many directions I've been given point to 'Multi SEAT' setups, using different input devices.

I've searched these forums (and many more forums) but the number of seemingly antiquated answers (it seems GDM 2.30 is incompatible with instructions for GDM 2.20 etc) and different setups to what I require (multi seat, different keyboards, GNOME based multi head etc) means I have lots of different instructions that don't seem to work with each other. :(

So sorry if I'm asking something already asked - please feel free to point me to the right HOW-TO and I promise never to shame myself again :P

Thank you very much for clarifying things for me, and pointing me in the right direction!

EDIT: Derp, perhaps I should add I am using Xubuntu 64bit 11.04 for this, with an Nvidia 8800GT Graphics card, with one monitor (LCD panel) on VGA (1920x1080x32 - Primary Monitor) and one on DVI (1366x768x32 - Second Monitor).

---

### Post by aphatak on 2011-07-19
Why would you want to settle for one screen per environment - what if you could have both the environments using both the screens and being able to flip between them at will?  If this will work for you, the way to do it would be to start a separate x-session - your first graphic desktop shows when you key ctl-alt-f7; you set the second to show up with ctl-alt-f8.  With this approach, you are not limited two two environments on the same computer; you could have up to six environments, with a mix of local sessions and remote (Linux running on another computer in the network) as you wish.  If you need a howto, let me know and I will post one.

If you absolutely must have two environments visible at the same time, I would try VirtualBox.  That way, you could have two, or three (or four or more!) independent environments and again flip among them at will.

---


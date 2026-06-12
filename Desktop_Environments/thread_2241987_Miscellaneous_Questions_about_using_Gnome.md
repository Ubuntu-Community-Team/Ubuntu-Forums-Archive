---
title: "Miscellaneous Questions about using Gnome"
date: 2014-08-29
forum: Desktop Environments
---

### Post by Robbyx on 2014-08-29
I think gnome 3 on 14.04,  is wonderful, especially on a double monitor. I have some questions:

1. There is a docky type panel on the left  of the monitor. It lists some applications. It does not open up unless I chose applications via either the mouse at the top left corner or clicking on the applications menu. 
     a. Can I add the mouse effect area to more than just the top left corner to the screen, so that other edges also bring    up the applications screen?

2. I have done some thing wrong with the colour scheme but do not know what. The result is that I can hardly read the search box in the application screen. The box is so faint it is unreadable. Does anyone know how to correct it?

3. If I hit the bottom of the screen the apps show. Does anyone know of a clickable icon that will open the apps panel instead of moving the mouse to the bottom of the screen? This way it will only open because I want it to open, not because I have stayed to the bottom of the screen. 

4. Logitech mouse control. This is a general problem. I find it quite hard to accurately place the mouse on the screen. Is there a program that offers better control of the G100 mouse movements?

Robin

---

### Post by Joeb on 2014-09-01
> **Robbyx said:**
> I think gnome 3 on 14.04,  is wonderful, especially on a double monitor. I have some questions:

1. There is a docky type panel on the left  of the monitor. It lists some applications. It does not open up unless I chose applications via either the mouse at the top left corner or clicking on the applications menu. 
     a. Can I add the mouse effect area to more than just the top left corner to the screen, so that other edges also bring    up the applications screen?

2. I have done some thing wrong with the colour scheme but do not know what. The result is that I can hardly read the search box in the application screen. The box is so faint it is unreadable. Does anyone know how to correct it?

3. If I hit the bottom of the screen the apps show. Does anyone know of a clickable icon that will open the apps panel instead of moving the mouse to the bottom of the screen? This way it will only open because I want it to open, not because I have stayed to the bottom of the screen. 

4. Logitech mouse control. This is a general problem. I find it quite hard to accurately place the mouse on the screen. Is there a program that offers better control of the G100 mouse movements?

Robin

1) If you go to extensions.gnome.org, you will find all sort of extensions to modify the behavior of how gnome-shell works.  There is one called "Dash to Dock" that will make the dock visible when it isn't covered by a window, and if it is covered, moving your mouse to the left edge will make it appear.  There are hundreds of extensions to allow you to customize gnome-shell, so check it out.

2) You might be able to run the gnome-tweak-tool to reset your color and themes.

3) Going to the bottom of the screen usually shows messages. Could you describe your problem a little more detailed?

4) If you go to the settings panel, or just go to the shell and type mouse, you can get to the mouse and trackpad settings. You should be able to adjust your settings there.

Joeb

---

### Post by Robbyx on 2014-09-02
> **Joeb said:**
> 1) If you go to extensions.gnome.org, you will find all sort of extensions to modify the behavior of how gnome-shell works.  There is one called "Dash to Dock" that will make the dock visible when it isn't covered by a window, and if it is covered, moving your mouse to the left edge will make it appear.  There are hundreds of extensions to allow you to customize gnome-shell, so check it out.

2) You might be able to run the gnome-tweak-tool to reset your color and themes.

3) Going to the bottom of the screen usually shows messages. Could you describe your problem a little more detailed?

4) If you go to the settings panel, or just go to the shell and type mouse, you can get to the mouse and trackpad settings. You should be able to adjust your settings there.

Joeb

1) Dash to dock: I have installed. Thank you. What I am trying to do is to see the docks including docky when I am in activities mode. Do you know how  to do it? Dash to dock does not seem to allow me to see the docky panel when I have clicked on the activities button.

2) One of the colours is supposed to be transparent but I have not worked out which one. What doesn't help is that Elegance colours can not be saved. What do you use instead?

3) At the bottom of the screen is a pop up area showing currently loaded programs. It would be great to be able to open that area with an icon rather than by mouse movement into the region. I find I stray into the area and open it up when I do not wish to do so. 

4) Slowing the mouse down has made all the difference. Thanks.

Robin

---

### Post by Robbyx on 2014-09-02
5) I have also noticed that the workspaces of the overview mode only show one screen not both. Do you know how to correct it?

R

---

### Post by Joeb on 2014-09-03
> **Robbyx said:**
> 1) Dash to dock: I have installed. Thank you. What I am trying to do is to see the docks including docky when I am in activities mode. Do you know how  to do it? Dash to dock does not seem to allow me to see the docky panel when I have clicked on the activities button.

2) One of the colours is supposed to be transparent but I have not worked out which one. What doesn't help is that Elegance colours can not be saved. What do you use instead?

3) At the bottom of the screen is a pop up area showing currently loaded programs. It would be great to be able to open that area with an icon rather than by mouse movement into the region. I find I stray into the area and open it up when I do not wish to do so. 

4) Slowing the mouse down has made all the difference. Thanks.

Robin


1) I don't use docky, so I won't be much help there, but since the dash is designed to be full screen, it seems unlikely that you will have a docky dock and a gnome-shell dash simultaneously.  I vaguely recall an extension that showed the gnome dock on the bottom of the screen, if that is what you are after. I don't recall the name of the extension or what version of gnome-shell it was for.  Personally, since my screen is wider than it is tall, I prefer the side of the screen. I was doing that even before Gnome3 and Unity went that route.

2) I tend to use the default theme, Adwaita, with gnome-shell. While it is not totally to my liking, I have found that most other themes have problems. I believe this is because of changes made to gnome-shell between different versions and the various theme makers haven't caught up. You might go to the site for Elegance and ask for specific help there.

3) The bottom is the message area. I actually use an extension called topicons (I think) so that the icons there display in the top panel (things like dropbox, etc.)

4) no problem, glad it helped.

So you know, you can also get specific help from ubuntu-gnome's mailing list and/or irc channel.  Instructions for both can be found on the ubuntugnome.org contact us link. The also have a facebook page.

---

### Post by Joeb on 2014-09-03
> **Robbyx said:**
> 5) I have also noticed that the workspaces of the overview mode only show one screen not both. Do you know how to correct it?

R

You might check the setting in gnome-tweak-tool to see how the workspaces are configured (automatic, only 1, etc.)

---

### Post by Robbyx on 2014-09-03
I am trying to get back to the Adwaita default theme. Using Gnome Tweak I have switched off the global dark theme. Changed Window, gtk+, cursor to Adwaita. Icons I have as Hicolor. Shell theme has a warning triangle next to it with no option in the box. Do you know what I should do next?

Worspace creation is set at static, No of workspaces 2, On primary display is off.

Robin

---

### Post by Joeb on 2014-09-03
> **Robbyx said:**
> I am trying to get back to the Adwaita default theme. Using Gnome Tweak I have switched off the global dark theme. Changed Window, gtk+, cursor to Adwaita. Icons I have as Hicolor. Shell theme has a warning triangle next to it with no option in the box. Do you know what I should do next?

Worspace creation is set at static, No of workspaces 2, On primary display is off.

Robin

To change a theme, you need to go to the extensions tab in gnome-tweak-tool and turn on the user themes setting. Then you can change the shell theme on the appearance tab. After changing the theme, I usually turn the extension back off.

The reason you don't see the workspaces is because primary is off. You are telling the system to show one workspace on your primary display and the other on your secondary display. 

After making the changes, you may need to restart the shell by logging out and back in or hit alt-F2 and type the letter r in the command box.

---


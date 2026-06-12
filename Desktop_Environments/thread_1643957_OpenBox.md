---
title: "OpenBox"
date: 2010-12-12
forum: Desktop Environments
---

### Post by yellowsn0w on 2010-12-12
Hello,

This might be a very noobish question and it might also be already solved in somewhat way, so if the mods want to force me to an intense research, go ahead ;)

All I know about openbox is that it's not a desktop environment, but a window manager, that it's extremely customizable and that there's awesome themes out for it.

So, I don't want to replace my current GNOME environment on 10.10, I want (if possible) an independent "desktop enviroment", like KDE, to run beside GNOME (so I can choose from the login-screen).

Also, I'd like to know if I can just install a theme for openbox via something like the "Appereance" settings in GNOME or, if not, how I can get my future openbox to look like (e.g.) this - [http://sunjack94.deviantart.com/art/End-Of-Light-175941917?q=gallery%3Alinux-users%2F23908865&qo=21](http://sunjack94.deviantart.com/art/End-Of-Light-175941917?q=gallery%3Alinux-users%2F23908865&qo=21) .

Looking forward to you help!

---

### Post by Rodney9 on 2010-12-12
[http://openbox.org/](http://openbox.org/)

When you install Openbox from the software manger it will add it to your login choice.

For the End of light theme download it -  [http://www.deviantart.com/download/175941917/End_Of_Light_by_SuNjACk94.tar](http://www.deviantart.com/download/175941917/End_Of_Light_by_SuNjACk94.tar)

and extract it, Openbox themes are stored in one of the following places:

    * System-wide themes are installed in /usr/share/themes.
    * User-specific themes can be installed in ~/.local/share/themes or in ~/.themes. 

learn more [http://openbox.org/wiki/Help:Themes](http://openbox.org/wiki/Help:Themes)

---

### Post by yellowsn0w on 2010-12-12
Thanks for your answer, that looks pretty easy.
I'll give it a try and excuse my noobish question again :D

---

### Post by 3Miro on 2010-12-12
I don't know if you know this, but you can run the OpenBox window manager in place of Gnome's window manager (compiz or metacity, depending on whether you have visual effects enabled).

You can test it with Alt + F2 and then type:
```
 openbox --replace 
```
or you can make that permanent by following this:

[https://wiki.archlinux.org/index.php/Openbox](https://wiki.archlinux.org/index.php/Openbox)

---

### Post by yellowsn0w on 2010-12-12
That's also interesting 3Miro, although I'm amazed by the speed of openbox standalone :D

Anyways, I applied the End of Light theme, at least as far as the GNOME appearance settings were going anyways...
Regarding the size of the Theme, I must say, I didn't expect it to look exacly like the screenshot, but... well, I'd like to at least have a taskbar or anything ;)

I'd appreciate any help.

---

### Post by snowpine on 2010-12-12
> **yellowsn0w said:**
> That's also interesting 3Miro, although I'm amazed by the speed of openbox standalone :D

Anyways, I applied the End of Light theme, at least as far as the GNOME appearance settings were going anyways...
Regarding the size of the Theme, I must say, I didn't expect it to look exacly like the screenshot, but... well, I'd like to at least have a taskbar or anything ;)

I'd appreciate any help.

OpenBox does not have its own taskbar. You can use it with the Gnome Panel by selecting Gnome+Openbox from the login screen (or openbox --replace as suggested by a previous poster).

---

### Post by yellowsn0w on 2010-12-12
Thanks for the answer,
so the mentioned DeviantArt poster is using GNOME (or whatever) too?
Or what exacly is GTX metioned in that post?

Edit: Choosing GNOME/Openbox from the login screen brought me to my usual GNOME desktop, I didn't recognize any changes and the window manager was obviously nautilus...

---

### Post by snowpine on 2010-12-12
> **yellowsn0w said:**
> Thanks for the answer,
so the mentioned DeviantArt poster is using GNOME (or whatever) too?
Or what exacly is GTX metioned in that post?

I don't know, but it appears he/she responds to comments if you want to ask there. :)

Since Openbox has no built in panel, you can use any one that you like. Personally I use one called tint2 (it is the default for the distro I use, CrunchBang).

---

### Post by yellowsn0w on 2010-12-12
Okay,
before asking that deviant about his panel, I'd like to know how I can add any panels to openbox...
Feel free to anwer, I'm out for today :D
Thanks again for your help so far!

---

### Post by m_duck on 2010-12-12
If you are in an Openbox only session, you can start a panel just by running it, e.g. from a terminal:```
gnome-panel &
```or```
tint2 &
```There will be no panel to begin with as Openbox does not include a panel. Being a window manager only, it includes very little (i.e. no way to set wallpaper on its own). This is a good thing as it allows you to choose the programs that *you want* to do everything. So, for example, I typically use feh to set the wallpaper, but alternatives could be nitrogen or simply xsetroot for example.

I'm not sure how Ubuntu is set up to run Openbox from (presumably) GDM, but I would imagine it is set to run an openbox-session. If this is the case, you could add **gnome-panel &** to ~/.config/openbox/autostart.sh to have it automatically run when you log in.

Apologies if I've jumped some steps...

[Older, but still very relevant reading for Openbox](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by uriel1998 on 2010-12-13
> **m_duck said:**
> If you are in an Openbox only session, you can start a panel just by running it, e.g. from a terminal:```
gnome-panel &
```or```
tint2 &
```

This, plus the rest of what is said there, works for me.  I have yet to get GNOME/Openbox to work - but each works wonderfully independently for me.

Relevant (and customized) bits of my autostart.sh to give you some ideas are below.  It is NOT the entire file, FWIW:
```


#for tweetdeck, etc.
export GNOME_DESKTOP_SESSION_ID="openbox"
#because I have deleted the wrong thing twice now.
export LD_PRELOAD=/usr/local/lib/libtrash.so.0 &

#Gnome stuffs
# Make Nautilus use spatial mode, should start-up quicker.
gconftool-2 -s -t bool /apps/nautilus/preferences/always_use_browser true &
# Make Nautilus show the advanced permissions dialog 
gconftool-2 -s -t bool /apps/nautilus/preferences/show_advanced_permissions true &
# Disable Nautilus desktop.
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false &
# Do not let Nautilus set the background image.
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false &

dropbox start -i &
nm-applet & 
bluetooth-applet &
gnome-power-manager &

#compositing
xcompmgr &

#sets background
nitrogen --restore --set-tiled
tint2 &

# replaced by synapse
#gnome-do &
synapse --startup &

xautolock -time 15 -locker "gnome-screensaver-command -l" &
parcellite &
conky -c .conkybar &
tilda &


```

---

### Post by yellowsn0w on 2010-12-13
Thanks for the answers guys,

As the gnome-panel itself in openbox is as "slow" as it is in gnome, I installed tint2.
Now, I didn't try any autostart changes yet because I'd like to know how the tint2 panel is costumizable or even brought to further function. Everything it does now is showing the time and tasks. It disappears on right-clicking...

Anyways, I actually just want a lightweight alternative to gnome. It runs perfectly fine but as I need to be very productive using my machine (lenovo x100e) at school, I wanted to have a lightweight alternative to gnome.
So, maybe I just need a beginners guide for openbox to make it do the very basic tasks, or I'm just totally wrong with openbox and someone could recommend me another alternative...

---

### Post by Jose Catre-Vandis on 2010-12-13
Good guide to get you started:

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

or my recent effort:
[http://bimma.me.uk/2010/12/30/minimal-install-xubuntu-1004-lts-openbox/](http://bimma.me.uk/2010/12/30/minimal-install-xubuntu-1004-lts-openbox/)

---

### Post by snowpine on 2010-12-13
You might also consider Fluxbox; it is as "lightweight" as Openbox but has a built-in panel.

---

### Post by uriel1998 on 2010-12-13
> **yellowsn0w said:**
> Thanks for the answers guys,
As the gnome-panel itself in openbox is as "slow" as it is in gnome, I installed tint2.


Customizing tint2 (newest release):  

[https://code.google.com/p/tint2/wiki/Configure](https://code.google.com/p/tint2/wiki/Configure)

Keep in mind that a good rule of thumb is that the lighter your distro, the more comfy you need to be with your configuration files.  Google is your friend;  you're trading off *higher productivity and speed over time* for *speedy GUI configuration*.  

I have a very simple tint2rc (in that it doesn't have all the options enabled, and so on.

```

#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 7
border_width = 2
background_color = #000000 60
border_color = #ffffff 18

rounded = 5
border_width = 0
background_color = #ffffff 40
border_color = #ffffff 50

rounded = 5
border_width = 0
background_color = #ffffff 18
border_color = #ffffff 70

#---------------------------------------------
# PANEL
#---------------------------------------------
#panel_monitor = 2
panel_monitor = all
panel_position = bottom center
panel_size = 94% 30
panel_margin = 0 0
panel_padding = 7 0
font_shadow = 0
panel_background_id = 1
wm_menu = 1

#---------------------------------------------
# TASKBAR
#---------------------------------------------
#taskbar_mode = multi_desktop
taskbar_mode = single_desktop
taskbar_padding = 2 3 2
taskbar_background_id = 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 1
task_width = 140
task_centered = 1
task_padding = 6 3
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85
task_background_id = 3
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray_padding = 0 4 5
systray_background_id = 0

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %H:%M
time1_font = sans 8
time2_format = %a %d %b
time2_font = sans 6
clock_font_color = #ffffff 76
clock_padding = 1 0
clock_background_id = 0
#clock_lclick_command = xclock
#clock_rclick_command = orage

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 0
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
bat1_font = sans 8
bat2_font = sans 6
battery_font_color = #ffffff 76
battery_padding = 1 0
battery_background_id = 0


#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = shade
mouse_right = iconify
#mouse_scroll_up = toggle
#mouse_scroll_down = iconify


```

---


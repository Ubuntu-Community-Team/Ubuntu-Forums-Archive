---
title: "Problem with Openbox"
date: 2017-07-07
forum: Desktop Environments
---

### Post by frogbrain on 2017-07-07
Hi.

Recently, I installed Lubuntu. After installing I wanted to add some shadows to it, and transparencies. It's the first time I use this distro, so I was (am) not very much familiar with LXDE or Openbox. 

I followed a guide I found online for compton and, after applying the settings, I got my shadows and transparencies, but something important failed: almost all buttons on different applications disappeared, instead windows options are now looking like text of something. The regular shadows and corners that should go with buttons and submenus are gone, and I don't know 1) what the hell happened, and 2) how to fix it. Also, a lot of key shortcuts are not working anymore. For example, the ones for opening archives (super+E) and the terminal stopped working and I had to set them again. For archives, it said "failed to execute child process kmfclient - The directory is not found or does not exists. The directory was /home. 

I already restored Openbox default settings but it didn't work. Did the same with Compton and didn't work either.

I hope you can help me.

Here is the text I used to make the .config file for Compton (/home/.config/compton.conf)

     
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# Shadow
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]shadow = true;
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]no-dnd-shadow = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]no-dock-shadow = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]clear-shadow = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]shadow-radius = 7;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]shadow-offset-x = -7;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]shadow-offset-y = -7;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# shadow-opacity = 0.7;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# shadow-red = 0.0;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# shadow-green = 0.0;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# shadow-blue = 0.0;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]shadow-exclude = [[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]	"name = 'Notification'",[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]	"class_g = 'Conky'",[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]	"class_g ?= 'Notify-osd'",[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]	"class_g = 'Cairo-clock'",[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]	"_GTK_FRAME_EXTENTS@:c"[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]];[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# shadow-exclude = "n:e:Notification";[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# shadow-exclude-reg = "x10+0+0";[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# xinerama-shadow-crop = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"] 
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# Opacity[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]menu-opacity = 0.8;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]inactive-opacity = 0.8;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# active-opacity = 0.8;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]frame-opacity = 0.7;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]inactive-opacity-override = false;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]alpha-step = 0.06;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# inactive-dim = 0.2;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# inactive-dim-fixed = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# blur-background = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# blur-background-frame = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]blur-kern = "3x3box";[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# blur-kern = "5,5,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1";[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# blur-background-fixed = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]blur-background-exclude = [[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]	"window_type = 'dock'",[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]	"window_type = 'desktop'",[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]	"_GTK_FRAME_EXTENTS@:c"[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]];[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# opacity-rule = [ "80:class_g = 'URxvt'" ];[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"] 
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# Fading[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]fading = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# fade-delta = 30;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]fade-in-step = 0.03;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]fade-out-step = 0.03;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# no-fading-openclose = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# no-fading-destroyed-argb = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]fade-exclude = [ ];[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"] 
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# Other[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]backend = "xrender";[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]mark-wmwin-focused = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]mark-ovredir-focused = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# use-ewmh-active-win = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]detect-rounded-corners = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]detect-client-opacity = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]refresh-rate = 0;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]vsync = "none";[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]dbe = false;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]paint-on-overlay = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# sw-opti = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# unredir-if-possible = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# unredir-if-possible-delay = 5000;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# unredir-if-possible-exclude = [ ];[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]focus-exclude = [ "class_g = 'Cairo-clock'" ];[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]detect-transient = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]detect-client-leader = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]invert-color-include = [ ];[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# resize-damage = 1;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"] 
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# GLX backend[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# glx-no-stencil = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]glx-copy-from-front = false;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# glx-use-copysubbuffermesa = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# glx-no-rebind-pixmap = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]glx-swap-method = "undefined";[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# glx-use-gpushader4 = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# xrender-sync = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# xrender-sync-fence = true;[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"] 
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]# Window type settings[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]wintypes:[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]{
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]  tooltip = { fade = true; shadow = true; opacity = 0.75; focus = true; };
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
};

```
# Shadow
shadow = true;
no-dnd-shadow = true;
no-dock-shadow = true;
clear-shadow = true;
shadow-radius = 7;
shadow-offset-x = -7;
shadow-offset-y = -7;
# shadow-opacity = 0.7;
# shadow-red = 0.0;
# shadow-green = 0.0;
# shadow-blue = 0.0;
shadow-exclude = [
"name = 'Notification'",
"class_g = 'Conky'",
"class_g ?= 'Notify-osd'",
"class_g = 'Cairo-clock'",
"_GTK_FRAME_EXTENTS@:c"
];
# shadow-exclude = "n:e:Notification";
# shadow-exclude-reg = "x10+0+0";
# xinerama-shadow-crop = true;
# Opacity
menu-opacity = 0.8;
inactive-opacity = 0.8;
# active-opacity = 0.8;
frame-opacity = 0.7;
inactive-opacity-override = false;
alpha-step = 0.06;
# inactive-dim = 0.2;
# inactive-dim-fixed = true;
# blur-background = true;
# blur-background-frame = true;
blur-kern = "3x3box";
# blur-kern = "5,5,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1 ,1";
# blur-background-fixed = true;
blur-background-exclude = [
"window_type = 'dock'",
"window_type = 'desktop'",
"_GTK_FRAME_EXTENTS@:c"
];
# opacity-rule = [ "80:class_g = 'URxvt'" ];
# Fading
fading = true;
# fade-delta = 30;
fade-in-step = 0.03;
fade-out-step = 0.03;
# no-fading-openclose = true;
# no-fading-destroyed-argb = true;
fade-exclude = [ ];
# Other
backend = "xrender";
mark-wmwin-focused = true;
mark-ovredir-focused = true;
# use-ewmh-active-win = true;
detect-rounded-corners = true;
detect-client-opacity = true;
refresh-rate = 0;
vsync = "none";
dbe = false;
paint-on-overlay = true;
# sw-opti = true;
# unredir-if-possible = true;
# unredir-if-possible-delay = 5000;
# unredir-if-possible-exclude = [ ];
focus-exclude = [ "class_g = 'Cairo-clock'" ];
detect-transient = true;
detect-client-leader = true;
invert-color-include = [ ];
# resize-damage = 1;
# GLX backend
# glx-no-stencil = true;
glx-copy-from-front = false;
# glx-use-copysubbuffermesa = true;
# glx-no-rebind-pixmap = true;
glx-swap-method = "undefined";
# glx-use-gpushader4 = true;
# xrender-sync = true;
# xrender-sync-fence = true;
# Window type settings
wintypes:
{
tooltip = { fade = true; shadow = true; opacity = 0.75; focus = true; };
};
```



I also add some pictures:

[https://image.ibb.co/h6C9Pa/2017_07_07_232854_1366x768_scrot.png](https://image.ibb.co/h6C9Pa/2017_07_07_232854_1366x768_scrot.png)
[https://image.ibb.co/kMGscv/2017_07_07_233334_1366x768_scrot.png](https://image.ibb.co/kMGscv/2017_07_07_233334_1366x768_scrot.png)
[https://image.ibb.co/epWEqF/2017_07_07_233402_1366x768_scrot.png](https://image.ibb.co/epWEqF/2017_07_07_233402_1366x768_scrot.png)
[https://image.ibb.co/hf7LVF/2017_07_07_233430_1366x768_scrot.png](https://image.ibb.co/hf7LVF/2017_07_07_233430_1366x768_scrot.png)
[https://image.ibb.co/iAKOja/2017_07_07_233544_1366x768_scrot.png](https://image.ibb.co/iAKOja/2017_07_07_233544_1366x768_scrot.png)

---

### Post by vasa1 on 2017-07-08
**Please** don't paste content the way you've done. Use code tags, the **#** icon.

Something like this is what we're used to:
```
# https://github.com/chjj/compton/blob/master/man/compton.1.asciidoc#format-of-conditions ::: explains syntax with examples
# https://bbs.archlinux.org/viewtopic.php?pid=1293686#p1293686
focus-exclude = ["n:a:Conky"];
inactive-opacity = 1.0;
inactive-dim = 0.2;
mark-ovredir-focused = true;
opacity-rule = [ 
				"60:name ~= '^Mahjongg$'",
#				"50:name ~= 'Gmail - Google Chrome$'",
#				"50:name ~= 'Photos - Google Chrome$'",
#				"50:name ~= 'Drive - Google Chrome$'",
#				"50:name ~= 'Banking - Google Chrome$'",
#				"50:name ~= 'Login - Google Chrome$'",
#				"50:name ~= 'Google Search - Google Chrome$'",
				"70:name ~= 'Settings - Google Chrome$'",
				"50:name ~= 'Bookmark Manager - Google Chrome$'",
				"70:name ~= 'Extensions - Google Chrome$'",
				"70:name ~= 'Stylish - Google Chrome$'",
				"50:name ~= '\.pdf - Google Chrome$'",
				"50:name ~= '*.* Logger - Google Chrome'",
				"50:name *= 'Network request log'",
#				"50:name *= 'Dashboard - Mozilla Firefox'",
#				"80:name ~= 'Ask Ubuntu - Mozilla Firefox$'",
#				"50:name ~= '^uBlock&#8320;'",
				"50:class_g *= 'Evince'",
#				"80:class_g ~= 'Google-chrome$'",
				"95:window_type *= 'dialog'",
				"95:window_type *= 'menu'"
				];
shadow = false;
no-dnd-shadow = true;
no-dock-shadow = true;
blur-background = false;

```

---


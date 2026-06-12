---
title: "Please help me customize my laptop..."
date: 2008-12-30
forum: General Help
---

### Post by shgadwa on 2008-12-30
I have been using Ubuntu for some time now. Although my Toshiba is fairly spiffy in speed, its 15.4 inch wide screen does not have the best resolution.

I am kind of tired of Ubuntu's general BIG look and feel. Such as, the buttons are much bigger, and its not as polished as I would of like it to be and in the end, It does not save me any money...

So, somehow, I want it to look great but also be compact. I have Compiz and Emerald installed. Please let me know what all I can do. I searched for compact themes and did not find much. The closest I have got is changing it to a Mac OS X look and feel but in some ways, its still not at all like Mac OS X in which case I would rather have it look like Linux (if it did not look 90% like a mac).

Any ideas?

---

### Post by hans.hook on 2008-12-30
Hi

Did a bit of customizations on my eeepc.

I have two files 22_my_desktop and 25_my_eee_desktop placed in 
/usr/share/gconf/defaults this will set up defaults for a slim ubuntu gnome desktop that saves space and looks exactly like I prefer it to.
For window borders I use alphacube metacity color condensed that you may download on gnome-look.org.
For tweaking your desktop in gnome  gconf-editor is your best friend but it 
takes a while to find all interesting options.
Therefore i provide my two default settings files as inspiration.
Hope it helps you - its a lot of fun playing with anyhow ... 
If you add default settings do not forget to clear out your own
local gconf settings in ~/.gonf.

(Tested in Ubuntu 8.04 and yes some of the settings are in Swedish ...)

Regards

HH

22_my_desktop
=============

/desktop/gnome/interface/gtk_theme      Clearlooks
/desktop/gnome/interface/icon_theme     glass-icons
/desktop/gnome/interface/font_name 	"Sans 10"
/desktop/gnome/interface/document_font_name "Sans 10"
/desktop/gnome/interface/monospace_font_name "Terminus 10"
/desktop/gnome/interface/gtk_color_scheme "fg_color:#000000000000;bg_color:#e6e6e7e7e8e8;text_color:#000000000000;base_color:#ffffffffffff;selected_fg_color:#ffffffffffff;selected_bg_color:#7da185818d44;tooltip_fg_color:#000000000000;tooltip_bg_color:#ffffffffffff"

/desktop/gnome/peripherals/mouse/cursor_theme   whiteglass
/desktop/gnome/peripherals/mouse/cursor_size    24


/desktop/gnome/applications/media/exec banshee
/desktop/gnome/volume_manager/autoburn_data_cd_command "k3b --datacd"
/desktop/gnome/volume_manager/autoburn_audio_cd_command "k3b --audiocd"
/desktop/gnome/volume_manager/autoburn true
/desktop/gnome/volume_manager/autoplay_cda true
/desktop/gnome/volume_manager/autoplay_cda_command "banshee %d"
/desktop/gnome/volume_manager/autoplay_vcd true
/desktop/gnome/volume_manager/autoplay_vcd_command "vlc %m"
/desktop/gnome/volume_manager/autoipod_command "banshee"

/desktop/gnome/url-handlers/cdda/enabled true
/desktop/gnome/url-handlers/cdda/command "banshee"
/desktop/gnome/url-handlers/mailto/enabled true
/desktop/gnome/url-handlers/mailto/command "thunderbird %s"

/apps/metacity/general/theme	"Alphacube-1.0-Metacity-Color"
/apps/metacity/general/titlebar_font	"Sans Bold 10"

/apps/metacity/window_keybindings/toggle_fullscreen "<Alt>F11"

/apps/nautilus/desktop/computer_icon_name	"Den här datorn"
/apps/nautilus/desktop/computer_icon_visible	true
/apps/nautilus/desktop/home_icon_name		"Mina filer"
/apps/nautilus/desktop/home_icon_visible	true
/apps/nautilus/desktop/network_icon_name	"Nätverk"
/apps/nautilus/desktop/network_icon_visible	true
/apps/nautilus/desktop/trash_icon_name		"Skräp"
/apps/nautilus/desktop/trash_icon_visible	true
/apps/nautilus/desktop/volumes_visible		true
/apps/nautilus/desktop/volumes_visible		true


/apps/nautilus/icon_view/thumbnail_size		42

/apps/nautilus/preferences/desktop_font		"Purisa Light 10"
/apps/nautilus/preferences/background_color		"#E5E5E5"
/apps/nautilus/preferences/start_with_location_bar	true
/apps/nautilus/preferences/start_with_sidebar		true
/apps/nautilus/preferences/start_with_status_bar	true
/apps/nautilus/preferences/start_with_tool_bar		true

/apps/gnome-terminal/profiles/Default/allow_bold true
/apps/gnome-terminal/profiles/Default/background_color "#FFFFDD"
/apps/gnome-terminal/profiles/Default/background_darkness 0.9
/apps/gnome-terminal/profiles/Default/background_type "transparent"


/apps/panel/default_setup/general/object_id_list	[menu_bar,browser_launcher,email_launcher,shell_launcher,yelp_launcher,session_dialog]
/apps/panel/default_setup/general/toplevel_id_list	[top_panel]

/apps/panel/default_setup/toplevels/top_panel/auto_hide	false
/apps/panel/default_setup/toplevels/top_panel/auto_hide_size	0
/apps/panel/default_setup/toplevels/top_panel/enable_animations	false
/apps/panel/default_setup/toplevels/top_panel/expand	true
/apps/panel/default_setup/toplevels/top_panel/hide_delay	100
/apps/panel/default_setup/toplevels/top_panel/unhide_delay	100


/apps/panel/default_setup/objects/browser_launcher/panel_right_stick false
/apps/panel/default_setup/objects/browser_launcher/position 1

/apps/panel/default_setup/objects/email_launcher/panel_right_stick false
/apps/panel/default_setup/objects/email_launcher/position 2
/apps/panel/default_setup/objects/email_launcher/launcher_location "thunderbird.desktop"

/apps/panel/default_setup/objects/yelp_launcher/position 5

/apps/panel/default_setup/objects/shell_launcher/panel_right_stick false
/apps/panel/default_setup/objects/shell_launcher/position 4
/apps/panel/default_setup/objects/shell_launcher/action_type lock
/apps/panel/default_setup/objects/shell_launcher/launcher_location "/usr/share/applications/gnome-terminal.desktop"
/apps/panel/default_setup/objects/shell_launcher/menu_path "applications:/"
/apps/panel/default_setup/objects/shell_launcher/object_type launcher-object
/apps/panel/default_setup/objects/shell_launcher/tooltip "Terminalskal"
/apps/panel/default_setup/objects/shell_launcher/toplevel_id top_panel

/apps/panel/default_setup/applets/show_desktop_button/panel_right_stick true
/apps/panel/default_setup/applets/show_desktop_button/position 7
/apps/panel/default_setup/applets/show_desktop_button/toplevel_id top_panel

/apps/panel/default_setup/applets/window_list/panel_right_stick false
/apps/panel/default_setup/applets/window_list/position 6
/apps/panel/default_setup/applets/window_list/toplevel_id top_panel

/apps/panel/default_setup/applets/workspace_switcher/panel_right_stick true
/apps/panel/default_setup/applets/workspace_switcher/position 6
/apps/panel/default_setup/applets/workspace_switcher/toplevel_id top_panel

25_my_eee-desktop
=================
/desktop/gnome/interface/font_name 	"Sans 8"
/desktop/gnome/interface/document_font_name "Sans 8"
/desktop/gnome/interface/monospace_font_name "Terminus 8"
/desktop/gnome/peripherals/mouse/cursor_size    12
/desktop/gnome/sound/default_mixer_tracks "[PCM]"
/apps/metacity/general/theme	"Alphacube-1.0-Metacity-Color-Condensed"
/apps/metacity/general/titlebar_font	"Sans Bold 8"
/apps/nautilus/icon_view/labels_beside_icons	true
/apps/nautilus/icon_view/thumbnail_size		42
/apps/nautilus/icon_view/default_zoom_level     small
/apps/nautilus/preferences/desktop_font		"Purisa Light 8"
/apps/nautilus/preferences/start_with_status_bar	false
/apps/gnome-power-manager/notify/low_capacity false
/apps/compiz/plugins/move/allscreens/options/constrain_y false
/apps/panel/default_setup/general/object_id_list	[menu_object,browser_launcher,email_launcher,shell_launcher,yelp_launcher,session_dialog]
/apps/panel/default_setup/toplevels/top_panel/auto_hide	true
/apps/panel/default_setup/toplevels/top_panel/size 19
/apps/panel/default_setup/toplevels/bottom_panel/size 19
/apps/panel/default_setup/objects/menu_object/panel_right_stick false
/apps/panel/default_setup/objects/menu_object/position 0
/apps/panel/default_setup/objects/menu_object/action_type lock
/apps/panel/default_setup/objects/menu_object/menu_path "applications:/"
/apps/panel/default_setup/objects/menu_object/object_type "menu-object"
/apps/panel/default_setup/objects/menu_object/tooltip "Huvudmeny"
/apps/panel/default_setup/objects/menu_object/toplevel_id top_panel

---

### Post by steveneddy on 2008-12-30
> **shgadwa said:**
> I have been using Ubuntu for some time now. Although my Toshiba is fairly spiffy in speed, its 15.4 inch wide screen does not have the best resolution.

I am kind of tired of Ubuntu's general BIG look and feel. Such as, the buttons are much bigger, and its not as polished as I would of like it to be and in the end, It does not save me any money...

So, somehow, I want it to look great but also be compact. I have Compiz and Emerald installed. Please let me know what all I can do. I searched for compact themes and did not find much. The closest I have got is changing it to a Mac OS X look and feel but in some ways, its still not at all like Mac OS X in which case I would rather have it look like Linux (if it did not look 90% like a mac).

Any ideas?

Have you tried changing the screen resolution?

Sounds like yolu have it set to 800 X 600.

What kind of video card is in this thing?

Or is it Intel onboard graphics?

---

### Post by shgadwa on 2008-12-30
Yes, I have tried but its set as high as it can go... which is 1080X800 somewhere around there, more or less. Its what the computer specs say it can do as well... I think it must be a cheaper screen, not able to do high enough resolution. Still, Ubuntu is big and there is hardly any compact thing... except mac4lin which would require more tweaking for me to get to like it, which I might just do, I suppose. I really wish I could change the resolution.

~Shawn

---

### Post by GeorgeMurango on 2008-12-31
If you're comfortable with this, go into appearance, then the interface tab. Either removing icons or text from buttons and menus helps slim things down.

---

### Post by steveneddy on 2009-01-01
You can also right click the bars, go to Properties and change the size of the bars in pixels.

Maybe that will help a little.

---


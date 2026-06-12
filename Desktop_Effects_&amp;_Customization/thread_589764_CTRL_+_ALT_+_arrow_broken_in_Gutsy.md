---
title: "CTRL + ALT + arrow broken in Gutsy"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by DouglasAWh on 2007-10-24
I've seen lots of posts about desktop effects being broken in Gutsy (which makes me wonder why it was released the way it was, but that's another thread...), but nothing specific to the CTRL + ALT + arrow desktop cube rotation problem.  I'd be happy changing work spaces with CTRL + ALT + LEFT/RIGHT even if the cube is broken.  Having to move the mouse to change work spaces makes having workspaces pretty useless to me.

---

### Post by itsbradman on 2007-10-27
have you gone into ccsm and made sure that rotate cube is enabled?

---

### Post by DouglasAWh on 2007-10-27
> **itsbradman said:**
> have you gone into ccsm and made sure that rotate cube is enabled?

Yes, but even if it wasn't, I ought to be able to change workspaces with CTRL + ALT + arrow.

---

### Post by DouglasAWh on 2007-10-28
for whatever reason, "Viewpoint Switcher" under Desktop in the compiz manager was the problem.

---

### Post by DouglasAWh on 2007-10-29
Ok, this is not as fixed as I thought it was.  My workspaces don't seem to align with what is in the task bar.  You can see what I am talking about at [http://www.ils.unc.edu/~whitdoug/Screenshot-taskbar.png](http://www.ils.unc.edu/~whitdoug/Screenshot-taskbar.png)

I remember there being something about workspaces versus desks with beryl, but I haven't figured things out in this abomination called compiz-fusion.

---

### Post by itsbradman on 2007-10-29
not sure what you mean about the workplaces not aligning from the screenshot.  In ccsm, make sure that the number of cube sides or length is set to the same # of workplaces you have selected for the panel workplace switcher.  Hope this helps.  btw, the settings I am referring to are in the desktop cube settings in ccsm

---

### Post by DouglasAWh on 2007-10-29
what I mean is that Thunderbird is showing, but the two items in the taskbar are Firefox and the file browser (nautilus is what that's called, right?).  Those two items aren't minimized, they are on another workspace or desk or something.  I'm so confused!

---

### Post by DouglasAWh on 2007-10-29
> **itsbradman said:**
>  In ccsm, make sure that the number of cube sides or length is set to the same # of workplaces you have selected for the panel workplace switcher.

I don't see where to do that in ccsm.  Here's my profile:

```

[addhelper]
as_toggle = <Super>p,Button0,,0,false
as_window_types = Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal
as_brightness = 30
as_saturation = 50
as_opacity = 100

[blur]
as_pulse = ,Button0,,0,false
s0_focus_blur_match = toolbar | menu | utility | normal | dialog | modaldialog
s0_focus_blur = false
s0_alpha_blur_match = 
s0_alpha_blur = true
s0_filter = 0
s0_gaussian_radius = 3
s0_saturation = 100
s0_occlusion = true

[bench]
as_initiate = <Super>F12,Button0,,0,false
as_disable_limiter = true
as_output_screen = true
as_position_x = 0
as_position_y = 0
as_output_console = false
as_console_update_time = 5

[wobbly]
as_snap = ,Button0,,0,false
as_snap_inverted = false
as_shiver = ,Button0,,0,false
s0_grid_resolution = 8
s0_min_grid_size = 8
s0_map_effect = 0
s0_focus_effect = 0
s0_map_window_match = Splash | DropdownMenu | PopupMenu | Tooltip | Notification | Combo | Dnd | Unknown
s0_focus_window_match = 
s0_grab_window_match = 
s0_move_window_match = Toolbar | Menu | Utility | Dialog | Normal | Unknown
s0_maximize_effect = true

[scaleaddon]
as_close = ,Button2,,0,false
as_zoom = ,Button3,,0,false
s0_window_title = true
s0_title_bold = false
s0_title_size = 10
s0_border_size = 3
s0_font_color = #ffffffff
s0_back_color = #00000099
s0_window_highlight = false
s0_highlight_color = #ffffff96
s0_layout_mode = 0

[wall]
as_show_switcher = true
as_miniscreen = false
as_edge_radius = 5
as_outline_color = #333333d9
as_background_gradient_base_color = #cccce6d9
as_background_gradient_highlight_color = #f3f3ffd9
as_background_gradient_shadow_color = #f3f3ffd9
as_thumb_gradient_base_color = #33333359
as_thumb_gradient_highlight_color = #3f3f3f3f
as_thumb_highlight_gradient_base_color = #fffffff3
as_thumb_highlight_gradient_shadow_color = #dfdfdfa6
as_arrow_base_color = #e6e6e6d9
as_arrow_shadow_color = #dcdcdcd9
as_allow_wraparound = false
as_left = <Control><Alt>Left,Button0,,0,false
as_right = <Control><Alt>Right,Button0,,0,false
as_up = <Control><Alt>Up,Button0,,0,false
as_down = <Control><Alt>Down,Button0,,0,false
as_next = <Control><Alt>Next,Button0,,0,false
as_prev = <Control><Alt>Prior,Button0,,0,false
as_left_window = <Shift><Control><Alt>Left,Button0,,0,false
as_right_window = <Shift><Control><Alt>Right,Button0,,0,false
as_up_window = <Shift><Control><Alt>Up,Button0,,0,false
as_down_window = <Shift><Control><Alt>Down,Button0,,0,false
as_flip_left = ,Button0,Left,0,false
as_flip_right = ,Button0,Right,0,false
as_flip_up = ,Button0,Top,0,false
as_flip_down = ,Button0,Bottom,0,false
s0_mmmode = 0
s0_edgeflip_pointer = false
s0_edgeflip_move = true
s0_edgeflip_dnd = false

[cubecaps]
as_top_next = space,Button0,,0,false
as_top_prev = ,Button0,,0,false
as_bottom_next = ,Button0,,0,false
as_bottom_prev = ,Button0,,0,false
s0_draw_top = true
s0_draw_bottom = true
s0_adjust_top = false
s0_adjust_bottom = false
s0_scale_top_image = false
s0_scale_bottom_image = false
s0_clamp_top_to_border = true
s0_clamp_bottom_to_border = true
s0_top_color = #ffffffff
s0_bottom_color = #ffffffff
s0_top_images = fusioncap.png
s0_bottom_images = compizcap.png

[splash]
as_initiate = <Control>F11,Button0,,0,false
as_firststart = true
as_background = splash_background.png
as_logo = splash_logo.png

[plane]
as_plane_left = <Control><Alt>Left,Button0,,0,false
as_plane_right = <Control><Alt>Right,Button0,,0,false
as_plane_down = <Control><Alt>Down,Button0,,0,false
as_plane_up = <Control><Alt>Up,Button0,,0,false
as_plane_to_1 = ,Button0,,0,false
as_plane_to_2 = ,Button0,,0,false
as_plane_to_3 = ,Button0,,0,false
as_plane_to_4 = ,Button0,,0,false
as_plane_to_5 = ,Button0,,0,false
as_plane_to_6 = ,Button0,,0,false
as_plane_to_7 = ,Button0,,0,false
as_plane_to_8 = ,Button0,,0,false
as_plane_to_9 = ,Button0,,0,false
as_plane_to_10 = ,Button0,,0,false
as_plane_to_11 = ,Button0,,0,false
as_plane_to_12 = ,Button0,,0,false

[firepaint]
as_initiate = ,<Shift><Super>Button1,,0,false
as_clear = <Shift><Super>c,Button0,,0,false
s0_num_particles = 3000
s0_fire_color = #ff3305ff
s0_fire_mystical = false
s0_bg_brightness = 50

[winrules]
s0_skiptaskbar_match = 
s0_skippager_match = 
s0_above_match = 
s0_below_match = 
s0_sticky_match = 
s0_fullscreen_match = 
s0_widget_match = 
s0_no_move_match = 
s0_no_resize_match = 
s0_no_minimize_match = 
s0_no_maximize_match = 
s0_no_close_match = 
s0_no_focus_match = 
s0_size_matches = 
s0_size_width_values = 
s0_size_height_values = 

[rotate]
as_initiate = ,<Control><Alt>Button1,,0,false
as_rotate_left = <Control><Alt>Left,Button0,,0,false
as_rotate_right = <Control><Alt>Right,Button0,,0,false
as_rotate_left_window = <Shift><Control><Alt>Left,Button0,,0,false
as_rotate_right_window = <Shift><Control><Alt>Right,Button0,,0,false
as_edge_flip_pointer = false
as_edge_flip_window = true
as_edge_flip_dnd = true
as_flip_time = 350
as_rotate_to_1 = ,Button0,,0,false
as_rotate_to_2 = ,Button0,,0,false
as_rotate_to_3 = ,Button0,,0,false
as_rotate_to_4 = ,Button0,,0,false
as_rotate_to_5 = ,Button0,,0,false
as_rotate_to_6 = ,Button0,,0,false
as_rotate_to_7 = ,Button0,,0,false
as_rotate_to_8 = ,Button0,,0,false
as_rotate_to_9 = ,Button0,,0,false
as_rotate_to_10 = ,Button0,,0,false
as_rotate_to_11 = ,Button0,,0,false
as_rotate_to_12 = ,Button0,,0,false
as_rotate_to_1_window = ,Button0,,0,false
as_rotate_to_2_window = ,Button0,,0,false
as_rotate_to_3_window = ,Button0,,0,false
as_rotate_to_4_window = ,Button0,,0,false
as_rotate_to_5_window = ,Button0,,0,false
as_rotate_to_6_window = ,Button0,,0,false
as_rotate_to_7_window = ,Button0,,0,false
as_rotate_to_8_window = ,Button0,,0,false
as_rotate_to_9_window = ,Button0,,0,false
as_rotate_to_10_window = ,Button0,,0,false
as_rotate_to_11_window = ,Button0,,0,false
as_rotate_to_12_window = ,Button0,,0,false
as_rotate_to = ,Button0,,0,false
as_rotate_window = ,Button0,,0,false
as_rotate_flip_left = ,Button0,Left,0,false
as_rotate_flip_right = ,Button0,Right,0,false
as_raise_on_rotate = false
s0_invert_y = false
s0_snap_top = false

[trailfocus]
s0_window_match = (type=toolbar | type=utility | type=dialog | type=normal) & !(state=skiptaskbar | state=skippager)
s0_windows_count = 5
s0_windows_start = 2
s0_max_opacity = 100
s0_min_opacity = 70
s0_max_brightness = 100
s0_min_brightness = 100
s0_max_saturation = 100
s0_min_saturation = 100

[workarounds]
as_legacy_fullscreen = true
as_firefox_menu_fix = true
as_notification_daemon_fix = true
as_java_fix = true
as_qt_fix = true
as_sticky_alldesktops = false
as_alldesktop_sticky_match = any

[ring]
as_next = <Super>Tab,Button0,,0,false
as_prev = <Shift><Super>Tab,Button0,,0,false
as_next_all = <Alt><Super>Tab,Button0,,0,false
as_prev_all = <Shift><Alt><Super>Tab,Button0,,0,false
as_next_group = ,Button0,,0,false
as_prev_group = ,Button0,,0,false
s0_inactive_opacity = 100
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_overlay_icon = 1
s0_darken_back = true
s0_minimized = true
s0_select_with_mouse = false
s0_ring_clockwise = false
s0_ring_width = 70
s0_ring_height = 60
s0_thumb_width = 350
s0_thumb_height = 250
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 0

[resize]
as_initiate_normal = ,Button0,,0,false
as_initiate_outline = ,Button0,,0,false
as_initiate_rectangle = ,Button0,,0,false
as_initiate_stretch = ,Button0,,0,false
as_initiate = <Alt>F8,<Alt>Button2,,0,false
as_mode = 2
as_border_color = #2f2f4f9f
as_fill_color = #2f2f4f4f
as_normal_match = 
as_outline_match = 
as_rectangle_match = 
as_stretch_match = 

[switcher]
as_next = <Alt>Tab,Button0,,0,false
as_prev = ,Button0,,0,false
as_next_all = <Control><Alt>Tab,Button0,,0,false
as_prev_all = <Shift><Control><Alt>Tab,Button0,,0,false
as_next_no_popup = ,Button0,,0,false
as_prev_no_popup = ,Button0,,0,false
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_mipmap = true
s0_saturation = 100
s0_brightness = 65
s0_opacity = 95
s0_bring_to_front = true
s0_icon = true
s0_minimized = true
s0_auto_rotate = false

[vpswitch]
as_begin = ,Button0,,0,false
as_switch_to_1 = ,Button0,,0,false
as_switch_to_2 = ,Button0,,0,false
as_switch_to_3 = ,Button0,,0,false
as_switch_to_4 = ,Button0,,0,false
as_switch_to_5 = ,Button0,,0,false
as_switch_to_6 = ,Button0,,0,false
as_switch_to_7 = ,Button0,,0,false
as_switch_to_8 = ,Button0,,0,false
as_switch_to_9 = ,Button0,,0,false
as_switch_to_10 = ,Button0,,0,false
as_switch_to_11 = ,Button0,,0,false
as_switch_to_12 = ,Button0,,0,false
as_left = ,Button0,,0,false
as_right = ,Button0,,0,false
as_up = ,Button0,,0,false
as_down = ,Button0,,0,false
as_next = ,Button5,,0,false
as_prev = ,Button4,,0,false
as_initiate = ,Button2,,0,false
as_init_plugin = rotate
as_init_action = initiate

[snap]
as_avoid_snap = 0
s0_snap_type = 
s0_edges_categories = 
s0_resistance_distance = 30
s0_attraction_distance = 20

[scale]
as_initiate = <Shift><Alt>Up,Button0,TopRight,0,false
as_initiate_all = ,Button0,,0,false
as_initiate_group = ,Button0,,0,false
as_initiate_output = ,Button0,,0,false
as_show_desktop = true
s0_spacing = 10
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_darken_back = true
s0_opacity = 75
s0_overlay_icon = 1
s0_hover_time = 750
s0_multioutput_mode = 0

[crashhandler]
as_enabled = true
as_start_wm = false
as_wm_cmd = 

[decoration]
as_shadow_color = #00000000
as_shadow_x_offset = 1
as_shadow_y_offset = 1
as_command = emerald --replace
as_mipmap = false
as_decoration_match = any
as_shadow_match = any

[video]
as_yv12 = true

[shift]
as_initiate = <Shift><Super>s,Button0,,0,false
as_initiate_all = ,Button0,,0,false
as_next = <Super>Tab,Button0,,0,false
as_prev = <Shift><Super>Tab,Button0,,0,false
as_next_all = <Alt><Super>Tab,Button0,,0,false
as_prev_all = <Shift><Alt><Super>Tab,Button0,,0,false
as_next_group = ,Button0,,0,false
as_prev_group = ,Button0,,0,false
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_minimized = true
s0_click_duration = 500
s0_mode = 0
s0_size = 50
s0_hide_all = false
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_flip_rotation = 30
s0_overlay_icon = 1
s0_mipmaps = false
s0_multioutput_mode = 0
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 2

[group]
as_select = ,Button0,,0,false
as_select_single = <Super>s,Button0,,0,false
as_group = <Super>g,Button0,,0,false
as_ungroup = <Super>u,Button0,,0,false
as_remove = <Super>r,Button0,,0,false
as_close = <Super>c,Button0,,0,false
as_ignore = <Super>x,Button0,,0,false
as_tabmode = <Super>t,Button0,,0,false
as_change_tab_left = <Super>Left,Button0,,0,false
as_change_tab_right = <Super>Right,Button0,,0,false
as_change_color = ,Button0,,0,false
s0_move_all = true
s0_resize_all = false
s0_raise_all = true
s0_maximize_unmaximize_all = false
s0_minimize_all = true
s0_shade_all = false
s0_auto_group = false
s0_auto_ungroup = true
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_select_opacity = 80
s0_select_saturation = 20
s0_select_brightness = 70
s0_select_precision = 25
s0_fill_color = #00000099
s0_line_color = #000000ab
s0_mipmaps = false
s0_untab_on_close = false
s0_autotab_create = false
s0_bar_animations = true
s0_thumb_size = 96
s0_thumb_space = 5
s0_border_radius = 10
s0_border_width = 1
s0_tab_base_color = #00000099
s0_tab_border_color = #000000ab
s0_tab_highlight_color = #ffffff99
s0_tab_style = 0
s0_tabbar_font_size = 12
s0_tabbar_font_color = #ffffffff
s0_spring_model_on_move = false
s0_dnd_ungroup_window = true
s0_drag_y_distance = 400
s0_drag_speed_limit = 800
s0_glow = true
s0_glow_size = 64
s0_glow_type = 0

[core]
as_active_plugins = regex;firepaint;text;workarounds;resize;decoration;video;shift;svg;minimize;png;resizeinfo;place;imgjpeg;move;dbus;extrawm;wobbly;fade;cube;expo;cubecaps;rotate;switcher;scale;ezoom
as_texture_filter = 1
as_click_to_focus = true
as_autoraise = true
as_autoraise_delay = 1000
as_close_window = <Alt>F4,Button0,,0,false
as_main_menu = <Alt>F1,Button0,,0,false
as_run = <Alt>F2,Button0,,0,false
as_command0 = 
as_command1 = 
as_command2 = 
as_command3 = 
as_command4 = 
as_command5 = 
as_command6 = 
as_command7 = 
as_command8 = 
as_command9 = 
as_command10 = 
as_command11 = 
as_run_command0 = ,Button0,,0,false
as_run_command1 = ,Button0,,0,false
as_run_command2 = ,Button0,,0,false
as_run_command3 = ,Button0,,0,false
as_run_command4 = ,Button0,,0,false
as_run_command5 = ,Button0,,0,false
as_run_command6 = ,Button0,,0,false
as_run_command7 = ,Button0,,0,false
as_run_command8 = ,Button0,,0,false
as_run_command9 = ,Button0,,0,false
as_run_command10 = ,Button0,,0,false
as_run_command11 = ,Button0,,0,false
as_slow_animations = <Shift>F10,Button0,,0,false
as_raise_window = ,<Control>Button6,,0,false
as_lower_window = ,<Alt>Button6,,0,false
as_unmaximize_window = <Alt>F5,Button0,,0,false
as_minimize_window = <Alt>F9,Button0,,0,false
as_maximize_window = <Alt>F10,Button0,,0,false
as_maximize_window_horizontally = ,Button0,,0,false
as_maximize_window_vertically = ,Button0,,0,false
as_opacity_increase = ,<Alt>Button4,,0,false
as_opacity_decrease = ,<Alt>Button5,,0,false
as_command_screenshot = gnome-screenshot
as_run_command_screenshot = Print,Button0,,0,false
as_command_window_screenshot = gnome-screenshot --window
as_run_command_window_screenshot = <Alt>Print,Button0,,0,false
as_window_menu = <Alt>space,<Alt>Button3,,0,false
as_show_desktop = <Control><Alt>d,Button0,,0,false
as_raise_on_click = true
as_audible_bell = false
as_toggle_window_maximized = ,Button0,,0,false
as_toggle_window_maximized_horizontally = ,Button0,,0,false
as_toggle_window_maximized_vertically = ,Button0,,0,false
as_hide_skip_taskbar_windows = true
as_toggle_window_shaded = ,Button0,,0,false
as_ignore_hints_when_maximized = true
as_command_terminal = gnome-terminal
as_run_command_terminal = ,Button0,,0,false
as_cursor_theme = Human
as_cursor_size = 18
as_ping_delay = 5000
s0_detect_refresh_rate = true
s0_lighting = true
s0_refresh_rate = 50
s0_hsize = 4
s0_vsize = 1
s0_opacity_step = 10
s0_unredirect_fullscreen_windows = true
s0_default_icon = icon
s0_sync_to_vblank = false
s0_number_of_desktops = 4
s0_detect_outputs = true
s0_outputs = 640x480+0+0
s0_focus_prevention_match = any
s0_opacity_matches = 
s0_opacity_values = 

[ezoom]
as_initiate = ,<Super>Button3,,0,false
as_zoom_in = ,<Super>Button4,,0,false
as_lock_zoom = <Super>l,Button0,,0,false
as_zoom_specific_1 = <Super>1,Button0,,0,false
as_zoom_specific_2 = <Super>2,Button0,,0,false
as_zoom_specific_3 = <Super>3,Button0,,0,false
as_fit_to_window = <Super>r,Button0,,0,false
as_pan_left = ,Button0,,0,false
as_pan_right = ,Button0,,0,false
as_pan_up = ,Button0,,0,false
as_pan_down = ,Button0,,0,false
as_zoom_out = ,<Super>Button5,,0,false
as_spec_target_focus = true
as_fit_to_zoom = <Super>v,Button0,,0,false
as_center_mouse = <Super>c,Button0,,0,false
s0_follow_focus = true
s0_focus_fit_window = false
s0_allways_focus_fit_window = false
s0_follow_focus_delay = 1
s0_sync_mouse = true
s0_scale_mouse = false
s0_hide_original_mouse = false
s0_restrain_mouse = false
s0_mouse_pan = false
s0_restrain_margin = 5
s0_mouse_poll_interval = 10
s0_filter_linear = true

[opacify]
as_toggle = <Super>o,Button0,,0,false
as_toggle_reset = true
as_timeout = 700
as_init_toggle = true
s0_only_if_block = false
s0_focus_instant = false
s0_no_delay_change = false
s0_window_match = Normal | Dialog | ModalDialog | Utility | Toolbar | Fullscreen
s0_active_opacity = 100
s0_passive_opacity = 10

[mblur]
as_initiate = <Control>F12,Button0,,0,false
s0_mode = 0
s0_on_transformed_screen = false

[fs]
as_mount_point = compiz

[water]
as_initiate = ,Button0,,0,false
as_toggle_rain = <Shift>F9,Button0,,0,false
as_toggle_wiper = <Shift>F8,Button0,,0,false
as_rain_delay = 250
as_title_wave = ,Button0,,0,false
as_point = ,Button0,,0,false
as_line = ,Button0,,0,false

[thumbnail]
s0_thumb_size = 200
s0_show_delay = 100
s0_border = 16
s0_thumb_color = #0000007f
s0_current_viewport = true
s0_always_on_top = true
s0_window_like = true
s0_mipmap = false
s0_title_enabled = true
s0_font_bold = true
s0_font_size = 12
s0_font_color = #000000ff

[fadedesktop]
s0_fadetime = 500
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown

[showdesktop]
s0_direction = 6
s0_window_match = type=toolbar | type=utility | type=dialog | type=normal
s0_window_part_size = 20

[minimize]
s0_window_match = toolbar | utility | dialog | normal
s0_shade_resistance = 75

[screenshot]
as_initiate = ,<Super>Button1,,0,false
as_directory = Desktop
as_launch_app = 

[put]
as_put_viewport = ,Button0,,0,false
as_put_viewport_1 = ,Button0,,0,false
as_put_viewport_2 = ,Button0,,0,false
as_put_viewport_3 = ,Button0,,0,false
as_put_viewport_4 = ,Button0,,0,false
as_put_viewport_5 = ,Button0,,0,false
as_put_viewport_6 = ,Button0,,0,false
as_put_viewport_7 = ,Button0,,0,false
as_put_viewport_8 = ,Button0,,0,false
as_put_viewport_9 = ,Button0,,0,false
as_put_viewport_10 = ,Button0,,0,false
as_put_viewport_11 = ,Button0,,0,false
as_put_viewport_12 = ,Button0,,0,false
as_put_viewport_left = ,Button0,,0,false
as_put_viewport_right = ,Button0,,0,false
as_put_viewport_up = ,Button0,,0,false
as_put_viewport_down = ,Button0,,0,false
as_put_center = <Super>KP_Begin,Button0,,0,false
as_put_left = <Super>KP_Left,Button0,,0,false
as_put_right = <Super>KP_Right,Button0,,0,false
as_put_top = <Super>KP_Up,Button0,,0,false
as_put_bottom = <Super>KP_Down,Button0,,0,false
as_put_topleft = <Super>KP_Home,Button0,,0,false
as_put_topright = <Super>KP_Prior,Button0,,0,false
as_put_bottomleft = <Super>KP_End,Button0,,0,false
as_put_bottomright = <Super>KP_Next,Button0,,0,false
as_put_restore = <Super>KP_Insert,Button0,,0,false
as_put_pointer = <Super>z,Button0,,0,false
as_put_exact = ,Button0,,0,false
s0_pad_left = 0
s0_pad_right = 0
s0_pad_top = 0
s0_pad_bottom = 0
s0_unfocus_window = false
s0_window_center = false
s0_avoid_offscreen = false

[resizeinfo]
as_fade_time = 500
as_always_show = false
as_text_color = #000000ff
as_gradient_1 = #cccce6cc
as_gradient_2 = #f3f3f3cc
as_gradient_3 = #d9d9d9cc

[clone]
as_initiate = ,<Shift><Super>Button1,,0,false

[place]
s0_workarounds = true
s0_mode = 2
s0_position_matches = 
s0_position_x_values = 
s0_position_y_values = 
s0_viewport_matches = 
s0_viewport_x_values = 
s0_viewport_y_values = 

[zoom]
as_initiate = ,<Super>Button3,,0,false
as_zoom_in = ,<Super>Button4,,0,false
as_zoom_out = ,<Super>Button5,,0,false
as_zoom_pan = ,<Super>Button2,,0,false
s0_filter_linear = false

[neg]
as_window_toggle = <Super>n,Button0,,0,false
as_screen_toggle = <Super>m,Button0,,0,false
s0_neg_match = any
s0_exclude_match = type=Desktop

[animation]
s0_close_effects = 12;9;9
s0_close_durations = 200;150;150
s0_close_matches = ((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver);(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal);(type=Tooltip | Notification)
s0_close_options = ;;
s0_close_random_effects = 0;1;2;3;4;5;6;7;8;9;10;11;12;13;14;15;16;17;18;19
s0_open_effects = 11;9;9
s0_open_durations = 200;150;150
s0_open_matches = ((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver);(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal);(type=Tooltip | Notification)
s0_open_options = ;;
s0_open_random_effects = 0;1;2;3;4;5;6;7;8;9;10;11;12;13;14;15;16;17;18;19
s0_minimize_effects = 19
s0_minimize_durations = 300
s0_minimize_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown)
s0_minimize_options = 
s0_minimize_random_effects = 0;1;2;3;4;5;6;7;8;9;10;11;12;13;14;15;16;17
s0_shade_effects = 4
s0_shade_durations = 300
s0_shade_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown)
s0_shade_options = 
s0_shade_random_effects = 0;1;2
s0_focus_effects = 2
s0_focus_durations = 150
s0_focus_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown)
s0_focus_options = 
s0_airplane_fly_to_taskbar = true
s0_fire_particles = 1000
s0_fire_color = #ff3305ff
s0_fire_direction = 0
s0_fire_constant_speed = false
s0_fire_smoke = false
s0_fire_mystical = false
s0_beam_spacing = 5
s0_beam_color = #7f7f7fff
s0_glide1_zoom_to_taskbar = false
s0_glide2_zoom_to_taskbar = true
s0_zoom_from_center = 0
s0_rollup_fixed_interior = false
s0_sidekick_zoom_from_center = 0
s0_dream_zoom_to_taskbar = true
s0_magic_lamp_moving_end = true
s0_magic_lamp_grid_res = 100
s0_magic_lamp_max_waves = 3
s0_magic_lamp_open_start_width = 30
s0_vacuum_moving_end = true
s0_vacuum_grid_res = 100
s0_vacuum_open_start_width = 30
s0_curved_fold_zoom_to_taskbar = true
s0_horizontal_folds_num_folds = 3
s0_horizontal_folds_zoom_to_taskbar = true
s0_domino_direction = 5
s0_razr_direction = 5
s0_explode_gridx = 13
s0_explode_gridy = 10
s0_explode_tessellation = 0
s0_fold_gridx = 3
s0_fold_gridy = 3
s0_fold_dir = 1
s0_skewer_direction = 8
s0_skewer_tessellation = 0
s0_skewer_gridx = 6
s0_skewer_gridy = 4
s0_skewer_rotation = 0
s0_all_random = false
s0_time_step = 10
s0_time_step_intense = 30

[widget]
as_toggle = F9,Button0,,0,false
s0_match = 
s0_end_on_click = true
s0_bg_brightness = 50
s0_bg_saturation = 100

[imgjpeg]
as_quality = 80

[cube]
as_unfold = <Control><Alt>Down,Button0,,0,false
as_next_slide = space,Button0,,0,false
as_prev_slide = ,Button0,,0,false
s0_color = #cdbe70ff
s0_in = false
s0_scale_image = false
s0_images = 
s0_skydome = false
s0_skydome_image = 
s0_skydome_animated = true
s0_skydome_gradient_start_color = #0db1fdff
s0_skydome_gradient_end_color = #feffc7ff
s0_mipmap = true
s0_backgrounds = 
s0_adjust_image = false
s0_transparent_manual_only = true
s0_multioutput_mode = 0

[move]
as_initiate = <Alt>F7,<Alt>Button1,,0,false
as_opacity = 100
as_constrain_y = true
as_snapoff_maximized = false
as_lazy_positioning = true

[cubereflex]
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_auto_zoom = true
s0_zoom_manual_only = true
s0_mode = 0

[expo]
as_expo = <Super>e,Button0,,0,false
as_double_click_time = 500
as_rotate = false
as_expo_immediate_move = false
as_expo_animation = 2
as_reflection = true
as_ground_color1 = #b3b3b3cc
as_ground_color2 = #b3b3b300
as_mipmaps = false
as_multioutput_mode = 0
as_hide_docks = true

[scalefilter]
s0_timeout = 0
s0_filter_case_insensitive = false
s0_filter_display = true
s0_font_bold = true
s0_font_size = 24
s0_border_size = 5
s0_font_color = #ffffffff
s0_back_color = #00000099

[fade]
s0_window_match = any
s0_visual_bell = true
s0_fullscreen_visual_bell = false

[reflex]
s0_file = reflection.png
s0_match = any
s0_window = false
s0_decoration = true
s0_threshold = 1
s0_moving = true

[annotate]
as_initiate = ,<Alt><Super>Button1,,0,false
as_draw = ,Button0,,0,false
as_erase = ,<Alt><Super>Button3,,0,false
as_clear = <Alt><Super>k,Button0,,0,false
as_fill_color = #ff0000ff
as_stroke_color = #00ff00ff

[colorfilter]
as_toggle_window = <Super>f,Button0,,0,false
as_toggle_screen = <Super>d,Button0,,0,false
as_switch_filter = <Super>s,Button0,,0,false
s0_filters = negative;negative-green;blueish-filter;sepia;grayscale
s0_filter_decorations = false
s0_filter_match = any
s0_exclude_match = type=Desktop

[extrawm]
as_activate = ,Button0,,0,false
as_toggle_redirect = ,Button0,,0,false
as_toggle_fullscreen = ,Button0,,0,false
as_toggle_always_on_top = ,Button0,,0,false
as_toggle_sticky = ,Button0,,0,false

```

---

### Post by itsbradman on 2007-10-30
I'll check it out when I'll get home and give you more specific info.

---

### Post by DouglasAWh on 2007-11-01
I figured it out!  It was pretty simple, actually.  The problem I was only looking in the check boxes under General Settings.  If you actually click on General Settings, the Desktop Size, there is a setting for "number of desktops."  I remember playing with this in Beryl, I just couldn't find it in Compiz Fusion!

However, there are still a couple problems...one of which I can live with.  My theme is still not as shiny and as OS X looking as Feisty.  I played with Emerald and I'm fine with what I've got.  

The bigger issue is that whenever I open a new window of any sort, it left-top aligns...underneath my top GNOME bar (whatever that is called).  This is very irritating because I can't drag it via the top or close it or maximize or minimize without going to the taskbar.

Thanks!

---


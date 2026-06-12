---
title: "Compiz Sphere had working on Ubuntu 10.10 now on 14.04"
date: 2015-04-25
forum: Desktop Environments
---

### Post by highspider on 2015-04-25
Backed up all my personal stuff from **Ubuntu 10.10** and jumped distro's (format and fresh install) **Ubuntu 14.04**

I get strange bleeding light with my desktop (note the pictures) compizconfig manger because I think I have something configured wrong

[ATTACH=CONFIG]261545[/ATTACH][ATTACH=CONFIG]261546[/ATTACH]                                                        [ATTACH=CONFIG]261547[/ATTACH][ATTACH=CONFIG]261548[/ATTACH]
Pic 1 My new install with sphere set up                                                                 Pic
Pic 2 My new install with sphere and skydome set up                                               
Pic 3 My old install with everything working
Pic 4 My old install with everything working

1st of all this is same PC Hardware as was working on 10.10 
2nd of all I've I reinstalled the NVIDIA GeForce 210 (open source) for my GT218 graphics card
3rd ofcources I installed compizconfig-settings-manager compiz-plugins compiz-plugins-extra

I backed up my old compiz profile before formatting my older distro. I tried to just import my old profile with CCSM but It doesn't work at all. nothing on desktop works right after import.
I thought I could import then just fix Unity. But I get no cube or sphere before and after fixing Unity

So I've been searching every site on compiz cube and sphere and trying to manually make changes to compiz. I cant get it to work.

**My old settings from oldsettings.profile **
```
[scale]
as_key_bindings_toggle = true
as_button_bindings_toggle = false
as_initiate_edge = 
as_initiate_key = <Super>w
as_initiate_button = Disabled
as_initiate_all_edge = 
as_initiate_all_button = Disabled
as_initiate_all_key = <Super>a
as_initiate_group_edge = 
as_initiate_group_button = Disabled
as_initiate_group_key = Disabled
as_initiate_output_edge = 
as_initiate_output_button = Disabled
as_initiate_output_key = Disabled
as_show_desktop = true
s0_spacing = 12
s0_speed = 2.400000
s0_timestep = 0.100000
s0_darken_back = false
s0_opacity = 100
s0_overlay_icon = 0
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_hover_time = 750
s0_multioutput_mode = 0

[video]
as_yv12 = true

[firepaint]
as_initiate_key = Disabled
as_initiate_button = <Shift><Super>Button1
as_clear_key = <Shift><Super>c
as_clear_button = Disabled
s0_num_particles = 3000
s0_fire_size = 15.000000
s0_fire_slowdown = 0.500000
s0_fire_life = 0.700000
s0_fire_color = #ff3305ff
s0_fire_mystical = false
s0_bg_brightness = 50

[move]
as_initiate_button = <Alt>Button1
as_initiate_key = <Alt>F7
as_opacity = 70
as_constrain_y = true
as_snapoff_maximized = false
as_lazy_positioning = true

[session]
as_save_legacy = false
as_ignore_match = 

[bench]
as_initiate_key = <Super>F12
as_disable_limiter = true
as_output_screen = true
as_position_x = 0
as_position_y = 0
as_output_console = false
as_console_update_time = 5

[clone]
as_initiate_button = <Shift><Super>Button1

[water]
as_initiate_key = <Control><Super>
as_toggle_rain_key = <Shift>F9
as_toggle_wiper_key = <Shift>F8
as_offset_scale = 1.000000
as_rain_delay = 250
as_title_wave = false

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

[mag]
as_initiate = <Super>m
as_zoom_in_button = <Shift><Super>Button4
as_zoom_out_button = <Shift><Super>Button5
s0_mode = 0
s0_zoom_factor = 2.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_keep_screen = true
s0_box_width = 300
s0_box_height = 200
s0_border = 2
s0_box_color = #000000ff
s0_overlay = Gnome/overlay.png
s0_mask = Gnome/mask.png
s0_x_offset = 155
s0_y_offset = 155
s0_radius = 200

[animationaddon]
s0_airplane_path_length = 1.000000
s0_airplane_fly_to_taskbar = true
s0_beam_size = 8.000000
s0_beam_spacing = 5
s0_beam_color = #7f7f7fff
s0_beam_slowdown = 1.000000
s0_beam_life = 0.700000
s0_fire_particles = 1000
s0_fire_size = 5.000000
s0_fire_slowdown = 0.500000
s0_fire_life = 0.520300
s0_fire_color = #ff5315ff
s0_fire_direction = 0
s0_fire_constant_speed = true
s0_fire_smoke = true
s0_fire_mystical = false
s0_domino_direction = 5
s0_explode_gridx = 17
s0_explode_gridy = 10
s0_explode_spokes = 30
s0_explode_tiers = 9
s0_explode_thickness = 15.000000
s0_explode_tessellation = 0
s0_fold_gridx = 3
s0_fold_gridy = 9
s0_fold_dir = 1
s0_glide3_away_position = -0.400000
s0_glide3_away_angle = 55.000000
s0_glide3_thickness = 0.000000
s0_razr_direction = 5
s0_skewer_direction = 8
s0_skewer_tessellation = 0
s0_skewer_gridx = 6
s0_skewer_gridy = 4
s0_skewer_thickness = 8.000000
s0_skewer_rotation = 0
s0_time_step_intense = 30

[shelf]
as_trigger_key = <Super>l
as_reset_key = Disabled
as_triggerscreen_key = <Super>p
as_dec_button = <Alt><Super>Button4
as_inc_button = <Alt><Super>Button5
as_animtime = 150
as_interval = 0.900000

[wallpaper]
s0_bg_image = 
s0_bg_image_pos = 
s0_bg_fill_type = 
s0_bg_color1 = 
s0_bg_color2 = 

[resizeinfo]
as_fade_time = 500
as_always_show = false
as_text_color = #000000ff
as_gradient_1 = #cccce6cc
as_gradient_2 = #f3f3f3cc
as_gradient_3 = #d9d9d9cc

[commands]
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
as_run_command0_key = Disabled
as_run_command1_key = Disabled
as_run_command2_key = Disabled
as_run_command3_key = Disabled
as_run_command4_key = Disabled
as_run_command5_key = Disabled
as_run_command6_key = Disabled
as_run_command7_key = Disabled
as_run_command8_key = Disabled
as_run_command9_key = Disabled
as_run_command10_key = Disabled
as_run_command11_key = Disabled
as_run_command0_button = Disabled
as_run_command1_button = Disabled
as_run_command2_button = Disabled
as_run_command3_button = Disabled
as_run_command4_button = Disabled
as_run_command5_button = Disabled
as_run_command6_button = Disabled
as_run_command7_button = Disabled
as_run_command8_button = Disabled
as_run_command9_button = Disabled
as_run_command10_button = Disabled
as_run_command11_button = Disabled
as_run_command0_edge = 
as_run_command1_edge = 
as_run_command2_edge = 
as_run_command3_edge = 
as_run_command4_edge = 
as_run_command5_edge = 
as_run_command6_edge = 
as_run_command7_edge = 
as_run_command8_edge = 
as_run_command9_edge = 
as_run_command10_edge = 
as_run_command11_edge = 

[workarounds]
as_legacy_fullscreen = false
as_firefox_menu_fix = false
as_ooo_menu_fix = true
as_notification_daemon_fix = false
as_java_fix = true
as_qt_fix = false
as_convert_urgency = false
as_aiglx_fragment_fix = true
as_fglrx_xgl_fix = false
as_force_glx_sync = true
as_sticky_alldesktops = false
as_alldesktop_sticky_match = any

[crashhandler]
as_enabled = true
as_directory = /tmp
as_start_wm = false
as_wm_cmd = 

[animation]
s0_open_effects = animationaddon:Burn;
s0_open_durations = 80;
s0_open_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver);
s0_open_options = ;
s0_open_random_effects = animationaddon:Burn;
s0_close_effects = animationaddon:Explode;
s0_close_durations = 80;
s0_close_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver);
s0_close_options = ;
s0_close_random_effects = animationaddon:Burn;
s0_minimize_effects = animation:Magic Lamp;
s0_minimize_durations = 220;
s0_minimize_matches = (type=Normal | Dialog | ModalDialog | Unknown);
s0_minimize_options = ;
s0_minimize_random_effects = animation:Magic Lamp;
s0_shade_effects = animation:Roll Up;
s0_shade_durations = 300;
s0_shade_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown);
s0_shade_options = ;
s0_shade_random_effects = animation:Roll Up;
s0_focus_effects = animation:Wave;
s0_focus_durations = 150;
s0_focus_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown) & !(name=compiz);
s0_focus_options = ;
s0_curved_fold_amp_mult = 0.800000
s0_curved_fold_zoom_to_taskbar = true
s0_dodge_gap_ratio = 0.500000
s0_dream_zoom_to_taskbar = true
s0_glide1_away_position = 1.000000
s0_glide1_away_angle = 50.000000
s0_glide1_zoom_to_taskbar = false
s0_glide2_away_position = 0.500000
s0_glide2_away_angle = -50.000000
s0_glide2_zoom_to_taskbar = true
s0_horizontal_folds_amp_mult = 1.000000
s0_horizontal_folds_num_folds = 3
s0_horizontal_folds_zoom_to_taskbar = true
s0_magic_lamp_moving_end = true
s0_magic_lamp_grid_res = 100
s0_magic_lamp_max_waves = 3
s0_magic_lamp_amp_min = 200.000000
s0_magic_lamp_amp_max = 300.000000
s0_magic_lamp_open_start_width = 30
s0_rollup_fixed_interior = false
s0_sidekick_num_rotations = 0.500000
s0_sidekick_springiness = 0.000000
s0_sidekick_zoom_from_center = 0
s0_vacuum_moving_end = true
s0_vacuum_grid_res = 100
s0_vacuum_open_start_width = 30
s0_wave_width = 0.700000
s0_wave_amp_mult = 1.000000
s0_zoom_from_center = 0
s0_zoom_springiness = 0.000000
s0_all_random = false
s0_time_step = 16

[kdecompat]
s0_plasma_thumbnails = true
s0_present_windows = true
s0_sliding_popups = true
s0_slide_in_duration = 250
s0_slide_out_duration = 250

[rotate]
as_edge_flip_pointer = false
as_edge_flip_window = true
as_edge_flip_dnd = true
as_flip_time = 350
as_raise_on_rotate = false
as_initiate_button = <Control><Alt>Button1
as_rotate_left_key = <Control><Alt>Left
as_rotate_left_button = Disabled
as_rotate_right_key = <Control><Alt>Right
as_rotate_right_button = Disabled
as_rotate_left_window_key = <Shift><Control><Alt>Left
as_rotate_left_window_button = Disabled
as_rotate_right_window_key = <Shift><Control><Alt>Right
as_rotate_right_window_button = Disabled
as_rotate_to_key = Disabled
as_rotate_window_key = Disabled
as_rotate_flip_left_edge = Left
as_rotate_flip_right_edge = Right
as_rotate_to_1_key = Disabled
as_rotate_to_2_key = Disabled
as_rotate_to_3_key = Disabled
as_rotate_to_4_key = Disabled
as_rotate_to_5_key = Disabled
as_rotate_to_6_key = Disabled
as_rotate_to_7_key = Disabled
as_rotate_to_8_key = Disabled
as_rotate_to_9_key = Disabled
as_rotate_to_10_key = Disabled
as_rotate_to_11_key = Disabled
as_rotate_to_12_key = Disabled
as_rotate_to_1_window_key = Disabled
as_rotate_to_2_window_key = Disabled
as_rotate_to_3_window_key = Disabled
as_rotate_to_4_window_key = Disabled
as_rotate_to_5_window_key = Disabled
as_rotate_to_6_window_key = Disabled
as_rotate_to_7_window_key = Disabled
as_rotate_to_8_window_key = Disabled
as_rotate_to_9_window_key = Disabled
as_rotate_to_10_window_key = Disabled
as_rotate_to_11_window_key = Disabled
as_rotate_to_12_window_key = Disabled
s0_invert_y = false
s0_sensitivity = 1.100000
s0_acceleration = 4.000000
s0_snap_top = false
s0_snap_bottom = false
s0_speed = 2.000000
s0_timestep = 1.000000
s0_zoom = 1.500000

[fs]
as_mount_point = compiz

[expo]
as_expo_key = <Super>e
as_expo_button = Disabled
as_expo_edge = 
as_double_click_time = 500
as_dnd_button = Button1
as_exit_button = Button3
as_next_vp_button = Button5
as_prev_vp_button = Button4
as_zoom_time = 0.300000
as_expo_immediate_move = false
as_expo_animation = 0
as_deform = 0
as_distance = 0.000000
as_vp_distance = 0.800000
as_aspect_ratio = 1.000000
as_curve = 0.500000
as_hide_docks = false
as_mipmaps = false
as_multioutput_mode = 0
as_vp_brightness = 80.000000
as_vp_saturation = 100.000000
as_reflection = true
as_ground_color1 = #b3b3b3cc
as_ground_color2 = #b3b3b300
as_ground_size = 0.500000
as_scale_factor = 1.000000

[group]
as_select_button = Disabled
as_select_single_key = <Super>s
as_group_key = <Super>g
as_ungroup_key = <Super>u
as_remove_key = <Super>r
as_close_key = <Super>c
as_ignore_key = <Super>x
as_tabmode_key = <Super>t
as_change_tab_left_key = <Super>Left
as_change_tab_right_key = <Super>Right
as_change_color_key = Disabled
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
s0_fill_color = #00000055
s0_line_color = #000000ab
s0_mipmaps = false
s0_untab_on_close = false
s0_autotab_create = false
s0_tabbar_show_delay = 0.400000
s0_tabbing_speed = 1.200000
s0_tabbing_timestep = 1.500000
s0_fade_time = 0.200000
s0_pulse_time = 0.600000
s0_reflex_time = 0.500000
s0_fade_text_time = 0.250000
s0_visibility_time = 0.500000
s0_change_animation_time = 0.500000
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
s0_dnd_ungroup_window = true
s0_drag_hover_time = 0.500000
s0_drag_spring_k = 8.000000
s0_drag_friction = 35.000000
s0_drag_y_distance = 400
s0_drag_speed_limit = 800
s0_glow = true
s0_glow_size = 64
s0_glow_type = 0

[wobbly]
as_snap_key = <Shift>
as_snap_inverted = true
as_shiver = false
s0_friction = 2.500000
s0_spring_k = 8.000000
s0_grid_resolution = 8
s0_min_grid_size = 8
s0_map_effect = 0
s0_focus_effect = 0
s0_map_window_match = Splash | DropdownMenu | PopupMenu | Tooltip | Notification | Combo | Dnd | Unknown
s0_focus_window_match = 
s0_grab_window_match = 
s0_move_window_match = Toolbar | Menu | Utility | Dialog | Normal | Unknown
s0_maximize_effect = true

[mblur]
as_initiate_key = <Control>F12
s0_mode = 0
s0_strength = 20.000000
s0_on_transformed_screen = false

[addhelper]
as_toggle_key = <Super>p
as_window_types = Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal
as_ononinit = false
as_brightness = 30
as_saturation = 50
as_opacity = 100

[ring]
as_next_key = <Super>Tab
as_next_button = Disabled
as_prev_key = <Shift><Super>Tab
as_prev_button = Disabled
as_next_all_key = <Alt><Super>Tab
as_next_all_button = Disabled
as_prev_all_key = <Shift><Alt><Super>Tab
as_prev_all_button = Disabled
as_next_group_key = Disabled
as_next_group_button = Disabled
as_prev_group_key = Disabled
as_prev_group_button = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
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
s0_min_brightness = 0.500000
s0_min_scale = 0.400000
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 0

[fade]
s0_fade_mode = 0
s0_fade_speed = 5.000000
s0_fade_time = 100
s0_window_match = any & !(title=notify-osd)
s0_visual_bell = false
s0_fullscreen_visual_bell = true
s0_minimize_open_close = true
s0_dim_unresponsive = true
s0_unresponsive_brightness = 65
s0_unresponsive_saturation = 0

[scaleaddon]
as_close_key = Disabled
as_close_button = Button2
as_pull_key = Disabled
as_pull_button = Disabled
as_zoom_key = Disabled
as_zoom_button = Button3
s0_window_title = 1
s0_title_bold = false
s0_title_size = 13
s0_border_size = 3
s0_font_color = #ffffffff
s0_back_color = #00000099
s0_window_highlight = false
s0_highlight_color = #ffffff96
s0_layout_mode = 0
s0_constrain_pull_to_screen = true
s0_exit_after_pull = false

[imgjpeg]
as_quality = 80

[showmouse]
as_initiate = <Super>k
as_initiate_button = Disabled
as_initiate_edge = 
s0_num_particles = 500
s0_size = 10.000000
s0_slowdown = 1.000000
s0_life = 0.700000
s0_darken = 0.900000
s0_blend = true
s0_color = #ffdf3fff
s0_random = false
s0_rotation_speed = 0.500000
s0_radius = 100
s0_emiters = 3

[place]
s0_workarounds = true
s0_mode = 2
s0_multioutput_mode = 0
s0_force_placement_match = 
s0_position_matches = 
s0_position_x_values = 
s0_position_y_values = 
s0_position_constrain_workarea = 
s0_mode_matches = 
s0_mode_modes = 
s0_viewport_matches = 
s0_viewport_x_values = 
s0_viewport_y_values = 

[decoration]
as_shadow_radius = 9.000000
as_shadow_opacity = 0.500000
as_shadow_color = #00000000
as_shadow_x_offset = 1
as_shadow_y_offset = 5
as_command = /usr/bin/compiz-decorator
as_mipmap = false
as_decoration_match = any
as_shadow_match = any

[cubeaddon]
as_top_next_key = space
as_top_next_button = Disabled
as_top_prev_key = Disabled
as_top_prev_button = Disabled
as_bottom_next_key = Disabled
as_bottom_next_button = Disabled
as_bottom_prev_key = Disabled
as_bottom_prev_button = Disabled
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.202800
s0_intensity = 0.400000
s0_auto_zoom = true
s0_zoom_manual_only = true
s0_mode = 0
s0_deformation = 2
s0_unfold_deformation = true
s0_cylinder_manual_only = true
s0_deform_caps = true
s0_sphere_aspect = 0.512900
s0_draw_top = true
s0_draw_bottom = true
s0_adjust_top = false
s0_adjust_bottom = false
s0_top_scale = true
s0_bottom_scale = true
s0_top_aspect = true
s0_bottom_aspect = true
s0_top_clamp = true
s0_bottom_clamp = true
s0_top_color = #ffffffff
s0_bottom_color = #ffffffff
s0_top_images = /home/keegan/Pictures/Photos/xlarge.cool-black-dragon-fiery (copy).jpg;
s0_bottom_images = /home/keegan/Pictures/Photos/xlarge.cool-black-dragon-fiery (copy).jpg;

[core]
as_active_plugins = core;ccp;move;resize;place;decoration;session;rege  x;dbus;png;commands;workarounds;text;imgjpeg;gnome  compat;shift;vpswitch;neg;mousepoll;svg;resizeinfo  ;animation;wobbly;fade;cube;3d;scale;animationaddo  n;rotate;scaleaddon;cubeaddon;expo;ezoom;staticswi  tcher;
as_audible_bell = true
as_ignore_hints_when_maximized = true
as_hide_skip_taskbar_windows = true
as_edge_delay = 0
as_cursor_theme = Azenis
as_cursor_size = 18
as_ping_delay = 5000
as_texture_filter = 1
as_click_to_focus = true
as_raise_on_click = true
as_autoraise = false
as_autoraise_delay = 500
as_close_window_key = <Alt>F4
as_close_window_button = Disabled
as_raise_window_key = Disabled
as_raise_window_button = <Control>Button6
as_lower_window_key = Disabled
as_lower_window_button = <Alt>Button6
as_unmaximize_window_key = <Alt>F5
as_minimize_window_key = <Alt>F9
as_minimize_window_button = Disabled
as_maximize_window_key = Disabled
as_maximize_window_horizontally_key = Disabled
as_maximize_window_vertically_key = Disabled
as_window_menu_button = <Alt>Button3
as_window_menu_key = <Alt>space
as_show_desktop_key = <Super>d
as_show_desktop_edge = 
as_toggle_window_maximized_key = <Alt>F10
as_toggle_window_maximized_button = Disabled
as_toggle_window_maximized_horizontally_key = Disabled
as_toggle_window_maximized_vertically_key = Disabled
as_toggle_window_shaded_key = Disabled
as_slow_animations_key = Disabled
s0_hsize = 4
s0_vsize = 1
s0_number_of_desktops = 1
s0_lighting = true
s0_detect_refresh_rate = true
s0_refresh_rate = 50
s0_detect_outputs = true
s0_overlapping_outputs = 0
s0_outputs = 1360x768+0+0;
s0_sync_to_vblank = false
s0_focus_prevention_level = 1
s0_focus_prevention_match = !(class=Polkit-gnome-authentication-agent-1)
s0_unredirect_fullscreen_windows = false
s0_default_icon = icon
s0_force_independent_output_painting = false
s0_texture_compression = false

[winrules]
s0_skiptaskbar_match = 
s0_skippager_match = 
s0_above_match = 
s0_below_match = 
s0_sticky_match = 
s0_fullscreen_match = 
s0_maximize_match = 
s0_no_argb_match = 
s0_no_move_match = 
s0_no_resize_match = 
s0_no_minimize_match = 
s0_no_maximize_match = 
s0_no_close_match = 
s0_no_focus_match = 
s0_size_matches = 
s0_size_width_values = 
s0_size_height_values = 

[gnomecompat]
as_main_menu_key = <Alt>F1
as_run_key = <Alt>F2
as_command_screenshot = gnome-screenshot
as_run_command_screenshot_key = Print
as_command_window_screenshot = gnome-screenshot --window
as_run_command_window_screenshot_key = <Alt>Print
as_command_terminal = gnome-terminal
as_run_command_terminal_key = <Control><Alt>t

[cube]
as_unfold_key = <Control><Alt>Down
as_next_slide_key = Disabled
as_prev_slide_key = Disabled
s0_mipmap = true
s0_multioutput_mode = 2
s0_in = false
s0_acceleration = 4.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_color = #cdbe70ff
s0_scale_image = false
s0_images = /usr/share/gdm/themes/Human/ubuntu.png;
s0_adjust_image = false
s0_skydome = true
s0_skydome_image = /home/keegan/Pictures/Photos/lightning.jpg
s0_skydome_animated = true
s0_skydome_gradient_start_color = #0db1fdff
s0_skydome_gradient_end_color = #feffc7ff
s0_active_opacity = 100.000000
s0_inactive_opacity = 100.000000
s0_transparent_manual_only = true

[reflex]
s0_file = reflection.png
s0_match = any
s0_window = false
s0_decoration = true
s0_threshold = 1
s0_moving = true

[shift]
as_initiate_key = <Shift><Super>s
as_initiate_button = Disabled
as_initiate_edge = 
as_initiate_all_key = Disabled
as_initiate_all_button = Disabled
as_initiate_all_edge = 
as_terminate_button = Button3
as_next_key = <Super>Tab
as_next_button = Disabled
as_prev_key = <Shift><Super>Tab
as_prev_button = Disabled
as_next_all_key = <Alt><Super>Tab
as_next_all_button = Disabled
as_prev_all_key = <Shift><Alt><Super>Tab
as_prev_all_button = Disabled
as_next_group_key = Disabled
as_next_group_button = Disabled
as_prev_group_key = Disabled
as_prev_group_button = Disabled
s0_speed = 1.500000
s0_shift_speed = 1.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_minimized = true
s0_mouse_speed = 10.000000
s0_click_duration = 500
s0_mode = 0
s0_size = 50
s0_background_intensity = 0.500000
s0_hide_all = false
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_intensity = 0.400000
s0_flip_rotation = 30
s0_cover_offset = 0.000000
s0_overlay_icon = 1
s0_mipmaps = false
s0_multioutput_mode = 0
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 2

[extrawm]
as_toggle_redirect_key = Disabled
as_toggle_fullscreen_key = Disabled
as_toggle_always_on_top_key = Disabled
as_toggle_sticky_key = Disabled
as_activate_demands_attention_key = Disabled
as_to_next_output_key = Disabled

[blur]
as_pulse = false
s0_blur_speed = 3.500000
s0_focus_blur_match = toolbar | menu | utility | normal | dialog | modaldialog
s0_focus_blur = false
s0_alpha_blur_match = any
s0_alpha_blur = true
s0_filter = 0
s0_gaussian_radius = 3
s0_gaussian_strength = 1.000000
s0_mipmap_lod = 2.500000
s0_saturation = 100
s0_occlusion = true
s0_independent_tex = false

[ezoom]
as_zoom_in_button = <Super>Button4
as_zoom_in_key = Disabled
as_zoom_out_button = <Super>Button5
as_zoom_out_key = Disabled
as_zoom_box_button = <Super>Button2
as_center_mouse_key = Disabled
as_zoom_specific_1_key = Disabled
as_zoom_spec1 = 1.000000
as_zoom_specific_2_key = Disabled
as_zoom_spec2 = 0.500000
as_zoom_specific_3_key = Disabled
as_zoom_spec3 = 0.200000
as_spec_target_focus = true
as_lock_zoom_key = Disabled
as_pan_left_key = Disabled
as_pan_right_key = Disabled
as_pan_up_key = Disabled
as_pan_down_key = Disabled
as_fit_to_zoom_key = Disabled
as_fit_to_window_key = Disabled
s0_zoom_factor = 1.150000
s0_minimum_zoom = 0.125000
s0_sync_mouse = true
s0_scale_mouse = false
s0_scale_mouse_dynamic = true
s0_scale_mouse_static = 0.200000
s0_hide_original_mouse = false
s0_restrain_mouse = false
s0_mouse_pan = false
s0_restrain_margin = 5
s0_pan_factor = 0.100000
s0_follow_focus = true
s0_focus_fit_window = false
s0_autoscale_min = 0.250000
s0_always_focus_fit_window = false
s0_follow_focus_delay = 1
s0_speed = 25.000000
s0_timestep = 1.200000
s0_filter_linear = true

[snap]
as_avoid_snap = 0;
s0_snap_type = 0;
s0_edges_categories = 0;1;
s0_resistance_distance = 18
s0_attraction_distance = 20

[staticswitcher]
as_next_button = Disabled
as_next_key = <Alt>Tab
as_prev_button = Disabled
as_prev_key = <Shift><Alt>Tab
as_next_all_button = Disabled
as_next_all_key = <Control><Alt>Tab
as_prev_all_button = Disabled
as_prev_all_key = <Shift><Control><Alt>Tab
as_next_group_button = Disabled
as_next_group_key = Disabled
as_prev_group_button = Disabled
as_prev_group_key = Disabled
as_next_no_popup_button = Disabled
as_next_no_popup_key = Disabled
as_prev_no_popup_button = Disabled
as_prev_no_popup_key = Disabled
as_next_panel_button = Disabled
as_next_panel_key = Disabled
as_prev_panel_button = Disabled
as_prev_panel_key = Disabled
s0_speed = 4.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | Toolbar | Utility | Unknown
s0_minimized = true
s0_auto_change_vp = true
s0_popup_delay = 0.200000
s0_mouse_select = true
s0_saturation = 100
s0_brightness = 100
s0_opacity = 0
s0_icon = true
s0_mipmap = true
s0_row_align = 1
s0_highlight_mode = 1
s0_highlight_rect_hidden = 1
s0_highlight_color = #00000096
s0_highlight_border_color = #000000c8
s0_highlight_border_inlay_color = #c8c8c8c8

[maximumize]
as_ignore_sticky = true
as_ignore_overlapping = false
as_allow_shrink = true
as_maximumize_left = true
as_maximumize_right = true
as_maximumize_up = true
as_maximumize_down = true
as_trigger_max_key = <Super>M
as_trigger_max_left = Disabled
as_trigger_max_right = Disabled
as_trigger_max_up = Disabled
as_trigger_max_down = Disabled
as_trigger_max_horizontally = Disabled
as_trigger_max_vertically = Disabled
as_trigger_max_up_left = Disabled
as_trigger_max_up_right = Disabled
as_trigger_max_down_left = Disabled
as_trigger_max_down_right = Disabled
as_trigger_min_key = <Shift><Super>M
as_trigger_min_left = Disabled
as_trigger_min_right = Disabled
as_trigger_min_up = Disabled
as_trigger_min_down = Disabled
as_trigger_min_horizontally = Disabled
as_trigger_min_vertically = Disabled
as_trigger_min_up_left = Disabled
as_trigger_min_up_right = Disabled
as_trigger_min_down_left = Disabled
as_trigger_min_down_right = Disabled

[showdesktop]
s0_speed = 1.200000
s0_timestep = 0.100000
s0_direction = 6
s0_window_match = type=toolbar | type=utility | type=dialog | type=normal
s0_window_opacity = 0.300000
s0_window_part_size = 20

[vpswitch]
as_begin_key = Disabled
as_switch_to_1_key = Disabled
as_switch_to_2_key = Disabled
as_switch_to_3_key = Disabled
as_switch_to_4_key = Disabled
as_switch_to_5_key = Disabled
as_switch_to_6_key = Disabled
as_switch_to_7_key = Disabled
as_switch_to_8_key = Disabled
as_switch_to_9_key = Disabled
as_switch_to_10_key = Disabled
as_switch_to_11_key = Disabled
as_switch_to_12_key = Disabled
as_left_button = Disabled
as_right_button = Disabled
as_up_button = Disabled
as_down_button = Disabled
as_next_button = Disabled
as_prev_button = Disabled
as_initiate_button = Button2
as_init_plugin = rotate
as_init_action = initiate_button

[neg]
as_window_toggle_key = <Super>n
as_screen_toggle_key = <Super>m
s0_neg_match = any
s0_exclude_match = type=Desktop

[3d]
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_min_cube_size = 60
s0_max_window_space = 10
s0_manual_only = true
s0_width = 0.300000
s0_bevel = 0
s0_width_color = #333333ff
s0_width_color_inactive = #333333ff
s0_bevel_topleft = true
s0_bevel_topright = true
s0_bevel_bottomleft = false
s0_bevel_bottomright = false

[thumbnail]
s0_thumb_size = 200
s0_show_delay = 100
s0_border = 16
s0_thumb_color = #0000007f
s0_fade_speed = 0.500000
s0_current_viewport = true
s0_always_on_top = true
s0_window_like = true
s0_mipmap = false
s0_title_enabled = true
s0_font_bold = true
s0_font_size = 12
s0_font_color = #000000ff

[grid]
as_put_center_key = <Control><Alt>KP_5
as_put_left_key = <Control><Alt>KP_4
as_put_right_key = <Control><Alt>KP_6
as_put_top_key = <Control><Alt>KP_8
as_put_bottom_key = <Control><Alt>KP_2
as_put_topleft_key = <Control><Alt>KP_7
as_put_topright_key = <Control><Alt>KP_9
as_put_bottomleft_key = <Control><Alt>KP_1
as_put_bottomright_key = <Control><Alt>KP_3

[colorfilter]
as_toggle_window_key = <Super>f
as_toggle_screen_key = <Super>d
as_switch_filter_key = <Control><Super>s
s0_filters = negative;negative-green;blueish-filter;sepia;grayscale;deuteranopia;protonopia;
s0_filter_decorations = false
s0_filter_match = any

[fadedesktop]
s0_fadetime = 500
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown

[zoom]
as_initiate_button = <Super>Button3
as_zoom_in_button = <Super>Button4
as_zoom_out_button = <Super>Button5
as_zoom_pan_button = <Super>Button2
s0_speed = 1.500000
s0_timestep = 1.200000
s0_zoom_factor = 2.000000
s0_filter_linear = false

[scalefilter]
s0_timeout = 0
s0_filter_case_insensitive = true
s0_filter_display = true
s0_font_bold = true
s0_font_size = 24
s0_border_size = 5
s0_font_color = #ffffffff
s0_back_color = #00000099

[widget]
as_toggle_key = F9
as_toggle_button = Disabled
as_toggle_edge = 
s0_match = 
s0_end_on_click = true
s0_fade_time = 0.500000
s0_bg_brightness = 50
s0_bg_saturation = 100

[titleinfo]
s0_show_remote_machine = true
s0_show_root = true

[opacify]
as_toggle_key = <Super>o
as_toggle_reset = true
as_timeout = 700
as_init_toggle = true
s0_only_if_block = false
s0_focus_instant = false
s0_no_delay_change = false
s0_window_match = Normal | Dialog | ModalDialog | Utility | Toolbar | Fullscreen
s0_active_opacity = 100
s0_passive_opacity = 10

[obs]
as_opacity_increase_key = Disabled
as_opacity_increase_button = <Alt>Button4
as_opacity_decrease_key = Disabled
as_opacity_decrease_button = <Alt>Button5
as_brightness_increase_key = Disabled
as_brightness_increase_button = Disabled
as_brightness_decrease_key = Disabled
as_brightness_decrease_button = Disabled
as_saturation_increase_key = Disabled
as_saturation_increase_button = Disabled
as_saturation_decrease_key = Disabled
as_saturation_decrease_button = Disabled
s0_opacity_step = 5
s0_opacity_matches = 
s0_opacity_values = 
s0_brightness_step = 5
s0_brightness_matches = 
s0_brightness_values = 
s0_saturation_step = 5
s0_saturation_matches = 
s0_saturation_values = 

[mousepoll]
as_mouse_poll_interval = 40

[loginout]
s0_in_match = (iclass=^ksplash)
s0_in_time = 1.000000
s0_in_saturation = 0.000000
s0_in_brightness = 100.000000
s0_in_opacity = 100.000000
s0_out_match = (iclass=ksmserver & (role=logoutdialog | role=logouteffect)) | (class=Libssui-tool & type=Dialog)
s0_out_time = 1.000000
s0_out_saturation = 0.000000
s0_out_brightness = 100.000000
s0_out_opacity = 100.000000

[splash]
as_initiate_key = <Control>F11
as_firststart = true
as_background = splash_background.png
as_logo = splash_logo.png
as_fade_time = 1.000000
as_display_time = 2.000000
as_saturation = 50.000000
as_brightness = 50.000000

[minimize]
s0_speed = 1.500000
s0_timestep = 0.500000
s0_window_match = toolbar | utility | dialog | normal
s0_shade_resistance = 75

[wall]
as_show_switcher = true
as_miniscreen = false
as_preview_timeout = 0.200000
as_preview_scale = 130
as_edge_radius = 5
as_border_width = 7
as_outline_color = #ffffff32
as_background_gradient_base_color = #00000064
as_background_gradient_highlight_color = #00000064
as_background_gradient_shadow_color = #00000064
as_thumb_gradient_base_color = #55555532
as_thumb_gradient_highlight_color = #55555532
as_thumb_highlight_gradient_base_color = #ffffffff
as_thumb_highlight_gradient_shadow_color = #dfdfdfff
as_arrow_base_color = #e6e6e6d9
as_arrow_shadow_color = #dcdcdcd9
as_allow_wraparound = false
as_slide_duration = 0.300000
as_no_slide_match = type=Dock | type=Desktop | state=Sticky
as_left_key = <Control><Alt>Left
as_left_button = Disabled
as_right_key = <Control><Alt>Right
as_right_button = Disabled
as_up_key = <Control><Alt>Up
as_up_button = Disabled
as_down_key = <Control><Alt>Down
as_down_button = Disabled
as_next_key = Disabled
as_next_button = Disabled
as_prev_key = Disabled
as_prev_button = Disabled
as_left_window_key = <Shift><Control><Alt>Left
as_right_window_key = <Shift><Control><Alt>Right
as_up_window_key = <Shift><Control><Alt>Up
as_down_window_key = <Shift><Control><Alt>Down
as_flip_left_edge = Left
as_flip_right_edge = Right
as_flip_up_edge = Top
as_flip_down_edge = Bottom
s0_mmmode = 0
s0_edgeflip_pointer = false
s0_edgeflip_move = false
s0_edgeflip_dnd = false

[annotate]
as_initiate_button = <Alt><Super>Button1
as_erase_button = <Alt><Super>Button3
as_clear_key = <Alt><Super>k
as_clear_button = Disabled
as_fill_color = #ff0000ff
as_stroke_color = #00ff00ff
as_line_width = 3.000000
as_stroke_width = 1.000000

[screenshot]
as_initiate_button = <Super>Button1
as_directory = 
as_launch_app = 

[switcher]
as_next_button = Disabled
as_next_key = <Alt>Tab
as_prev_button = Disabled
as_prev_key = <Shift><Alt>Tab
as_next_all_button = Disabled
as_next_all_key = <Control><Alt>Tab
as_prev_all_button = Disabled
as_prev_all_key = <Shift><Control><Alt>Tab
as_next_no_popup_button = Disabled
as_next_no_popup_key = Disabled
as_prev_no_popup_button = Disabled
as_prev_no_popup_key = Disabled
as_next_panel_button = Disabled
as_next_panel_key = Disabled
as_prev_panel_button = Disabled
as_prev_panel_key = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_mipmap = true
s0_saturation = 100
s0_brightness = 65
s0_opacity = 40
s0_bring_to_front = true
s0_zoom = 1.000000
s0_icon = true
s0_minimized = true
s0_auto_rotate = false

[resize]
as_initiate_normal_key = Disabled
as_initiate_outline_key = Disabled
as_initiate_rectangle_key = Disabled
as_initiate_stretch_key = Disabled
as_initiate_button = <Alt>Button2
as_initiate_key = <Alt>F8
as_mode = 2
as_border_color = #ffffff64
as_fill_color = #0000001e
as_normal_match = 
as_outline_match = 
as_rectangle_match = 
as_stretch_match = 

[put]
as_put_viewport_1_key = Disabled
as_put_viewport_2_key = Disabled
as_put_viewport_3_key = Disabled
as_put_viewport_4_key = Disabled
as_put_viewport_5_key = Disabled
as_put_viewport_6_key = Disabled
as_put_viewport_7_key = Disabled
as_put_viewport_8_key = Disabled
as_put_viewport_9_key = Disabled
as_put_viewport_10_key = Disabled
as_put_viewport_11_key = Disabled
as_put_viewport_12_key = Disabled
as_put_viewport_left_key = Disabled
as_put_viewport_right_key = Disabled
as_put_viewport_up_key = Disabled
as_put_viewport_down_key = Disabled
as_put_center_key = <Super>KP_Begin
as_put_center_button = Disabled
as_put_left_key = Disabled
as_put_left_button = Disabled
as_put_right_key = Disabled
as_put_right_button = Disabled
as_put_top_key = Disabled
as_put_top_button = Disabled
as_put_bottom_key = Disabled
as_put_bottom_button = Disabled
as_put_topleft_key = Disabled
as_put_topleft_button = Disabled
as_put_topright_key = Disabled
as_put_topright_button = Disabled
as_put_bottomleft_key = Disabled
as_put_bottomleft_button = Disabled
as_put_bottomright_key = Disabled
as_put_bottomright_button = Disabled
as_put_restore_key = <Super>KP_Insert
as_put_restore_button = Disabled
as_put_pointer_key = <Super>z
as_put_pointer_button = Disabled
as_put_next_output_key = Disabled
as_put_next_output_button = Disabled
s0_pad_left = 0
s0_pad_right = 0
s0_pad_top = 0
s0_pad_bottom = 0
s0_unfocus_window = false
s0_window_center = false
s0_avoid_offscreen = false
s0_speed = 2.500000
s0_timestep = 0.500000

```

[B]
My new profile with the glicthing light[/B]
```

[imgjpeg]
s0_quality = 80

[cubeaddon]
s0_top_next_key = space
s0_top_next_button = Disabled
s0_top_prev_key = Disabled
s0_top_prev_button = Disabled
s0_bottom_next_key = Disabled
s0_bottom_next_button = Disabled
s0_bottom_prev_key = Disabled
s0_bottom_prev_button = Disabled
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_intensity = 0.400000
s0_auto_zoom = true
s0_zoom_manual_only = true
s0_mode = 0
s0_deformation = 2
s0_unfold_deformation = true
s0_cylinder_manual_only = false
s0_deform_caps = true
s0_sphere_aspect = 1.000000
s0_draw_top = true
s0_draw_bottom = true
s0_adjust_top = false
s0_adjust_bottom = false
s0_top_scale = true
s0_bottom_scale = true
s0_top_aspect = true
s0_bottom_aspect = true
s0_top_clamp = true
s0_bottom_clamp = true
s0_top_images = /home/keegan/Pictures/Photos/xlarge.cool-black-dragon-fiery (copy).jpg;fusioncap.png;
s0_bottom_images = /home/keegan/Pictures/Photos/xlarge.cool-black-dragon-fiery (copy).jpg;compizcap.png;

[showmouse]
s0_initiate = <Super>k
s0_initiate_button = Disabled
s0_initiate_edge = 
s0_rotation_speed = 0.500000
s0_radius = 100
s0_emitters = 3
s0_num_particles = 500
s0_size = 10.000000
s0_slowdown = 1.000000
s0_life = 0.700000
s0_darken = 0.900000
s0_blend = true
s0_color = #ffdf3fff
s0_random = false

[thumbnail]
s0_always_on_top = true
s0_thumb_size = 200
s0_show_delay = 100
s0_fade_speed = 0.500000
s0_border = 16
s0_thumb_color = #0000007f
s0_window_like = true
s0_mipmap = false
s0_current_viewport = false
s0_title_enabled = true
s0_font_bold = true
s0_text_distance = 10
s0_font_size = 12
s0_font_color = #ffffffff
s0_font_background_color = #0000007f

[neg]
s0_window_toggle_key = <Super>n
s0_screen_toggle_key = <Super>m
s0_neg_match = any
s0_exclude_match = type=Desktop
s0_neg_decorations = false

[wizard]
s0_toggle = <Super>w
s0_gx = 0.000000
s0_gy = 0.000500
s0_g_strength = 200;
s0_g_posx = 0;
s0_g_posy = 0;
s0_g_speed = 100;
s0_g_angle = 20;
s0_g_movement = 2;
s0_e_active = false;false;true;true;false;true;true;true;true;tr  ue;
s0_e_name = Fire Ball;Flame Pointer;Magic Pointer;Magic Rain (On/Off);Magic Rain with Gravity Particles;Random Red Explosion;Random Yellow Explosion;Random Green Explosion;Random Blue Explosion;Random Purple Explosion;
s0_e_trigger = 0;0;1;3;0;2;2;2;2;2;
s0_e_posx = 0;0;0;1000;1000;0;0;0;0;0;
s0_e_posy = 0;0;0;0;0;0;0;0;0;0;
s0_e_speed = 100;0;0;0;0;1000;1000;1000;1000;1000;
s0_e_angle = 326;0;0;0;0;13;33;53;73;93;
s0_e_movement = 2;0;0;3;3;3;3;3;3;3;
s0_e_count = 50;20;40;20;20;200;200;200;200;200;
s0_e_h = 67;100;0;0;0;0;167;333;667;833;
s0_e_dh = 100;150;500;500;500;133;133;133;133;133;
s0_e_l = 450;600;650;650;650;650;650;650;650;650;
s0_e_dl = 250;100;150;150;150;150;150;150;150;150;
s0_e_a = 500;400;700;700;700;700;700;700;700;700;
s0_e_da = 200;200;200;200;200;200;200;200;200;200;
s0_e_dx = 0;0;0;1000;1000;0;0;0;0;0;
s0_e_dy = 0;0;0;0;0;0;0;0;0;0;
s0_e_dcirc = 30;5;20;0;0;5;5;5;5;5;
s0_e_vx = 0;0;0;0;0;0;0;0;0;0;
s0_e_vy = 0;-200;0;0;0;0;0;0;0;0;
s0_e_vt = -30;-30;-5;-5;-5;-10;-10;-10;-10;-10;
s0_e_vphi = 0;0;0;0;0;0;0;0;0;0;
s0_e_dvx = 0;50;0;0;0;0;0;0;0;0;
s0_e_dvy = 0;200;0;0;0;0;0;0;0;0;
s0_e_dvcirc = 50;0;100;50;50;500;500;500;500;500;
s0_e_dvt = 30;10;4;3;3;5;5;5;5;5;
s0_e_dvphi = 50;50;50;50;50;50;50;50;50;50;
s0_e_s = 50;20;50;50;50;50;50;50;50;50;
s0_e_ds = 25;10;25;25;25;25;25;25;25;25;
s0_e_snew = 300;50;100;125;125;50;50;50;50;50;
s0_e_dsnew = 150;30;25;50;50;25;25;25;25;25;
s0_e_g = 0;0;0;0;0;0;0;0;0;0;
s0_e_dg = 0;0;0;0;200;0;0;0;0;0;
s0_e_gp = 0;0;0;0;10;0;0;0;0;0;
s0_hard_limit = 3000
s0_soft_limit = 2000
s0_darken = 0.900000
s0_blend = true
s0_tnew = 0.980000
s0_told = 0.400000

[expo]
s0_expo_key = <Super>s
s0_expo_button = Disabled
s0_expo_edge = 
s0_double_click_time = 500
s0_dnd_button = Button1
s0_exit_button = Button3
s0_next_vp_button = Button5
s0_prev_vp_button = Button4
s0_zoom_time = 0.300000
s0_expo_immediate_move = false
s0_expo_animation = 0
s0_deform = 0
s0_curve = 0.500000
s0_x_offset = 64
s0_y_offset = 24
s0_distance = 0.000000
s0_vp_distance = 0.200000
s0_aspect_ratio = 1.000000
s0_hide_docks = false
s0_mipmaps = false
s0_multioutput_mode = 1
s0_vp_brightness = 40.000000
s0_vp_saturation = 100.000000
s0_selected_color = #fb8b00ff
s0_reflection = false
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_scale_factor = 0.750000

[decor]
s0_active_shadow_radius = 8.000000
s0_active_shadow_opacity = 0.800000
s0_active_shadow_color = #00000080
s0_active_shadow_x_offset = 1
s0_active_shadow_y_offset = 1
s0_inactive_shadow_radius = 5.000000
s0_inactive_shadow_opacity = 0.400000
s0_inactive_shadow_color = #000000ff
s0_inactive_shadow_x_offset = 1
s0_inactive_shadow_y_offset = 1
s0_command = /usr/bin/gtk-window-decorator
s0_mipmap = false
s0_decoration_match = any
s0_shadow_match = any

[vpswitch]
s0_begin_key = Disabled
s0_switch_to_1_key = Disabled
s0_switch_to_2_key = Disabled
s0_switch_to_3_key = Disabled
s0_switch_to_4_key = Disabled
s0_switch_to_5_key = Disabled
s0_switch_to_6_key = Disabled
s0_switch_to_7_key = Disabled
s0_switch_to_8_key = Disabled
s0_switch_to_9_key = Disabled
s0_switch_to_10_key = Disabled
s0_switch_to_11_key = Disabled
s0_switch_to_12_key = Disabled
s0_left_button = Disabled
s0_right_button = Disabled
s0_up_button = Disabled
s0_down_button = Disabled
s0_next_button = Disabled
s0_prev_button = Disabled
s0_initiate_button = Button2
s0_init_plugin = rotate
s0_init_action = initiate_button

[animation]
s0_open_effects = animation:Glide 2;animation:Fade;animation:Fade;
s0_open_durations = 120;80;80;
s0_open_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver);(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal);(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd);
s0_open_options = ;;;
s0_open_random_effects = 
s0_close_effects = animation:Glide 2;animation:Fade;animation:Fade;
s0_close_durations = 120;80;50;
s0_close_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver) & !(name=gnome-screenshot);(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal);(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd);
s0_close_options = ;;;
s0_close_random_effects = 
s0_minimize_effects = animation:Zoom;
s0_minimize_durations = 220;
s0_minimize_matches = (type=Normal | Dialog | ModalDialog | Unknown);
s0_minimize_options = ;
s0_minimize_random_effects = 
s0_unminimize_effects = animation:Glide 2;
s0_unminimize_durations = 300;
s0_unminimize_matches = (type=Normal | Dialog | ModalDialog | Unknown);
s0_unminimize_options = ;
s0_unminimize_random_effects = 
s0_shade_effects = animation:Roll Up;
s0_shade_durations = 300;
s0_shade_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown);
s0_shade_options = ;
s0_shade_random_effects = 
s0_focus_effects = animation:Fade;
s0_focus_durations = 150;
s0_focus_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown) & !(name=compiz);
s0_focus_options = ;
s0_all_random = false
s0_time_step = 16
s0_curved_fold_amp_mult = 1.000000
s0_curved_fold_zoom_to_taskbar = true
s0_dodge_mode = 1
s0_dodge_gap_ratio = 0.500000
s0_dream_zoom_to_taskbar = true
s0_glide1_away_position = 1.000000
s0_glide1_away_angle = 0.000000
s0_glide1_zoom_to_taskbar = false
s0_glide2_away_position = -0.100000
s0_glide2_away_angle = 0.000000
s0_glide2_zoom_to_taskbar = true
s0_horizontal_folds_amp_mult = 1.000000
s0_horizontal_folds_num_folds = 3
s0_horizontal_folds_zoom_to_taskbar = true
s0_magic_lamp_moving_end = true
s0_magic_lamp_grid_res = 100
s0_magic_lamp_open_start_width = 30
s0_magic_lamp_wavy_moving_end = true
s0_magic_lamp_wavy_grid_res = 100
s0_magic_lamp_wavy_max_waves = 3
s0_magic_lamp_wavy_amp_min = 200.000000
s0_magic_lamp_wavy_amp_max = 300.000000
s0_magic_lamp_wavy_open_start_width = 30
s0_rollup_fixed_interior = false
s0_sidekick_num_rotations = 0.500000
s0_sidekick_springiness = 0.000000
s0_sidekick_zoom_from_center = 0
s0_wave_width = 0.700000
s0_wave_amp_mult = 1.000000
s0_zoom_from_center = 0
s0_zoom_springiness = 0.080000

[shelf]
s0_trigger_key = <Super>l
s0_reset_key = Disabled
s0_triggerscreen_key = <Super>p
s0_dec_button = <Alt><Super>Button4
s0_inc_button = <Alt><Super>Button5
s0_animtime = 150
s0_interval = 0.900000

[bench]
s0_initiate_key = <Super>F12
s0_fps_limiter_mode = 0
s0_output_screen = true
s0_position_x = 100
s0_position_y = 50
s0_output_console = false
s0_console_update_time = 5

[td]
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_min_cube_size = 60
s0_max_window_space = 10
s0_manual_only = true
s0_width = 0.300000
s0_bevel = 0
s0_width_color = #333333ff
s0_width_color_inactive = #333333ff
s0_bevel_topleft = true
s0_bevel_topright = true
s0_bevel_bottomleft = false
s0_bevel_bottomright = false

[unityshell]
s0_show_menu_bar = <Alt>
s0_lock_screen = <Super>l
s0_show_hud = <Alt>
s0_execute_command = <Alt>F2
s0_show_desktop_key = <Control><Super>d
s0_panel_first_menu = <Alt>F10
s0_panel_opacity = 1.000000
s0_panel_opacity_maximized_toggle = false
s0_background_color = #00000000
s0_dash_blur_experimental = 2
s0_automaximize_value = 75
s0_shortcut_overlay = true
s0_override_decoration_theme = false
s0_shadow_x_offset = 1
s0_shadow_y_offset = 1
s0_active_shadow_radius = 8
s0_active_shadow_color = #00000066
s0_inactive_shadow_radius = 5
s0_inactive_shadow_color = #000000a5
s0_show_launcher = <Super>
s0_keyboard_focus = <Alt>F1
s0_launcher_switcher_forward = <Super>Tab
s0_launcher_switcher_prev = <Shift><Super>Tab
s0_dash_tap_duration = 250
s0_launcher_opacity = 0.666700
s0_launcher_hide_mode = 0
s0_autohide_animation = 3
s0_reveal_trigger = 0
s0_num_launchers = 0
s0_launcher_capture_mouse = true
s0_scroll_inactive_icons = true
s0_launcher_minimize_window = false
s0_edge_responsiveness = 2.000000
s0_reveal_pressure = 20
s0_overcome_pressure = 20
s0_decay_rate = 15
s0_stop_velocity = 65
s0_edge_passed_disabled_ms = 1000
s0_icon_size = 48
s0_backlight_mode = 1
s0_launch_animation = 1
s0_urgent_animation = 2
s0_menus_fadein = 100
s0_menus_fadeout = 120
s0_menus_discovery_duration = 2
s0_menus_discovery_fadein = 200
s0_menus_discovery_fadeout = 300
s0_alt_tab_forward = <Alt>Tab
s0_alt_tab_prev = <Shift><Alt>Tab
s0_alt_tab_forward_all = <Control><Alt>Tab
s0_alt_tab_prev_all = <Shift><Control><Alt>Tab
s0_alt_tab_next_window = Disabled
s0_alt_tab_prev_window = Disabled
s0_show_minimized_windows = true
s0_alt_tab_timeout = true
s0_alt_tab_bias_viewport = true
s0_disable_show_desktop = false
s0_disable_mouse = false

[splash]
s0_initiate_key = <Control>F11
s0_firststart = true
s0_background = splash_background.png
s0_logo = splash_logo.png
s0_fade_time = 1.000000
s0_display_time = 2.000000
s0_saturation = 50.000000
s0_brightness = 50.000000

[titleinfo]
s0_show_remote_machine = true
s0_show_root = true

[rotate]
s0_edge_flip_pointer = false
s0_edge_flip_window = true
s0_edge_flip_dnd = true
s0_raise_on_rotate = false
s0_invert_y = false
s0_snap_top = false
s0_snap_bottom = false
s0_zoom = 1.000000
s0_flip_time = 350
s0_sensitivity = 1.000000
s0_acceleration = 4.000000
s0_speed = 2.000000
s0_timestep = 1.000000
s0_initiate_button = <Control><Alt>Button1
s0_rotate_left_key = <Control><Alt>Left
s0_rotate_left_button = Disabled
s0_rotate_right_key = <Control><Alt>Right
s0_rotate_right_button = Disabled
s0_rotate_left_window_key = <Shift><Control><Alt>Left
s0_rotate_left_window_button = Disabled
s0_rotate_right_window_key = <Shift><Control><Alt>Right
s0_rotate_right_window_button = Disabled
s0_rotate_to_key = Disabled
s0_rotate_window_key = Disabled
s0_rotate_flip_left_edge = Left
s0_rotate_flip_right_edge = Right
s0_rotate_to_1_key = Disabled
s0_rotate_to_2_key = Disabled
s0_rotate_to_3_key = Disabled
s0_rotate_to_4_key = Disabled
s0_rotate_to_5_key = Disabled
s0_rotate_to_6_key = Disabled
s0_rotate_to_7_key = Disabled
s0_rotate_to_8_key = Disabled
s0_rotate_to_9_key = Disabled
s0_rotate_to_10_key = Disabled
s0_rotate_to_11_key = Disabled
s0_rotate_to_12_key = Disabled
s0_rotate_to_1_window_key = Disabled
s0_rotate_to_2_window_key = Disabled
s0_rotate_to_3_window_key = Disabled
s0_rotate_to_4_window_key = Disabled
s0_rotate_to_5_window_key = Disabled
s0_rotate_to_6_window_key = Disabled
s0_rotate_to_7_window_key = Disabled
s0_rotate_to_8_window_key = Disabled
s0_rotate_to_9_window_key = Disabled
s0_rotate_to_10_window_key = Disabled
s0_rotate_to_11_window_key = Disabled
s0_rotate_to_12_window_key = Disabled

[scale]
s0_spacing = 20
s0_x_offset = 0
s0_y_offset = 0
s0_speed = 5.000000
s0_timestep = 0.100000
s0_darken_back = true
s0_opacity = 100
s0_overlay_icon = 0
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_hover_time = 750
s0_dnd_distance = 6
s0_dnd_timeout_spinner = true
s0_dnd_timeout_spinner_speed = 100
s0_multioutput_mode = 1
s0_key_bindings_toggle = true
s0_button_bindings_toggle = false
s0_initiate_edge = 
s0_initiate_key = <Super>w
s0_initiate_button = Disabled
s0_initiate_all_edge = 
s0_initiate_all_button = Disabled
s0_initiate_all_key = <Shift><Super>w
s0_initiate_group_edge = 
s0_initiate_group_button = Disabled
s0_initiate_group_key = Disabled
s0_initiate_output_edge = 
s0_initiate_output_button = Disabled
s0_initiate_output_key = Disabled
s0_click_on_desktop = 2

[unitymtgrabhandles]
s0_toggle_handles_key = Disabled
s0_show_handles_key = Disabled
s0_hide_handles_key = Disabled
s0_fade_duration = 150

[wallpaper]
s0_bg_image = 
s0_bg_image_pos = 
s0_bg_fill_type = 
s0_bg_color1 = 
s0_bg_color2 = 
s0_cycle_wallpapers = false
s0_cycle_timeout = 10.000000
s0_fade_duration = 2.000000

[obs]
s0_opacity_increase_key = Disabled
s0_opacity_increase_button = <Alt>Button4
s0_opacity_decrease_key = Disabled
s0_opacity_decrease_button = <Alt>Button5
s0_opacity_step = 5
s0_opacity_matches = 
s0_opacity_values = 90;
s0_brightness_increase_key = Disabled
s0_brightness_increase_button = Disabled
s0_brightness_decrease_key = Disabled
s0_brightness_decrease_button = Disabled
s0_brightness_step = 5
s0_brightness_matches = 
s0_brightness_values = 90;
s0_saturation_increase_key = Disabled
s0_saturation_increase_button = Disabled
s0_saturation_decrease_key = Disabled
s0_saturation_decrease_button = Disabled
s0_saturation_step = 5
s0_saturation_matches = 
s0_saturation_values = 90;

[wobbly]
s0_snap_key = <Shift>
s0_snap_inverted = false
s0_shiver = false
s0_friction = 3.000000
s0_spring_k = 8.000000
s0_grid_resolution = 8
s0_min_grid_size = 8
s0_map_effect = 0
s0_focus_effect = 0
s0_map_window_match = Splash | DropdownMenu | PopupMenu | Tooltip | Notification | Combo | Dnd | Unknown
s0_focus_window_match = 
s0_grab_window_match = 
s0_move_window_match = Toolbar | Menu | Utility | Dialog | Normal | Unknown
s0_maximize_effect = true

[ring]
s0_next_key = <Super>Tab
s0_next_button = Disabled
s0_prev_key = <Shift><Super>Tab
s0_prev_button = Disabled
s0_next_all_key = <Alt><Super>Tab
s0_next_all_button = Disabled
s0_prev_all_key = <Shift><Alt><Super>Tab
s0_prev_all_button = Disabled
s0_next_group_key = Disabled
s0_next_group_button = Disabled
s0_prev_group_key = Disabled
s0_prev_group_button = Disabled
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_overlay_icon = 1
s0_speed = 1.500000
s0_timestep = 1.200000
s0_inactive_opacity = 100
s0_darken_back = true
s0_minimized = true
s0_select_with_mouse = false
s0_ring_clockwise = false
s0_ring_width = 70
s0_ring_height = 60
s0_thumb_width = 350
s0_thumb_height = 250
s0_min_brightness = 0.500000
s0_min_scale = 0.400000
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 0
s0_vertical_offset = 50

[scalefilter]
s0_timeout = 0
s0_filter_case_insensitive = true
s0_filter_display = true
s0_font_bold = true
s0_font_size = 24
s0_border_size = 5
s0_font_color = #ffffffff
s0_back_color = #00000099

[switcher]
s0_next_button = Disabled
s0_next_key = <Alt>Tab
s0_prev_button = Disabled
s0_prev_key = <Shift><Alt>Tab
s0_next_all_button = Disabled
s0_next_all_key = <Control><Alt>Tab
s0_prev_all_button = Disabled
s0_prev_all_key = <Shift><Control><Alt>Tab
s0_next_no_popup_button = Disabled
s0_next_no_popup_key = Disabled
s0_prev_no_popup_button = Disabled
s0_prev_no_popup_key = Disabled
s0_next_panel_button = Disabled
s0_next_panel_key = Disabled
s0_prev_panel_button = Disabled
s0_prev_panel_key = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_mipmap = true
s0_saturation = 100
s0_brightness = 65
s0_opacity = 40
s0_focus_on_switch = false
s0_bring_to_front = true
s0_zoom = 1.000000
s0_icon = true
s0_icon_only = false
s0_minimized = true
s0_auto_rotate = false

[mousepoll]
s0_mouse_poll_interval = 10

[crashhandler]
s0_enabled = true
s0_directory = /tmp
s0_start_wm = false
s0_wm_cmd = 

[cube]
s0_unfold_key = <Control><Alt>Down
s0_mipmap = true
s0_multioutput_mode = 0
s0_in = false
s0_acceleration = 4.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_top_color = #ffffffff
s0_bottom_color = #ffffffff
s0_skydome = true
s0_skydome_image = /home/keegan/Pictures/Photos/lightning.jpg
s0_skydome_animated = true
s0_skydome_gradient_start_color = #0db1fdff
s0_skydome_gradient_end_color = #feffc7ff
s0_active_opacity = 100.000000
s0_inactive_opacity = 100.000000
s0_transparent_manual_only = true

[mag]
s0_initiate = <Super>m
s0_zoom_in_button = <Shift><Super>Button4
s0_zoom_out_button = <Shift><Super>Button5
s0_mode = 0
s0_zoom_factor = 2.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_keep_screen = true
s0_box_width = 300
s0_box_height = 200
s0_border = 2
s0_box_color = #000000ff
s0_overlay = Gnome/overlay.png
s0_mask = Gnome/mask.png
s0_x_offset = 155
s0_y_offset = 155
s0_radius = 200

[snap]
s0_avoid_snap = 0;
s0_snap_type = 0;
s0_edges_categories = 0;
s0_resistance_distance = 30
s0_attraction_distance = 20

[grid]
s0_put_center_key = <Control><Alt>KP_5
s0_put_left_key = <Control><Alt>KP_4
s0_put_right_key = <Control><Alt>KP_6
s0_put_top_key = <Control><Alt>KP_8
s0_put_bottom_key = <Control><Alt>KP_2
s0_put_topleft_key = <Control><Alt>KP_7
s0_put_topright_key = <Control><Alt>KP_9
s0_put_bottomleft_key = <Control><Alt>KP_1
s0_put_bottomright_key = <Control><Alt>KP_3
s0_put_maximize_key = <Control><Super>Up
s0_put_restore_key = <Control><Super>Down
s0_left_maximize = <Control><Super>Left
s0_right_maximize = <Control><Super>Right
s0_top_left_corner_action = 4
s0_top_edge_action = 10
s0_top_right_corner_action = 6
s0_left_edge_action = 4
s0_right_edge_action = 6
s0_bottom_left_corner_action = 4
s0_bottom_edge_action = 0
s0_bottom_right_corner_action = 6
s0_snapback_windows = true
s0_cycle_sizes = false
s0_left_edge_threshold = 15
s0_right_edge_threshold = 15
s0_top_edge_threshold = 20
s0_bottom_edge_threshold = 5
s0_snapoff_threshold = 50
s0_draw_indicator = true
s0_draw_stretched_window = true
s0_animation_duration = 350
s0_outline_color = #fb8b009f
s0_fill_color = #fb8b004f

[showdesktop]
s0_speed = 1.200000
s0_timestep = 0.100000
s0_direction = 10
s0_window_match = type=toolbar | type=utility | type=dialog | type=normal
s0_window_opacity = 0.300000
s0_window_part_size = 20

[commands]
s0_command0 = 
s0_command1 = 
s0_command2 = 
s0_command3 = 
s0_command4 = 
s0_command5 = 
s0_command6 = 
s0_command7 = 
s0_command8 = 
s0_command9 = 
s0_command10 = 
s0_command11 = 
s0_command12 = 
s0_command13 = 
s0_command14 = 
s0_command15 = 
s0_command16 = 
s0_command17 = 
s0_command18 = 
s0_command19 = 
s0_command20 = /usr/bin/gnome-system-monitor -p
s0_run_command0_key = Disabled
s0_run_command1_key = Disabled
s0_run_command2_key = Disabled
s0_run_command3_key = Disabled
s0_run_command4_key = Disabled
s0_run_command5_key = Disabled
s0_run_command6_key = Disabled
s0_run_command7_key = Disabled
s0_run_command8_key = Disabled
s0_run_command9_key = Disabled
s0_run_command10_key = Disabled
s0_run_command11_key = Disabled
s0_run_command12_key = Disabled
s0_run_command13_key = Disabled
s0_run_command14_key = Disabled
s0_run_command15_key = Disabled
s0_run_command16_key = Disabled
s0_run_command17_key = Disabled
s0_run_command18_key = Disabled
s0_run_command19_key = Disabled
s0_run_command20_key = <Control><Alt>Delete
s0_run_command0_button = Disabled
s0_run_command1_button = Disabled
s0_run_command2_button = Disabled
s0_run_command3_button = Disabled
s0_run_command4_button = Disabled
s0_run_command5_button = Disabled
s0_run_command6_button = Disabled
s0_run_command7_button = Disabled
s0_run_command8_button = Disabled
s0_run_command9_button = Disabled
s0_run_command10_button = Disabled
s0_run_command11_button = Disabled
s0_run_command12_button = Disabled
s0_run_command13_button = Disabled
s0_run_command14_button = Disabled
s0_run_command15_button = Disabled
s0_run_command16_button = Disabled
s0_run_command17_button = Disabled
s0_run_command18_button = Disabled
s0_run_command19_button = Disabled
s0_run_command20_button = Disabled
s0_run_command0_edge = 
s0_run_command1_edge = 
s0_run_command2_edge = 
s0_run_command3_edge = 
s0_run_command4_edge = 
s0_run_command5_edge = 
s0_run_command6_edge = 
s0_run_command7_edge = 
s0_run_command8_edge = 
s0_run_command9_edge = 
s0_run_command10_edge = 
s0_run_command11_edge = 
s0_run_command12_edge = 
s0_run_command13_edge = 
s0_run_command14_edge = 
s0_run_command15_edge = 
s0_run_command16_edge = 
s0_run_command17_edge = 
s0_run_command18_edge = 
s0_run_command19_edge = 
s0_run_command20_edge = 

[wall]
s0_show_switcher = true
s0_miniscreen = true
s0_preview_timeout = 0.200000
s0_preview_scale = 130
s0_edge_radius = 5
s0_border_width = 7
s0_outline_color = #ffffff32
s0_background_gradient_base_color = #00000064
s0_background_gradient_highlight_color = #00000064
s0_background_gradient_shadow_color = #00000064
s0_thumb_gradient_base_color = #55555532
s0_thumb_gradient_highlight_color = #55555532
s0_thumb_highlight_gradient_base_color = #ffffffff
s0_thumb_highlight_gradient_shadow_color = #dfdfdfff
s0_arrow_base_color = #e6e6e6d9
s0_arrow_shadow_color = #dcdcdcd9
s0_allow_wraparound = false
s0_slide_duration = 0.300000
s0_no_slide_match = type=Dock | type=Desktop | state=Sticky
s0_auto_switch_vp_and_window = false
s0_left_key = <Control><Alt>Left
s0_left_button = Disabled
s0_right_key = <Control><Alt>Right
s0_right_button = Disabled
s0_up_key = <Control><Alt>Up
s0_up_button = Disabled
s0_down_key = <Control><Alt>Down
s0_down_button = Disabled
s0_next_key = Disabled
s0_next_button = Disabled
s0_prev_key = Disabled
s0_prev_button = Disabled
s0_left_window_key = <Shift><Control><Alt>Left
s0_right_window_key = <Shift><Control><Alt>Right
s0_up_window_key = <Shift><Control><Alt>Up
s0_down_window_key = <Shift><Control><Alt>Down
s0_flip_left_edge = Left
s0_flip_right_edge = Right
s0_flip_up_edge = Top
s0_flip_down_edge = Bottom
s0_mmmode = 0
s0_edgeflip_pointer = false
s0_edgeflip_move = false
s0_edgeflip_dnd = false

[put]
s0_put_viewport_1_key = Disabled
s0_put_viewport_2_key = Disabled
s0_put_viewport_3_key = Disabled
s0_put_viewport_4_key = Disabled
s0_put_viewport_5_key = Disabled
s0_put_viewport_6_key = Disabled
s0_put_viewport_7_key = Disabled
s0_put_viewport_8_key = Disabled
s0_put_viewport_9_key = Disabled
s0_put_viewport_10_key = Disabled
s0_put_viewport_11_key = Disabled
s0_put_viewport_12_key = Disabled
s0_put_viewport_left_key = Disabled
s0_put_viewport_right_key = Disabled
s0_put_viewport_up_key = Disabled
s0_put_viewport_down_key = Disabled
s0_put_center_key = <Super>KP_Begin
s0_put_center_button = Disabled
s0_put_left_key = <Control><Alt>KP_Left
s0_put_left_button = Disabled
s0_put_right_key = <Control><Alt>KP_Right
s0_put_right_button = Disabled
s0_put_top_key = <Control><Alt>KP_Up
s0_put_top_button = Disabled
s0_put_bottom_key = <Control><Alt>KP_Down
s0_put_bottom_button = Disabled
s0_put_topleft_key = <Control><Alt>KP_Home
s0_put_topleft_button = Disabled
s0_put_topright_key = <Control><Alt>KP_Prior
s0_put_topright_button = Disabled
s0_put_bottomleft_key = <Control><Alt>KP_End
s0_put_bottomleft_button = Disabled
s0_put_bottomright_key = <Control><Alt>KP_Next
s0_put_bottomright_button = Disabled
s0_put_empty_center_key = Disabled
s0_put_empty_center_button = Disabled
s0_put_empty_left_key = Disabled
s0_put_empty_left_button = Disabled
s0_put_empty_right_key = Disabled
s0_put_empty_right_button = Disabled
s0_put_empty_top_key = Disabled
s0_put_empty_top_button = Disabled
s0_put_empty_bottom_key = Disabled
s0_put_empty_bottom_button = Disabled
s0_put_empty_topleft_key = Disabled
s0_put_empty_topleft_button = Disabled
s0_put_empty_topright_key = Disabled
s0_put_empty_topright_button = Disabled
s0_put_empty_bottomleft_key = Disabled
s0_put_empty_bottomleft_button = Disabled
s0_put_empty_bottomright_key = Disabled
s0_put_empty_bottomright_button = Disabled
s0_put_restore_key = <Super>KP_Insert
s0_put_restore_button = Disabled
s0_put_pointer_key = <Super>z
s0_put_pointer_button = Disabled
s0_put_next_output_key = Disabled
s0_put_next_output_button = Disabled
s0_put_previous_output_key = Disabled
s0_put_previous_output_button = Disabled
s0_pad_left = 0
s0_pad_right = 0
s0_pad_top = 0
s0_pad_bottom = 0
s0_unfocus_window = false
s0_window_center = false
s0_avoid_offscreen = false
s0_speed = 2.500000
s0_timestep = 0.500000

[resize]
s0_initiate_button = <Alt>Button2
s0_initiate_key = <Alt>F8
s0_mode = 0
s0_resize_from_center = false
s0_maximize_vertically = true
s0_border_color = #fb8b009f
s0_fill_color = #fb8b0019
s0_normal_match = 
s0_outline_match = 
s0_rectangle_match = 
s0_stretch_match = 
s0_resize_from_center_match = 
s0_outline_modifier = 
s0_rectangle_modifier = 
s0_stretch_modifier = 
s0_centered_modifier = 0;

[winrules]
s0_skiptaskbar_match = 
s0_skippager_match = 
s0_above_match = 
s0_below_match = 
s0_sticky_match = 
s0_fullscreen_match = 
s0_maximize_match = 
s0_no_argb_match = 
s0_no_move_match = 
s0_no_resize_match = 
s0_no_minimize_match = 
s0_no_maximize_match = 
s0_no_close_match = 
s0_no_focus_match = 
s0_size_matches = 
s0_size_width_values = 
s0_size_height_values = 

[notification]
s0_timeout = -1
s0_max_log_level = 1

[ezoom]
s0_zoom_in_button = Disabled
s0_zoom_in_key = Disabled
s0_zoom_out_button = Disabled
s0_zoom_out_key = Disabled
s0_zoom_box_button = Disabled
s0_zoom_box_outline_color = #2f2f4f9f
s0_zoom_box_fill_color = #2f2f2f4f
s0_center_mouse_key = Disabled
s0_zoom_specific_1_key = Disabled
s0_zoom_spec1 = 1.000000
s0_zoom_specific_2_key = Disabled
s0_zoom_spec2 = 0.500000
s0_zoom_specific_3_key = Disabled
s0_zoom_spec3 = 0.200000
s0_spec_target_focus = true
s0_lock_zoom_key = Disabled
s0_pan_left_key = Disabled
s0_pan_right_key = Disabled
s0_pan_up_key = Disabled
s0_pan_down_key = Disabled
s0_fit_to_zoom_key = Disabled
s0_fit_to_window_key = Disabled
s0_zoom_factor = 1.150000
s0_minimum_zoom = 0.125000
s0_zoom_mode = 0
s0_scale_mouse = true
s0_scale_mouse_dynamic = true
s0_scale_mouse_static = 0.200000
s0_hide_original_mouse = true
s0_restrain_mouse = false
s0_restrain_margin = 5
s0_pan_factor = 0.100000
s0_follow_focus = true
s0_focus_fit_window = false
s0_autoscale_min = 0.250000
s0_always_focus_fit_window = false
s0_follow_focus_delay = 0
s0_speed = 25.000000
s0_timestep = 1.200000

[scaleaddon]
s0_close_key = Disabled
s0_close_button = Button2
s0_pull_key = Disabled
s0_pull_button = Disabled
s0_zoom_key = Disabled
s0_zoom_button = Button3
s0_window_title = 1
s0_title_bold = false
s0_title_size = 10
s0_border_size = 3
s0_font_color = #ffffffff
s0_back_color = #00000099
s0_window_highlight = false
s0_highlight_color = #ffffff96
s0_layout_mode = 0
s0_natural_precision = 2.000000
s0_constrain_pull_to_screen = true
s0_exit_after_pull = false

[place]
s0_workarounds = true
s0_mode = 2
s0_multioutput_mode = 0
s0_force_placement_match = 
s0_position_matches = 
s0_position_x_values = 
s0_position_y_values = 
s0_position_constrain_workarea = 
s0_mode_matches = 
s0_mode_modes = 
s0_viewport_matches = 
s0_viewport_x_values = 
s0_viewport_y_values = 

[opengl]
s0_texture_filter = 1
s0_lighting = false
s0_sync_to_vblank = true
s0_texture_compression = false
s0_framebuffer_object = true
s0_vertex_buffer_object = true
s0_always_swap_buffers = true
s0_enable_x11_sync = true
s0_unredirect_driver_blacklist = (nouveau|Intel).*Mesa 8.0

[freewins]
s0_initiate_rotation_button = <Shift><Control>Button1
s0_initiate_scale_button = <Shift><Control>Button3
s0_reset_button = <Shift><Control>Button2
s0_reset_key = <Shift><Control>r
s0_toggle_axis_key = <Shift><Control>h
s0_snap_mods = 
s0_invert_mods = 
s0_scale_up_button = <Shift><Control>Button4
s0_scale_down_button = <Shift><Control>Button5
s0_scale_up_key = <Shift><Control>Prior
s0_scale_down_key = <Shift><Control>Next
s0_rotate_up_key = <Shift><Control>w
s0_rotate_down_key = <Shift><Control>s
s0_rotate_left_key = <Shift><Control>d
s0_rotate_right_key = <Shift><Control>a
s0_rotate_c_key = <Shift><Control>e
s0_rotate_cc_key = <Shift><Control>q
s0_snap = false
s0_snap_threshold = 50
s0_mouse_sensitivity = 1.000000
s0_scale_mode = 0
s0_allow_negative = true
s0_scale_uniform = true
s0_min_scale = 0.100000
s0_z_axis_rotation = 2
s0_rotation_axis = 0
s0_td_percent = 35.000000
s0_auto_zoom = false
s0_disable_on_transformed_screen = false
s0_speed = 5.000000
s0_rotate_increment_amount = 10.000000
s0_scale_increment_amount = 0.300000
s0_shape_window_types = (Toolbar | Utility | Dialog | ModalDialog | Normal)
s0_do_shape_input = true
s0_immediate_moves = true
s0_circle_color = #54befb80
s0_line_color = #1800ffff
s0_cross_line_color = #1800ffff
s0_show_circle = true
s0_show_gizmo = true
s0_show_cross = true
s0_show_region = true

[widget]
s0_toggle_key = F9
s0_toggle_button = Disabled
s0_toggle_edge = 
s0_match = 
s0_end_on_click = true
s0_fade_time = 0.500000
s0_bg_brightness = 50
s0_bg_saturation = 100

[staticswitcher]
s0_next_button = Disabled
s0_next_key = Disabled
s0_prev_button = Disabled
s0_prev_key = Disabled
s0_next_all_button = Disabled
s0_next_all_key = <Control><Alt>Tab
s0_prev_all_button = Disabled
s0_prev_all_key = <Shift><Control><Alt>Tab
s0_next_group_button = Disabled
s0_next_group_key = Disabled
s0_prev_group_button = Disabled
s0_prev_group_key = Disabled
s0_next_no_popup_button = Disabled
s0_next_no_popup_key = Disabled
s0_prev_no_popup_button = Disabled
s0_prev_no_popup_key = Disabled
s0_next_panel_button = Disabled
s0_next_panel_key = Disabled
s0_prev_panel_button = Disabled
s0_prev_panel_key = Disabled
s0_speed = 4.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | Toolbar | Utility | Unknown
s0_minimized = true
s0_auto_change_vp = true
s0_popup_delay = 0.200000
s0_mouse_select = true
s0_saturation = 100
s0_brightness = 100
s0_opacity = 100
s0_icon = true
s0_icon_only = false
s0_mipmap = false
s0_row_align = 1
s0_focus_on_switch = false
s0_bring_to_front = false
s0_highlight_mode = 0
s0_highlight_rect_hidden = 1
s0_highlight_color = #00000096
s0_highlight_border_color = #000000c8
s0_highlight_border_inlay_color = #c8c8c8c8

[move]
s0_initiate_button = <Alt>Button1
s0_initiate_key = <Alt>F7
s0_opacity = 100
s0_key_move_inc = 24
s0_constrain_y = true
s0_snapoff_semimaximized = true
s0_snapoff_distance = 100
s0_snapback_semimaximized = true
s0_snapback_distance = 20
s0_lazy_positioning = false

[shift]
s0_initiate_key = <Shift><Super>s
s0_initiate_button = Disabled
s0_initiate_edge = 
s0_initiate_all_key = Disabled
s0_initiate_all_button = Disabled
s0_initiate_all_edge = 
s0_next_key = <Super>Tab
s0_next_button = Disabled
s0_prev_key = <Shift><Super>Tab
s0_prev_button = Disabled
s0_next_all_key = <Alt><Super>Tab
s0_next_all_button = Disabled
s0_prev_all_key = <Shift><Alt><Super>Tab
s0_prev_all_button = Disabled
s0_next_group_key = Disabled
s0_next_group_button = Disabled
s0_prev_group_key = Disabled
s0_prev_group_button = Disabled
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_minimized = true
s0_speed = 1.500000
s0_shift_speed = 1.000000
s0_timestep = 1.200000
s0_mouse_speed = 10.000000
s0_click_duration = 500
s0_size = 50
s0_background_intensity = 0.500000
s0_hide_all = false
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_intensity = 0.400000
s0_overlay_icon = 1
s0_mipmaps = false
s0_multioutput_mode = 0
s0_mode = 0
s0_flip_rotation = 30
s0_cover_offset = 0.000000
s0_cover_angle = 60.000000
s0_cover_extra_space = 1.000000
s0_cover_max_visible_windows = 10
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 2
s0_vertical_offset = 50

[mblur]
s0_initiate_key = <Control>F12
s0_mode = 0
s0_strength = 20.000000
s0_on_transformed_screen = false

[annotate]
s0_initiate_free_draw_button = <Alt><Super>Button1
s0_initiate_line_button = <Alt><Super>Button2
s0_initiate_rectangle_button = <Shift><Alt><Super>Button1
s0_initiate_ellipse_button = <Shift><Alt><Super>Button2
s0_erase_button = <Alt><Super>Button3
s0_clear_button = Disabled
s0_clear_key = <Alt><Super>k
s0_draw_shapes_from_center = true
s0_fill_color = #ff000088
s0_stroke_color = #00ff00ff
s0_erase_width = 20.000000
s0_stroke_width = 3.000000

[water]
s0_initiate_key = <Control><Super>
s0_toggle_rain_key = <Shift>F9
s0_toggle_wiper_key = <Shift>F8
s0_offset_scale = 10.000000
s0_rain_delay = 250
s0_light_vec_x = -1.000000
s0_light_vec_y = 1.000000
s0_light_vec_z = 0.000000
s0_title_wave = false

[extrawm]
s0_toggle_redirect_key = Disabled
s0_toggle_fullscreen_key = Disabled
s0_toggle_always_on_top_key = Disabled
s0_toggle_sticky_key = Disabled
s0_activate_demands_attention_key = Disabled

[addhelper]
s0_toggle_key = <Super>p
s0_window_types = Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal
s0_ononinit = false
s0_brightness = 30
s0_saturation = 50
s0_opacity = 100

[composite]
s0_slow_animations_key = Disabled
s0_detect_refresh_rate = true
s0_refresh_rate = 50
s0_unredirect_fullscreen_windows = true
s0_unredirect_match = (any) & !(class=Totem) & !(class=MPlayer) & !(class=Vlc) & !(class=Plugin-container) & !(class=Firefox)
s0_force_independent_output_painting = false

[workarounds]
s0_keep_minimized_windows = false
s0_legacy_fullscreen = false
s0_firefox_menu_fix = false
s0_ooo_menu_fix = true
s0_notification_daemon_fix = false
s0_java_fix = true
s0_java_taskbar_fix = true
s0_qt_fix = false
s0_convert_urgency = false
s0_aiglx_fragment_fix = true
s0_fglrx_xgl_fix = false
s0_force_glx_sync = false
s0_no_wait_for_video_sync = false
s0_initial_damage_complete_redraw = true
s0_force_swap_buffers = false
s0_sticky_alldesktops = false
s0_alldesktop_sticky_match = any

[fade]
s0_fade_mode = 0
s0_fade_speed = 5.000000
s0_fade_time = 100
s0_window_match = any & !(title=notify-osd)
s0_visual_bell = false
s0_fullscreen_visual_bell = false
s0_dim_unresponsive = true
s0_unresponsive_brightness = 65
s0_unresponsive_saturation = 0

[session]
s0_save_legacy = false
s0_ignore_match = 

[firepaint]
s0_initiate_key = Disabled
s0_initiate_button = <Shift><Super>Button1
s0_clear_key = <Shift><Super>c
s0_clear_button = Disabled
s0_bg_brightness = 50.000000
s0_num_particles = 3000
s0_fire_size = 15.000000
s0_fire_slowdown = 0.500000
s0_fire_life = 0.700000
s0_fire_color = #ff3305ff
s0_fire_mystical = false

[core]
s0_active_plugins = core;composite;opengl;move;regex;imgpng;workaround  s;imgjpeg;vpswitch;mousepoll;cube;snap;compiztoolb  ox;commands;resize;place;session;rotate;scale;cube  addon;expo;unityshell;
s0_audible_bell = true
s0_ignore_hints_when_maximized = true
s0_hide_skip_taskbar_windows = true
s0_edge_delay = 0
s0_ping_delay = 5000
s0_default_icon = icon
s0_do_serialize = false
s0_overlapping_outputs = 0
s0_detect_outputs = true
s0_outputs = 640x480+0+0;
s0_click_to_focus = true
s0_raise_on_click = true
s0_autoraise = false
s0_autoraise_delay = 500
s0_focus_prevention_level = 1
s0_focus_prevention_match = !(class=Polkit-gnome-authentication-agent-1)
s0_close_window_key = <Alt>F4
s0_close_window_button = Disabled
s0_raise_window_key = Disabled
s0_raise_window_button = <Control>Button6
s0_lower_window_key = Disabled
s0_lower_window_button = <Alt>Button6
s0_minimize_window_key = <Control><Alt>KP_0
s0_minimize_window_button = Disabled
s0_maximize_window_key = <Control><Super>Up
s0_unmaximize_window_key = Disabled
s0_unmaximize_or_minimize_window_key = <Control><Super>Down
s0_maximize_window_horizontally_key = Disabled
s0_maximize_window_vertically_key = Disabled
s0_window_menu_key = <Alt>space
s0_window_menu_button = <Alt>Button3
s0_show_desktop_key = Disabled
s0_show_desktop_edge = 
s0_toggle_window_maximized_key = <Control><Alt>KP_5
s0_toggle_window_maximized_button = Disabled
s0_toggle_window_maximized_horizontally_key = Disabled
s0_toggle_window_maximized_vertically_key = Disabled
s0_toggle_window_shaded_key = <Control><Alt>s
s0_hsize = 4
s0_vsize = 1

[screenshot]
s0_initiate_button = <Super>Button1
s0_draw_selection_indicator = true
s0_selection_outline_color = #2f2f4f9f
s0_selection_fill_color = #2f2f4f4f
s0_directory = 
s0_launch_app = 

[gnomecompat]
s0_main_menu_key = Disabled
s0_run_key = <Alt>F2
s0_command_screenshot = gnome-screenshot
s0_run_command_screenshot_key = Print
s0_command_window_screenshot = gnome-screenshot -w
s0_run_command_window_screenshot_key = <Alt>Print
s0_command_terminal = x-terminal-emulator
s0_run_command_terminal_key = <Control><Alt>t

[workspacenames]
s0_viewports = 1;2;3;4;
s0_names = Viewport 1;Viewport 2;Viewport 3;Viewport 4;
s0_display_time = 1.500000
s0_fade_time = 0.250000
s0_bold_text = true
s0_text_font_size = 24
s0_text_placement = 0
s0_vertical_offset = 50
s0_back_color = #00000099
s0_font_color = #ffffffff

[resizeinfo]
s0_fade_time = 500
s0_always_show = false
s0_resizeinfo_font_bold = true
s0_resizeinfo_font_size = 12
s0_text_color = #000000ff
s0_gradient_1 = #cccce6cc
s0_gradient_2 = #f3f3f3cc
s0_gradient_3 = #d9d9d9cc
s0_outline_color = #e6e6e6ff

[maximumize]
s0_ignore_sticky = true
s0_ignore_overlapping = false
s0_allow_shrink = true
s0_maximumize_left = true
s0_maximumize_right = true
s0_maximumize_up = true
s0_maximumize_down = true
s0_trigger_max_key = <Super>M
s0_trigger_max_left = Disabled
s0_trigger_max_right = Disabled
s0_trigger_max_up = Disabled
s0_trigger_max_down = Disabled
s0_trigger_max_horizontally = Disabled
s0_trigger_max_vertically = Disabled
s0_trigger_max_up_left = Disabled
s0_trigger_max_up_right = Disabled
s0_trigger_max_down_left = Disabled
s0_trigger_max_down_right = Disabled
s0_trigger_min_key = <Shift><Super>M
s0_trigger_min_left = Disabled
s0_trigger_min_right = Disabled
s0_trigger_min_up = Disabled
s0_trigger_min_down = Disabled
s0_trigger_min_horizontally = Disabled
s0_trigger_min_vertically = Disabled
s0_trigger_min_up_left = Disabled
s0_trigger_min_up_right = Disabled
s0_trigger_min_down_left = Disabled
s0_trigger_min_down_right = Disabled

[fadedesktop]
s0_fadetime = 500
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown

[kdecompat]
s0_plasma_thumbnails = true
s0_present_windows = true
s0_window_blur = true
s0_sliding_popups = true
s0_slide_in_duration = 250
s0_slide_out_duration = 250

[opacify]
s0_toggle_key = <Super>o
s0_toggle_reset = true
s0_timeout = 700
s0_init_toggle = true
s0_only_if_block = false
s0_focus_instant = false
s0_no_delay_change = false
s0_window_match = Normal | Dialog | ModalDialog | Utility | Toolbar | Fullscreen
s0_active_opacity = 100
s0_passive_opacity = 10

[showrepaint]
s0_toggle_key = <Alt><Super>r
s0_intensity = 20

[clone]
s0_initiate_button = <Shift><Super>Button1

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

```

Any Ideas what Im missing or doing wrong to get that looking though the corner and behind widow effect in pic 1
 and that werid bleeding light in photo 2

---

### Post by egeezer on 2015-04-25
The number and extent of the changes in Compiz from Ubuntu 10.10 to 14.04 are so great that I would recommend you simply start from scratch with no more than the images you want for your cube (sphere) tops and background and set up the CCSM entirely fresh.  It's always relatively easy doing it that way each fresh install.

---

### Post by highspider on 2015-04-25
Thanks for a reply Egeezer!
Tried for scratch.
I can get all my sphere and cube working if I disable all (everything) and then one by one enabling putting everything back in 
except **Ubuntu Unity Plug-in **once it enables and enables its required plug-ins things get the bleeding light glitch guessing scale plugin

thank God for DISPLAY=:0 xterm from tty1 because I can't even get CLT+ALT+T after disabling all and enabling all except Ubuntu Unity Plug-in

I think I have to remove Ubuntu Unity and figure find a new Desktop

---

### Post by highspider on 2015-04-25
I just went back to classic gnome and got rid of Unity desktop and it works fine
```

 sudo apt-get install gnome-session-fallback

```[ATTACH=CONFIG]261556[/ATTACH]

---


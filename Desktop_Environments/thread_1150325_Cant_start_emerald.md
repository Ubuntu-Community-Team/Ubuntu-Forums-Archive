---
title: "Cant start emerald"
date: 2009-05-06
forum: Desktop Environments
---

### Post by KittyChow on 2009-05-06
i tried 
```
emerald --replace
```which didnt really do anything
and i also tried
```
compiz --replace
```and got 
```
Checking for Xgl: not present.     
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA:                                                               
Checking for texture_from_pixmap: present.                                             
Checking for non power of two support: present.                                        
Checking for Composite extension: present.                                             
Checking screen 1Comparing resolution (1920x1200) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present.                                              
Checking for nVidia: present.                                                               
Checking for FBConfig: present.                                                             
Checking for Xgl: not present.                                                              
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'                         
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active                            
[ERROR]: Option "mouse_poll_interval" already defined                                       
[ERROR]: Option "save_legacy" already defined                                               
[ERROR]: Option "ignore_match" already defined                                              
[ERROR]: Option "activate" already defined                                                  
[ERROR]: Option "toggle_redirect_key" already defined                                       
[ERROR]: Option "toggle_fullscreen_key" already defined                                     
[ERROR]: Option "toggle_always_on_top_key" already defined                                  
[ERROR]: Option "toggle_sticky_key" already defined                                         
[ERROR]: Option "activate_demands_attention_key" already defined                            
[ERROR]: Option "to_next_output_key" already defined                                        
[ERROR]: Option "begin_key" already defined                                                 
[ERROR]: Option "switch_to_1_key" already defined                                           
[ERROR]: Option "switch_to_2_key" already defined                                           
[ERROR]: Option "switch_to_3_key" already defined                                           
[ERROR]: Option "switch_to_4_key" already defined                                           
[ERROR]: Option "switch_to_5_key" already defined                                           
[ERROR]: Option "switch_to_6_key" already defined                                           
[ERROR]: Option "switch_to_7_key" already defined                                           
[ERROR]: Option "switch_to_8_key" already defined                                           
[ERROR]: Option "switch_to_9_key" already defined                                           
[ERROR]: Option "switch_to_10_key" already defined                                          
[ERROR]: Option "switch_to_11_key" already defined                                          
[ERROR]: Option "switch_to_12_key" already defined                                          
[ERROR]: Option "left_button" already defined                                               
[ERROR]: Option "right_button" already defined                                              
[ERROR]: Option "up_button" already defined                                                 
[ERROR]: Option "down_button" already defined                                               
[ERROR]: Option "next_button" already defined                                               
[ERROR]: Option "prev_button" already defined                                               
[ERROR]: Option "initiate_button" already defined                                           
[ERROR]: Option "init_plugin" already defined                                               
[ERROR]: Option "init_action" already defined                                               
[ERROR]: Option "shadow_radius" already defined                                             
[ERROR]: Option "shadow_opacity" already defined                                            
[ERROR]: Option "shadow_color" already defined                                              
[ERROR]: Option "shadow_x_offset" already defined                                           
[ERROR]: Option "shadow_y_offset" already defined                                           
[ERROR]: Option "command" already defined                                                   
[ERROR]: Option "mipmap" already defined                                                    
[ERROR]: Option "decoration_match" already defined                                          
[ERROR]: Option "shadow_match" already defined                                              
[ERROR]: Option "legacy_fullscreen" already defined                                         
[ERROR]: Option "firefox_menu_fix" already defined                                          
[ERROR]: Option "ooo_menu_fix" already defined                                              
[ERROR]: Option "notification_daemon_fix" already defined                                   
[ERROR]: Option "java_fix" already defined                                                  
[ERROR]: Option "qt_fix" already defined                                                    
[ERROR]: Option "convert_urgency" already defined                                           
[ERROR]: Option "aiglx_fragment_fix" already defined                                        
[ERROR]: Option "fglrx_xgl_fix" already defined                                             
[ERROR]: Option "force_glx_sync" already defined                                            
[ERROR]: Option "sticky_alldesktops" already defined                                        
[ERROR]: Option "alldesktop_sticky_match" already defined                                   
[ERROR]: Option "window_toggle_key" already defined                                         
[ERROR]: Option "screen_toggle_key" already defined                                         
[ERROR]: Option "neg_match" already defined                                                 
[ERROR]: Option "exclude_match" already defined                                             
[ERROR]: Option "quality" already defined                                                   
[ERROR]: Option "workarounds" already defined                                               
[ERROR]: Option "mode" already defined                                                      
[ERROR]: Option "multioutput_mode" already defined                                          
[ERROR]: Option "force_placement_match" already defined                                     
[ERROR]: Option "position_matches" already defined                                          
[ERROR]: Option "position_x_values" already defined                                         
[ERROR]: Option "position_y_values" already defined                                         
[ERROR]: Option "position_constrain_workarea" already defined                               
[ERROR]: Option "viewport_matches" already defined                                          
[ERROR]: Option "viewport_x_values" already defined                                         
[ERROR]: Option "viewport_y_values" already defined                                         
[ERROR]: Option "main_menu_key" already defined                                             
[ERROR]: Option "run_key" already defined                                                   
[ERROR]: Option "command_screenshot" already defined                                        
[ERROR]: Option "run_command_screenshot_key" already defined                                
[ERROR]: Option "command_window_screenshot" already defined                                 
[ERROR]: Option "run_command_window_screenshot_key" already defined                         
[ERROR]: Option "command_terminal" already defined                                          
[ERROR]: Option "run_command_terminal_key" already defined                                  
[ERROR]: Option "initiate_normal_key" already defined                                       
[ERROR]: Option "initiate_outline_key" already defined                                      
[ERROR]: Option "initiate_rectangle_key" already defined                                    
[ERROR]: Option "initiate_stretch_key" already defined                                      
[ERROR]: Option "initiate_button" already defined                                           
[ERROR]: Option "initiate_key" already defined                                              
[ERROR]: Option "mode" already defined                                                      
[ERROR]: Option "border_color" already defined                                              
[ERROR]: Option "fill_color" already defined                                                
[ERROR]: Option "normal_match" already defined                                              
[ERROR]: Option "outline_match" already defined                                             
[ERROR]: Option "rectangle_match" already defined                                           
[ERROR]: Option "stretch_match" already defined                                             
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[ERROR]: Option "yv12" already defined                                                      
[ERROR]: Option "avoid_snap" already defined                                                
[ERROR]: Option "snap_type" already defined                                                 
[ERROR]: Option "edges_categories" already defined                                          
[ERROR]: Option "resistance_distance" already defined                                       
[ERROR]: Option "attraction_distance" already defined                                       
[ERROR]: Option "fade_time" already defined                                                 
[ERROR]: Option "always_show" already defined                                               
[ERROR]: Option "text_color" already defined                                                
[ERROR]: Option "gradient_1" already defined                                                
[ERROR]: Option "gradient_2" already defined                                                
[ERROR]: Option "gradient_3" already defined                                                
[ERROR]: Option "fade_mode" already defined                                                 
[ERROR]: Option "fade_speed" already defined                                                
[ERROR]: Option "fade_time" already defined                                                 
[ERROR]: Option "window_match" already defined                                              
[ERROR]: Option "visual_bell" already defined                                               
[ERROR]: Option "fullscreen_visual_bell" already defined                                    
[ERROR]: Option "minimize_open_close" already defined                                       
[ERROR]: Option "dim_unresponsive" already defined                                          
[ERROR]: Option "unresponsive_brightness" already defined                                   
[ERROR]: Option "unresponsive_saturation" already defined                                   
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
[ERROR]: Option "key_bindings_toggle" already defined                                           
[ERROR]: Option "button_bindings_toggle" already defined                                        
[ERROR]: Option "initiate_edge" already defined                                                 
[ERROR]: Option "initiate_key" already defined                                                  
[ERROR]: Option "initiate_button" already defined                                               
[ERROR]: Option "initiate_all_edge" already defined                                             
[ERROR]: Option "initiate_all_button" already defined                                           
[ERROR]: Option "initiate_all_key" already defined                                              
[ERROR]: Option "initiate_group_edge" already defined                                           
[ERROR]: Option "initiate_group_button" already defined                                         
[ERROR]: Option "initiate_group_key" already defined                                            
[ERROR]: Option "initiate_output_edge" already defined                                          
[ERROR]: Option "initiate_output_button" already defined                                        
[ERROR]: Option "initiate_output_key" already defined                                           
[ERROR]: Option "show_desktop" already defined                                                  
[ERROR]: Option "spacing" already defined                                                       
[ERROR]: Option "speed" already defined                                                         
[ERROR]: Option "timestep" already defined                                                      
[ERROR]: Option "darken_back" already defined                                                   
[ERROR]: Option "opacity" already defined                                                       
[ERROR]: Option "overlay_icon" already defined                                                  
[ERROR]: Option "window_match" already defined                                                  
[ERROR]: Option "hover_time" already defined                                                    
[ERROR]: Option "multioutput_mode" already defined                                              
[ERROR]: Option "close_key" already defined                                                     
[ERROR]: Option "close_button" already defined                                                  
[ERROR]: Option "pull_key" already defined                                                      
[ERROR]: Option "pull_button" already defined                                                   
[ERROR]: Option "zoom_key" already defined                                                      
[ERROR]: Option "zoom_button" already defined                                                   
[ERROR]: Option "window_title" already defined                                                  
[ERROR]: Option "title_bold" already defined                                                    
[ERROR]: Option "title_size" already defined                                                    
[ERROR]: Option "border_size" already defined                                                   
[ERROR]: Option "font_color" already defined                                                    
[ERROR]: Option "back_color" already defined                                                    
[ERROR]: Option "window_highlight" already defined                                              
[ERROR]: Option "highlight_color" already defined                                               
[ERROR]: Option "layout_mode" already defined                                                   
[ERROR]: Option "constrain_pull_to_screen" already defined                                      
[ERROR]: Option "exit_after_pull" already defined                                               
[ERROR]: Option "initiate_button" already defined                                               
[ERROR]: Option "initiate_key" already defined                                                  
[ERROR]: Option "opacity" already defined                                                       
[ERROR]: Option "constrain_y" already defined                                                   
[ERROR]: Option "snapoff_maximized" already defined                                             
[ERROR]: Option "lazy_positioning" already defined                                              
[ERROR]: Option "expo_key" already defined                                                      
[ERROR]: Option "expo_button" already defined                                                   
[ERROR]: Option "expo_edge" already defined                                                     
[ERROR]: Option "double_click_time" already defined                                             
[ERROR]: Option "dnd_button" already defined                                                    
[ERROR]: Option "exit_button" already defined                                                   
[ERROR]: Option "next_vp_button" already defined                                                
[ERROR]: Option "prev_vp_button" already defined                                                
[ERROR]: Option "zoom_time" already defined                                                     
[ERROR]: Option "expo_immediate_move" already defined                                           
[ERROR]: Option "expo_animation" already defined                                                
[ERROR]: Option "deform" already defined                                                        
[ERROR]: Option "distance" already defined                                                      
[ERROR]: Option "vp_distance" already defined                                                   
[ERROR]: Option "aspect_ratio" already defined                                                  
[ERROR]: Option "curve" already defined                                                         
[ERROR]: Option "hide_docks" already defined                                                    
[ERROR]: Option "mipmaps" already defined                                                       
[ERROR]: Option "multioutput_mode" already defined                                              
[ERROR]: Option "vp_brightness" already defined                                                 
[ERROR]: Option "vp_saturation" already defined                                                 
[ERROR]: Option "reflection" already defined                                                    
[ERROR]: Option "ground_color1" already defined                                                 
[ERROR]: Option "ground_color2" already defined                                                 
[ERROR]: Option "ground_size" already defined                                                   
[ERROR]: Option "scale_factor" already defined                                                  
[ERROR]: Option "zoom_in_button" already defined                                                
[ERROR]: Option "zoom_in_key" already defined                                                   
[ERROR]: Option "zoom_out_button" already defined                                               
[ERROR]: Option "zoom_out_key" already defined                                                  
[ERROR]: Option "zoom_box_button" already defined                                               
[ERROR]: Option "center_mouse_key" already defined                                              
[ERROR]: Option "zoom_specific_1_key" already defined                                           
[ERROR]: Option "zoom_spec1" already defined                                                    
[ERROR]: Option "zoom_specific_2_key" already defined                                           
[ERROR]: Option "zoom_spec2" already defined                                                    
[ERROR]: Option "zoom_specific_3_key" already defined                                           
[ERROR]: Option "zoom_spec3" already defined                                                    
[ERROR]: Option "spec_target_focus" already defined                                             
[ERROR]: Option "lock_zoom_key" already defined                                                 
[ERROR]: Option "pan_left_key" already defined                                                  
[ERROR]: Option "pan_right_key" already defined                                                 
[ERROR]: Option "pan_up_key" already defined                                                    
[ERROR]: Option "pan_down_key" already defined                                                  
[ERROR]: Option "fit_to_zoom_key" already defined                                               
[ERROR]: Option "fit_to_window_key" already defined                                             
[ERROR]: Option "zoom_factor" already defined                                                   
[ERROR]: Option "minimum_zoom" already defined                                                  
[ERROR]: Option "sync_mouse" already defined                                                    
[ERROR]: Option "scale_mouse" already defined                                                   
[ERROR]: Option "scale_mouse_dynamic" already defined                                           
[ERROR]: Option "scale_mouse_static" already defined                                            
[ERROR]: Option "hide_original_mouse" already defined                                           
[ERROR]: Option "restrain_mouse" already defined                                                
[ERROR]: Option "mouse_pan" already defined                                                     
[ERROR]: Option "restrain_margin" already defined                                               
[ERROR]: Option "pan_factor" already defined                                                    
[ERROR]: Option "follow_focus" already defined                                                  
[ERROR]: Option "focus_fit_window" already defined                                              
[ERROR]: Option "autoscale_min" already defined                                                 
[ERROR]: Option "always_focus_fit_window" already defined                                       
[ERROR]: Option "follow_focus_delay" already defined                                            
[ERROR]: Option "speed" already defined                                                         
[ERROR]: Option "timestep" already defined                                                      
[ERROR]: Option "filter_linear" already defined                                                 
[ERROR]: Option "next_button" already defined                                                   
[ERROR]: Option "next_key" already defined                                                      
[ERROR]: Option "prev_button" already defined                                                   
[ERROR]: Option "prev_key" already defined                                                      
[ERROR]: Option "next_all_button" already defined                                               
[ERROR]: Option "next_all_key" already defined                                                  
[ERROR]: Option "prev_all_button" already defined                                               
[ERROR]: Option "prev_all_key" already defined                                                  
[ERROR]: Option "next_group_button" already defined                                             
[ERROR]: Option "next_group_key" already defined                                                
[ERROR]: Option "prev_group_button" already defined                                             
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "next_no_popup_button" already defined
[ERROR]: Option "next_no_popup_key" already defined
[ERROR]: Option "prev_no_popup_button" already defined
[ERROR]: Option "prev_no_popup_key" already defined
[ERROR]: Option "next_panel_button" already defined
[ERROR]: Option "next_panel_key" already defined
[ERROR]: Option "prev_panel_button" already defined
[ERROR]: Option "prev_panel_key" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "auto_change_vp" already defined
[ERROR]: Option "popup_delay" already defined
[ERROR]: Option "mouse_select" already defined
[ERROR]: Option "saturation" already defined
[ERROR]: Option "brightness" already defined
[ERROR]: Option "opacity" already defined
[ERROR]: Option "icon" already defined
[ERROR]: Option "mipmap" already defined
[ERROR]: Option "row_align" already defined
[ERROR]: Option "highlight_mode" already defined
[ERROR]: Option "highlight_rect_hidden" already defined
[ERROR]: Option "highlight_color" already defined
[ERROR]: Option "highlight_border_color" already defined
[ERROR]: Option "highlight_border_inlay_color" already defined
```it started emerald but got rid of the desktop defects
any ideas?

---

### Post by KittyChow on 2009-05-06
:( bumpidy bump bump

---

### Post by KittyChow on 2009-05-06
doesnt any one know?????????:confused:

---

### Post by overdrank on 2009-05-06
Please do not bump so quickly. :)
What version of Ubuntu are you using? The model of the graphics card?
You may have a look at the FAQ's link in my signature also.

---

### Post by KittyChow on 2009-05-06
im running 9.04
geforce 6150 le

---

### Post by overdrank on 2009-05-07
Ok have you installed the nvidia drivers, you may look under system, administration, hardware drivers.

---

### Post by KittyChow on 2009-05-07
yup also got compiz installed if you were wondering

---

### Post by BazookaAce on 2009-05-07
Have you checked the thread Overdrank mentioned? Check out the Emerald-section. It helped me alot when i had a similar problem like you.

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by KittyChow on 2009-05-07
yeah ive read through it a couple times already but still cant seem to figure it out

---

### Post by BazookaAce on 2009-05-07
Try this:

- System--> Preferences--> CompizConfig Settings-->Window Decorator-->Command: Emerald --replace 

- System--> Preferences--> Sessions. Click the Add button, and type in Emerald for Name and emerald --replace for Command. Click OK and close the Sessions window.

PS. Remember to choose a Emerald theme.

Reboot

---

### Post by KittyChow on 2009-05-07
already did the first one 
went to system menu but no preferences or session settings
checked under settings menu no session settings
used the system settings -->session manager and there like no options like that
im using kde 
i remember menus like that when i was using gnome

couldnt find session setting under gnome either 
 but 
 ```
emerald --replace 
```
worked in gnome O o

cant get it to work kde :-k

---

### Post by KittyChow on 2009-05-08
bump? or is it too soon:lolflag:
but seriously folks i dont mean to nag but my title bar on kde is flat looking while the panel is glossy which is a bit annoying an ideas?

---

### Post by BazookaAce on 2009-05-08
Well, i don't know what the problem is since i'm running Gnome. ):P

So a KDE-guy must help you! :D

---

### Post by overdrank on 2009-05-08
I remember seeing a thread about compiz conflicting with Kwin in KDE. Cant find the thread now but maybe a good place to start searching. :)

---

### Post by KittyChow on 2009-05-09
nice idea overdrank
well i tried killing kwin with the system monitor then i ran
```
compiz --replace
```it gave me the same error messages as before but it worked
so i logged out and logged back in and it was back to was it was before 
but now everytime i run ```
compiz --replace
``` it works with out having to kill kwin :)
it just wont stay that way:confused:
was thinking some thing along what bazookaace said
> **BazookaAce said:**
> 
- System--> Preferences--> Sessions. Click the Add button, and type in Emerald for Name and emerald --replace for Command. Click OK and close the Sessions window.

but i dont know how do do that in kde
any ideas?

---

### Post by KittyChow on 2009-05-09
:tongue: now its working from start up 
dont know why 
but thanks for the help

---


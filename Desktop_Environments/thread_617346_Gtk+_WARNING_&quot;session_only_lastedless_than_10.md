---
title: "Gtk+ WARNING &quot;session only lastedless than 10 sec.&quot;"
date: 2007-11-19
forum: Desktop Environments
---

### Post by Salleman on 2007-11-19
So sorry.. About one minute after posting my problem, I found a solution. I deleted the .profile in my home directory. That solved the problem, except that i had to go through my CCSM settings..

And I thought i had tried everything..


Old post:

First off, this is my first post. I hope this is the right place to ask this question, and that I am asking the right way. I have done some searching, but haven't been able to find anything that can solve my problem

Last night I got this error message when trying to start gnome:
> 
(process:5769): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5773): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/home/salle/.profile: 1: [opacify]: not found
/home/salle/.profile: 2: cannot open Super: No such file
/home/salle/.profile: 2: as_toggle: not found
/home/salle/.profile: 3: as_toggle_reset: not found
/home/salle/.profile: 4: as_timeout: not found
/home/salle/.profile: 5: as_init_toggle: not found
/home/salle/.profile: 6: s0_only_if_block: not found
/home/salle/.profile: 7: s0_focus_instant: not found
/home/salle/.profile: 8: s0_no_delay_change: not found
/home/salle/.profile: 9: s0_window_match: not found
/home/salle/.profile: 9: Dialog: not found
/home/salle/.profile: 9: ModalDialog: not found
/home/salle/.profile: 9: Utility: not found
/home/salle/.profile: 9: Toolbar: not found
/home/salle/.profile: 9: Fullscreen: not found
/home/salle/.profile: 10: s0_active_opacity: not found
/home/salle/.profile: 11: s0_passive_opacity: not found
/home/salle/.profile: 13: [thumbnail]: not found
/home/salle/.profile: 14: s0_thumb_size: not found
/home/salle/.profile: 15: s0_show_delay: not found
/home/salle/.profile: 16: s0_border: not found
/home/salle/.profile: 17: s0_thumb_color: not found
/home/salle/.profile: 18: s0_current_viewport: not found
/home/salle/.profile: 19: s0_always_on_top: not found
/home/salle/.profile: 20: s0_window_like: not found
/home/salle/.profile: 21: s0_mipmap: not found
/home/salle/.profile: 22: s0_title_enabled: not found
/home/salle/.profile: 23: s0_font_bold: not found
/home/salle/.profile: 24: s0_font_size: not found
/home/salle/.profile: 25: s0_font_color: not found
/home/salle/.profile: 27: [colorfilter]: not found
/home/salle/.profile: 28: cannot open Super: No such file
/home/salle/.profile: 28: as_toggle_window: not found
/home/salle/.profile: 29: cannot open Super: No such file
/home/salle/.profile: 29: as_toggle_screen: not found
/home/salle/.profile: 30: cannot open Super: No such file
/home/salle/.profile: 30: as_switch_filter: not found
/home/salle/.profile: 31: s0_filters: not found
/home/salle/.profile: 31: negative-green: not found
/home/salle/.profile: 31: blueish-filter: not found
/home/salle/.profile: 31: sepia: not found
/home/salle/.profile: 31: grayscale: not found
/home/salle/.profile: 32: s0_filter_decorations: not found
/home/salle/.profile: 33: s0_filter_match: not found
/home/salle/.profile: 34: s0_exclude_match: not found
/home/salle/.profile: 36: [zoom]: not found
/home/salle/.profile: 37: cannot open Super: No such file
/home/salle/.profile: 37: as_initiate: not found
/home/salle/.profile: 38: cannot open Super: No such file
/home/salle/.profile: 38: as_zoom_in: not found
/home/salle/.profile: 39: cannot open Super: No such file
/home/salle/.profile: 39: as_zoom_out: not found
/home/salle/.profile: 40: cannot open Super: No such file
/home/salle/.profile: 40: as_zoom_pan: not found
/home/salle/.profile: 41: s0_filter_linear: not found
/home/salle/.profile: 43: [wall]: not found
/home/salle/.profile: 44: as_show_switcher: not found
/home/salle/.profile: 45: as_miniscreen: not found
/home/salle/.profile: 46: as_edge_radius: not found
/home/salle/.profile: 47: as_outline_color: not found
/home/salle/.profile: 48: as_background_gradient_base_color: not found
/home/salle/.profile: 49: as_background_gradient_highlight_color: not found
/home/salle/.profile: 50: as_background_gradient_shadow_color: not found
/home/salle/.profile: 51: as_thumb_gradient_base_color: not found
/home/salle/.profile: 52: as_thumb_gradient_highlight_color: not found
/home/salle/.profile: 53: as_thumb_highlight_gradient_base_color: not found
/home/salle/.profile: 54: as_thumb_highlight_gradient_shadow_color: not found
/home/salle/.profile: 55: as_arrow_base_color: not found
/home/salle/.profile: 56: as_arrow_shadow_color: not found
/home/salle/.profile: 57: as_allow_wraparound: not found
/home/salle/.profile: 58: Syntax error: redirection unexpected

I am no expert, but i thing it has something to do with Compiz. I recently installed compizFusion and before the error I had just saved a profile in CCSM. 

I can start in failsafe mode.

Thanks in advance.

---


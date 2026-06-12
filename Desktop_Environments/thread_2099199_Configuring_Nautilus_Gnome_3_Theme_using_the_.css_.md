---
title: "Configuring Nautilus Gnome 3 Theme using the .css files"
date: 2012-12-28
forum: Desktop Environments
---

### Post by Drone4four on 2012-12-28
Here is what my Nautilus [_**looks like**_]("http://picpaste.com/Ugly_Nautilus-GWDtaqpx.png").
How do I make Nautilus look [**_the way it does on gnome-look.org_**]("http://gnome-look.org/CONTENT/content-pre3/148398-3.png")? 
I have the nautilus36.css file in /usr/share/themes/MediterraneanLight/gtk-3.0/ open in gedit, but I don’t know which parameter to change.  The comments aren’t explanatory enough for me to determine what to change.  Any advice?

---

### Post by mc4man on 2012-12-29
For starters you'd want to be using nautilus-3.6.x or 3.7.x

---

### Post by Drone4four on 2012-12-31
@**mc4man**: I thought I was running and tweaking the 3.6 config files all along.  What made you think I was tweaking 3.4 or 3.2 or 3.4?  Here are the contents of nautilus36.css and gtk.css, respectively.  

```

/****************
 * Applications *
 ****************/

NautilusWindow .primary-toolbar.toolbar {
	/* search-toolbar */
    background-image: -gtk-gradient (linear,
                                     left top, left bottom,
                                     from (shade(@theme_bg_dark_color, 0.47)),
                                     color-stop (0.20, shade(@theme_bg_dark_color, 0.55)),
                                     to   (shade(@theme_bg_dark_color, 0.59)));

    border-width: 1px 0px 1px 1px;
    border-radius: 0px;
    border-style: solid;
    border-color: shade(@theme_bg_dark_color, 0.32) @transparent shade(@theme_bg_dark_color, 0.50) shade(@theme_bg_dark_color, 0.50);

    padding: 3px 5px 4px;
    -GtkWidget-window-dragging: true;
    -GtkToolbar-button-relief: normal;    
}


NautilusWindow .toolbar {
	/* secundary search-toolbar */
    border-left-width: 1px;
    border-left-color: shade(@toolbar_gradient_base, 0.84);
/*
    background-image: -gtk-gradient (linear,
                                     left top, left bottom,
                                     from (shade(@sidebar_background, 0.63)),
                                     color-stop (0.20, shade(@sidebar_background, 0.68)),
                                     to   (shade(@sidebar_background, 0.74)));


    border-radius: 0px;
    border-style: solid;
    border-color: shade(@sidebar_background, 0.32) @transparent shade(@sidebar_background, 0.50) shade(@sidebar_background, 0.50);

    padding: 3px 5px 4px;
*/
    -GtkWidget-window-dragging: true;
    -GtkToolbar-button-relief: normal;    
}

/* Nautilus 3.6 Toolbar-buttons */
NautilusToolbar .button,
NautilusToolbar .button:active,
NautilusToolbar .button:hover,
NautilusToolbar .button:hover:active {     
    border-style: solid;
    border-radius: 0px;
	border-color: @theme_bg_dark_color;
    border-image: none;
    box-shadow: none;
}

NautilusToolbar .button {
    icon-shadow: 0 1px @theme_shadow_color;
}


NautilusToolbar .button *:active {
    icon-shadow: 0 1px @theme_selected_shadow_color;
}

NautilusToolbar .button *:insensitive,
NautilusToolbar .button *:active:insensitive {
    text-shadow: none;
}

.toolbar NautilusPathBar .button *:active,
.toolbar NautilusPathBar .button *:hover {
	
}

NautilusFloatingBar {
    background-image: -gtk-gradient (linear,
                                     left top, left bottom,
                                     from 	(shade(@theme_bg_color, 0.97)),
                                     to 	(shade(@theme_bg_color, 0.90)));

    border-color: shade (@notebook_tab_gradient_b, 0.80);

    border-radius: 3px 3px 0px 0px;
    border-width: 1px;
    border-style: solid;
}

NautilusFloatingBar .button {
    background-color: alpha (@theme_base_color, 0.0);
    background-image: none;

    border-style: none;
    border-image: none;

    -GtkButton-image-spacing: 0;
    -GtkButton-inner-border: 0;
}

NautilusWindow .sidebar .scrollbar {
	-GtkRange-trough-border: 	1;
    -GtkRange-slider-width:     6;
}

NautilusWindow .sidebar .scrollbar.trough,
NautilusWindow .sidebar .scrollbar.trough.vertical {
    background-image: none;
    background-color: @sidebar_background;
	-unico-inner-stroke-width:        0px;
}

NautilusWindow .sidebar .frame {
    border-width: 0px;
    border-style: none;	
}


NautilusWindow > GtkTable > .pane-separator,
NautilusWindow .pane-separator {
    background-color: @sidebar_background;
    /* border-color: @sidebar_background; */
    border-style: none;
    border-width: 0px;
    background-image: -gtk-gradient(linear,
                                    left top, right top,
                                    from (@sidebar_background),
                                    color-stop (0.50, @sidebar_background),
                                    to   (shade(@theme_bg_color, 0.70)));
}

```

As you can see in gtk.css, I have specifically imported the Nautilus 3.6 config file:

```
/* Default color scheme */
@define-color base_color #FBFBFB;
@define-color bg_color #E9E9E9;
@define-color text_color #303030;
@define-color fg_color #424242;
@define-color selected_bg_color #4D6E92;
@define-color selected_fg_color #ffffff;
@define-color tooltip_bg_color #040404;
@define-color tooltip_fg_color #ffffff;

/* Colormap actually used by the theme, to be overridden in other css files */
@define-color theme_base_color @base_color;
@define-color theme_bg_color @bg_color;
@define-color theme_text_color @text_color;
@define-color theme_fg_color @fg_color;
@define-color theme_shadow_color alpha(#fff, 0.18);
@define-color theme_selected_bg_color shade(#4D6E92, 1.00);
@define-color theme_selected_fg_color @selected_fg_color;
@define-color theme_selected_shadow_color alpha(#000, 0.12);
@define-color theme_tooltip_bg_color @tooltip_bg_color;
@define-color theme_tooltip_fg_color @tooltip_fg_color;

/***************[Mediterranean-Night]***************/
@define-color theme_bg_dark_color #AAAAAA;
@define-color theme_fg_dark_color #e4e4e4;
@define-color theme_text_dark_color #F1F1F1;
@define-color theme_shadow_dark_color alpha(#000, 0.20);
/*********************************************************/

/******************[Mediterranean-Gray]*******************
@define-color theme_bg_dark_color #F4F4F4;
@define-color theme_fg_dark_color #F4F4F4;
@define-color theme_text_dark_color #ffffff;
@define-color theme_shadow_dark_color alpha(#000, 0.15);
**********************************************************/

@define-color theme_button_border_dark shade(@theme_bg_dark_color, 0.35);
@define-color button_raised_gradient_color_a shade(@theme_bg_dark_color, 0.55);
@define-color button_raised_gradient_color_b shade(@theme_bg_dark_color, 0.45);
@define-color button_raised_linked_shadow alpha(@theme_base_color, 0.70);

/*
@define-color menu_bg_color shade(@theme_bg_color, 1.04);
@define-color menu_fg_color shade(@theme_fg_color, 1.00);
@define-color menu_controls_color shade (@theme_fg_dark_color, 0.89);
@define-color menu_combobox_border #3277bf;
@define-color menu_separator shade(@menu_bg_color, 0.95);
*/
@define-color menu_bg_color shade(@theme_bg_dark_color, 0.40);
@define-color menu_fg_color shade(@theme_fg_dark_color, 0.94);
@define-color menu_controls_color shade (@theme_fg_dark_color, 0.89);
@define-color menu_combobox_border #3277bf;
@define-color menu_separator mix (@menu_fg_color, @menu_bg_color, 0.95);
@define-color menu_shadow_color alpha(#000, 0.20);

@define-color link_color #4a90d9;
@define-color frame_color #808080;
@define-color inactive_frame_color #bbbbbb;
@define-color warning_color #f57900;
@define-color error_color #cc0000;
@define-color success_color #4e9a06;

@define-color info_fg_color rgb (181, 171, 156);
@define-color info_bg_color rgb (252, 252, 189);
@define-color warning_fg_color rgb (173, 120, 41);
@define-color warning_bg_color rgb (250, 173, 61);
@define-color question_fg_color rgb (97, 122, 214);
@define-color question_bg_color rgb (138, 173, 212);
@define-color error_fg_color rgb (106, 18, 18);
@define-color error_bg_color rgb (240, 54, 54);

@define-color keyboard_focus_border_a #a2c9f1;
@define-color keyboard_focus_border_b #6794cf;

@define-color os_chrome_bg_color #484848;
@define-color os_chrome_fg_color #F0F0F0; 

@define-color os_chrome_selected_bg_color  @theme_selected_bg_color;
@define-color os_chrome_selected_fg_color  @theme_selected_fg_color;

@define-color chrome_bg_color @theme_bg_color;
@define-color chrome_fg_color @theme_fg_color;

@define-color focused_entry_border shade(mix (@theme_selected_bg_color, @theme_bg_color, 0.10), 1.25);
@define-color focused_entry_inset alpha (#d7e4f1, 0.50);

/* @define-color sidebar_background shade(#E1E5E8, 0.95); */
@define-color sidebar_background #d5dade;
@define-color sidebar_selected_bg shade(@theme_selected_bg_color,0.90);

@define-color button_gradient_color_a shade(@theme_selected_bg_color, 1.25);
@define-color button_gradient_color_b shade(#80B8EA, 0.85);
@define-color button_border #B0B0B0;

@define-color button_active_gradient_color_a #a4a4a4;
@define-color button_active_gradient_color_b shade (@button_active_gradient_color_a, 0.83);

@define-color button_hover_gradient_color_a @theme_base_color;
@define-color button_hover_gradient_color_b shade (#fefefe, 0.94);

@define-color button_raised_active_gradient_color_a @button_active_gradient_color_a;
@define-color button_raised_active_gradient_color_b alpha(@button_active_gradient_color_b, 0.13);

@define-color insensitive_bg_color shade(@bg_color, 0.93);
@define-color insensitive_fg_color shade(@bg_color, 0.70);
@define-color insensitive_border_color shade(@bg_color, 0.80);

@define-color trough_bg_color_a shade (@theme_bg_color, 0.88);
@define-color trough_bg_color_b shade (@theme_bg_color, 0.95);


@define-color progressbar_pattern #000000;

@define-color entry_text_color @theme_text_color;

@define-color entry_background_a shade (@theme_base_color, 0.86);
@define-color entry_background_b shade (@theme_base_color, 0.96);
@define-color entry_background_c shade (@theme_base_color, 0.98);
@define-color entry_background_d shade (@theme_base_color, 1.00);

@define-color internal_element_color #646464;
@define-color internal_element_prelight @theme_text_color;
@define-color internal_element_insensitive shade (@internal_element_color, 1.4);

@define-color scale_fill @insensitive_border_color;
@define-color scale_border_a @internal_element_color;
@define-color scale_border_b shade (@internal_element_color, 1.25);
@define-color scale_progress_fill #2c85e2;
@define-color scale_progress_border_a #1864b2;
@define-color scale_progress_border_b #3e90e5;

@define-color highlighted_border #8f8f8f;
@define-color transparent alpha(#000, 0.0);

@define-color notebook_border shade(@theme_bg_color, 0.65);

@define-color toolbar_gradient_base shade (mix(#d5dade, @theme_bg_dark_color, 0.75), 0.87); 

@define-color toolbar_gradient_step1 #bcbcb4;
@define-color toolbar_gradient_step2 #d9d9d7;
@define-color toolbar_gradient_final #e5e5e2;

@define-color toolbar_border_top    shade (@toolbar_gradient_base, 1.04);
@define-color toolbar_border_bottom shade (@toolbar_gradient_base, 0.88);

@define-color toolbar_active_button_color #909081;

@define-color primary_toolbar_entry_bg @theme_base_color;
@define-color primary_toolbar_entry_fg @theme_text_color;

@define-color nautilus_cluebar_color shade(@sidebar_background, 1.00);
@define-color treeview_focus_border  @nautilus_cluebar_color;

@define-color expander_row_selected_color #FFF;
@define-color test #f00;

/* Metacity ¡No modificar! */
@define-color wm_highlight #ffffff;
@define-color wm_title_highlight #ffffff;

@define-color wm_bg_a shade (@bg_color, 1.1);
@define-color wm_bg_b @bg_color;

@define-color wm_button_bg_a shade (@bg_color, 1.0);
@define-color wm_button_bg_b shade (@bg_color, 0.85);
@define-color wm_button_bg_c shade (@bg_color, 0.8);
@define-color wm_button_bg_d shade (@bg_color, 0.9);

@define-color wm_button_bg_hover_a shade (@wm_button_bg_a, 1.1);
@define-color wm_button_bg_hover_b shade (@wm_button_bg_b, 1.1);
@define-color wm_button_bg_hover_c shade (@wm_button_bg_c, 1.1);
@define-color wm_button_bg_hover_d shade (@wm_button_bg_d, 1.1);

@define-color wm_button_bg_active_a shade (@bg_color, 0.7);
@define-color wm_button_bg_active_b shade (@bg_color, 0.9);
@define-color wm_button_bg_active_c shade (@bg_color, 0.9);

@import url("gtk-widgets.css");
@import url("menu_frame.css");
@import url("scrollbar.css");
@import url("sidebar.css");
@import url("gtk-widgets-assets.css");
@import url("gnome-panel.css");

/* Select style for TABS 

	1.- tabs dark gray (full)
	@import url("tabs-dark.css");

	2.- tabs themed blue (full)
	@import url("tabs-themed.css");

	3.- Default theme tabs
	@import url("tabs.css");

	4.- tabs with dark gray highlight
	@import url("tabs-mono.css");

	5.- more traditional style tabs
	@import url("tabs-classic.css");

	(Be careful to leave only ONE of the five,
	edit the line below according to the style you want) 
*/
@import url("tabs.css");

/* some gnome-mdi-apps */
@import url("gnome-mdi.css");


/* 
	There are 2 options for Unity panel:

	If you prefer the dark panel "Unity" 
	------------------------------------
	@import url("unity-darkest.css");

	If you prefer the default (perfect fit with maximized windows)
	--------------------------------------------------------------
	@import url("unity.css");

	(edit the line below according to the style you want) 	
-------------------------------------------------------------- */
@import url("unity.css");

/*  
	There are 7 options for nautilus:

	-----------------------------------
	 Nautilus 3.6 (default)
	-----------------------------------
	Nautilus 3.6.x for gnome-shell 3.6.x or unity
		@import url("nautilus36.css"); 
	
	-----------------------------------
	 3 for Nautilus 3.4 GNOME-SHELL
	-----------------------------------
	1.- nautilus sidebar and pathbar dark gray:
		@import url("gnome-nautilus34-gray.css");
	OR
	2.- nautilus sidebar and pathbar light:
		@import url("gnome-nautilus34-light.css"); 
	OR
	3.- nautilus sidebar dark gray and pathbar light:
		@import url("gnome-nautilus34-gray-light.css"); 

	-----------------------------------
	 3 for Nautilus 3.4 UNITY
	-----------------------------------
	1.- nautilus sidebar and pathbar dark gray:
		@import url("unity-nautilus34-gray.css");
	OR
	2.- nautilus sidebar and pathbar light:
		@import url("unity-nautilus34-light.css"); 
	OR
	3.- nautilus sidebar dark gray and pathbar light:
		@import url("unity-nautilus34-gray-light.css"); 


	(edit the line below according to the style of nautilus you want) 
-------------------------------------------------------------------- */
@import url("nautilus36.css");


/*
	Select your enviroment 
	----------------------
	1.- Gnome-shell and Cinnamon
	@import url("gnome-apps.css");

	2.- Unity (GlobalMenu)
	@import url("unity-apps.css");
	(edit the line below according your enviroment) 
---------------------------------------------------*/
@import url("gnome-apps.css");

```

---

### Post by mc4man on 2013-01-09
> **Drone4four said:**
> @**mc4man**: I thought I was running and tweaking the 3.6 config files all along.  What made you think I was tweaking 3.4 or 3.2 or 3.4?  Here are the contents of nautilus36.css and gtk.css, respectively.  


wasn't really referring to what you were 'tweaking', from the screenshot you linked it certainly looks like nautilus 3.2 or 3.4.

What does the 'About' menu entry show? (screen is 3.6.3 slightly modded

---

### Post by Drone4four on 2013-01-10
My 'About' menu said 3.4.x.  I was running nautilus 3.4 and not 36.  I assumed that since I was running gnome-shell 3.6, I was necessarily running all the latest software that comes with the DE, including nautilus 3.6.  You were right.  Thanks for pointing that out. 

I then Googled 'nautilus 36 ubuntu' and found a guide for upgrading nautilus. My nautilus now looks much closer to the nautilus pictured in my original post. See attached. @**mc4man**: Thanks for your insight and thanks for following up. 

Cheers.

By the way, 'tweaking' wasn't the best word choice to describe what I was doing with the nautilus config files.  Perhaps 'configuring' would have been more appropriate.

---


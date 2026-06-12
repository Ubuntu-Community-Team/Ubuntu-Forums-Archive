---
title: "wanted:themers"
date: 2010-08-31
forum: Desktop Environments
---

### Post by dzon65 on 2010-08-31
Well,it's a long shot but....
I did some color modifications to the equinox light theme.Somehow the color doesn't apply to the gtk selected in the sidepanel (see screenshot),so I guess someting else has to be edited but dunno what.I'll add the gtkrc.
                                       [LEFT]# GTK theme Equinox 1.20[/LEFT]
    [LEFT]# Author : Matthieu James[/LEFT]
    [LEFT]# Licence : GPL[/LEFT]
    
    [LEFT]# ===[ scroll bars ]===[/LEFT]
    [LEFT]#  bg[ACTIVE] is slider color[/LEFT]
    [LEFT]#  bg[NORMAL] is steppers color[/LEFT]
    [LEFT]#  base[NORMAL] is trough color[/LEFT]
    
    [LEFT]# ===[ check and radio buttons ]===[/LEFT]
    [LEFT]#  text[SELECTED] is the active bullet color[/LEFT]
    [LEFT]#  text[INSENSITIVE] is the inactive bullet color[/LEFT]
    [LEFT]#  base[PRELIGHT] is the unchecked base color[/LEFT]
    [LEFT]#  base[SELECTED] is the checked base color[/LEFT]
    [LEFT]#  base[ACTIVE] is the unchecked base color when pressed[/LEFT]
    
    [LEFT]# ===[ scales ]===[/LEFT]
    [LEFT]#  bg[NORMAL] is slider color[/LEFT]
    [LEFT]#  bg[PRELIGHT] is slider prelight color[/LEFT]
    [LEFT]#  bg[SELECTED] is slider's focus border color[/LEFT]
    [LEFT]#  base[SELECTED] is trough color[/LEFT]
    
    [LEFT]# ===[ progressbars ]===[/LEFT]
    [LEFT]#  bg[NORMAL] is trough color[/LEFT]
    [LEFT]#  bg[SELECTED] is fill color[/LEFT]
    
    [LEFT]gtk_color_scheme = "fg_color:#232323\nbg_color:#B5B5B5\nbase_color:#CFCFCF\ntext_color:#232323\nselected_bg_color:#303030\nselected_fg_color:#00FFFF\ntooltip_fg_color:#00FFFF\ntooltip_bg_color:#303030"[/LEFT]
    [LEFT]gtk-icon-sizes = "panel-menu=22,22:panel=22,22:gtk-button=16,16:gtk-large-toolbar=22,22"[/LEFT]
    
    [LEFT]gtk-auto-mnemonic = 1[/LEFT]
    
    [LEFT]style "theme-default" {[/LEFT]
    
    [LEFT]	GtkButton::default_border = { 0, 0, 0, 0 }[/LEFT]
    [LEFT]    GtkButton::child-displacement-x = 0[/LEFT]
    [LEFT]    GtkButton::child-displacement-y = 1[/LEFT]
    [LEFT]    GtkWidget::focus-padding = 0[/LEFT]
    
    [LEFT]    GtkRange::trough-border   = 0[/LEFT]
    [LEFT]    GtkRange::slider-width    = 13[/LEFT]
    [LEFT]    GtkRange::stepper_size    = 13[/LEFT]
    [LEFT]    GtkRange::stepper_spacing = 0[/LEFT]
    
    [LEFT]    GtkScrollbar::min_slider_length = 50[/LEFT]
    [LEFT]    GtkScrollbar::has-secondary-forward-stepper = 0[/LEFT]
    [LEFT]    GtkScrollbar::has-secondary-backward-stepper = 1[/LEFT]
    
    [LEFT]    GtkPaned::handle_size  = 6[/LEFT]
    
    [LEFT]    GtkMenuBar::internal-padding  = 0[/LEFT]
    [LEFT]	GtkMenuBar:: shadow-type = GTK_SHADOW_NONE[/LEFT]
    
    [LEFT]	GtkToolBar:: shadow-type = GTK_SHADOW_NONE[/LEFT]
    
    [LEFT]    GtkTreeView::expander_size    = 13[/LEFT]
    [LEFT]    GtkExpander::expander_size    = 13[/LEFT]
    
    [LEFT]    GtkScale::slider-length = 12[/LEFT]
    [LEFT]    GtkScale::slider-width  = 12[/LEFT]
    [LEFT]    GtkScale::trough-border = 2[/LEFT]
    
    [LEFT]    GtkWidget::link-color = "#0062dc" #blue[/LEFT]
    [LEFT]    GtkIMHtml::hyperlink-color = "#0062dc"[/LEFT]
    [LEFT]	GtkHTML::link-color = "#0062dc"[/LEFT]
    
    [LEFT]    WnckTasklist::fade-overlay-rect = 0[/LEFT]
    [LEFT]    WnckTasklist::fade-loop-time    = 5.0 # 5 seconds[/LEFT]
    [LEFT]    WnckTasklist::fade-opacity      = 0.5 # final opacity[/LEFT]
    
    [LEFT]    #makes menu only overlap border[/LEFT]
    [LEFT]    #GtkMenu::horizontal-offset  = -2[/LEFT]
    [LEFT]    GtkMenu::horizontal-padding = 0[/LEFT]
    
    [LEFT]    #removes extra padding at top and bottom of menus.  Makes menuitem overlap border[/LEFT]
    [LEFT]    GtkMenu::vertical-padding = 0[/LEFT]
    
    [LEFT]    #set to the same as roundness, used for better hotspot selection of tabs[/LEFT]
    [LEFT]    GtkNotebook::tab-curvature = 2.5[/LEFT]
    [LEFT]    GtkNotebook::tab-overlap   = 3[/LEFT]
    
    [LEFT]    GtkMenuItem::arrow-spacing = 10[/LEFT]
    [LEFT]    #Spacing between edge with indicator and text[/LEFT]
    [LEFT]    GtkOptionMenu  ::indicator-size = {11, 5}[/LEFT]
    [LEFT]    #GtkOptionMenu  ::indicator-spacing = {6, 5, 4, 4}[/LEFT]
    
    [LEFT]    GtkCheckButton ::indicator-size    = 15[/LEFT]
    [LEFT]    GtkCheckButton ::indicator-spacing = 1[/LEFT]
    [LEFT]    GtkRadioButton ::indicator-size    = 15[/LEFT]
    
    [LEFT]    # A new color must be defined since affectation of mix or shade functions to GtkTreeView::odd_row_color raise this message :[/LEFT]
    [LEFT]    # Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::odd-row-color' of type `GdkColor' from rc file value "((GString*) 0x9ccba00)" of type `GString'[/LEFT]
    [LEFT]    color["odd_row_color"] = mix(0.96, shade (0.98, @base_color), @selected_bg_color)[/LEFT]
    [LEFT]    GtkTreeView::horizontal_separator = 2[/LEFT]
    [LEFT]    GtkTreeView::odd_row_color = @odd_row_color[/LEFT]
    
    [LEFT]    GtkScrolledWindow::scrollbar-spacing       = 0[/LEFT]
    [LEFT]    GtkScrolledWindow::scrollbars-within-bevel = 1[/LEFT]
    [LEFT]    GtkScrolledWindow::window-placement-set    = 0[/LEFT]
    
    [LEFT]    GtkEntry::honors-transparent-bg-hint = 1[/LEFT]
    
    [LEFT]    GtkWidget::new-tooltip-style = 1[/LEFT]
    [LEFT]	GtkImage::x-ayatana-indicator-dynamic = 1[/LEFT]
        
    [LEFT]	xthickness = 1[/LEFT]
    [LEFT]    ythickness = 1[/LEFT]
    
    [LEFT]    fg[NORMAL]        =  @fg_color[/LEFT]
    [LEFT]    fg[ACTIVE]        =  @fg_color[/LEFT]
    [LEFT]    fg[PRELIGHT]      =  @fg_color[/LEFT]
    [LEFT]    fg[SELECTED]      =  @selected_fg_color[/LEFT]
    [LEFT]    fg[INSENSITIVE]   =  shade (3.0, @fg_color)[/LEFT]
    
    [LEFT]    bg[NORMAL]        =  @bg_color[/LEFT]
    [LEFT]    bg[ACTIVE]          =  shade (1.0125, @bg_color) # inactive tab color[/LEFT]
    [LEFT]    bg[PRELIGHT]        =  mix (0.85, shade (1.1, @bg_color), @selected_bg_color) # middle progressbar color[/LEFT]
    [LEFT]    bg[SELECTED]        =  @selected_bg_color[/LEFT]
    [LEFT]    bg[INSENSITIVE]   =  shade (1.03, @bg_color)[/LEFT]
    
    [LEFT]    base[NORMAL]      =  @base_color[/LEFT]
    [LEFT]    base[ACTIVE]      =  mix (0.35, @selected_bg_color, shade (0.9, @base_color)) # background color for inactive selected items[/LEFT]
    [LEFT]    base[PRELIGHT]    =  @base_color[/LEFT]
    [LEFT]    base[SELECTED]      =  @selected_bg_color[/LEFT]
    [LEFT]    base[INSENSITIVE]	=  shade (1.05, @bg_color)[/LEFT]
    
    [LEFT]    text[NORMAL]      =  @text_color[/LEFT]
    [LEFT]    text[ACTIVE]        =  @text_color # text color for inactive selected items[/LEFT]
    [LEFT]    text[PRELIGHT]    =  @text_color[/LEFT]
    [LEFT]    text[SELECTED]    =  @selected_fg_color[/LEFT]
    [LEFT]    text[INSENSITIVE]	=  mix (0.575, shade (0.95, @bg_color), @fg_color)[/LEFT]
    
    [LEFT]    engine "equinox" {[/LEFT]
    [LEFT]        curvature           = 2.5[/LEFT]
    [LEFT]        menubarstyle        = 3 # 0 = flat, 1 = gradient, 2 = flat without border, 3 = gradient without border[/LEFT]
    [LEFT]        toolbarstyle        = 5 # 0 = flat, 1 = gradient, 2 = flat without border, 3 = gradient without border, 4 = flat with bottom border, 5 = gradient with bottom border[/LEFT]
    [LEFT]        buttonstyle         = 0 # 0 = normal, 1 = glassy[/LEFT]
    [LEFT]        menuitemstyle       = 0 # 0 = normal, 1 = glassy[/LEFT]
    [LEFT]        listviewheaderstyle = 0 # 0 = normal, 1 = glassy[/LEFT]
    [LEFT]        scrollbarstyle      = 0 # 0 = normal, 1 = glassy, 2 = normal with handles, 3 = glassy with handles[/LEFT]
    [LEFT]        scalesliderstyle    = 0 # 0 = normal, 1 = glassy, 2 = normal with bullet[/LEFT]
    [LEFT]        checkradiostyle     = 0 # 0 = normal, 1 = glassy[/LEFT]
    [LEFT]        progressbarstyle    = 0 # 0 = normal, 1 = glassy[/LEFT]
    [LEFT]        separatorstyle     = 1 # 0 = solid, 1 = gradient[/LEFT]
    [LEFT]        animation           = TRUE # FALSE = disabled, TRUE = enabled[/LEFT]
    [LEFT]        arrowsize           = 0.1 # controls combo_arrow circle size.  Diameter set by (11 + 2 * arrowsize)[/LEFT]
        }
    }
    
    [LEFT]style "theme-wide" = "theme-default" {[/LEFT]
    [LEFT]    xthickness = 2[/LEFT]
    [LEFT]    ythickness = 2[/LEFT]
    }
    
    [LEFT]style "theme-wider" = "theme-default" {[/LEFT]
    [LEFT]    xthickness = 3[/LEFT]
    [LEFT]    ythickness = 3[/LEFT]
    }
    
    [LEFT]style "theme-widest" = "theme-default" {[/LEFT]
    [LEFT]    xthickness = 4[/LEFT]
    [LEFT]    ythickness = 3[/LEFT]
    }
    
    [LEFT]style "theme-button" = "theme-wider" {[/LEFT]
    [LEFT]    bg[NORMAL]   = shade (1.10, @bg_color)[/LEFT]
    [LEFT]    bg[ACTIVE]   = shade (0.86, @bg_color)[/LEFT]
    [LEFT]    bg[PRELIGHT] = shade (1.20, @bg_color)[/LEFT]
    }
    
    [LEFT]style "theme-toolbar-button" = "theme-button" {[/LEFT]
    [LEFT]    bg[NORMAL]   = shade (1.05, @bg_color)[/LEFT]
    [LEFT]    bg[ACTIVE]   = shade (0.80, @bg_color)[/LEFT]
    [LEFT]    bg[PRELIGHT] = shade (1.15, @bg_color)[/LEFT]
    }
    
    [LEFT]style "theme-scrollbar" = "theme-default" {[/LEFT]
    [LEFT]    xthickness   = 0[/LEFT]
    [LEFT]    ythickness   = 0[/LEFT]
    [LEFT]    text[ACTIVE] = @text_color[/LEFT]
    [LEFT]    bg[ACTIVE]   = shade (1.1, @bg_color)[/LEFT]
    [LEFT]    base[NORMAL] = mix (0.25, @bg_color, @base_color)[/LEFT]
    [LEFT]    bg[PRELIGHT] = shade (1.15, @bg_color) #mix (0.5, shade (1.2, @bg_color), @selected_bg_color)[/LEFT]
    [LEFT]    engine "equinox" {[/LEFT]
    [LEFT]        curvature = 6[/LEFT]
    	}
    }
    
    [LEFT]style "theme-entry" = "theme-button" {[/LEFT]
    [LEFT]    bg[PRELIGHT] = @bg_color[/LEFT]
    }
    
    [LEFT]style "theme-frame" = "theme-wide" {[/LEFT]
    [LEFT]    GtkWidget::draw-border = {1,1,1,1}[/LEFT]
    }
    
    [LEFT]style "theme-handlebox" = "theme-default" {[/LEFT]
    [LEFT]    bg[NORMAL] = shade (0.95, @bg_color)[/LEFT]
    }
    
    [LEFT]style "theme-scale" = "theme-default" {[/LEFT]
    [LEFT]    bg[NORMAL]     = shade (1.05, @bg_color)[/LEFT]
    [LEFT]    bg[PRELIGHT]   = shade (1.20, @bg_color)[/LEFT]
    [LEFT]    base[SELECTED] = mix (0.5, @selected_bg_color, shade (0.85, @bg_color))[/LEFT]
    }
    
    [LEFT]style "theme-range" = "theme-default" {[/LEFT]
    [LEFT]    bg[NORMAL]        = shade (1.0930, @bg_color)[/LEFT]
    [LEFT]    bg[PRELIGHT]      = mix (0.93, shade (1.14, @bg_color), @selected_bg_color)[/LEFT]
    
    [LEFT]    #Arrows[/LEFT]
    [LEFT]    text[NORMAL]      = shade (0.275,@selected_fg_color)[/LEFT]
    [LEFT]    text[PRELIGHT]    = @selected_fg_color[/LEFT]
    [LEFT]    text[ACTIVE]      = shade (0.10,@selected_fg_color)[/LEFT]
    [LEFT]    text[INSENSITIVE] = mix (0.80,shade (0.90,@bg_color),@fg_color)[/LEFT]
    }
    
    [LEFT]style "theme-notebook-bg" = "theme-default" {[/LEFT]
    [LEFT]	bg[NORMAL]   = shade (1.05, @bg_color)[/LEFT]
    }
    
    [LEFT]style "theme-notebook" = "theme-notebook-bg" {[/LEFT]
    [LEFT]    xthickness = 1[/LEFT]
    [LEFT]    ythickness = 1[/LEFT]
    }
    
    [LEFT]style "theme-menu" = "theme-default" {[/LEFT]
    [LEFT]    xthickness = 0[/LEFT]
    [LEFT]    ythickness = 0[/LEFT]
    [LEFT]    bg[NORMAL] = shade (1.05,@bg_color)[/LEFT]
    [LEFT]    bg[ACTIVE] = shade (1.075,@bg_color)[/LEFT]
    }
    
    [LEFT]style "theme-menuitem" = "theme-wider" {[/LEFT]
    [LEFT]    fg[PRELIGHT]   =  @selected_fg_color[/LEFT]
    [LEFT]    text[PRELIGHT] =  @selected_fg_color[/LEFT]
    }
    
    [LEFT]style "theme-menubar" = "theme-default" {[/LEFT]
    [LEFT]    xthickness = 0[/LEFT]
    [LEFT]    ythickness = 1[/LEFT]
    }
    
    [LEFT]style "theme-menubar-item" = "theme-menuitem" {[/LEFT]
    [LEFT]    bg[SELECTED]   = shade (0.90, @bg_color)[/LEFT]
    [LEFT]    fg[PRELIGHT]   = @fg_color[/LEFT]
    [LEFT]    fg[NORMAL] = mix (0.85, @fg_color, @bg_color)[/LEFT]
    }
    
    [LEFT]style "theme-toolbar" = "theme-default" { }[/LEFT]
    
    [LEFT]style "theme-tree" = "theme-default" {[/LEFT]
    [LEFT]    xthickness   = 2[/LEFT]
    [LEFT]    ythickness   = 1[/LEFT]
    
    [LEFT]    GtkWidget::focus-padding = 0[/LEFT]
    
    [LEFT]    bg[NORMAL]   = shade (1.05, @bg_color)[/LEFT]
    [LEFT]    bg[PRELIGHT] = shade (1.15, @bg_color)[/LEFT]
    [LEFT]    bg[ACTIVE]   = shade (1.15, @bg_color)[/LEFT]
    }
    
    [LEFT]style "theme-tree-arrow" = "theme-default" {[/LEFT]
    [LEFT]    bg[NORMAL]   =  mix (0.70, shade (0.75, @bg_color), shade (0.80, @selected_bg_color))[/LEFT]
    [LEFT]    bg[PRELIGHT] =  mix (0.80, @bg_color, @selected_bg_color)[/LEFT]
    }
    
    [LEFT]style "theme-calendar" {[/LEFT]
    [LEFT]    xthickness     = 0[/LEFT]
    [LEFT]    ythickness     = 0[/LEFT]
    [LEFT]    bg[NORMAL]     = shade (0.92, @bg_color)[/LEFT]
    [LEFT]    bg[PRELIGHT]   = shade (0.92, @bg_color)[/LEFT]
    [LEFT]    bg[ACTIVE]     = shade (0.85, @bg_color)[/LEFT]
    [LEFT]    text[PRELIGHT] = @selected_fg_color[/LEFT]
    }
    
    [LEFT]style "theme-tooltips" = "theme-widest" {[/LEFT]
    [LEFT]    bg[NORMAL]   = @tooltip_bg_color[/LEFT]
    [LEFT]    bg[SELECTED] = @tooltip_bg_color[/LEFT]
    [LEFT]    fg[NORMAL]   = @tooltip_fg_color[/LEFT]
    [LEFT]    text[NORMAL] = shade (0.92, @tooltip_bg_color) # border color[/LEFT]
    }
    
    [LEFT]style "theme-progressbar" = "theme-default" {[/LEFT]
    [LEFT]    xthickness   = 2[/LEFT]
    [LEFT]    ythickness   = 2[/LEFT]
    [LEFT]    font_name    = "Bold"[/LEFT]
    [LEFT]    bg[NORMAL]   = shade (1.20, @bg_color)[/LEFT]
    [LEFT]    fg[PRELIGHT] = @selected_fg_color[/LEFT]
    }
    
    [LEFT]style "theme-combo" = "theme-button" {[/LEFT]
    [LEFT]    GtkButton::inner-border = { 0, 1, 0, 0 }[/LEFT]
    [LEFT]    base[ACTIVE] = @base_color[/LEFT]
    [LEFT]    text[ACTIVE] = @fg_color[/LEFT]
    }
    
    [LEFT]style "theme-combo-box" = "theme-button" {}[/LEFT]
    
    [LEFT]style "theme-combo-arrow" = "theme-button" {[/LEFT]
    [LEFT]    xthickness = 1[/LEFT]
    [LEFT]    ythickness = 1[/LEFT]
    }
    
    [LEFT]style "theme-viewport" = "theme-default" {[/LEFT]
    [LEFT]    xthickness = 8[/LEFT]
    [LEFT]    ythickness = 0[/LEFT]
    [LEFT]	engine "pixmap" {[/LEFT]
    [LEFT]	 image {[/LEFT]
    [LEFT]	  function	= SHADOW[/LEFT]
    	 }	 
    	}
    }
    
    [LEFT]style "theme-check-radio-buttons" = "theme-button" {[/LEFT]
    [LEFT]    #GtkWidget::interior-focus = 0[/LEFT]
    [LEFT]    GtkWidget::focus-padding = 1[/LEFT]
    [LEFT]    text[SELECTED]    = mix(0.1, @bg_color, @fg_color)[/LEFT]
    [LEFT]    text[INSENSITIVE] = shade (0.625, @bg_color)[/LEFT]
    [LEFT]    base[PRELIGHT]    = mix (0.75, @base_color, @selected_bg_color)[/LEFT]
    [LEFT]    base[SELECTED]    = shade (1.15, @bg_color)[/LEFT]
    [LEFT]    base[ACTIVE]      = @base_color[/LEFT]
    }
    
    [LEFT]# widget styles[/LEFT]
    [LEFT]class "GtkWidget"       style "theme-default"[/LEFT]
    [LEFT]class "GtkScale"        style "theme-scale"[/LEFT]
    [LEFT]class "GtkRange"        style "theme-range"[/LEFT]
    [LEFT]class "GtkFrame"        style "theme-frame"[/LEFT]
    [LEFT]class "GtkEntry"        style "theme-entry"[/LEFT]
    [LEFT]class "GtkProgressBar"  style "theme-progressbar"[/LEFT]
    [LEFT]class "GtkSeparator"    style "theme-wide"[/LEFT]
    [LEFT]class "GtkScrollbar"	style "theme-scrollbar"[/LEFT]
    [LEFT]class "GtkCalendar"     style "theme-calendar"[/LEFT]
    [LEFT]class "GtkViewport"     style "theme-viewport"[/LEFT]
    
    [LEFT]widget_class "*<GtkButton>"                 style "theme-button"[/LEFT]
    [LEFT]widget_class "*<GtkToolbar>*<GtkButton>"    style "theme-toolbar-button"[/LEFT]
    [LEFT]widget_class "*<GtkCheckButton>"            style  "theme-check-radio-buttons"[/LEFT]
    [LEFT]widget_class "*<GtkHandleBox>"              style "theme-handlebox"[/LEFT]
    
    [LEFT]# Toolbar[/LEFT]
    [LEFT]class "*HandleBox"          style "theme-toolbar"[/LEFT]
    [LEFT]class "GtkToolbar"          style "theme-toolbar"[/LEFT]
    [LEFT]widget_class "*HandleBox"   style "theme-toolbar"[/LEFT]
    
    [LEFT]# Notebook[/LEFT]
    [LEFT]widget_class "*<GtkNotebook>*<GtkEventBox>"     style "theme-notebook-bg"[/LEFT]
    [LEFT]widget_class "*<GtkNotebook>*<GtkDrawingArea>"  style "theme-notebook-bg"[/LEFT]
    [LEFT]widget_class "*<GtkNotebook>*<GtkLayout>"       style "theme-notebook-bg"[/LEFT]
    [LEFT]widget_class "*<GtkNotebook>"                   style "theme-notebook"[/LEFT]
    
    [LEFT]# combobox stuff[/LEFT]
    [LEFT]widget_class "*<GtkCombo>*"                 style "theme-combo"[/LEFT]
    [LEFT]widget_class "*<GtkComboBox>*<GtkButton>"   style "theme-combo-box"[/LEFT]
    [LEFT]widget_class "*<GtkComboBoxEntry>*"         style "theme-combo"[/LEFT]
    [LEFT]widget_class "*<GtkSpinButton>*"            style "theme-combo"[/LEFT]
    
    [LEFT]# tooltips stuff[/LEFT]
    [LEFT]widget "gtk-tooltip*"  style "theme-tooltips"[/LEFT]
    
    [LEFT]# treeview stuff[/LEFT]
    [LEFT]widget_class "*<GtkTreeView>.<GtkButton>"   style "theme-tree"[/LEFT]
    [LEFT]widget_class "*<GtkCTree>.<GtkButton>"      style "theme-tree"[/LEFT]
    [LEFT]widget_class "*<GtkList>.<GtkButton>"      style "theme-tree"[/LEFT]
    [LEFT]widget_class "*<GtkCList>.<GtkButton>"      style "theme-tree"[/LEFT]
    
    [LEFT]#For arrow bg[/LEFT]
    [LEFT]widget_class "*<GtkTreeView>.<GtkButton>*<GtkArrow>"    style "theme-tree-arrow"[/LEFT]
    [LEFT]widget_class "*<GtkCTree>.<GtkButton>*<GtkArrow>"      style "theme-tree-arrow"[/LEFT]
    [LEFT]widget_class "*<GtkList>.<GtkButton>*<GtkArrow>"      style "theme-tree-arrow"[/LEFT]
    
    [LEFT]# Menus[/LEFT]
    [LEFT]class "GtkMenu"                             style "theme-menu"[/LEFT]
    [LEFT]class "GtkMenubar"                          style "theme-menubar"[/LEFT]
    [LEFT]widget_class "*<GtkMenuItem>*"              style "theme-menuitem"[/LEFT]
    [LEFT]widget_class "*<GtkMenuBar>.<GtkMenuItem>*" style "theme-menubar-item"[/LEFT]
    
    
    #######################################################
    [LEFT]##  Panel[/LEFT]
    #######################################################
    
    [LEFT]style "theme-panel" {[/LEFT]
    [LEFT]    color["panel_bg"]  = shade(1.0, @bg_color)[/LEFT]
    [LEFT]    bg[NORMAL]         = @panel_bg[/LEFT]
    [LEFT]  bg[ACTIVE]	    = shade (0.9, @panel_bg)[/LEFT]
    [LEFT]    bg[SELECTED]     = shade (1.0, @panel_bg)[/LEFT]
    [LEFT]    bg[PRELIGHT]      = shade (1.15, @panel_bg) [/LEFT]
    }
    
    [LEFT]style "theme-panel-background" = "theme-panel" {[/LEFT]
    [LEFT]    xthickness   = 0[/LEFT]
    [LEFT]    ythickness   = 0[/LEFT]
    [LEFT]    bg_pixmap[NORMAL] = "images/panel_bg.png"[/LEFT]
    }
    
    [LEFT]widget "*PanelWidget*"      style "theme-panel-background"[/LEFT]
    [LEFT]widget "*PanelApplet*"      style "theme-panel-background"[/LEFT]
    [LEFT]widget "*fast-user-switch*"	   style "theme-panel-background" # Workaround for Fast User Switch applet[/LEFT]
    [LEFT]class "PanelApp*"       style "theme-panel-background"[/LEFT]
    [LEFT]class "PanelToplevel*"      style "theme-panel-background"[/LEFT]
    [LEFT]widget_class "*Panel*<GtkMenuBar>*"     style:highest "theme-panel-background" # The panel menubar[/LEFT]
    [LEFT]widget "*TomboyTray*"	    style "theme-panel-background" # Workaround for Tomboy[/LEFT]
    [LEFT]widget "*TomboyApplet*"	    style "theme-panel-background"[/LEFT]
    [LEFT]#XFCE panel[/LEFT]
    [LEFT]widget_class "*notif*"	    style "theme-panel-background"[/LEFT]
    [LEFT]widget_class "*Notif*"	    style "theme-panel-background"[/LEFT]
    [LEFT]widget_class "*Tray*"	    style "theme-panel-background"[/LEFT]
    [LEFT]widget_class "*tray*"	    style "theme-panel-background"[/LEFT]
    [LEFT]widget "*Xfce*Panel*"	    style "theme-panel-background"[/LEFT]
    [LEFT]class "*Xfce*Panel*"	    style "theme-panel-background"[/LEFT]
    
    [LEFT]style "theme-button-panel" {[/LEFT]
    [LEFT]    xthickness   = 3[/LEFT]
    [LEFT]    ythickness   = 3[/LEFT]
    }
    [LEFT]widget_class "*Panel*<GtkButton>"     style:highest "theme-button-panel"[/LEFT]
    
    [LEFT]style "theme-panelbutton" = "theme-panel" {[/LEFT]
    [LEFT]    bg[NORMAL]	 = shade(1.1, @panel_bg)[/LEFT]
    [LEFT]    bg[PRELIGHT] = shade(1.25, @panel_bg)[/LEFT]
    [LEFT]    bg[SELECTED] = @selected_bg_color[/LEFT]
    }
    
    [LEFT]widget "*PanelButton*"      style:highest "theme-panelbutton"[/LEFT]
    [LEFT]widget_class "*Panel*GtkToggleButton"	style:highest "theme-panelbutton"[/LEFT]
    [LEFT]widget_class "*Panel*GtkButton"	  style:highest "theme-panelbutton" [/LEFT]
    
    #######################################################
    [LEFT]##  GNOME specific[/LEFT]
    #######################################################
    
    [LEFT]widget_class "*.ETree.ECanvas"      style "theme-tree" #evolution[/LEFT]
    [LEFT]widget_class "*.ETable.ECanvas"  style "theme-tree" #evolution[/LEFT]
    
    [LEFT]#nautilus search stripe and other specialties[/LEFT]
    [LEFT]style "extra-view" {[/LEFT]
    [LEFT]	bg[NORMAL] = shade (0.6, @bg_color)[/LEFT]
    [LEFT]	fg[NORMAL] = @selected_fg_color[/LEFT]
    }
    
    [LEFT]style "evolution-new-button-workaround" {[/LEFT]
    [LEFT]    bg[NORMAL] = @bg_color[/LEFT]
    [LEFT]	engine "equinox" {[/LEFT]
    [LEFT]	 toolbarstyle = 0[/LEFT]
    	}
    }
    [LEFT]widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "evolution-new-button-workaround"[/LEFT]
    
    [LEFT]include "apps/nautilus.rc"[/LEFT]
    [LEFT]include "apps/gnome-system-monitor.rc"[/LEFT]
    [LEFT]include "apps/gnome-terminal.rc"[/LEFT]

---

### Post by dzon65 on 2010-08-31
Yeeeh!!Found it.Everything's matching.Problem solved.

---


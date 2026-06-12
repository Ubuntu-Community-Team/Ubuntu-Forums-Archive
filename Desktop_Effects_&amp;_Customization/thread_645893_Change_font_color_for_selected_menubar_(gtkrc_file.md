---
title: "Change font color for selected menubar (gtkrc file)?"
date: 2007-12-20
forum: Desktop Effects &amp; Customization
---

### Post by Ub1476 on 2007-12-20
Hi, I'm trying to change the font color for the the selected drop-down menu in the menubar (see screenshot). However, I just can't get it to work. I think I've tried every font setting now. Any help please? gtkrc file below:

```
##################################################
#												  				  #
#   	 				Creamy theme   by uel							  #
#						http://uel.jogger.pl							  #
#												  				  #
##################################################

gtk-icon-sizes = "panel-menu=24,24:panel=24,24:gtk-button=16,16:gtk-large-toolbar=24,24"

gtk_color_scheme = "fg_color:#000\nbg_color:#FBF8F1\nbase_color:#fff\ntext_color:#FDFAF6\nselected_bg_color:#E3AC57\nselected_fg_color:#202020\ntooltip_bg_color:#F5F5B5\ntooltip_fg_color:#000"

style "theme-default"
   {
  	GtkButton      	::default_border     	= { 0, 0, 0, 0 }
	GtkButton      ::child-displacement-x = 0
	GtkButton      ::child-displacement-y = 0
  	GtkRange       	::trough_border     	= 0
  	GtkPaned       	::handle_size        	= 6
  	GtkRange       	::slider_width       	= 16
  	GtkRange       	::stepper_size      	= 16

  	GtkScrollbar   		::min_slider_length  	= 35
  	GtkCheckButton 	::indicator_size    		= 10
  	GtkRadioButton 	::indicator_size     		= 10
  	GtkMenuBar     	::internal-padding 		= 3
  	GtkTreeView    	::expander_size     		= 14
	GtkTreeView    	::vertical-separator   	= 0
  	GtkExpander    	::expander_size     		= 16
  	GtkScale       		::slider-length         	= 16
	GtkScale       		::trough-side-details  	= 1
	GtkToolbar     		::internal-padding     	= 1
	GtkMenu        		::horizontal-padding   	= 0
	GtkMenu        		::vertical-padding		= 1
	WnckTasklist		::fade-overlay-rect		= 5
  
  	xthickness = 1
  	ythickness = 1

  	fg[NORMAL]        	= "#222222"
  	fg[PRELIGHT]      	= "#222222"
  	fg[SELECTED]      	= "#222222"
  	fg[ACTIVE]          	= "#222222" # notebook
  	fg[INSENSITIVE]   	= "#170E0E"

  	bg[NORMAL]        	= "#FDFBF8" # base color
  	bg[PRELIGHT]      	= "#FFFEFC" # prelight
  	bg[SELECTED]	= "#E5D499" # handlers color
  	bg[INSENSITIVE]   	= "#F7F1E5" # bg of inactive item
  	bg[ACTIVE]          	= "#E7DEC8" # background inactive notebook

  	base[NORMAL]      	= "#FDFCFA"
  	base[PRELIGHT]    	= "#B86D3C"
  	base[ACTIVE]        		= "#DFC091" # inactive/unmark
  	base[SELECTED]    	= "#E3AC57" # mark
  	base[INSENSITIVE] 	= "#F6EFE0"

  	text[NORMAL]      	= "#202020"
  	text[PRELIGHT]    	= "#202020"
  	text[ACTIVE]        	= "#202020"
  	text[SELECTED]    	= "#202020"
  	text[INSENSITIVE] 	= "#202020"

  engine "clearlooks" 
  {
    scrollbar_color   = "#F6EFE0"  #E3AC57 #EEDC82 #E5BB7D
    #colorize_scrollbar = TRUE
    menubarstyle      = 2 # 0 = flat, 1 = sunken, 2 = flat gradient
    toolbarstyle      = 1 # 0 = flat, 1 = enable effects
    animation         = TRUE
    style             = GLOSSY
  }
}

style "theme-wide" = "theme-default"
{
  xthickness = 2
  ythickness = 2
  text[NORMAL]      		= "#505050"
}

style "theme-wider" = "theme-default"
{
  xthickness = 3
  ythickness = 3
  text[NORMAL]      		= "#505050"
}

style "theme-entry" = "theme-wider"
{
  	bg[SELECTED]	   	= "#B86D3C"
  	text[NORMAL]      	= "#505050" 
  	text[PRELIGHT]      	= "#505050"
  	text[INSENSITIVE]      	= "#505050"
  	text[ACTIVE]      	= "#505050"
}

style "theme-button" = "theme-wider" # buttons on a panel
{
    #bg[NORMAL] 		= "#F4ECE3" 
    bg[ACTIVE]			= "#EDE7E0" 
    bg[SELECTED]		= "#E7DAB3" 
    bg[PRELIGHT]		= "#F2E2DC"
    fg[NORMAL]		= "#202020"
    fg[ACTIVE]			= "#202020"
    fg[PRELIGHT]		= "#202020"

  engine "clearlooks" 
	{
    radius = 0.0
    style  = GLOSSY
    	}
}

style "theme-buttons" = "theme-wider" # buttons
{
bg[NORMAL]      		= "#FDFAF6"
  	bg[INSENSITIVE] 		= "#FBF3EC"
  	bg[SELECTED]    		= "#D6AB8A"
  	bg[ACTIVE]      		= "#F1E7CF"  
 	bg[PRELIGHT]      		= "#F0E8CE"

	fg[PRELIGHT]	= "#8F7462"
	#fg[NORMAL]		= "#ffffff"
  	#fg[INSENSITIVE] = "#FFFEFC"
  	fg[ACTIVE]      = "#858282"

  engine "clearlooks" 
	{
    radius = 1.5
    style  = GLOSSY
    	}
}


style "theme-notebook" = "theme-wide" # notebook
{
	bg[NORMAL] 			= "#FDFCFA"
  	#bg[NORMAL]      		= "#FAF8F3" # WA&#379;NE
  	bg[INSENSITIVE] 		= "#FBF8F1"
  	bg[SELECTED]    		= "#FDFCFA" # pasek aktywnej zak&#322;adki
  	#bg[ACTIVE]      		= "#EBE6DA" # t&#322;o nieaktywnej zak&#322;adki
 	bg[PRELIGHT]      		= "#E1DCC8"

  	text[NORMAL]      		= "#8F7462"
  	text[PRELIGHT]      	= "#8F7462"
  	text[INSENSITIVE]      	= "#8F7462"
  	text[ACTIVE]      		= "#8F7462"

	fg[PRELIGHT]			= "#8F7462" #ffffff
	fg[NORMAL]			= "#ffffff" #f0f0f0
  	fg[INSENSITIVE] 		= "#FFFEFC" #a la biel
  	fg[ACTIVE]      		= "#505050" #ciemno-szary
        
  engine "clearlooks" 
	{
    radius = 0.0
    style  = GUMMY
    	}
}

style "theme-tasklist" = "theme-default"
{
  	xthickness = 4
  	ythickness = 2

  	bg[NORMAL]      		= "#505050"
  	text[NORMAL]      		= "#505050"
  	text[PRELIGHT]      	= "#505050"
  	text[INSENSITIVE]     	= "#505050"
  	text[ACTIVE]      		= "#505050"
}

style "theme-menu" = "theme-default"
{
  	xthickness = 2
  	ythickness = 1

  bg[NORMAL]		= "#202020"
  bg[SELECTED]		= "#202020"
  fg[PRELIGHT]		= "#202020"
  fg[NORMAL]			= "#FDFAF6"
  text[PRELIGHT]		= "#FDFAF6"
  text[NORMAL]		= "#FDFAF6"
}
style "theme-menu-item" = "theme-default"
{
  	xthickness = 2
  	ythickness = 2
  
  fg[PRELIGHT]	= "#202020"
  fg[NORMAL]		= "#FDFAF6"
  fg[ACTIVE]		= "#FDFAF6" 
  fg[INSENSITIVE]	= "#6B6B6B"
  
  text[PRELIGHT]	= "#FDFAF6"
  text[NORMAL]	= "#FDFAF6"
  text[ACTIVE]	= "#FDFAF6"
  text[INSENSITIVE] = "#FDFAF6"

  base[PRELIGHT]	= "#FDFAF6"
  base[NORMAL]	= "#202020" #fixes gimp
  
  bg[NORMAL]	= "#202020"
  bg[SELECTED]	= "#FF3300" #BAKGRUNDSFARGE FOR MERKEDE ITEMS I DROP-MENY

  engine "clearlooks" 
	{
    radius = 1.0
    style  = GLOSSY
    	}
}

style "theme-menubar" = "theme-default"
{
  	bg[NORMAL] = "#202020"
	bg[PRELIGHT]        = "#FDFAF6" #separators
  	fg[NORMAL] = "#202020" #ciemno-szary
	fg[PRELIGHT]      = "#202020"  #zmieniony
  	fg[ACTIVE] = "#202020" #ciemno-szary
  	text[NORMAL] = "#FDFAF6"#ciemno-szary
  	text[PRELIGHT] = "#202020" #ciemno-szary
  	text[INSENSITIVE]      = "#202020" #ciemno-szary
  	text[ACTIVE]      = "#FDFAF6" #ciemno-szary
        text[SELECTED]   = "#FDFAF6" 
}

style "theme-menubar-item" = "theme-default"
{
	fg[PRELIGHT]      = "#312619"
	fg[NORMAL]        = "#FDFAF6" # czcionka górnego menbara
	bg[PRELIGHT] = "#FBF8F1"
	bg[NORMAL]        = "#E5D499"
     	bg[SELECTED]	= "#202020" # FARGEN NÅR MAN KLIKKER PÅ EN MENY  
        text[SELECTED]   = "#FDFAF6"
        text[NORMAL] = "#FDFAF6"#ciemno-szary
}

style "theme-tree" = "theme-button"
{
  xthickness = 2
  ythickness = 2
  bg[NORMAL]        	= "#F6EFE0"
  bg[PRELIGHT]        	= "#ffffff"
  bg[INSENSITIVE]        	= "#ffffff"

  fg[NORMAL]        		= "#505050"
  fg[PRELIGHT]        	= "#ffffff"
  fg[INSENSITIVE]        	= "#ffffff"
}

style "theme-frame-title" = "theme-default"
{
  fg[NORMAL] 		= "#737373"
  fg[PRELIGHT]      		= "#202020" #????
  fg[INSENSITIVE]      	= "#FFF1D4"
  fg[ACTIVE]      		= "#FFF1D4" 
  bg[NORMAL] 		= "#737373"
  bg[PRELIGHT]        	= "#ffffff"
  bg[INSENSITIVE]        	= "#ffffff"
  bg[ACTIVE]        		= "#ffffff"
}

style "theme-tooltips" 	= "theme-default"
{
	xthickness = 4
	ythickness = 4
	bg[NORMAL] = @tooltip_bg_color
	fg[NORMAL] = @tooltip_fg_color
}

style "theme-progressbar" = "theme-wide"
{
  xthickness = 1
  ythickness = 1

base[SELECTED] = "#C39F4A"
bg[SELECTED] = "#C9A775"

  engine "clearlooks" 
	{
    radius = 1.0
    style  = GLOSSY
    	}
}

style "theme-scrollbar" = "theme-wide"
{
  xthickness = 0
  ythickness = 0

  base[PRELIGHT]	= "#353535"
  base[NORMAL]	= "#FFFFFF"

  engine "clearlooks" 
	{
    radius = 1.5
    style  = GUMMY
    	}
}

style "handlebox"		= "theme-default"
{
  xthickness = 1
  ythickness = 1
}



style "theme-combo" = "theme-wider"
{
  	xthickness = 1
  	ythickness = 1
}

style "metacity-frame"
{
  # Normal base color
  #bg[NORMAL]  = "#bbbbbb"

  # Unfocused title background color
  #bg[INSENSITIVE]  = { 0.8, 0.8, 0.8 }

  # Unfocused title text color
  #fg[INSENSITIVE]  = { 1.55, 1.55, 1.55 }

  # Focused icon color
  #fg[NORMAL]  = { 0.2, 0.2, 0.2 }

  # Focused title background color
  bg[SELECTED]  		= "#444444"
  base[ACTIVE]  		= "#E6B68A"

  # Focused title text color
  fg[SELECTED]  		= "#444444"
  fg[INSENSITIVE]  	= "#656565"
  fg[NORMAL]  		= "#656565"
  text[ACTIVE]  		= "#FDFAF6"
}

class "MetaFrames" 	  					style "metacity-frame"
class "GtkWindow"      						style "metacity-frame"

# widget styles
class "GtkWidget"      						style "theme-default"
class "GtkButton"      						style "theme-buttons"
class "GtkScale"       						style "theme-default"
class "GtkCombo"       						style "theme-combo"
class "GtkRange"       						style "theme-wider"
class "GtkFrame"       						style "theme-wider"
class "GtkMenu"        						style "theme-menu"
class "GtkEntry"       						style "theme-entry"
class "GtkMenuItem"    					style "theme-menu-item"
class "GtkNotebook"    						style "theme-notebook"
class "GtkProgress" 						style "theme-default"
class "GtkProgressBar" 					style "theme-progressbar"
class "*MenuBar*"      						style "theme-menubar"

class "GtkTreeView"       					style "theme-default"
class "GtkList"       						style "theme-default"
class "GtkListItem"       					style "theme-default"
class "GtkCList"       						style "theme-default"
class "GtkContainer"						style "theme-default"
class "GtkListView"						style "theme-default"
class "GtkListHeader"						style "theme-default"


class "GtkStyle"       						style "theme-default"
class "GtkCTree"       						style "theme-default"

class "GtkTree"       						style "theme-default"
class "GtkTreeItem"       					style "theme-default"

class "GtkScrollbar"						style "theme-scrollbar"

class "GtkCheckButton"     					style "theme-default"
class "GtkRadioButton"     					style "theme-default"
class "GtkRadioMenuItem"    				style "theme-default"
class "GtkCheckMenuItem"   				style "theme-default"

# OO and FF fonts menubar
class "GtkMenuItem" 						style "theme-menu-item"
class "GtkTearoffMenuItem" 				style "theme-menu-item"
class "GtkImageMenuItem" 					style "theme-menu-item"
class "GtkHandleBox"    					style "handlebox"



widget_class "*GtkList*"       				style "theme-default"

widget_class "*MenuItem.*" 				style "theme-menu-item"
widget_class "*MenuBar.*"  				style "theme-menubar-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" 		style "theme-wider"
widget_class "*.GtkCombo.GtkButton"    			style "theme-wider"
widget_class "*.GtkComboBoxEntry.GtkButton" 	style "theme-wider"
widget_class "*GtkCombo*" 					style "theme-wider"
widget_class "*Combo*"						style "theme-default"
widget_class "*ComboBoxEntry*"				style "theme-wider"

# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" 		style "theme-tasklist"
widget "gtk-tooltips" 							style "theme-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.*" 					style "theme-default"
widget_class "*.GtkCTree.*" 					style "theme-default"
widget_class "*.GtkList.*" 						style "theme-default"
widget_class "*.GtkCList.*" 					style "theme-default"
widget_class "*.GtkFrame.GtkLabel" 			style "theme-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" 		style "theme-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" 		style "theme-notebook"

# PANEL
style "panel"
{
	bg[NORMAL]   = "#202020"
	fg[NORMAL]   = "#202020" #fdfdfd
	text[NORMAL] = "#575757" #tekst nieaktywnych w "dodaj do panelu..."
}
style "panelbuttons" = "theme-button"
{
    bg[NORMAL] 		= "#202020"
    bg[ACTIVE]		= "#353535" #br&#261;z  #995021 #1F4450 #213B40
    bg[SELECTED]	= "#819230" #CF7643 #5B7004 #8B8715
    bg[PRELIGHT]	= "#3E3E3E" #3B5155
    
    fg[NORMAL]		= "#D6D6D6" #fdfd fd #D6D6D6
    fg[ACTIVE]		= "#DCDCDC" #DCDCDC
    fg[PRELIGHT]	= "#D6D6D6" #D6D6D6
}

style "panel-menubar-black" = "theme-menubar"
{
#font_name = "Segoe UI Bold 9"
#font_name = "Sans 8"
  bg[NORMAL] 		= "#202020"
  bg[ACTIVE]		= "#353535" #br&#261;z  #995021 #1F4450 #213B40
  bg[SELECTED]	= "#819230" #CF7643 #5B7004 #8B8715
  bg[PRELIGHT]	= "#3E3E3E" #3B5155
  fg[NORMAL] = "#FBF8F1"
  text[NORMAL] = "#FBF8F1"
  fg[PRELIGHT] = "#E2E2E2"
  fg[ACTIVE] = "#202020" #???

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/mnbar.png"
			border	= { 0, 0, 0, 0 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/mnbar.png"
			border	= { 0, 0, 0, 0 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/mnbar.png"
			border	= { 0, 0, 0, 0 }
			stretch	= TRUE
    		}

		image
		{
			function			= BOX
			recolorable		= TRUE
			state = PRELIGHT
			file				= "Menu-Menubar/menubar-item.png"
			border			= { 10, 10, 10, 10 }
			stretch			= TRUE
		}

 	}

}

class "*Panel*" 							style	"panel"
class "*PanelMenubar*" 					style	"panel-menubar-black"
widget_class "*Panel*GtkToggleButton" 		style	"theme-button"
widget_class "*Panel*Button" 				style	"panelbuttons"
widget_class "*Panel*b*" 					style	"panelbuttons"
widget_class "*Panel*.*MenuBar*"		style "panel-menubar-black"

```

It's just a couple modifications by the theme "Creamy" by uel, as I trying to learn myself some theming!:)

---

### Post by Ub1476 on 2007-12-21
bump

---

### Post by Ub1476 on 2007-12-21
bump

---


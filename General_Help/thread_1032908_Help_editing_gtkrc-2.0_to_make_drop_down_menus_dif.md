---
title: "Help editing gtkrc-2.0 to make drop down menus different color."
date: 2009-01-06
forum: General Help
---

### Post by cjohn106 on 2009-01-06
I am trying to edit the following theme's gtkrc. The drop down menus in windows and applications (File, Edit, View...) are black, transparent and have white text. I can't find where to change these values in the gtkrc. If someone could point it out to me that would be awesome. Here it is:



# Murrina-LiNsta v0.1.0
# Uses Murrina Engine by Cimi
# Created by Etienne Alaurent

style "theme-default"
{
  GtkButton			::default_border		= { 1, 1, 1, 1 }
  GtkButton			::default_outside_border	= { 2, 2, 2, 2 }
  GtkButton			::child-displacement-x	= 1
  GtkButton			::child-displacement-y	= 1
  GtkRange       		::trough_border		= 0
  GtkRange       		::slider_width			= 15
  GtkRange       		::stepper_size			= 15
  GtkPaned       		::handle_size			= 6
  GtkScrollbar   		::min_slider_length		= 30
  GtkRadioMenuItem	::indicator_size		= 12
  GtkCheckMenuItem	::indicator_size		= 12
  GtkRadioButton		::indicator_size		= 12
  GtkCheckButton		::indicator_size		= 12
  GtkMenuBar			::internal-padding		= 1
  GtkTreeView			::expander_size		= 12
  GtkExpander			::expander_size		= 12
  GtkScale			::slider-length			= 24

  xthickness = 2
  ythickness = 2
  
#  gtk-icon-sizes = "panel-menu=24,24:panel=24,24:gtk-button=24,24:gtk-large-toolbar=24,24"

#  NORMAL : The normal color, nothing special happening.
#  PRELIGHT : Prelight means mouse over effects. Usually the background will be slightly lighter.
#  ACTIVE : This state is used for buttons while the mouse is pressed, texts in tabs unselected, texts in check and radio buttons activated.
#  INSENSITIVE : Used for widgets that are insensitive and cannot be used at that point.
#  SELECTED : This state is used for example for selected text.

# Used for text on buttons. Also used for the button borders in some engines.
  fg[NORMAL]		= "#353535"
  fg[PRELIGHT]		= "#353535" #"#3585AF" #
  fg[ACTIVE]		= "#353535"
  fg[SELECTED]	= "#353535"
  fg[INSENSITIVE]	= "#9B9B9B"

# This is the background color of windows and buttons.
  bg[NORMAL]		= "#F7F7F7"
  bg[PRELIGHT]	= "#ABDDF8" #"#CEEEFF" # Couleur de range
  bg[ACTIVE]		= "#DEDEDE" #"#DADADA" #"#D8E8F0" # Couleur des tabs non sélectionnées
  bg[SELECTED]	= "#ABDDF8" #"#9AD2F0" # Couleur de fond de la ligne de range, des boutons checks et radio et du contours de la zone de saisie spin
  bg[INSENSITIVE]	= "#EEEEEE"

# Background color of text widgets and lists.
  base[NORMAL]	= "#FFFFFF"
  base[PRELIGHT]	= "#FFFFFF"
  base[ACTIVE]	= "#C8ECFF" # Couleur de fond active dans les listes quand la fenêtre n'est pas sélectionnée
  base[SELECTED]	= "#ABDDF8"
  base[INSENSITIVE] = "#FFFFFF"

# Text color for text input widgets and lists
  text[NORMAL]	= "#353535"
  text[PRELIGHT]	= "#353535"
  text[ACTIVE]		= "#353535"
  text[SELECTED]	= "#353535"
  text[INSENSITIVE]	= "#9B9B9B"

  engine "murrine"
  {
	 scrollbarstyle		= 2 # Enable or disable circles, stripes, handles
	 menuitemstyle	= 1 # 0 = flat, 1 = glassy, 2
	 listviewstyle		= 1 # 0 = nothing, 1 = dotted
	 glazestyle		= 0 # 0 = flat hilight, 1 = curved hilight, 2 = concave style, 3 = top curved hilight, 4 = beryl style
	 scrollbar_color	= "#9AD2F0"
         contrast			= 1.0 #2
         hilight_ratio		= 1.0
         gradients		= TRUE
         menustyle		= 1
	 menubarstyle		= 1 # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
	 menubaritemstyle	= 1 # 0 = menuitem look, 1 = button look
	 listviewheaderstyle	= 1 # 0 = flat, 1 = glassy, 2 = raised
	 roundness		= 2 # 0 = squared, 1 = old default, more will increase roundness
         animation		= TRUE # FALSE = disabled, TRUE = enabled
  }
}

style "theme-wide" = "theme-default"
{
  xthickness = 1
  ythickness = 1
}

style "theme-wider" = "theme-default"
{
  xthickness = 3
  ythickness = 3
}

style "theme-menubar" = "theme-default"
{
  xthickness = 2
  ythickness = 2
}

style "theme-button" = "theme-wider"
{
  fg[NORMAL]		= "#353535"	# texte barre d'outils & tabs + titre & boutons inactifs metacity
  fg[PRELIGHT]		= "#353535"	# boutons et menu survolés
	
  bg[NORMAL]		= "#D7D7D7"
  bg[PRELIGHT]	= "#ABDDF8"
  bg[ACTIVE]		= "#9AD2F0" #"#8EC7E6" #
  bg[INSENSITIVE]	= "#EEEEEE"
}

style "theme-tool-button" = "theme-wider"
{
  fg[NORMAL]		= "#353535"	# texte barre d'outils & tabs + titre & boutons inactifs metacity
  fg[PRELIGHT]		= "#353535"	# boutons et menu survolés
	
  bg[NORMAL]		= "#D7D7D7"
  bg[PRELIGHT]	= "#5FA9B3"
  bg[ACTIVE]		= "#479EAB" #"#8EC7E6" #
  bg[INSENSITIVE]	= "#EEEEEE"
  engine "murrine"
  {
         contrast			= 1.2 #2
         #hilight_ratio		= 1.2
  }
}

style "theme-combo" = "theme-button"
{
}

style "theme-scale" = "theme-wider"
{
  bg[PRELIGHT]	= "#9AD2F0"
  bg[SELECTED]	= "#ABDDF8" #"#CEEEFF" #"#ABDDF8"
}

style "theme-range" = "theme-default"
{
  xthickness = 3
  ythickness = 3
  bg[NORMAL]		= "#F0F0F0"
}

style "theme-checkradiomenuitem" = "theme-default"
{
  bg[SELECTED]	= "#9AD2F0"
  base[NORMAL]	= "#FFFFFF"
}

style "theme-notebook" = "theme-wide"
{
  bg[NORMAL]		= "#F0F0F0"
  bg[SELECTED]	= "#ABDDF8"
  bg[INSENSITIVE]	= "#EEEEEE"
}

style "theme-tasklist" = "theme-default"
{
  xthickness = 5
  ythickness = 3
  #bg[ACTIVE] = "#000000"
}

style "theme-menu-black" = "theme-default"
{
  xthickness = 3
  ythickness = 2
  bg[NORMAL]		= "#353535"
  bg[SELECTED]	= "#8EC7E6"

  #PanelMenu::gradient_bg = 1
  #PanelMenu::stripe-color = { 0.24, 0.44, 0.66 }
  #PanelMenu::stripe-color-light = { 0.54, 0.74, 0.96 }
}

style "theme-menu-gray" = "theme-default"
{
  xthickness = 3
  ythickness = 2
  bg[NORMAL]		= "#D0D0D0"
  bg[SELECTED]	= "#8EC7E6"

  #PanelMenu::gradient_bg = 1
  #PanelMenu::stripe-color = { 0.24, 0.44, 0.66 }
  #PanelMenu::stripe-color-light = { 0.54, 0.74, 0.96 }
}

style "theme-menu-item-black" = "theme-default"
{
  xthickness = 2
  ythickness = 2 #3  
  fg[PRELIGHT]		= "#353535" #"#3585AF" # couleur des flêches
  fg[NORMAL]		= "#FFFFFF"
  fg[INSENSITIVE]	= "#6B6B6B" #"#353535" #
  
  text[PRELIGHT]	= "#353535"
  text[NORMAL]	= "#FFFFFF"

  base[PRELIGHT]	= "#353535"
  base[NORMAL]	= "#FFFFFF" #fixes gimp
  
  bg[NORMAL]		= "#414141" #"#393939" #color of separators in menu
  bg[SELECTED]	= "#9AD2F0"
}

style "theme-menu-item-gray" = "theme-default"
{
  xthickness = 2
  ythickness = 2 #3  
  fg[PRELIGHT]		= "#000000" # couleur des flêches
  fg[NORMAL]		= "#353535"
  fg[INSENSITIVE]	= "#6B6B6B"
  
  text[PRELIGHT]	= "#000000"
  text[NORMAL]	= "#353535"

  base[PRELIGHT]	= "#000000"
  base[NORMAL]	= "#353535" #fixes gimp
  
  bg[NORMAL]		= "#C9C9C9" #color of separators in menu
  bg[SELECTED]	= "#9AD2F0"
}

style "menubar-blue-green" = "theme-menubar"
{
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
  fg[PRELIGHT] = "#C7DBFC"
  fg[ACTIVE] = "#C7DBFC"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/menubar-blue-green.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/menubar-blue-green.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/menubar-inactive.png"
			border	= { 2, 2, 2, 2 }
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

style "menubar-blue" = "theme-menubar"
{
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
  fg[PRELIGHT] = "#C7DBFC"
  fg[ACTIVE] = "#C7DBFC"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/menubar-blue.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/menubar-blue.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/menubar-inactive.png"
			border	= { 2, 2, 2, 2 }
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

style "menubar-blue-vista" = "theme-menubar"
{
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
  fg[PRELIGHT] = "#C7DBFC"
  fg[ACTIVE] = "#C7DBFC"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/menubar-blue-vista.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/menubar-blue-vista.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/menubar-inactive.png"
			border	= { 2, 2, 2, 2 }
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

style "menubar-black" = "theme-menubar"
{
#font_name = "Segoe UI Bold 9"
#font_name = "Sans 8"
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
  fg[PRELIGHT] = "#B9B9B9"
  fg[ACTIVE] = "#B9B9B9"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/menubar-black.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/menubar-black.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/menubar-inactive.png"
			border	= { 2, 2, 2, 2 }
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

style "menubar-graphite" = "theme-menubar"
{
#font_name = "Segoe UI Bold 9"
#font_name = "Sans 8"
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
  fg[PRELIGHT] = "#B9B9B9"
  fg[ACTIVE] = "#B9B9B9"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/menubar-graphite.png"
			#border	= { 2, 2, 2, 2 }
			stretch	= FALSE #TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/menubar-graphite.png"
			#border	= { 2, 2, 2, 2 }
			stretch	= FALSE #TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/menubar-graphite-inactive.png"
			#border	= { 2, 2, 2, 2 }
			stretch	= FALSE #TRUE
    		}

		image
		{
			function			= BOX
			recolorable		= TRUE
			state = PRELIGHT
			file				= "Menu-Menubar/menubar-item.png"
			#border			= { 10, 10, 10, 10 }
			stretch			= TRUE
		}

 	}
}

style "menubar-red" = "theme-menubar"
{
#font_name = "Segoe UI Bold 9"
#font_name = "Sans 8"
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
  fg[PRELIGHT] = "#FFE8E8"
  fg[ACTIVE] = "#FFE8E8"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/menubar-red.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/menubar-red.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/menubar-inactive.png"
			border	= { 2, 2, 2, 2 }
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

style "toolbar-clear-alt-1" =  "theme-menubar"
{
  #bg_pixmap[NORMAL] =*"Toolbar/toolbar-clear-alt-1.png"
  fg[NORMAL] = "#000000"
  text[NORMAL] = "#000000"
  fg[PRELIGHT] = "#404040"
  fg[ACTIVE] = "#404040"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			file		= "Toolbar/toolbar-clear-alt-1.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}
 	}
}

style "toolbar-blue-light-1" =  "theme-menubar"
{
  fg[NORMAL] = "#000000"
  text[NORMAL] = "#000000"
  fg[PRELIGHT] = "#404040"
  fg[ACTIVE] = "#404040"
  #bg_pixmap[NORMAL] =*"Toolbar/toolbar-blue-light-1.png"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			file		= "Toolbar/toolbar-blue-light-1.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}
 	}
}

style "toolbar-blue-light-2" =  "theme-menubar"
{
  fg[NORMAL] = "#000000"
  text[NORMAL] = "#000000"
  fg[PRELIGHT] = "#404040"
  fg[ACTIVE] = "#404040"
  #bg_pixmap[NORMAL] =*"Toolbar/toolbar-blue-light-2.png"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			file		= "Toolbar/toolbar-blue-light-2.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}
 	}
}

style "toolbar-blue-light-4" =  "theme-menubar"
{
  fg[NORMAL] = "#000000"
  text[NORMAL] = "#000000"
  fg[PRELIGHT] = "#404040"
  fg[ACTIVE] = "#404040"
  #bg_pixmap[NORMAL] =*"Toolbar/toolbar-blue-light-4.png"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			file		= "Toolbar/toolbar-blue-light-4.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}
 	}
}

style "panel-translucent" = "theme-default"
{
  xthickness            		= 2
  ythickness            		= 0

  fg[NORMAL]			= "#353535"
  fg[PRELIGHT]			= "#FFFFFF" #"#3585AF" #
  fg[ACTIVE]			= "#FFFFFF"
  fg[SELECTED]		= "#000000"
  fg[INSENSITIVE]		= "#6B6B6B" #"#8A857C"
  
  bg[SELECTED]		= "#9AD2F0"
  bg_pixmap[NORMAL]	= "Panel/panel-bg-translucent-3-24.png"
}

style "panel-black" = "theme-default"
{
  xthickness            		= 2
  ythickness            		= 0

  fg[NORMAL]			= "#FFFFFF"
  fg[PRELIGHT]			= "#FFFFFF" #"#3585AF" #
  fg[ACTIVE]			= "#FFFFFF"
  fg[SELECTED]		= "#000000"
  fg[INSENSITIVE]		= "#6B6B6B" #"#8A857C"
  
  bg[SELECTED]		= "#9AD2F0"
  bg_pixmap[NORMAL]	= "Panel/panel-bg-black-36.png"
}

style "panel-gray" = "theme-default"
{
  xthickness            		= 2
  ythickness            		= 0

  fg[NORMAL]			= "#000000"
  fg[PRELIGHT]			= "#FFFFFF"
  fg[ACTIVE]			= "#FFFFFF"
  fg[SELECTED]		= "#353535"
  fg[INSENSITIVE]		= "#6B6B6B"
  
  bg[SELECTED]		= "#9AD2F0"
  bg_pixmap[NORMAL]	= "Panel/panel-bg-gray-24.png"
}

style "panel-graphite" = "theme-default"
{
  xthickness            		= 2
  ythickness            		= 0

  fg[NORMAL]			= "#FFFFFF"
  fg[PRELIGHT]			= "#FFFFFF" #"#3585AF" #
  fg[ACTIVE]			= "#FFFFFF"
  fg[SELECTED]		= "#000000"
  fg[INSENSITIVE]		= "#6B6B6B" #"#8A857C"
  
  bg[SELECTED]		= "#9AD2F0"
  bg_pixmap[NORMAL]	= "Panel/panel-bg-graphite-24.png"
}

style "panel-blue" = "theme-default"
{
  xthickness            		= 2
  ythickness            		= 0

  fg[NORMAL]			= "#FFFFFF"
  fg[PRELIGHT]			= "#FFFFFF" #"#3585AF" #
  fg[ACTIVE]			= "#FFFFFF"
  fg[SELECTED]		= "#000000"
  fg[INSENSITIVE]		= "#6B6B6B" #"#8A857C"
  
  bg[SELECTED]		= "#9AD2F0"
  bg_pixmap[NORMAL]	= "Panel/panel-bg-blue-24.png"
}

style "panelbuttons-black" = "theme-menu-item-black"
{
  GtkWidget::focus_padding = 2

	engine "pixmap" {

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= NORMAL
			file			= "Panel/panelbutton_black_2.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= PRELIGHT
			file			= "Panel/panelbutton_black_1b.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			shadow		= OUT
			state			= PRELIGHT
			file			= "Panel/panelbutton_black_2.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			shadow		= IN
			state			= PRELIGHT
			file			= "Panel/panelbutton_black_4b.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= ACTIVE
			file			= "Panel/panelbutton_black_4c.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= INSENSITIVE
			file			= "Panel/panelbutton_black_1.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}  

	}

}

style "panelbuttons-gray" = "theme-menu-item-gray"
{
  GtkWidget::focus_padding = 2

	engine "pixmap" {

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= NORMAL
			file			= "Panel/panelbutton_gray_2.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= PRELIGHT
			file			= "Panel/panelbutton_gray_1.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			shadow		= OUT
			state			= PRELIGHT
			file			= "Panel/panelbutton_gray_2.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			shadow		= IN
			state			= PRELIGHT
			file			= "Panel/panelbutton_gray_4.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= ACTIVE
			file			= "Panel/panelbutton_gray_4.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= INSENSITIVE
			file			= "Panel/panelbutton_gray_1.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}  

	}

}

style "panelbuttons-base" = "theme-menu-item-black"
{
  GtkWidget::focus_padding = 2

	engine "pixmap" {

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= NORMAL
			file			= "Panel/panelbutton_2.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= PRELIGHT
			file			= "Panel/panelbutton_1.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			shadow		= OUT
			state			= PRELIGHT
			file			= "Panel/panelbutton_2.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			shadow		= IN
			state			= PRELIGHT
			file			= "Panel/panelbutton_4.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= ACTIVE
			file			= "Panel/panelbutton_4.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}

		image
		{
			function		= BOX
			recolorable	= TRUE
			state			= INSENSITIVE
			file			= "Panel/panelbutton_1.png"
			border		= { 4, 4, 4, 4 }
			stretch		= TRUE
		}  

	}

}

style "panel-menubar-black" = "theme-menubar"
{
#font_name = "Segoe UI Bold 9"
#font_name = "Sans 8"
  fg[NORMAL] = "#FFFFFF"
  text[NORMAL] = "#FFFFFF"
  fg[PRELIGHT] = "#E2E2E2"
  fg[ACTIVE] = "#E2E2E2"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/menubar-panel.png"
			border	= { 0, 0, 0, 0 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/menubar-panel.png"
			border	= { 0, 0, 0, 0 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/menubar-panel.png"
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

style "panel-menubar-gray" = "theme-menubar"
{
#font_name = "Segoe UI Bold 9"
#font_name = "Sans 8"
  fg[NORMAL] = "#000000"
  text[NORMAL] = "#000000"
  fg[PRELIGHT] = "#353535"
  fg[ACTIVE] = "#353535"

	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "Menu-Menubar/menubar-panel.png"
			border	= { 0, 0, 0, 0 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "Menu-Menubar/menubar-panel.png"
			border	= { 0, 0, 0, 0 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "Menu-Menubar/menubar-panel.png"
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

style "theme-tree" = "theme-default"
{
  #GtkTreeView::odd_row_color		= "#ff0000"
  #GtkTreeView::even_row_color	= "#ff0000"
  xthickness = 2
  ythickness = 2
  bg[NORMAL]		= "#E8E8E8"
  bg[PRELIGHT]	= "#CEEEFF"
  bg[ACTIVE]		= "#BDE8FF"
  engine "murrine"
  {
         contrast			= 1.1
         hilight_ratio		= 0.9
         gradients		= TRUE
  }
}

style "theme-tooltips" = "theme-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] 		= "#FFFCDB"
}

style "theme-progressbar" = "theme-wide"
{
  xthickness = 1
  ythickness = 1
  bg[SELECTED]	= "#85FF8B" #"#6BF56F" #
  fg[PRELIGHT]		= "#FFFFFF"
  bg[NORMAL]		= "#F0F0F0"
}

style "theme-frame-title" = "theme-default"
{
  fg[NORMAL]		= "#404040"
}

style "metacity-frame" = "theme-default"
{
  bg[SELECTED]	= "#ABDDF8"

  # Focused title text color
  fg[SELECTED]	= "#FFFFFF"
}

style "theme-slab" = "theme-default"
{
    bg[SELECTED]	= "#84b0da"    # Outline
    bg[NORMAL]	= "#fdfbf7"      # Base bg color
    bg[ACTIVE]		= "#e9eef5"      # Right side bg color
    fg[NORMAL]		= "#6a97c5"      # Left side caption text color
    fg[INSENSITIVE]	= "#5c8dbf" # Right side caption text color
}

style "theme-evolution-hack" #= "clearlooks-default"
{
  bg[ACTIVE]		= "#C8ECFF"
  bg[SELECTED]	= "#ABDDF8"
  fg[ACTIVE]		= "#353535"
  fg[SELECTED]	= "#353535"
}

style "theme-shell-highlight" = "theme-default"
{
}

#nautilus search stripe and other specialties
style "theme-extra-view"
{
	bg[NORMAL]	= "#C8ECFF"
	#font = "Sans 6"
}

style "theme-desktop-icon"
{
	NautilusIconContainer::frame_text = 0
	text[NORMAL] =	"#FFFFFF"
	base[NORMAL] =	"#353535"
	NautilusIconContainer::normal_alpha = 100
}

# Nautilus search stripe
widget "*.nautilus-extra-view-widget"		style:highest "theme-extra-view"

# Color Desktop font
widget_class "*DesktopIcon*" style "theme-desktop-icon"

# GNOME-main-menu slab
#class "SlabWindow" style "theme-slab"

# Evolution
widget_class "*GtkCTree*"				style "theme-evolution-hack"
widget_class "*GtkList*"				style "theme-evolution-hack"
widget_class "*GtkCList*"				style "theme-evolution-hack"
widget_class "*.ETree.*"				style "theme-evolution-hack"

# widget styles
class "GtkWidget"						style "theme-default"
class "GtkButton"						style "theme-button"
class "GtkToggleButton"					style "theme-button"
class "GtkScale"						style "theme-range"
class "GtkCombo"						style "theme-combo" #"theme-button" #
class "GtkRange"						style "theme-range" #"theme-wide" #
class "GtkFrame"						style "theme-wide"
class "GtkMenu"						style "theme-menu-black" #"theme-menu-gray" #
class "GtkEntry"						style "theme-wider"
class "GtkMenuItem"					style "theme-menu-item-black" #"theme-menu-item-gray" #
class "GtkTearoffMenuItem"				style "theme-menu-item-black" #"theme-menu-item-gray" #
class "GtkImageMenuItem"				style "theme-menu-item-black" #"theme-menu-item-gray" #
class "GtkNotebook"					style "theme-notebook"
class "GtkProgressBar"					style "theme-progressbar"
class "GtkSpinButton"					style "theme-button"

# panel stuff
widget "*PanelApplet*"					style "panel-black" #"panel-gray" #"panel-graphite" #"panel-blue" #
widget "*TrayIcon*"					style "panel-black" #"panel-gray" #"panel-graphite" #"panel-blue" #
class "Panel*"							style "panel-black" #"panel-gray" #"panel-graphite" #"panel-blue" #
widget_class "*Panel*GtkToggleButton"	style "panelbuttons-black" #"panelbuttons-base" #"panelbuttons-gray" #
widget_class "Panel*GtkButton"			style "panelbuttons-black" #"panelbuttons-base" #"panelbuttons-gray" #

# menu and menubar stuff
widget_class "*MenuItem.*"				style "theme-menu-item-black" #"theme-menu-item-gray" #
class "*MenuBar*"						style "menubar-blue-vista" #"menubar-blue-green" #
widget_class "*MenuBar.*" 				style "menubar-blue-vista" #"menubar-blue-green" #
widget_class "Nautilus*.GtkMenuBar*"		style "menubar-blue-green" #"menubar-blue" #"menubar-black" #"menubar-graphite" #
widget_class "*Panel*.*MenuBar*"		style "panel-menubar-black" #"panel-menubar-gray" #
#widget_class "E*.GtkMenuBar*"			style "menubar-black"


# toolbar stuff
class "*Toolbar"						style "toolbar-blue-light-2" #"toolbar-blue-light-4" #"toolbar-blue-light-1" #"toolbar-clear-alt-1" #
widget_class "*Toolbar"					style "toolbar-blue-light-2" #"toolbar-blue-light-4" #"toolbar-blue-light-1" #"toolbar-clear-alt-1" #
widget_class "Nautilus*Toolbar"			style "toolbar-clear-alt-1" #"toolbar-blue-green" #"toolbar-blue-light-1" #
#widget_class "E*Toolbar"				style "toolbar-clear-alt-1" #"toolbar-blue-green" #"toolbar-blue-light-1" #
class "*BonoboDockItem"				style "toolbar-clear-alt-1"
widget_class "*BonoboDockItem"			style "toolbar-clear-alt-1"
widget_class "*Tool*GtkToggleButton"		style "theme-button" #"theme-tool-button"
widget_class "*Tool*GtkButton"			style "theme-button" #"theme-tool-button"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton"	style "theme-combo" #"theme-button"
widget_class "*.GtkCombo.GtkButton"		style "theme-combo" #"theme-button"

# check & radio menuitem stuff
class "GtkRadioMenuItem"    				style "theme-checkradiomenuitem"
class "GtkCheckMenuItem"   				style "theme-checkradiomenuitem"

# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton"	style "theme-tasklist"
widget "gtk-tooltips"					style "theme-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton"	style "theme-tree"
widget_class "*.GtkCTree.GtkButton"		style "theme-tree"
widget_class "*.GtkList.GtkButton" 		style "theme-tree"
widget_class "*.GtkCList.GtkButton"		style "theme-tree"
widget_class "*.GtkFrame.GtkLabel"		style "theme-frame-title"

#class "GtkList"						style "list-header"
#class "GtkTree"						style "list-header"
#class "GtkCList"						style "list-header"
#class "GtkCTree"						style "list-header"
#class "GtkTreeView"					style "list-header"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "theme-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "theme-notebook"

# wm stuff
class "MetaFrames"					style "metacity-frame"
class "GtkWindow"						style "metacity-frame"

---

### Post by IceReaver75 on 2009-01-06
in the gtk-2.0 folder for the theme there should be a folder called menu there.  Open that folder and then open the menu.png in gimp and change the color to what color you would like your drop down menus to be.  Save the new color and then restart x by pressing ctrl-alt-backspace.  when desktop reloads the drop down menus should have changed to your new color.

---

### Post by Ivo Moelans on 2009-01-07
Except that this theme isn't using pixmaps for the menu.

First (if you haven't done this already) when you have opened the gtkrc-2.0 file in Text Editor go to *View&#8594;Highlight Mode&#8594;Others&#8594;GtkRC*. The file should now be color coded.

On line 165 you'll find this code

```
style "theme-menu-black" = "theme-default"
{
  xthickness = 3
  ythickness = 2
  bg[NORMAL]		= "#353535"
  bg[SELECTED]	= "#8EC7E6"

  #PanelMenu::gradient_bg = 1
  #PanelMenu::stripe-color = { 0.24, 0.44, 0.66 }
  #PanelMenu::stripe-color-light = { 0.54, 0.74, 0.96 }
}

```
And on line 189 you'll find this code:

```
style "theme-menu-item-black" = "theme-default"
{
  xthickness = 2
  ythickness = 2 #3  
  fg[PRELIGHT]		= "#353535" #"#3585AF" # couleur des flêches
  fg[NORMAL]		= "#FFFFFF"
  fg[INSENSITIVE]	= "#6B6B6B" #"#353535" #
  
  text[PRELIGHT]	= "#353535"
  text[NORMAL]	= "#FFFFFF"

  base[PRELIGHT]	= "#353535"
  base[NORMAL]	= "#FFFFFF" #fixes gimp
  
  bg[NORMAL]		= "#414141" #"#393939" #color of separators in menu
  bg[SELECTED]	= "#9AD2F0"
}

```
Text after '#' is commented out, i.e. it is not considered as code. You can use it to make notes, like the author has done (e.g. # couleur des flêches = color of arrows).

To see what effect each item has you could use ***"#FF0000" #*** before the color code that is currently used. *"#FF0000"* is red, so you can easily see which elements are influenced by this item. The *#* comments out the previously used color.

Example:

if you change line 169 from

 ```
bg[NORMAL]		= "#353535"
```

to

 ```
bg[NORMAL]		= "#FF0000" #"#353535"
```

you'll see that the background of the drop down menu has changed to red.

You can see which color is represented by each color code with *Applications&#8594;Graphics&#8594;Gcolor2*. If it is not there, install it with synaptic.

You should now be able to control the colors of each element of the drop down menu. If there are still things that are not clear, please ask.

---

### Post by cjohn106 on 2009-01-10
Awesome, this worked. Thanks.

---

### Post by themagicmanfromtrent on 2009-01-25
@Ivo

What values determine the tranparancy of the menus? I'm making a style for mine, and I know Bg is the background color, but how do i give that a percentage which would determine the transparancy of it.

---

### Post by Ivo Moelans on 2009-01-25
Opacity is controlled by Compiz as far as I can make out. (Don't use it myself).
Try this:
Go to *System&#8594;Appearance&#8594;CompizConfig Settings Manager*, section *Accesibility*, plugin *Opacity, Brightness and Saturation*, tab *Opacity*.
In *Windows specific settings* you can determine the widgets and a value.
Try *DropDownMenu* and e.g. *50*.

---

### Post by themagicmanfromtrent on 2009-01-25
I don't have those options. I think I may have a different version of compiz to you. I have to go System>Preferences>Advanced Desktop Effects Settings>Accessibility>Opacify.

And even then, it doesn't give me a dropdownmenu option.

Could this be related to the fact that I'm running Gutsy?

---

### Post by Ivo Moelans on 2009-01-25
I'd really like to help you, but I'm afraid I'm out my dept here. But it is probably related to you running Gutsy. I remember vaguely reading somewhere that some things were changed in compiz. In fact compiz is fairly new and constantly changing. Maybe you should try their [_forum_]("http://forum.compiz-fusion.org/").

---

### Post by Ampersand. on 2009-02-21
ok i sorted those questions out myself. some more arise though:

i know     widget_class "*Menu*" style "menu_color"    is for the menus at the top of window (file, edit, view ...) but what command would i use to change the background color of the drop menu in the panel bar?

also: would i use gtkrc to make it so the menu font is different to the one used by the rest of the applications? 
eg. i want to use sans for regular apps (firefox, file browser etc) but something more fancy for the drop menu

thanks guys

---

### Post by pd0x on 2009-03-20
Hi everyone.

I am having trouble editing a theme I am using.  I want to change the color of the text in the drop down menus.  The default theme is a white background with black text, I wanted to reverse this.  So I swapped out the background picture with a dark background, but now the text is still dark and I can't see the options!!!  Anyway, here is the default code.

```
style "default"
{
  GtkWidget::interior_focus			= 7
  GtkWidget::focus_padding			= 0
  GtkButton::default_border			= { 0, 0, 0, 0 }
  GtkButton::default_outside_border		= { 0, 0, 0, 0 }
 
  GtkRange::trough_border			= 0
  GtkRange::slider_width			= 15
  GtkRange::stepper_size			= 15
 
  GtkVScale::slider_length 			= 11

  GtkVScale::slider_width 			= 21

  GtkHScale::slider_length 			= 11

  GtkHScale::slider_width 			= 21

  GtkPaned::handle_size				= 6
  GtkScrollbar::min_slider_length		= 50
  GtkCheckButton::indicator_size		= 12
  GtkCheckButton::indicator_spacing		= 3
  GtkMenuBar::internal_padding			= 1
  GtkOptionMenu::indicator_size			= { 15, 8 }
  GtkOptionMenu::indicator_spacing		= { 8, 2, 0, 0 }
  GtkStatusbar::shadow_type			= GTK_SHADOW_NONE
  GtkSpinButton::shadow_type 			= GTK_SHADOW_NONE

  xthickness            	= 2
  ythickness            	= 2

  fg[NORMAL]       	= "#222222" # Metacity and mouseover, Most text 222
  fg[ACTIVE]       	= "#222222"  #222
  fg[PRELIGHT]     	= "#e0e0e0"
  fg[SELECTED]     	= "#ffffff"
  fg[INSENSITIVE]  	= "#808080"

  bg[NORMAL]       	= "#ffffff" # Normal Background
  bg[ACTIVE]       	= "#ffffff" # Mouseclicking, Tabs, active window list
  bg[PRELIGHT]     	= "#ffffff" # Expand prelight bg
  bg[SELECTED]     	= "#222222"
  bg[INSENSITIVE]  	= "#ffffff"

  base[NORMAL]     	= "#ffffff" # Background, most
  base[ACTIVE]     	= "#222222" # Menu active item in inactive window
  base[PRELIGHT]   	= "#ffffff"
  base[INSENSITIVE]	= "#ffffff" # Inactive Entry bg
  base[SELECTED]   	= "#222222" # Menu active item in active window

  text[NORMAL]	  	= "#222222" # Text in window, arrows 222222
  text[INSENSITIVE]	= "#222222" # Insensitive arrows 
  text[SELECTED]   	= "#ffffff" # Active text in active window
  text[ACTIVE]     	= "#c0c0c0" # Active text in inactive window
  text[PRELIGHT]   	= "#ffffff" # Text on Mouseover

  engine "pixmap"
  {
    image
    {
      function				= HANDLE
      recolorable			= TRUE
      overlay_file			= "Panel/handle-v.png"
      overlay_stretch	= FALSE
      orientation			= HORIZONTAL
    }
    image
    {
      function				= HANDLE
      recolorable			= TRUE
      overlay_file			= "Panel/handle-h.png"
      overlay_stretch	= FALSE
      orientation			= VERTICAL
    }
    



####################### SHADOWS ############################x

    image
    {
      function			= SHADOW
      shadow			= IN
      recolorable		= FALSE
      file				= "Shadows/shadow-in.png"
      border			= { 3, 3, 2, 2 }
      stretch			= TRUE
    }
    image
    {
       function		= SHADOW
       shadow			= OUT
       recolorable		= TRUE
       file				= "Shadows/shadow-out.png"
       stretch			= TRUE
    }

    image
    {
       function		= SHADOW
       shadow			= ETCHED_IN
       recolorable		= TRUE
       file				= "Frame-Gap/frame1.png"				
       border			= { 2, 2, 2, 2 }
       stretch			= TRUE
    }
    image
    {
       function		= SHADOW
       shadow			= ETCHED_OUT
       recolorable		= TRUE
       file				= "Shadows/shadow-none.png"
       border			= { 2, 2, 2, 2 }
       stretch			= TRUE
    }
    image
    {
       function			= SHADOW_GAP
       recolorable			= TRUE
       file					= "Frame-Gap/frame1.png"
       border				= { 2, 2, 2, 2 }
       stretch				= TRUE
       gap_start_file		= "Frame-Gap/frame-gap-start.png"
       gap_start_border	= { 2, 0, 2, 0 }
       gap_end_file		= "Frame-Gap/frame-gap-end.png"
       gap_end_border	= { 0, 2, 2, 0 }
       gap_side			= TOP
    }

    image
    {
       function		= VLINE
       recolorable		= TRUE
       file				= "Lines/line-v.png"
       border			= { 1, 1, 0, 0 }
       stretch			= TRUE
    }
    image
    {
      function			= HLINE
      recolorable		= TRUE
      file				= "Lines/line-h.png"
      border			= { 0, 0, 1, 1 }
      stretch			= TRUE
    }

    # focus

    image
    {
      function			= FOCUS
      recolorable		= TRUE
      file				= "Others/focus.png"
      border			= { 6, 0, 6, 0 }
      stretch			= TRUE
    }	

    # arrows

    image
    {
      function				= ARROW
      recolorable			= TRUE
      overlay_file			= "Arrows/arrow-up.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= UP
    }
    image
    {
      function				= ARROW
      state				= NORMAL
      recolorable			= TRUE
      overlay_file			= "Arrows/arrow-down.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= DOWN
    }
    image
    {
      function				= ARROW
      state				= PRELIGHT
      recolorable			= TRUE
      overlay_file			= "Arrows/arrow-down-prelight.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= DOWN
    }
    image
    {
      function				= ARROW
      state				= ACTIVE
      recolorable			= TRUE
      overlay_file			= "Arrows/arrow-down-pressed.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= DOWN
    }

    image
    {
      function				= ARROW
      state				= INSENSITIVE
      recolorable			= TRUE
      overlay_file			= "Arrows/arrow-down-insens.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= DOWN
    }

    image
    {
      function				= ARROW
      recolorable			= TRUE
      overlay_file			= "Arrows/arrow-left.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= LEFT
    }
    image
    {
      function				= ARROW
      recolorable			= TRUE
      overlay_file			= "Arrows/arrow-right.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= RIGHT
    }
    image 
      {
     function			= BOX
	recolorable		= TRUE
	file        			= "Others/null.png"
	border      		= { 3, 3, 3, 3 }
	stretch         	= TRUE
      }
  }

}

```

and here is the menu code I tried changing
```

################### MENU #################################
  
style "menu"			= "default" 
{

 xthickness			= 3
 ythickness			= 1
 
  
  engine "pixmap"
  {
    image
    {
      function			= BOX
      recolorable    	= TRUE
      detail				= "menu"
      file				= "Menu-Menubar/menu.png"
      border			= { 34, 3, 3, 3 }
      stretch			= TRUE
    }
  }
}

########################### Menuitem #############################
style "menuitem"	= "default" 
{
  xthickness				= 1
  fg[PRELIGHT] 		= "#ffffff"
  
  
engine "pixmap"
  {
    image
    {
      function			= BOX
      recolorable		= TRUE
      file				= "Menu-Menubar/menuitem.png"
      border			= { 10, 10, 10, 10 }
      stretch			= TRUE
    }
    image
    {
      function				= ARROW
      recolorable			= TRUE
      state					= NORMAL
      overlay_file			= "Arrows/arrow-right-norm.png"
      overlay_stretch	= FALSE
      arrow_direction	= RIGHT
    }
  image
    {
      function				= ARROW
      recolorable			= TRUE
      state					= PRELIGHT
      overlay_file			= "Arrows/arrow-right-prelight.png"
      overlay_stretch	= FALSE
      arrow_direction	= RIGHT
    }
  }
}

```

I tried adding fg[NORMAL]=#FFFFFF to the menu and menuitem style and changing the 'default' value to 'mymenu', but get nothing. then i change the 'widget styles' code to match 'mymenu' and still nada.  but when I add fg[NORMAL]="#ffffff" it to the default style it will work!  but then all the other code using the default style will change, like toolbar buttons, etc. and will mess everything up.  I just want to change the menu text color to white, but not any other widgets using the default style.

here is the rest of the code

```
 # widget styles

class "GtkButton"          		style "button"
class "GtkRadioButton"     		style "radiobutton"
class "GtkRadioMenuItem"    		style "radiobutton"
class "GtkCheckButton"     		style "checkbutton"
class "GtkCheckMenuItem"   		style "checkbutton"
class "GtkOptionMenu"			style "optionmenu"
class "GtkCombo*"      			style "optionmenu"
class "*Font*"      			style "optionmenu"
class "GtkEntry"           		style "entry"
class "GtkOldEditable" 			style "entry"
class "GtkSpinButton"   	 	style "spinbutton"
class "GtkRuler"           		style "ruler"
class "GtkScrollbar"       		style "scrollbar"
class "GtkStatusbar"			style "statusbar"
class "GtkProgressBar"     		style "progressbar"
class "GtkRange"         		style "range"
class "GtkMenu"       			style "menu" 
class "GtkMenuBar*" 		     	style "menubar"
widget_class "*MenuBar.*" 		style "menubar"
widget_class "*.<MenuItem>."		style "menuitem"
class "GtkMenuItem"           		style "menuitem"
class "GtkTearoffMenuItem"		style "menuitem"
class "GtkNotebook"      		style "notebook"
class "GtkToolbar"       		style "flat"					
class "GtkHandleBox"    		style "handlebox"
class "GtkEventBox"    			style "flat"
class "GtkPaned"       			style "handlebox"
class "GtkLayout"     			style "layout"
class "SPButton"         			style "SPbutton"
widget "gtk-tooltips"  			style "tooltips"

# prevent Sodipodi from crashing
class "SPColorSlider" 			style "unstyle"
```


what am I missing here?  thanks for your help.

---

### Post by pd0x on 2009-03-21
Ampersand,

I am not entirely sure about this but i believe to target your dropdown menu from the panel would be class "GtkMenu".  "*Menu*" would target all things menu, your menubar (file, edit, etc.), your popup menus, and dropdown menus, etc.

Also for your font issue, I have tested with xchat and this works from this blog. I don't think it will work with firefox because isn't gtk. but if it did, in your master gtkrc-2.0 you can specify fancy font for menus, and use this way for your application....

[http://urukrama.wordpress.com/2008/07/13/setting-a-custom-gtk-theme-for-specific-applications/]("http://urukrama.wordpress.com/2008/07/13/setting-a-custom-gtk-theme-for-specific-applications/")

Hope this helps.

---


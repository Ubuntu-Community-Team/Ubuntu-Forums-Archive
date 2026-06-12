---
title: "Panel-Applet colour problems"
date: 2008-12-06
forum: General Help
---

### Post by Sugz on 2008-12-06
Ok, so i revecently found a new theme for ubuntu, i applied it and it tries to apply a panel background. however this must be bugged as all i see is this.

[[IMG]http://e.imagehost.org/t/0647/screenshot2.jpg[/IMG]](http://e.imagehost.org/view/0647/screenshot2)

But i want the panel to be black and opaque like the rest of it. 
if i apply another theme for example any of my Aurora Themes, it is fine, 

is there a way to disable this Background setting, i have tried to adjust it with Gnom-color-chooser, with no luck. 
also i have fiddled with the properties of the panel again nothing and i have also run the command 
killall gnome-panel. 

Any help on this issue will be apprediated. 

Here is the GTKRC file of the theme

```
#Carbonite

gtk-icon-sizes = "panel-menu=20,20:panel=22,22:gtk-button=16,16:gtk-large-toolbar=26,23"
gtk-menu-drop-shadow = 0
gtk-menu-shadow-delay = 0

include "icons/iconrc" 
include "menubar.rc"
#include "panel.rc"
include "spin/spinbuttons.rc"
include "combobox/combobox.rc"
include "shadows/text-entry.rc"
include "tabs/tabs.rc"

style "default"

{


  GtkScrollbar::has_secondary_backward_stepper 		= 0
  GtkScrollbar::has_secondary_forward_stepper 		= 0
  GtkWidget::interior_focus				= 7
  GtkWidget::focus_padding				= 0
  GtkButton::default_border				= { 0, 0, 0, 0 }
  GtkButton::default_outside_border			= { 0, 0, 0, 0 }

  GtkRange::trough_border				= 0
  GtkRange::slider_width				= 15
  GtkRange::stepper_size				= 15
  GtkPaned::handle_size					= 6
  GtkScrollbar::min_slider_length			= 30

  GtkCheckButton::indicator_size			= 17
  GtkCheckButton::indicator_spacing			= 3
  GtkMenuBar::internal_padding				= 0
  #GtkOptionMenu::indicator_size				= { 23, 8 }
  #GtkOptionMenu::indicator_spacing			= { 25, 0, 0, 0 }
  GtkEntry::padding 					= 0
  GtkStatusbar::shadow_type 				= GTK_SHADOW_NONE
  GtkVScale::slider_length 				= 15

  GtkVScale::slider_width 				= 16

  GtkHScale::slider_length 				= 15

  GtkHScale::slider_width 				= 16
  GtkTreeView::odd_row_color 				= "#e4ebf5"

    
  fg[NORMAL]       	= "#000000"
  fg[ACTIVE]       	= "#353535" 
  fg[PRELIGHT]     	= "#000000"
  fg[SELECTED]     	= "#000000"
  fg[INSENSITIVE]  	= "#9B9B9B"

  bg[NORMAL]       	= "#d3d3d3"
  bg[ACTIVE]        	= "#E0E0E0"
  bg[PRELIGHT]     	= "#f0f0f0"
  bg[SELECTED]     	= "#606060"
  bg[INSENSITIVE]  	= "#e0e0e0"

  base[NORMAL]     	= "#ffffff" 
  base[ACTIVE]     	= "#b5cadb" 
  base[PRELIGHT]   	= "#94afe5" 
  base[SELECTED]	= "#b5cadb" 
  base[INSENSITIVE]	= "#e0e0e0" 

  text[NORMAL]     	= "#000000"
  text[ACTIVE]		= "#000000"  
  text[PRELIGHT]   	= "#ffffff"
  text[SELECTED]   	= "#ffffff" 
  text[INSENSITIVE]	= "#9B9B9B"


  engine "pixmap"
  {
    image
    {
      function				= HANDLE
      recolorable			= TRUE
      overlay_file			= "Handles/handle-v.png"
      overlay_stretch	= FALSE
      orientation			= HORIZONTAL
    }
    image
    {
      function				= HANDLE
      recolorable			= TRUE
      overlay_file			= "Handles/handle-h.png"
      overlay_stretch	= FALSE
      orientation			= VERTICAL
    }

    image
    {
      function			= SHADOW
      shadow			= IN
      recolorable		= FALSE
      file				= "Shadows/shadow-in.png"
      border			= { 4, 4, 4, 4 }
      stretch			= TRUE
    }
    image
    {
       function			= SHADOW
       shadow			= OUT
       recolorable		= TRUE
       file				= "Shadows/shadow-out.png"
       #border			= { 1, 1, 1, 1 }
       stretch			= TRUE
    }



    image
    {
       function			= SHADOW
       shadow			= ETCHED_IN
       recolorable		= TRUE
       file				= "Frame-Gap/frame1.png"				
       border			= { 4, 4, 4, 4 }
       stretch			= TRUE
    }
    image
    {
       function			= SHADOW
       shadow			= ETCHED_OUT
       recolorable		= TRUE
       file				= "Shadows/shadow-none.png"
       border			= { 4, 4, 2, 4 }
       stretch			= TRUE
    }
    image
    {
       function			= SHADOW_GAP
       recolorable		= TRUE
       file				= "Frame-Gap/frame2.png"
       border			= { 4, 4, 2, 4 }
       stretch			= TRUE
       gap_start_file		= "Frame-Gap/frame-gap-start.png"
       gap_start_border	= { 2, 0, 0, 0 }
       gap_end_file		= "Frame-Gap/frame-gap-end.png"
       gap_end_border	= { 0, 2, 0, 0 }
       gap_side			= TOP
    }
    image
    {
       function			= VLINE
       recolorable		= TRUE
       file			= "Lines/line-v.png"
       border			= { 0, 0, 0, 0 }
       stretch			= TRUE
    }
    image
    {
      function			= HLINE
      recolorable		= TRUE
      file			= "Lines/line-h.png"
      border			= { 0, 0, 0, 0 }
      stretch			= TRUE
    }


    # focus

    image
    {
      function			= FOCUS
      recolorable		= TRUE
      file			= "Others/focus.png"
      border			= { 6, 0, 6, 0 }
      stretch			= TRUE
    }	

    # arrows

    image
    {
      function			= ARROW
      recolorable		= TRUE
      overlay_file		= "Arrows/arrow-up.png"
      overlay_border		= { 0, 0, 0, 0 }
      overlay_stretch		= FALSE
      arrow_direction		= UP
    }
    image
    {
      function			= ARROW
      recolorable		= TRUE
      overlay_file		= "Arrows/arrow-down.png"
      overlay_border		= { 0, 0, 0, 0 }
      overlay_stretch		= FALSE
      arrow_direction		= DOWN
    }
    image
    {
      function			= ARROW
      recolorable		= TRUE
      overlay_file		= "Arrows/arrow-left.png"
      overlay_border		= { 0, 0, 0, 0 }
      overlay_stretch		= FALSE
      arrow_direction		= LEFT
    }
    image
    {
      function			= ARROW
      recolorable		= TRUE
      overlay_file		= "Arrows/arrow-right.png"
      overlay_border		= { 0, 0, 0, 0 }
      overlay_stretch		= FALSE
      arrow_direction		= RIGHT
    }
    image 
      {
        function		= BOX
	recolorable		= TRUE
	file        		= "Toolbar/toolbar.png"
	border      		= { 3, 3, 3, 3 }
	stretch         	= TRUE
      }
  }
  
  

}

class "GtkWidget"          style "default"

###########################################
# Scrollbars 
###########################################
#



style "scrollbar" {

 GtkRange::trough_border = 0

  GtkVScale::slider_length = 16

  GtkVScale::slider_width = 19

  GtkHScale::slider_length = 17

  GtkHScale::slider_width = 19
  GtkRange::slider_width = 15
  GtkRange::stepper_size = 15
GtkScrollbar::min_slider_length = 30


    engine "pixmap" {

        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "Scroll2/vertical_trough.png"
            border          = { 0, 0, 22, 22 }
            stretch         = TRUE
            orientation     = VERTICAL
        }
        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "Scroll2/horizontal_trough.png"
            border          = { 22, 22, 0, 0 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
        image {
            function        = SLIDER
            recolorable     = TRUE
            state           = NORMAL
            file            = "Scroll2/scrollbar_horizontal.png"
            border          = { 11, 11, 6, 6 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
        image {
            function        = SLIDER 
            recolorable     = TRUE
            state           = PRELIGHT
            file            = "Scroll2/scrollbar_horizontal_prelight.png"
            border          = { 11, 11, 6, 6 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
	   image {
            function        = SLIDER 
            recolorable     = TRUE
            state           = INSENSITIVE
            file            = "Scroll2/scrollbar_horizontal_insens.png"
            border          = { 11, 11, 6, 6 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
      

  image {
            function        = SLIDER
            recolorable     = TRUE
            state           = NORMAL
            file            = "Scroll2/scrollbar_vertical.png"
            border          = { 6, 6, 11, 11 }
            stretch         = TRUE
            orientation     = VERTICAL
        }
        image {
            function        = SLIDER 
            recolorable     = TRUE
            state           = PRELIGHT
            file            = "Scroll2/scrollbar_vertical_prelight.png"
            border          = { 6, 6, 11, 11 }
            stretch         = TRUE
            orientation     = VERTICAL
        }
	image {
            function        = SLIDER 
            recolorable     = TRUE
            state           = INSENSITIVE
            file            = "Scroll2/scrollbar_vertical_insens.png"
            border          = { 6, 6, 11, 11 }
            stretch         = TRUE
            orientation     = VERTICAL
        }
  
# innen a nyilak
      image {
            function        = BOX
            recolorable     = TRUE
            state           = NORMAL 
            file            = "Scroll2/null.png"
            border          = { 0, 0, 0, 0 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = PRELIGHT
            file            = "Scroll2/null.png"
            border          = { 0, 0, 0, 0 }
            stretch         = TRUE
	    orientation     = HORIZONTAL
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = ACTIVE
            file            = "Scroll2/null.png"
            border          = { 0, 0, 0, 0 }
            stretch         = TRUE
        }
  image {
            function        = BOX
            recolorable     = TRUE
            state           = INSENSITIVE
            file            = "Scroll2/null.png"
            border          = { 0, 0, 0, 0 }
            stretch         = TRUE
        }

image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= NORMAL
	overlay_file	= "Scroll2/scroll_arrow_up.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= UP
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= NORMAL
	overlay_file	= "Scroll2/scroll_arrow_down.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= DOWN
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= NORMAL
	overlay_file	= "Scroll2/scroll_arrow_left.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= LEFT
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= NORMAL
	overlay_file	= "Scroll2/scroll_arrow_right.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= RIGHT
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= PRELIGHT
	overlay_file	= "Scroll2/scroll_arrow_up_prelight.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= UP
      }

    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= PRELIGHT
	overlay_file	= "Scroll2/scroll_arrow_down_prelight.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= DOWN
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= PRELIGHT
	overlay_file	= "Scroll2/scroll_arrow_left_prelight.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= LEFT
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= PRELIGHT
	overlay_file	= "Scroll2/scroll_arrow_right_prelight.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= RIGHT
      }

# itt az insensitive
 image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= INSENSITIVE
	overlay_file	= "Scroll2/scroll_arrow_up_prelight.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= UP
      }

    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		=INSENSITIVE
	overlay_file	= "Scroll2/scroll_arrow_down_prelight.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= DOWN
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= INSENSITIVE
	overlay_file	= "Scroll2/scroll_arrow_left_prelight.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= LEFT
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	state		= INSENSITIVE
	overlay_file	= "Scroll2/scroll_arrow_right_prelight.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= RIGHT
      }
# idáig insensitive

    image 
      {
	function	= ARROW
	recolorable	= TRUE
	shadow		= IN
	overlay_file	= "Scroll2/scroll_arrow_up_push.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= UP
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	shadow		= IN
	overlay_file	= "Scroll2/scroll_arrow_down_push.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= DOWN
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	shadow		= IN
	overlay_file	= "Scroll2/scroll_arrow_left_push.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= LEFT
      }
    image 
      {
	function	= ARROW
	recolorable	= TRUE
	shadow		= IN
	overlay_file	= "Scroll2/scroll_arrow_right_push.png"
	overlay_border	= { 0, 0, 0, 0 }
	overlay_stretch	= FALSE
	arrow_direction	= RIGHT
      }

}
}


#################### BUTTONS #######################

style "button"			= "default"
{
  xthickness            			= 4
  ythickness            			= 4
  engine "pixmap"
  {
    image
    {
      function			= BOX
      detail			= "buttondefault"
      recolorable		= TRUE
      file			= "Buttons/button-default.png"
      border			= {7, 7, 7, 7}
      stretch			= TRUE
    }
    image
    {
      function			= BOX
      state			= PRELIGHT
      recolorable		= TRUE
      file			= "Buttons/button-prelight.png"
      border			= { 7, 7, 7, 7 }
      stretch			= TRUE
    }
    image
    {
      function			= BOX
      state			= ACTIVE
      file			= "Buttons/button-pressed.png"
      border			= { 7, 7, 7, 7 }
      stretch			= TRUE
    }	
    image 
   {
     function			= BOX
     state			= INSENSITIVE
     file			= "Buttons/button-insensitive.png"
      border			= { 7, 7, 7, 7 }
     stretch			= TRUE
    }
    image 
    {
      function			= BOX
      file			= "Buttons/button-normal.png"		
      border			= { 7, 7, 7, 7 }
      stretch			= TRUE
    }	
  }
}


style "checkradiobutton" {
  engine "pixmap" {
    image 
	{
	function		= FLAT_BOX
	recolorable		= TRUE
	file			= "Check-Radio/highlight.png"
	border			= { 2, 5, 2, 5 }
	stretch			= TRUE
       }
    }
}

class "GtkRadioButton" style "checkradiobutton"
class "GtkCheckButton" style "checkradiobutton"

style "optionmenu"		= "default"
{	

  text[NORMAL] 			= "#000000"	
  text[PRELIGHT] 		= "#000000"

}

#widget_class "*Combo*" style "optionmenu"





#######################################################

style "radiobutton"	= "default"
{
  engine "pixmap" 
    {
	#This is the image used to draw an unchecked box.
        image 
	{
            function        		= OPTION
            recolorable    		= TRUE
            state 			= NORMAL
            shadow          		= OUT
            overlay_file    		= "Check-Radio/option1.png"
            overlay_stretch 		= FALSE
        }
 image 
	{
            function        		= OPTION
            recolorable     		= TRUE
            state 			= PRELIGHT
            shadow          		= OUT
            overlay_file    		= "Check-Radio/option1.png"
            overlay_stretch 		= FALSE
        }
 image 
	{
            function        		= OPTION
            recolorable     		= TRUE
            state 			= ACTIVE
            shadow          		= OUT
            overlay_file    		= "Check-Radio/option1.png"
            overlay_stretch 		= FALSE
        }
 image 
	{
            function        		= OPTION
            recolorable     		= TRUE
            state 			= INSENSITIVE
            shadow         		= OUT
            overlay_file    		= "Check-Radio/option1.png"
            overlay_stretch 		= FALSE
        }

	#This is the image used to draw a selected (checked) box.

        image 
	{
            function        		= OPTION
            recolorable     		= TRUE
	    	  state 		= NORMAL
            shadow          		= IN
            overlay_file    		= "Check-Radio/option2.png"
            overlay_stretch 		= FALSE
        }
  image 
	{
            function        		= OPTION
            recolorable     		= TRUE
	    	  state 		= PRELIGHT
            shadow          		= IN
            overlay_file    		= "Check-Radio/option4.png"
            overlay_stretch 		= FALSE
        }
 image 
	{
            function        		= OPTION
            recolorable     		= TRUE
	    	  state 		= ACTIVE
            shadow          		= IN
            overlay_file    		= "Check-Radio/option4.png"
            overlay_stretch 		= FALSE
        }
     image 
	{
            function        		= OPTION
            recolorable     		= TRUE
	   	  state 		= INSENSITIVE
            shadow          		= IN
            overlay_file    		= "Check-Radio/option3.png"
            overlay_stretch 		= FALSE
        }

	#Use this image to draw the highlight when a line with a check box
	#is moused over.

	image 
	{
          function        		= FLAT_BOX
          recolorable     		= TRUE
      	stretch				= TRUE
          file            		= "Check-Radio/checklight.png"
          border          		= { 2, 2, 2, 2 }
        }
    }
}

##########################################

####################################################
style "checkbutton"	= "default"
{
  engine "pixmap" 
    {
	#This is the image used to draw an unchecked box.
        image 
	{
            function        		= CHECK
            recolorable     		= TRUE
            state 			= NORMAL
            shadow          		= OUT
            overlay_file    		= "Check-Radio/check1.png"
            overlay_stretch 		= FALSE
        }
 image 
	{
            function        		= CHECK
            recolorable     		= TRUE
            state 			= PRELIGHT
            shadow          		= OUT
            overlay_file    		= "Check-Radio/check3.png"
            overlay_stretch 		= FALSE
        }
 image 
	{
            function        		= CHECK
            recolorable     		= TRUE
            state 			= ACTIVE
            shadow          		= OUT
            overlay_file    		= "Check-Radio/check1.png"
            overlay_stretch 		= FALSE
        }
 image 
	{
            function        		= CHECK
            recolorable     		= TRUE
            state 			= INSENSITIVE
            shadow          		= OUT
            overlay_file    		= "Check-Radio/check1.png"
            overlay_stretch 		= FALSE
        }

	#This is the image used to draw a selected (checked) box.

        image 
	{
            function        		= CHECK
            recolorable     		= TRUE
	    	  state 		= NORMAL
            shadow          		= IN
            overlay_file    		= "Check-Radio/check2.png"
            overlay_stretch 		= FALSE
        }
  image 
	{
            function        		= CHECK
            recolorable     		= TRUE
	    	  state 		= PRELIGHT
            shadow          		= IN
            overlay_file    		= "Check-Radio/check4.png"
            overlay_stretch 		= FALSE
        }
 image 
	{
            function        		= CHECK
            recolorable     		= TRUE
	    	  state 		= ACTIVE
            shadow          		= IN
            overlay_file    		= "Check-Radio/check4.png"
            overlay_stretch 		= FALSE
        }
     image 
	{
            function        		= CHECK
            recolorable     		= TRUE
	    	  state 		= INSENSITIVE
            shadow          		= IN
            overlay_file   		= "Check-Radio/check3.png"
            overlay_stretch 		= FALSE
        }

	#Use this image to draw the highlight when a line with a check box
	#is moused over.

	image 
	{
          function        		= FLAT_BOX
          recolorable     		= TRUE
     	stretch				= TRUE
          file            		= "Check-Radio/checklight.png"
          border          		= { 2, 2, 2, 2 }
        }
    }
}

####################### ENTRY #####################xx

style "entry"			= "default"
{

  xthickness            			= 3
  ythickness            			= 1
  
	GtkWidget::interior_focus	= 0
 #GtkEntry::shadow_type = GTK_SHADOW_NONE
  engine "pixmap"
  {
    image
    {
      function			= FOCUS
      recolorable		= TRUE
      file			= "Shadows/entry-shadow-in.png"
      border			= { 3,3,3,3 }
      stretch			= TRUE
    }	
 image
    {
      function			= BOX
      recolorable		= TRUE
      shadow			= IN
      state			= NORMAL
      file			= "Shadows/entry-shadow-in.png"
      border			= { 3,3,3,3 }
      stretch			= TRUE
    }	
image
    {
      function			= BOX
      recolorable		= TRUE
	 shadow			= OUT
      state			= NORMAL
      file			= "Shadows/text-entry.png"
      border			= { 3,3,3,3 }
      stretch			= TRUE
    }	
  image
   {
     function			= SHADOW
     detail			= "entry"
     shadow			= IN
     recolorable		= FALSE
     file			= "Shadows/text-entry.png"
     border			= { 3,3,3,3 }
     stretch			= TRUE
    }
  }
}





############################# RANGE #######################

style "range"			= "default"
{	
  engine "pixmap" 
  {
    image 
    {
      function			= BOX
      recolorable		= TRUE
      detail				= "trough"
      file				= "Range/trough-horizontal.png"
      border			= { 10, 10, 1, 16 }
      stretch			= TRUE
      orientation		= HORIZONTAL
    }	
    image 
    {
      function			= BOX
      recolorable		= TRUE
      detail				= "trough"
      file				= "Range/trough-vertical.png"
      border			= { 0, 19, 10, 10 }
      stretch			= TRUE
      orientation		= VERTICAL
    }

############### the sliders ###############

    image 
    {
      function				= SLIDER
      recolorable			= TRUE
      state           		= NORMAL
      file					= "Range/null.png"
      border				= { 0, 0, 0, 0 }
      stretch				= TRUE
      overlay_file			= "Range/slider-horiz.png"
      overlay_stretch	= FALSE
      orientation			= HORIZONTAL
    }
    image 
    {
      function				= SLIDER
      recolorable			= TRUE
     state           			= PRELIGHT
      file					= "Range/null.png"
      border				= { 0, 0, 0, 0 }
      stretch				= TRUE
      overlay_file			= "Range/slider-horiz-prelight.png"
      overlay_stretch	= FALSE
      orientation			= HORIZONTAL
    }
    image 
    {
      function				= SLIDER
      recolorable			= TRUE
      state           		= INSENSITIVE
      file					= "Range/null.png"
      border				= { 0, 0, 0, 0 }
      stretch				= TRUE
      overlay_file			= "Range/slider-horiz.png"
      overlay_stretch	= FALSE
      orientation			= HORIZONTAL
    }

######################### VERTICAL ###########################

    image 
    {
      function				= SLIDER
      recolorable			= TRUE
      state           		= NORMAL
      file					= "Range/null.png"
      border				= { 0, 0, 0, 0 }
      stretch				= TRUE
      overlay_file			= "Range/slider-vert.png"
      overlay_stretch	= FALSE
      orientation			= VERTICAL
    }
    image 
    {
      function				= SLIDER
      recolorable			= TRUE
     state           			= PRELIGHT
      file					= "Range/null.png"
      border				= { 0, 0, 0, 0 }
      stretch				= TRUE
      overlay_file			= "Range/slider-vert-prelight.png"
      overlay_stretch	= FALSE
      orientation			= VERTICAL
    }
    image 
    {
      function				= SLIDER
      recolorable			= TRUE
      state           		= INSENSITIVE
      file					= "Range/null.png"
      border				= { 0, 0, 0, 0 }
      stretch				= TRUE
      overlay_file			= "Range/slider-vert.png"
      overlay_stretch	= FALSE
      orientation			= VERTICAL
    }
  }
}

################### TOOLBAR ###########################

style "toolbar" 
{	

	engine "pixmap"
	{
		image
		{
			function	= BOX
			file		= "Toolbar/toolbar.png"
			border	= { 0, 0, 0, 0}
			stretch	= TRUE
    		}
 	}
}
widget_class "*BonoboDockItem" style "toolbar"
class "*BonoboDockItem" style "toolbar"

widget_class "*HandleBox" style "toolbar"
class "*HandleBox" style "toolbar"

widget_class "*Toolbar" style "toolbar"
class "*Toolbar" style "toolbar"

##################### TOOLBAR BUTTONS ###############################

style "toolbuttons" = "default"
{
  xthickness            			= 0
  ythickness            			= 0

	GtkWidget::focus_padding = 2

	engine "pixmap" {
      
image
		{
			function        		= BOX
			recolorable     		= TRUE
			state					= NORMAL
			file            			= "Toolbar/toolbutton-normal.png"
			border          		= { 5, 5, 5, 5 }
			stretch         		= TRUE
		}
image
		{
			function        		= BOX
			recolorable     		= TRUE
			state					= PRELIGHT
			file            			= "Toolbar/toolbutton-prelight.png"
			border          		= { 5, 5, 5, 5 }
			stretch         		= TRUE
		}
image
		{
			function        		= BOX
			recolorable     		= TRUE
			state					= ACTIVE
			file            			= "Toolbar/toolbutton-pressed.png"
			border          		= { 5, 5, 5, 5 }
			stretch         		= TRUE
		}  
image
		{
			function        		= BOX
			recolorable     		= TRUE
			state					= INSENSITIVE
			file            			= "Toolbar/toolbutton-normal.png"
			border          		= { 5, 5, 5, 5 }
			stretch         		= TRUE
		}  
	}
}
widget_class "*Tool*GtkToggleButton" style "toolbuttons"
widget_class "*Tool*GtkButton" style "toolbuttons"

################### PANEL GRAPHICS #################################

################### MENU #################################
style "menu"			= "default"
{
engine "pixmap"
  {
    image
    {
      function			= BOX
      recolorable    		= TRUE
      detail			= "menu"
      file			= "Menu-Menubar/menu.png"
      border			= { 0, 0, 0, 0 }
      stretch			= FALSE
    }
  }
}

style "theme-menubar-item" = "theme-menu-item"
{
  fg[NORMAL]   		= "#000000"
  fg[PRELIGHT] 		= "#FFFFFF"
  bg[PRELIGHT]          = "#1A1B1C"
  
  text[NORMAL] 		= "#000000"
  
  engine "pixmap"
  {
    image
    {
      function			= BOX
      recolorable		= TRUE
      file				= "Menu-Menubar/menubar-item5.png"
      border			= {8, 6, 0, 6 }
      state			= PRELIGHT
      stretch			= TRUE
    }
   } 

}


########################### Menuitem #############################
style "menuitem"	= "default"
{
  xthickness				= 1
  fg[NORMAL]           = "#000000"
  fg[PRELIGHT]         = "#ffffff" 
  fg[INSENSITIVE]      = "#aaaaaa"

  text[NORMAL]           = "#000000"
  text[PRELIGHT]           = "#ffffff" 

  bg[NORMAL]       	= "#1A1B1C"
  base[NORMAL]        = "#ffffff"

  engine "pixmap"
  {
    image
    {
      function			= BOX
      recolorable		= TRUE
      file				= "Menu-Menubar/menubar-item.png"
      border			= {5, 5, 5, 5 }
      stretch			= TRUE
    }
    
    image{
               function			= HLINE
               recolorable		= TRUE
               file				= "Menu-Menubar/menuline.png"
               border			= { 1, 1, 1, 1 }
               stretch			= TRUE
          }

    image
    {
      function				= ARROW
      recolorable			= TRUE
      state					= NORMAL
      overlay_file			= "Arrows/arrow-right.png"
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


style "tooltips"	= "default"
{
  bg[NORMAL]		= "#d7d7d7"
}

##################### RULER ##################

style "ruler"		= "default"
{
  engine "pixmap" {
    image 
      {
     function			= BOX
	recolorable		= TRUE
	detail				= "vruler"
	file					= "Others/ruler.png"
	border			= { 2, 2, 2, 2 }
	stretch			= TRUE
      }
    image 
      {
     function			= BOX
	recolorable		= TRUE
	detail				= "hruler"
	file					= "Others/ruler.png"
	border			= { 2, 2, 2, 2 }
	stretch			= TRUE
      }
  }
}

################# HANDLES ###################x


style "handlebox"	= "default"
{
  engine "pixmap"
  {
    image
    {
      #function			 = SHADOW
    }
    image
    {
      function				= HANDLE
      recolorable			= TRUE
      overlay_file			= "Handles/handle-v.png"
      overlay_stretch	= FALSE
      orientation			= VERTICAL
    }
    image
    {
      function				= HANDLE
      overlay_file			= "Handles/handle-h.png"
      overlay_stretch 	= FALSE
      orientation			= HORIZONTAL
    }
  }
}

style "flat" 		= "default"
{
  engine "pixmap"
  {
    image
    {
      function		= SHADOW
    }
  }
}

style "layout"	= "default"
{
  engine "pixmap"
  {
   image
   {
     function		= SHADOW
     detail			= "entry"
     shadow		= IN
     recolorable	= FALSE
     file			= "Shadows/text.png"
     border		= { 1, 1, 1, 1 }
     stretch		= TRUE
   }
    image
    {
      function		= BOX
      detail		= "button"
      state			= NORMAL
      file			= "Buttons/button-normal.png"
      recolorable	= TRUE
      border		= { 2, 3, 2, 3 }
      stretch		= TRUE
    }
  }
}

##################### LISTHEADERS ###################x

style "list-header"
{
   #Comment out the ythickness setting below for thicker column headers.
   #ythickness = 0
   GtkTreeView::odd_row_color 	= "#ffffff"
   GtkTreeView::even_row_color 	= "#ffffff"

#  fg[NORMAL] = "#ffffff"
#  text[NORMAL] = "#ffffff"

   engine "pixmap" 
	{

	#This image is used to draw the headers of columns in list views when they are
	#not selected.
    	image
      		{
        		function        	= BOX
			recolorable    	= TRUE
			state				= NORMAL
			file            		= "ListHeaders/list_header.png"
			border          	= { 2, 2, 2, 2 }
			stretch         	= TRUE
      		}

	#This image is used to draw the column headers in list views when they are
	#clicked.
    	image
      		{
        		function        	= BOX
			recolorable    	= TRUE
			state				= PRELIGHT
			file            		= "ListHeaders/list_header-prelight.png"
			border          	= { 2, 2, 2, 2 }
			stretch         	= TRUE
      		}

	#Does this do anything?

	image
      		{
        		function        	= BOX
			recolorable    	= TRUE
			state				= ACTIVE
			file					= "ListHeaders/list_header-pressed.png"
			border          	= { 2, 2, 2, 2}
			stretch         	= TRUE
      		}
	image
      		{
        		function        	= BOX
			recolorable    	= TRUE
			state				= SELECTED
			file					= "ListHeaders/list_header-prelight.png"
			border          	= { 2, 2, 2, 2 }
			stretch         	= TRUE
      		}
	image
      		{
        		function        	= BOX
			recolorable    	= TRUE
			state				= INSENSITIVE
			file					= "ListHeaders/list_header-insens.png"
			border          	= { 2, 2, 2, 2 }
			stretch         	= TRUE
      	}
  	}
}

widget_class "*List" style "list-header"
widget_class "*GtkTree*" style "list-header"
widget_class "*GtkCList*" style "list-header"
#widget_class "*Tree*" style "list-header"

# This prevents Sodipodi from crashing while opening the
# Object-Style dialog.

style "unstyle"
{
  engine ""
  {
  }
}

# recognizable pressed toggle buttons
# SPIcons seem to erase the background first. That's why I can't use
# the button style.

style "SPbutton"
{
  engine "pixmap"
  {
    image
    {
      function		= BOX
      shadow		= IN
      recolorable	= TRUE
      file			= "Shadows/shadow-out.png"
      border		= { 2, 2, 2, 2 }
      stretch		= TRUE
    }
    image
    {
      function		= BOX
    }
  }
}

style "treecol"
{
    bg[NORMAL] = "#000000"
}


##################### PROGRESSBAR ###################x

style "progressbar" {
  fg[PRELIGHT]       		= "#838383"
  text[PRELIGHT]       		= "#838383"
  xthickness            		= 1
  ythickness            		= 1
  engine "pixmap" 
  {
    image
    {
      function				= BOX
      detail					= "trough"
      file					= "ProgressBar/trough-progressbar-horiz.png"
      border				= { 2, 2, 2, 2 }
      stretch				= TRUE
      orientation		= HORIZONTAL
    }
    image
    {
      function				= BOX
      detail					= "bar"
      file					= "ProgressBar/progressbar-horiz.png"
      border				= { 2, 2, 2, 2 }
      stretch				= TRUE
      orientation		= HORIZONTAL
    } 
    image
    {
      function				= BOX
      detail					= "trough"
      file					= "ProgressBar/trough-progressbar-vertical.png"
      border				= { 2, 2, 2, 2 }
      stretch				= TRUE
      orientation		= VERTICAL
    }
    image
    {
      function				= BOX
      detail					= "bar"
      file					= "ProgressBar/progressbar-vertical.png"
      border				= { 2, 2, 2, 2 }
      stretch				= TRUE
      orientation		= VERTICAL
    } 
  }
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
  bg[SELECTED]  = "#4A4A4A"

  # Focused title text color
  fg[SELECTED]  = "#F9F9F9"
}

# widget styles
class "MetaFrames" 				style "metacity-frame"
class "GtkButton"          			style "button"
class "GtkRadioButton"     			style "radiobutton"
class "GtkRadioMenuItem"    			style "radiobutton"
class "GtkCheckButton"     			style "checkbutton"
class "GtkCheckMenuItem"   			style "checkbutton"

class "GtkRuler"           			style "ruler"


class "GtkRange"         			style "range"

class "GtkScrollbar"       			style "scrollbar"
class "GtkProgressBar"     			style "progressbar"

class "GtkMenu"       				style "menu"
class "GtkMenuItem"           			style "menuitem"
class "GtkMenuBar"				style "theme-menubar-item"
			

widget_class "*Menu.*"				style "menu"
widget_class "*MenuItem.*"       		style "menuitem"
widget_class "*MenuBar.*" 			style "theme-menubar-item"

class "GtkHandleBox"    			style "handlebox"
class "GtkEventBox"    				style "flat"
class "GtkPaned"       				style "handlebox"
class "GtkLayout"     				style "layout"
class "SPButton"         			style "SPbutton"


widget "gtk-tooltips"  				style "tooltips"

class "SPColorSlider" 				style "unstyle"
```

The colour of the applet backgrounds is d3d3d3, however, i have not been able to find any solution anywhere..

---

### Post by eternalnewbee on 2008-12-06
Really no idea. Just a question: Are you running compiz?

---

### Post by Sugz on 2008-12-06
yup thats correct, i am running compiz, though i'm not sure why this should make a difference.. 

-Sugz

---

### Post by Sugz on 2008-12-06
FIXED>> and consequently, my very first attempt at GTK styling :)

Basically what i did was compare the GTKRC file with another theme that worked. WHat ill do is post up the solution when i figure out myself what i did :)

---


---
title: "A Question regarding customising the look of GNOME..."
date: 2006-10-15
forum: Desktop Environments
---

### Post by jclmusic on 2006-10-15
how do i get rid of the border at 1, and change the text colour of the writing at 2, 3 and 4?

[img]http://img222.imageshack.us/img222/9429/screenshotly6.png[/img]

hopefully that makes sense, lol.

---

### Post by notarikon on 2006-10-16
1. Find the location of the theme you're using, e.g. /home/yourname/.themes/nameoftheme/

2. Open the gtk-2.0 folder and edit the gtkrc file you see in their with your text editor.

3. Add the following at the top above the first style declaration:

```
style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
```

4. Add the following at the end of the file:

```
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
```

5. Restart Gnome

---

### Post by jclmusic on 2006-10-16
thanks! that looks great! :) 

now how do i get rid of the border around "applications, places, system"?

---

### Post by notarikon on 2006-10-16
Hmm, not sure about the border - that doesn't appear by default as far as I'm aware, so it may be something in your theme file ... check any styles that are used for classes/widgets that have Panel in them. If in doubt, perhaps post your theme file in a code block?

[ edit ]

Try adding the following to the style you use for your GtkWidget class:

```
  GtkMenuBar::shadow-type = GTK_SHADOW_NONE
  GtkMenuBar::internal-padding = 0
  GtkToolbar::shadow_type = GTK_SHADOW_NONE
  GtkToolbar::internal-padding = 0
  GtkFrame::shadow_type = GTK_SHADOW_NONE
```
Only one of them should be required, can't remember which off the top of my head so might want to remove one at a time if it does to eliminate those you don't need.

---

### Post by jclmusic on 2006-10-17
i'm afraid neither of those worked. here's the code:

```
# E17-GTK by bvc

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}

style "default"
{
  GtkWidget::interior_focus				= 0
  GtkWidget::focus_padding				= 0
  GtkButton::default_border				= { 2, 2, 2, 2 }
  GtkButton::default_outside_border		= { 2, 2, 2, 2 }

  GtkRange::trough_border			= 0
  GtkRange::slider_width				= 18
  GtkRange::stepper_size				= 18
  GtkScrollbar::min_slider_length		= 42

  GtkPaned::handle_size				= 8

  GtkVScale::slider_length 				= 18

  GtkVScale::slider_width 				= 18

  GtkHScale::slider_length 				= 18

  GtkHScale::slider_width 				= 18

  GtkCheckButton::indicator_size			= 13
  GtkCheckButton::indicator_spacing		= 3
  GtkMenuBar::internal_padding			= 0
  GtkMenuBar::shadow-type = GTK_SHADOW_NONE
  GtkMenuBar::internal-padding = 0
  GtkToolbar::shadow_type = GTK_SHADOW_NONE
  GtkToolbar::internal-padding = 0
  GtkFrame::shadow_type = GTK_SHADOW_NONE
  GtkOptionMenu::indicator_size			= { 12, 8 }
  GtkOptionMenu::indicator_spacing		= { 6, 5, 0, 0 }

  GtkEntry::interior_focus				= 0
  GtkEntry::focus_padding				= 0
  GtkScrollbar::has_secondary_backward_stepper = 1
  GtkScrollbar::has_secondary_forward_stepper = 0

  GtkButton::child_displacement_x = 1
  GtkButton::child_displacement_y = 1
  
  #GtkToolbar::button-relief  = GTK_RELIEF_NORMAL
  GtkStatusbar::shadow_type = GTK_SHADOW_NONE
  GtkSpinButton::shadow_type = GTK_SHADOW_NONE

  fg[NORMAL]				= "#161616"
  fg[PRELIGHT]				= "#000000"
  fg[ACTIVE]					= "#000000"
  fg[SELECTED]				= "#000000"
  fg[INSENSITIVE]				= "#8A857C"
  
  bg[NORMAL]				= "#dfdfdf"
  bg[PRELIGHT]				= "#dfdfdf"
  bg[ACTIVE]					= "#D0D0D0"
  bg[SELECTED]				= "#D8BB75"
  bg[INSENSITIVE]				= "#EFEFEF"

  base[NORMAL]				= "#ffffff"
  base[PRELIGHT]				= "#EFEFEF"
  base[ACTIVE]				= "#D0D0D0"
  base[SELECTED]				= "#DAB566"
  base[INSENSITIVE]			= "#E8E8E8"	

  text[NORMAL]				= "#161616"
  text[PRELIGHT]				= "#000000"
  text[ACTIVE]				= "#000000"
  text[SELECTED]				= "#ffffff"
  text[INSENSITIVE]			= "#8A857C"

  engine "pixmap"
  {
    image
    {
      function          		= HANDLE
      file              		= "null.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      overlay_file      	= "handle-v.png"
      overlay_border      = { 0, 0, 0, 0 }
      overlay_stretch   	= FALSE
    }
    image
    {
      function          	= BOX
      detail            	= "toolbar"
      file              	= "null.png"
      border            	= { 0, 0, 0, 0 }
      stretch           	= TRUE
    }
    image
    {
      function          	= BOX
      shadow            	= IN
      file              	= "null.png"
      border           	= { 4, 4, 4, 4 }
      stretch           	= TRUE
    }
    image
    {
      function          	= BOX
      shadow            	= OUT
      file              	= "null.png"
      border            	= { 4, 4, 4, 4 }
      stretch           	= TRUE
    }
    image
    {
      function			= SHADOW
      shadow			= IN
      file				= "shadow-in.png"
      border			= { 4, 4, 4, 4 }
      stretch				= TRUE
    }
    image
   {
      function			= SHADOW
      shadow			= IN
     state				= INSENSITIVE
      file				= "entry-ins.png"
      border			= { 4, 4, 4, 4 }
      stretch				= TRUE
    }
    image
   {
      function			= SHADOW
      shadow			= OUT
     state				= INSENSITIVE
      file				= "entry-ins.png"
      border			= { 4, 4, 4, 4 }
      stretch				= TRUE
    }
    image
    {
      function			= SHADOW
      shadow			= OUT
      file				= "shadow-out.png"
      border			= { 4, 4, 4, 4 }
      stretch				= TRUE
    }
    image
    {
       function			= SHADOW
       shadow			= ETCHED_IN
       file				= "shadow-in.png"				
       border			= { 4, 4, 4, 4 }
       stretch			= TRUE
    }
    image
    {
       function			= SHADOW
       shadow			= ETCHED_OUT
       file				= "shadow-out.png"
       border			= { 4, 4, 4, 4 }
       stretch			= TRUE
    }
    image
    {
      function         		= SHADOW
      file             		= "shadow-in.png"
      border           		= { 4, 4, 4, 4 }
      stretch          		= TRUE
    }
    image
    {
       function			= VLINE
       file				= "line-v.png"
       border			= { 1, 1, 2, 2 }
       stretch			= TRUE
    }
    image
    {
      function			= HLINE
      file				= "null.png"
      border			= { 1, 1, 1, 1 }
      stretch				= TRUE
    }
    image
    {
      function			= FOCUS
      file				= "null.png"
      border			= { 6, 0, 6, 0 }
      stretch				= TRUE
    }	
    image
    {
      function			= ARROW
      state				= NORMAL
      file				= "null.png"
      overlay_file		= "arrow-up.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= UP
    }
    image
    {
      function		= ARROW
      state				= PRELIGHT
      file				= "null.png"
      overlay_file		= "arrow-up-pre.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= UP
    }
    image
    {
      function		= ARROW
      state				= INSENSITIVE
      overlay_file		= "arrow-up-ins.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= UP
    }
    image
    {
      function			= ARROW
      file				= "null.png"
      state				= NORMAL
      overlay_file		= "arrow-down.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= DOWN
    }
    image
    {
      function			= ARROW
      state				= PRELIGHT
      file				= "null.png"
      overlay_file		= "arrow-down-pre.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= DOWN
    }
    image
    {
      function			= ARROW
      state				= INSENSITIVE
      overlay_file		= "arrow-down-ins.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= DOWN
    }
    image
    {
      function			= ARROW
      file				= "null.png"
      state				= NORMAL
      overlay_file		= "arrow-left.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= LEFT
    }
    image
    {
      function		= ARROW
      state				= PRELIGHT
      file				= "null.png"
      overlay_file		= "arrow-left-pre.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= LEFT
    }
    image
    {
      function			= ARROW
     state				= INSENSITIVE
      overlay_file		= "arrow-left-ins.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= LEFT
    }
    image
    {
      function			= ARROW
      file				= "null.png"
      state				= NORMAL
      overlay_file		= "arrow-right.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= RIGHT
    }
    image
    {
      function		= ARROW
      state				= PRELIGHT
      file				= "null.png"
      overlay_file		= "arrow-right-pre.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= RIGHT
    }
    image
    {
      function			= ARROW
     state				= INSENSITIVE
      overlay_file		= "arrow-right-ins.png"
      overlay_border	= { 0, 0, 0, 0 }
      overlay_stretch	= FALSE
      arrow_direction	= RIGHT
    }
  }
}
class "GtkWidget"          style "default"

style "button"			= "default"
{
  xthickness			= 2
  ythickness			= 2
  engine "pixmap"
  {
    image
    {
      function			= FOCUS
      file              		= "focus_button.png"
      border            		= { 6, 6, 6, 6 }
      stretch           		= TRUE
    }
    image
    {
      function			= BOX
      detail			= "buttondefault"
      file				= "button-default.png"
      border			= { 6, 6, 6, 6 }
      stretch			= TRUE
    }
    image 
    {
      function			= BOX
      state				= NORMAL
      file				= "button-normal.png"
      border			= { 6, 7, 6, 7 }
      stretch			= TRUE
    }	
    image
    {
      function			= BOX
      state				= PRELIGHT
      file				= "button-prelight.png"
      border			= { 6, 7, 6, 7 }
      stretch			= TRUE
    }
    image
    {
      function			= BOX
      state				= ACTIVE
      file				= "button-pressed.png"
      border			= { 8, 8, 7, 7 }
      stretch			= TRUE
    }	
    image 
   {
     function			= BOX
     state				= INSENSITIVE
     file				= "button-insensitive.png"
     border			= { 6, 7, 6, 7 }
     stretch			= TRUE
    }
  }
}

style "optionmenu"		= "default"
{
  xthickness			= 2
  ythickness			= 2
  engine "pixmap"
  {
    image
    {
      function			= BOX
      state				= NORMAL
      file				= "button-normal.png"
      border			= { 6, 7, 6, 7 }
      stretch			= TRUE
    }
    image
    {
      function			= BOX
      state				= PRELIGHT
      file				= "button-prelight.png"
      border			= { 6, 7, 6, 7 }
      stretch			= TRUE
    }
    image
    {
      function			= BOX
      state				= INSENSITIVE
     file				= "button-insensitive.png"
      border			= { 6, 7, 6, 7 }
      stretch			= TRUE
    }
    image
    {
      function				= TAB
      state					= INSENSITIVE
      overlay_file			= "arrow-down-ins.png"
      overlay_stretch		= FALSE
    }
    image
    {
      function				= TAB
      state					= NORMAL
      overlay_file			= "arrow-down.png"
      overlay_stretch		= FALSE
    }
    image
    {
      function				= TAB
      state					= PRELIGHT
      overlay_file			= "arrow-down-pre.png"
      overlay_stretch		= FALSE
    }
  }
}

style "combobox"		= "default"
{
  xthickness			= 1
  ythickness			= 1
engine "pixmap" { 
 image
    {
      function			= BOX
      recolorable		= TRUE
      state				= NORMAL
      file				= "button-normal.png"
      border			= { 6, 7, 6, 7 }
      stretch			= TRUE
    }   
image
    {
      function			= BOX
      recolorable		= TRUE
      state				= PRELIGHT
      file				= "button-prelight.png"
      border			= { 6, 7, 6, 7 }
      stretch			= TRUE
    }
image
    {
      function			= BOX
      recolorable		= TRUE
      state				= ACTIVE
      file				= "button-pressed.png"
      border			= { 8, 8, 7, 7 }
      stretch			= TRUE
    }
image
    {
      function			= BOX
      recolorable		= TRUE
      state				= INSENSITIVE
      file				= "button-insensitive.png"
      border			= { 6, 7, 6, 7 }
      stretch			= TRUE
    }
image
    {
      function			= ARROW
      recolorable		= TRUE
      state				= NORMAL
      file				= "combo-arrow.png"
      border			= { 0, 0, 0, 0}
      stretch			= TRUE
    }
image
    {
      function			= ARROW
      recolorable		= TRUE
      state				= PRELIGHT
      file				= "combo-arrow.png"
      border			= { 0, 0, 0, 0}
      stretch			= TRUE
    }
image
    {
      function			= ARROW
      recolorable		= TRUE
      state				= ACTIVE
      file				= "combo-arrow.png"
      border			= { 0, 0, 0, 0}
      stretch			= TRUE
    }
image
    {
      function			= ARROW
      recolorable		= TRUE
      state				= INSENSITIVE
      file				= "combo-arrow-ins.png"
      border			= { 0, 0, 0, 0}
      stretch			= TRUE
    }
    	image
    	{
      	function			= FOCUS
      	recolorable		= TRUE
      	file				= "focus_entry.png"
      	border			= { 6, 6, 4, 4 }
      	stretch			= TRUE
        }
	image
	{
	function			= SHADOW
	recolorable 		= TRUE
	state			= SELECTED
	file				= "entry-out.png"
	border			= { 4, 8, 4, 8}
	stretch			= TRUE
	}
	image
	{
	function			= FOCUS
	recolorable 		= TRUE
	state			= INSENSITIVE
	file				= "entry-ins.png"
	border			= { 8, 4, 8, 4}
	stretch			= TRUE
	}
	image 
	{
	function			= SHADOW
	shadow			= IN
	state			= NORMAL
	file				= "entry-in.png"
	border			= { 8, 4, 8, 4}
	stretch			= TRUE
    }
  }
}
class "GTKCombo" style "combobox"
widget_class "*Combo.*" style "combobox"

style "radiobutton"		= "default"
{
  engine "pixmap"
   {
    	image
    	{
      	function				= FOCUS
      	file					= "focus_option.png"
      	border				= { 4, 4, 4, 4 }
      	stretch				= TRUE
    	}

	
	image {
	function          		= OPTION
	recolorable       		= TRUE
	state             			= NORMAL
	shadow            		= IN
      	file              			= "null.png"
	overlay_file      		= "option-in.png"
	overlay_stretch   	= FALSE
	}
	image {
	function          		= OPTION
	recolorable       		= TRUE
	state             			= PRELIGHT
	shadow            		= IN
      	file              			= "null.png"
	overlay_file      		= "option-pin.png"
	overlay_stretch   	= FALSE
	}
	image {
	function          		= OPTION
	recolorable       		= TRUE
	state             			= ACTIVE
	shadow            		= IN
      	file              			= "null.png"
	overlay_file      		= "option-a.png"
	overlay_stretch   	= FALSE
	}
	image {
	function          		= OPTION
	recolorable       		= TRUE
	state             			= INSENSITIVE
	shadow            		= IN
      	file              			= "null.png"
	overlay_file      		= "option-in-ins.png"
	overlay_stretch   	= FALSE
	}


	image {
	function          		= OPTION
	recolorable       		= TRUE
	state             			= NORMAL
	shadow            		= OUT
      	file              			= "null.png"
	overlay_file      		= "option-out.png"
	overlay_stretch   	= FALSE
	}
	image {
	function          		= OPTION
	recolorable       		= TRUE
	state             			= PRELIGHT
	shadow            		= OUT
      	file              			= "null.png"
	overlay_file      		= "option-pout.png"
	overlay_stretch   	= FALSE
	}
	image {
	function          		= OPTION
	recolorable       		= TRUE
	state             			= ACTIVE
	shadow            		= OUT
      	file              			= "null.png"
	overlay_file      		= "option-aout.png"
	overlay_stretch   	= FALSE
	}
	image {
	function          		= OPTION
	recolorable       		= TRUE
	state             			= INSENSITIVE
	shadow            		= OUT
      	file              			= "null.png"
	overlay_file      		= "option-out-ins.png"
	overlay_stretch   	= FALSE
	}
    }
}
class "GtkRadioButton"     		style "radiobutton"
class "GtkRadioMenuItem"    	style "radiobutton"

style "checkbutton"		= "default"
{
  engine "pixmap"
  {
     image
    	{
      	function			= FOCUS
      	file				= "focus_option.png"
      	border			= { 4, 4, 4, 4 }
      	stretch			= TRUE
    	}


    	image {
	function				= FLAT_BOX
	file					= "null.png"
	border				= { 3, 3, 3, 3 }
	stretch				= TRUE
       	}
	image {
	function          		= CHECK
	recolorable       		= TRUE
	state             			= NORMAL
	shadow            		= IN
      	file              			= "null.png"
	overlay_file      		= "check.png"
	overlay_stretch   		= FALSE
	}
	image {
	function          		= CHECK
	recolorable       		= TRUE
	state             			= PRELIGHT
	shadow            		= IN
      	file              			= "null.png"
	overlay_file      		= "check-p.png"
	overlay_stretch   		= FALSE
	}
	image {
	function          		= CHECK
	recolorable       		= TRUE
	state             			= ACTIVE
	shadow            		= IN
      	file              			= "null.png"
	overlay_file      		= "check-a.png"
	overlay_stretch   		= FALSE
	}
	image {
	function          		= CHECK
	state             			= INSENSITIVE
	shadow            		= IN
	overlay_file      		= "check-ins.png"
	overlay_stretch   		= FALSE
	}


	image {
	function          		= CHECK
	state             			= NORMAL
	recolorable       		= TRUE
	shadow            		= OUT
      	file              			= "null.png"
	overlay_file      		= "check-out.png"
	overlay_stretch   		= FALSE
	}
	image {
	function          		= CHECK
	state             			= PRELIGHT
	shadow            		= OUT
      	file              			= "null.png"
	overlay_file      		= "check-pout.png"
	overlay_stretch   		= FALSE
	}
	image {
	function          		= CHECK
	state             			= ACTIVE
	shadow            		= OUT
      	file              			= "null.png"
	overlay_file      		= "check-aout.png"
	overlay_stretch   		= FALSE
	} 
	image {
	function          		= CHECK
	state             			= INSENSITIVE
	shadow            		= OUT
      	file              			= "null.png"
	overlay_file      		= "check-out-ins.png"
	overlay_stretch   		= FALSE
	}
    }
}
class "GtkCheckButton"     		style "checkbutton"
class "GtkCheckMenuItem"   	style "checkbutton"
class "GtkRadioButton" 		style "checkbutton"

style "entry"			= "default"
{
  xthickness			= 1
  ythickness			= 1
  engine "pixmap"
  {
    	image
    	{
      	function			= FOCUS
      	recolorable		= TRUE
      	file				= "focus_entry.png"
      	border			= { 6, 6, 4, 4 }
      	stretch			= TRUE
        }
	image
	{
	function			= SHADOW
	recolorable 		= TRUE
	state			= SELECTED
	file				= "entry-out.png"
	border			= { 4, 8, 4, 8}
	stretch			= TRUE
	}
	image
	{
	function			= FOCUS
	recolorable 		= TRUE
	state			= INSENSITIVE
	file				= "entry-ins.png"
	border			= { 8, 4, 8, 4}
	stretch			= TRUE
	}
	image 
	{
	function			= SHADOW
	shadow			= IN
	state			= NORMAL
	file				= "entry-in.png"
	border			= { 8, 4, 8, 4}
	stretch			= TRUE
    }
  }
}

style "scrollbar"
{
#GtkRange::trough_border	= 2
  engine "pixmap" 
  {
    image 
    {
      function				= BOX
      detail				= "trough"
      file					= "trough2.png"
      border				= { 2, 2, 18, 18 }
      stretch				= TRUE
      orientation			= VERTICAL
    }
    image 
    {
      function				= BOX
      detail				= "trough"
      file					= "trough2-h.png"
      border				= { 18, 18, 2, 2 }
      stretch				= TRUE
      orientation			= HORIZONTAL
    }
    image 
    {
      function			= SLIDER
      state           		= NORMAL
      file				= "slider-h.png" 
      border			= { 10, 10, 6, 6 }
      stretch				= TRUE
      orientation			= HORIZONTAL
      overlay_file			= "handle-h-scr.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function			= SLIDER
      state           		= PRELIGHT
      file				= "slider-prelight-h.png" 
      border			= { 10, 10, 6, 6 }
      stretch				= TRUE
      orientation			= HORIZONTAL
      overlay_file			= "handle-h-scr-p.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function			= SLIDER
      state           		= INSENSITIVE
      file				= "slider-h-ins.png"
      border			= { 10, 10, 6, 6 }
      stretch				= TRUE
      orientation			= HORIZONTAL
    }
    image 
    {
      function			= SLIDER
      state           		= NORMAL
      file				= "slider.png" 
      border			= { 6, 6, 10, 10 }
      stretch				= TRUE
      orientation			= VERTICAL
      overlay_file			= "handle-v-scr.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function			= SLIDER
      state           		= PRELIGHT
      file				= "slider-prelight.png" 
      border			= { 6, 6, 10, 10 }
      stretch				= TRUE
      orientation			= VERTICAL
      overlay_file			= "handle-v-scr-p.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function			= SLIDER
      state           		= INSENSITIVE
      file				= "slider-ins.png"
      border			= { 6, 6, 10, 10 }
      stretch				= TRUE
      orientation			= VERTICAL
    }
    image 
    {
      function				= STEPPER
      state					= NORMAL
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= UP
      overlay_file			= "stepper-arrow-n.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= PRELIGHT
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= UP
      overlay_file			= "stepper-arrow--n-pre.png"
      overlay_stretch		= FALSE
    }
    image
    {
      function				= STEPPER
      state					= ACTIVE
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= UP
      overlay_file			= "stepper-arrow-n-a.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= INSENSITIVE
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= UP
      overlay_file			= "null.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= NORMAL
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= DOWN
      overlay_file			= "stepper-arrow-s.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= PRELIGHT
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= DOWN
      overlay_file			= "stepper-arrow-s-pre.png"
      overlay_stretch		= FALSE
    }
    image
    {
      function				= STEPPER
      state					= ACTIVE
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= DOWN
      overlay_file			= "stepper-arrow-s-a.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= INSENSITIVE
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= DOWN
      overlay_file			= "null.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= NORMAL
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= RIGHT
      overlay_file			= "stepper-arrow-e.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= PRELIGHT
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= RIGHT
      overlay_file			= "stepper-arrow-e-pre.png"
      overlay_stretch		= FALSE
    }
    image
    {
      function				= STEPPER
      state					= ACTIVE
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= RIGHT
      overlay_file			= "stepper-arrow-e-a.png"
      overlay_stretch		= FALSE
    }
    image
    {
      function				= STEPPER
      state					= INSENSITIVE
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= RIGHT
      overlay_file			= "null.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= NORMAL
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= LEFT
      overlay_file			= "stepper-arrow-w.png"
      overlay_stretch		= FALSE
    }
   image 
    {
      function				= STEPPER
      state					= PRELIGHT
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= LEFT
      overlay_file			= "stepper-arrow-w-pre.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= ACTIVE
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= LEFT
      overlay_file			= "stepper-arrow-w-a.png"
      overlay_stretch		= FALSE
    }
    image 
    {
      function				= STEPPER
      state					= INSENSITIVE
      file					= "stepper.png"
      border				= { 4, 4, 4, 4 }
      stretch				= TRUE
      arrow_direction		= LEFT
      overlay_file			= "null.png"
      overlay_stretch		= FALSE
    }
  }
}

style "range"			= "default"
{
  engine "pixmap" 
  {
    image
    {
      function			= FOCUS
      file				= "null.png"
      border			= { 2, 2, 2, 2 }
      stretch				= TRUE
    }	
    image 
    {
      function			= BOX
      detail			= "trough"
      file				= "trough-range-h.png"
      border			= { 4, 4, 2, 2 }
      stretch			= TRUE
      orientation		= HORIZONTAL
    }	
    image 
    {
      function			= BOX
      detail			= "trough"
      file				= "trough-range.png"
      border			= { 2, 2, 4, 4 }
      stretch			= TRUE
      orientation		= VERTICAL
    }
    image 
    {
      function		= SLIDER
      state           	= NORMAL
      file			= "slider-range-h.png"
      border		= { 6, 6, 2, 2 }
      stretch		= TRUE
      orientation	= HORIZONTAL
    }
    image 
    {
      function		= SLIDER
     state           	= PRELIGHT
      file			= "slider-range-pre-h.png"
      border		= { 6, 6, 2, 2 }
      stretch		= TRUE
      orientation	= HORIZONTAL
    }
    image 
    {
      function		= SLIDER
      state           	= ACTIVE
      file			= "slider-range-h-a.png"
      border		= { 6, 6, 2, 2 }
      stretch		= TRUE
      orientation	= HORIZONTAL
    }
    image 
    {
      function		= SLIDER
      state           	= INSENSITIVE
      file			= "slider-range-h-ins.png"
      border		= { 6, 6, 2, 2 }
      stretch		= TRUE
      orientation	= HORIZONTAL
    }
    image 
    {
      function		= SLIDER
      state           	= NORMAL
      file			= "slider-range.png"
      border		= { 2, 2, 8, 4 }
      stretch		= TRUE
      orientation	= VERTICAL
    }
    image 
    {
      function		= SLIDER
     state           	= PRELIGHT
      file			= "slider-range-pre.png"
      border		= { 2, 2, 8, 4 }
      stretch		= TRUE
      orientation	= VERTICAL
    }
    image 
    {
      function		= SLIDER
      state           	= ACTIVE
      file			= "slider-range-a.png"
      border		= { 2, 2, 8, 4 }
      stretch		= TRUE
      orientation	= VERTICAL
    }
    image 
    {
      function		= SLIDER
      state           	= INSENSITIVE
      file			= "slider-ins.png"
      border		= { 2, 2, 8, 4 }
      stretch		= TRUE
      orientation	= VERTICAL
    }
  }
}

style "spin"
{
  xthickness			= 2
  ythickness			= 2
#bg_pixmap[NORMAL]	= "null.png"
  engine "pixmap" 
   {
    image
    {
      function			= ARROW
      file              		= "null.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
    }
    image
    {
      function			= BOX
      detail			= "spinbutton_up"
      state				= NORMAL
      file				= "null.png"
      border			= { 1, 1, 1, 1 }
      stretch			= TRUE
      overlay_file		= "spin-up.png"
      overlay_stretch	= TRUE
    }
  image
    {
      function			= BOX
      detail			= "spinbutton_up"
      state				= PRELIGHT
      file				= "null.png"
      border			= { 1, 1, 1, 1 }
      stretch			= TRUE
      overlay_file		= "spin-up.png"
      overlay_stretch	= TRUE
    }
  image
    {
      function			= BOX
      detail			= "spinbutton_up"
      state				= ACTIVE
      file				= "null.png"
      border			= { 1, 1, 1, 1 }
      stretch			= TRUE
      overlay_file		= "spin-up-a.png"
      overlay_stretch	= TRUE
    }
  image
    {
      function			= BOX
      detail			= "spinbutton_up"
      state				= INSENSITIVE
      file				= "null.png"
      border			= { 1, 1, 1, 1 }
      stretch			= TRUE
      overlay_file		= "spin-up-i.png"
      overlay_stretch	= TRUE
    }
    image
    {
      function			= BOX
      detail			= "spinbutton_down"
      state				= NORMAL
      file				= "null.png"
      border			={ 1, 1, 1, 1 }
      stretch			= TRUE
      overlay_file		= "spin-down.png"
      overlay_stretch	= TRUE
    }
  image
    {
      function			= BOX
      detail			= "spinbutton_down"
      state				= PRELIGHT
      file				= "null.png"
      border			= { 1, 1, 1, 1 }
      stretch			= TRUE
      overlay_file		= "spin-down.png"
      overlay_stretch	= TRUE
    }
  image
    {
      function			= BOX
      detail			= "spinbutton_down"
      state				= ACTIVE
      file				= "null.png"
      border			= { 1, 1, 1, 1 }
      stretch			= TRUE
      overlay_file		= "spin-down-a.png"
      overlay_stretch	= TRUE
    }
  image
    {
      function			= BOX
      detail			= "spinbutton_down"
      state				= INSENSITIVE
      file				= "null.png"
      border			= { 1, 1, 1, 1 }
      stretch			= TRUE
      overlay_file		= "spin-down-i.png"
      overlay_stretch	= TRUE
    }
  }
}
class "GtkSpinButton"   	 style "spin"

style "progressbar"		= "default"
{
GtkRange::trough_border				= 0
  fg[NORMAL]				= "#333333"
  fg[PRELIGHT]				= "#000000"
  engine "pixmap" 
  {
    image
    {
      function			= BOX
      detail			= "trough"
      file				= "trough2.png"
      border			= { 4, 4, 3, 3 }
      stretch			= TRUE
      orientation		= HORIZONTAL
    }
    image
    {
      function			= BOX
      detail			= "bar"
      file				= "progressbar.png"
      border			= { 4, 4, 5, 2 }
      stretch			= TRUE
      orientation		= HORIZONTAL
    }
      image
    {
      function			= BOX
      detail			= "trough"
      file				= "trough2.png"
      border			= { 4, 4, 3, 3 }
      stretch			= TRUE
      orientation		= VERTICAL
    }
    image
    {
      function			= BOX
      detail			= "bar"
      file				= "progressbar.png"
      border			= { 4, 4, 5, 2 }
      stretch			= TRUE
      orientation		= VERTICAL
    } 
  }
}

style "menu"			= "default"
{
#bg_pixmap[NORMAL]	= "menubg.svg"
  xthickness			= 2
  ythickness			= 1
  engine "pixmap"
  {
    image
    {
      function			= BOX
      detail			= "menu"
      file				= "menu.png"
      border			= { 7, 7, 7, 7 }
      stretch			= TRUE
    }
  }
}

style "menuitem"		= "default"
{
  xthickness			= 2
  ythickness			= 4
  engine "pixmap"
  {
    image
    {
      function			= BOX
      file				= "menuitem.png"
      border			= { 6, 6, 6, 6 }
      stretch			= TRUE
    }
    image
    {
      function			= HLINE
      file				= "line-h.png"
      border			= { 4, 4, 1, 1 }
      stretch			= TRUE
    }
    image
    {
      function			= ARROW
      state				= NORMAL
      overlay_file		= "menu-arrow-right.png"
      overlay_stretch	= FALSE
      arrow_direction	= RIGHT
    }
    image
    {
      function			= ARROW
      state				= PRELIGHT
      overlay_file		= "menu-arrow-right-pre.png"
      overlay_stretch	= FALSE
      arrow_direction	= RIGHT
    }
  }
}

style "menubar" {
  ythickness = 1
  engine "pixmap" {
	image {
	function          	= BOX
	shadow            	= OUT
	file              		= "menubar.png"
	border            	= { 3, 3, 3, 3 }
	stretch           	= TRUE
	}
  }
}
class "GtkMenuBar" style "menubar"

style "toolbar" {
  ythickness = 1
  engine "pixmap" {
	image {
	function          	= BOX
	file              		= "menubar.png"
	border            	= { 8, 8, 2, 2 }
	stretch           	= TRUE
	orientation       	= HORIZONTAL
    }
  }
}
class "*Tool*" style "toolbar"
#widget_class "*ToolButton.*" style "toolbar"

style "tearoffmenuitem"	= "menuitem"
{
  engine "pixmap"
  {
    image
    {
      function			= ARROW
      state				= NORMAL
      file				= "menu-arrow-left.png"
      stretch			= TRUE
      arrow_direction	= LEFT
    }
    image
    {
      function			= ARROW
      state				= PRELIGHT
      file				= "menu-arrow-left-pre.png"
      stretch			= TRUE
      arrow_direction	= LEFT
    }
  }
}

style "notebook"		= "default"
{
  #fg[ACTIVE]					= "#ffffff"
  engine "pixmap"
    {
    image 
      {
        function			= EXTENSION
	state			= NORMAL
	file				= "extension-top.png"
	border			= { 8, 16, 10, 2 }
	stretch			= TRUE
	gap_side		= BOTTOM
      }
    image 
      {
        function			= EXTENSION
	state			= ACTIVE
	file				= "ext-top.png"
	border			= { 6, 6, 6, 2 }
	stretch			= TRUE
	gap_side		= BOTTOM
      }

    image 
      {
        function			= BOX_GAP
	file				= "notebook.png" 
	border			= { 10, 8, 12, 12 }
	stretch			= TRUE
	gap_file			= "null.png"
	gap_border     	= { 0, 0, 0, 0 }
	gap_start_file	= "null.png"
	gap_end_file		= "null.png"
	gap_side		= TOP
      }
    image 
      {
        function			= BOX_GAP
	file				= "notebook.png"
	border			= { 10, 8, 12, 12 }
	stretch			= TRUE
	gap_file			= "null.png"
	gap_border     	= { 0, 0, 0, 0 }
	gap_start_file	= "null.png"
	gap_end_file		= "null.png"
	gap_side		= BOTTOM
      }
    image 
      {
        function			= BOX_GAP
	file				= "notebook.png"
	border			= { 10, 8, 12, 12 }
	stretch			= TRUE
	gap_file			= "null.png"
	gap_border     	= { 0, 0, 0, 0 }
	gap_start_file	= "null.png"
	gap_end_file		= "null.png"
	gap_side		= LEFT
      }
    image 
      {
        function			= BOX_GAP
	file				= "notebook.png"
	border			= { 10, 8, 12, 12 }
	stretch			= TRUE
	gap_file			= "null.png"
	gap_border     	= { 0, 0, 0, 0 }
	gap_start_file	= "null.png"
	gap_end_file		= "null.png"
	gap_side		= RIGHT
      }
#
# How to draw the box of a notebook when it isnt attached to a tab
#
    image 
      {
        function			= BOX
	file				= "notebook.png"
	border			= { 10, 8, 12, 12 }
	stretch			= TRUE
	gap_side			= TOP
      }
  }
}

#style "notebook-label"
#{
#  fg[NORMAL]				= "#161616"
#  fg[PRELIGHT]				= "#000000"
#  fg[ACTIVE]					= "#7F715A"
#}
#widget_class "*.GtkNotebook*GtkLabel" style "notebook-label"

style "tooltips"		= "default"
{
  bg[NORMAL]		= "#DAB566"
}

style "ruler"			= "default"
{
  engine "pixmap" {
    image 
      {
        function			= BOX
	detail			= "vruler"
	file				= "ruler.png"
	border			= { 2, 2, 2, 2 }
	stretch			= TRUE
      }
    image 
      {
        function			= BOX
	detail			= "hruler"
	file				= "ruler.png"
	border			= { 2, 2, 2, 2 }
	stretch			= TRUE
      }
  }
}

style "handlebox"		= "default"
{
  engine "pixmap"
  {
    image
    {
      function          		= BOX
      file              		= "null.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
    }
    image
    {
      function          		= SHADOW
      file              		= "null.png"
      border            		= { 0, 0, 0, 0 }
      stretch          	 	= TRUE
    }
    image
    {
      function			= HANDLE
      overlay_file			= "handle-v.png"
      overlay_stretch		= FALSE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      overlay_file			= "handle-h.png"
      overlay_stretch 		= FALSE
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
      file              	= "null.png"
      border            	= { 0, 0, 0, 0 }
      stretch           	= TRUE
    }
    image
    {
      function          	= BOX
      file              	= "null.png"
      border            	= { 4, 4, 4, 4 }
      stretch           	= TRUE
    }
  }
}

style "frame"
{
  GtkFrame::shadow_type = GTK_SHADOW_NONE
  fg[NORMAL]				= "#000000"
  bg[NORMAL]				= "#998960"
  bg[INSENSITIVE]				= "#777777"
  engine "pixmap"
  {
    image
    {
       function			= SHADOW_GAP
       file				= "null.png"
       border			= { 2, 2, 2, 2 }
       stretch			= TRUE
       gap_start_file	= "null.png"
       gap_start_border	= { 2, 0, 2, 0 }
       gap_end_file		= "null.png"
       gap_end_border	= { 0, 2, 2, 0 }
       gap_side			= TOP
    }
  }
}
class "GtkFrame" style "frame"
widget_class "*.GtkFrame.GtkLabel" style "frame"
widget_class "*.GtkFrame.GtkCheckButton.GtkLabel" style "frame"
widget_class "BasePWidget.GtkEventBox.GtkTable.GtkFrame" style "frame"

style "list-header"
{
   GtkTreeView::odd_row_color = "#F5F5F5"
   GtkTreeView::even_row_color = "#FFFFFF"
  xthickness			= 1
  ythickness			= 1
   engine "pixmap" 
	{
    	image
      		{
        	function        	= BOX
		state			= NORMAL
		file            	= "list_header.png"
		border          	= { 8, 8, 8, 8 }
		stretch         	= TRUE
      		}
    	image
      		{
        	function        	= BOX
		state			= PRELIGHT
		file            	= "list_header-pressed.png"
		border          	= { 8, 8, 8, 8 }
		stretch         	= TRUE
      		}
  	}	
}
widget_class "*List" style "list-header"
widget_class "*Tree*" style "list-header"
widget_class "GtkCList" style "list-header"

class "GtkButton"          			style "button"
class "GtkOptionMenu"      		style "optionmenu"
class "GtkEntry"           				style "entry"
class "GtkRuler"           			style "ruler"
class "GtkScrollbar"       			style "scrollbar"
class "GtkProgressBar"     			style "progressbar"
class "GtkRange"         				style "range"
class "GtkMenu"       				style "menu"
class "GtkItem"           				style "menuitem"
class "GtkTearoffMenuItem"		style "tearoffmenuitem"
class "GtkNotebook"      			style "notebook"				
class "GtkHandleBox"    			style "handlebox"
class "GtkEventBox"    				style "flat"
class "GtkPaned"       				style "handlebox"
widget "gtk-tooltips"  				style "tooltips"
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"


```

---

### Post by notarikon on 2006-10-17
Heh, change these two lines:

```
  GtkButton::default_border				= { 2, 2, 2, 2 }
  GtkButton::default_outside_border		= { 2, 2, 2, 2 }
```

to this one:

```
  GtkButton::default_border				= { 0, 0, 0, 0 }
```

---

### Post by jclmusic on 2006-10-18
doesn't work :(

---


---
title: "How can i make the panel black with white font?"
date: 2008-04-19
forum: Desktop Effects &amp; Customization
---

### Post by Brii on 2008-04-19
like this

[http://www.hackszine.com/blog/archive/2008/03/run_safari_in_ubuntu.html](http://www.hackszine.com/blog/archive/2008/03/run_safari_in_ubuntu.html)

I KNOW ITS NOT THE REGULAR EDITION OF UBUNTU


but it looks cool

---

### Post by tommyhakinen on 2008-04-19
yeah I like it too. here it is.
1. go to your home directory and show all the hidden folders
2. go to home/user/.themes and select the current theme you are using: eg. home/user/.theme/Elegance
3. then look for the panel.rc file and open it with text editor. it should be located at /home/user/.themes/<your current theme>/gtk-2.0/panel.rc
4. then look for style "panel" and replace it with
> 
style "panel"
{
	fg[NORMAL] 			= "#ffffff" 
	fg[PRELIGHT] 			= "#ffffff"
	fg[ACTIVE] 			= "#ffffff"
	fg[SELECTED] 			= "#ffffff"


}

5. close all your active windows and press
> 
Ctrl + Alt + Backspace


after you restart, you should have your panel font colors to be white

---

### Post by Brii on 2008-04-20
heres the one im using i cant find what your talking about:



gtk_color_scheme = "fg_color:#000\nbg_color:#DFE4E8\nbase_color:#fff\ntext_color:#000\nselected_bg_color:#5598d7\nselected_fg_color:#fff"

style "clearlooks-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15

  GtkScrollbar   ::min_slider_length = 30
  GtkCheckButton ::indicator_size    = 14
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 15
#  GtkToolbar     ::button-relief     = GTK_RELIEF_NORMAL
#  GtkMenuBar     ::shadow-type       = GTK_SHADOW_OUT
#  GtkScrollbar   ::has-secondary-forward-stepper = 1
#  GtkScrollbar   ::has-secondary-backward-stepper = 1

  GtkButton      ::child-displacement-x = 1
  GtkButton      ::child-displacement-y = 1

  GtkMenu        ::horizontal_padding = 0
  GtkMenu        ::vertical_padding = 0

  WnckTasklist   ::fade-overlay-rect = 0

  xthickness = 1
  ythickness = 1


  fg[NORMAL]        = @fg_color #"#000000" # black
  fg[PRELIGHT]      = @fg_color #"#000000" # black
  fg[SELECTED]      = @selected_fg_color #"#ffffff" # white 
  fg[ACTIVE]        = @fg_color #"#000000" # black
  fg[INSENSITIVE]   = darker (@bg_color) #"#b5b3ac" # dark beige

  bg[NORMAL]        = @bg_color # "#ede9e3"
  bg[PRELIGHT]      = shade (1.02, @bg_color) #"#f9f7f3" # very light beige
  bg[SELECTED]	    = @selected_bg_color # "#5598d7" # deepsky
  bg[INSENSITIVE]   = @bg_color # "#efebe5" # beige
  bg[ACTIVE]        = shade (0.9, @bg_color) #"#dcd4c9" #"#d7d3ca" # dark beige

  base[NORMAL]      = @base_color # "#ffffff" # white 
  base[PRELIGHT]    = shade (0.95, @bg_color) # "#5f8ec4" # dark beige
  base[ACTIVE]      = shade (0.9, @selected_bg_color) # "#a69f91" # darker deepsky
  base[SELECTED]    = @selected_bg_color # "#5598d7" # deepsky
  base[INSENSITIVE] = @bg_color # "#e8e5de" # beige

  text[NORMAL]      = @text_color # "#000000" # black
  text[PRELIGHT]    = @text_color # "#000000" # black
  text[ACTIVE]      = @selected_fg_color # "#ffffff" # white
  text[SELECTED]    = @selected_fg_color # "#ffffff" # white
  text[INSENSITIVE] = darker (@bg_color) # "#b5b3ac" # dark beige

  engine "clearlooks" 
  {
    #scrollbar_color   = "#76acde"
    colorize_scrollbar = TRUE
    menubarstyle      = 2 # 0 = flat, 1 = sunken, 2 = flat gradient
    toolbarstyle      = 0 # 0 = flat, 1 = enable effects
    animation         = FALSE
    style             = GLOSSY
  }
}


style "clearlooks-wide" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-wider" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-button" = "clearlooks-wider"
{
  bg[NORMAL]        = shade (1.05, @bg_color) # "#f6f4f1"
#  bg[INSENSITIVE]   = shade (1.04, @bg_color) # "#f2efeb"
  bg[PRELIGHT]      =  mix(0.60, shade (1.05,@bg_color), @selected_bg_color)
#  bg[PRELIGHT]      = shade (1.08, @bg_color) # "#faf9f8"
  bg[ACTIVE]        = shade (0.85, @bg_color)
}

style "clearlooks-notebook" = "clearlooks-wide"
{
#  bg[NORMAL]      = "#efebe5"
#  bg[INSENSITIVE] = "#efebe5"
  bg[NORMAL]        = shade (1.04, @bg_color)
}

style "clearlooks-tasklist" = "clearlooks-default"
{
  xthickness = 5
  ythickness = 3
}

style "clearlooks-toolbar" = "clearlooks-wide"
{
  bg[NORMAL]       = shade (1.02, @bg_color)
}

style "clearlooks-menu" = "clearlooks-default"
{
  xthickness = 0
  ythickness = 0
  bg[NORMAL] = shade (1.08, @bg_color) # "#f9f7f3"
}

style "clearlooks-menubar-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
  fg[PRELIGHT] = @selected_fg_color
  engine "clearlooks" {
    radius = 3.0
    style  = GLOSSY
  }
}
                  
style "clearlooks-menu-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
  fg[PRELIGHT] = @selected_fg_color  
  engine "clearlooks" {
    radius = 0.0
    style  = GLOSSY
  }
}


style "clearlooks-tree" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 1
}

style "clearlooks-frame-title" = "clearlooks-default"
{
  fg[NORMAL] = lighter (@fg_color) # "#404040"
}

style "clearlooks-tooltips" = "clearlooks-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = mix(0.60, shade (1.05,@bg_color), @selected_bg_color)
}

style "clearlooks-progressbar" = "clearlooks-wide"
{
  xthickness = 1
  ythickness = 1
  # fg[PRELIGHT]  = "#ffffff"
}

style "clearlooks-combo" = "clearlooks-button"
{
}

style "clearlooks-menubar" = "blackrock-default"
{
#  bg[NORMAL]   = "#bacedb"
}

style "clearlooks-scale" = "clearooks-button"
{
	GtkRange::trough-side-details = 1
}	

style "nautilus-location" {
  bg[NORMAL] = mix(0.60, shade (1.05,@bg_color), @selected_bg_color)
}
widget "*.nautilus-extra-view-widget" style:highest "nautilus-location"

# widget styles
class "GtkWidget"    style "clearlooks-default"
class "GtkButton"    style "clearlooks-button"
class "GtkScale"     style "clearlooks-scale"
class "GtkCombo"     style "clearlooks-button"
class "GtkRange"     style "clearlooks-wide"
class "GtkFrame"     style "clearlooks-wide"
class "GtkSeparator" style "clearlooks-wide"
class "GtkMenu"      style "clearlooks-menu"
class "GtkEntry"     style "clearlooks-wider"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
class "GtkToolbar"   style "clearlooks-toolbar" 
#class "GtkMenuBar" style "clearlooks-menubar"

widget_class "*.<GtkMenuItem>*" style "clearlooks-menu-item"
widget_class "*.<GtkMenuBar>.*" style "clearlooks-menubar-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton"    style "clearlooks-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget "gtk-tooltip*" style "clearlooks-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "clearlooks-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "clearlooks-notebook"






is it possible to make it so that its only the font on the panel thats white (and then one can make the background black)

really appreciate your help	:cool:

---

### Post by tommyhakinen on 2008-04-20
Ok. Looks like that's the gtkrc. You may try to chang the fg color to #FFFFFF which is white.But i am not sure will it works. Anyway, just remember the changes you made or back up the files in case something goes wrong.

 If you like black theme, you may try this theme:
> 
[http://www.gnome-look.org/content/show.php?content=44495](http://www.gnome-look.org/content/show.php?content=44495)


just download and install it.

here how it looks like on my laptop.

---

### Post by Saint Angeles on 2008-04-20
check out these too:

[http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210](http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210)
[http://www.gnome-look.org/content/show.php/SlicknesS?content=71993](http://www.gnome-look.org/content/show.php/SlicknesS?content=71993)

i'm using the black one and i can't find a better theme anywhere.

---

### Post by Brii on 2008-04-20
hmm 


i downloaded one of them then i go to appearance then into themes then to install find the one  i downloaded then it says "theme correctly installed" 


how do i make it the theme i use?

---

### Post by Saint Angeles on 2008-04-20
there are step by step instructions on the download page

---

### Post by featherking on 2008-04-20
here is a package for a program called gnome-color-chooser its basically a gui that creates the gtkrc file but also shows you each color you can change

i didnt write the program but ive had this package for so long i forget exactly where it came from, this is how i have always set up my black panel/white text

---

### Post by tommyhakinen on 2008-04-20
did you downloaded the gtk-2.0 themes? If yes, it will prompt you if you want to change to new installed theme or not.

---

### Post by Lantesh on 2008-04-21
> **featherking said:**
> here is a package for a program called gnome-color-chooser its basically a gui that creates the gtkrc file but also shows you each color you can change

i didnt write the program but ive had this package for so long i forget exactly where it came from, this is how i have always set up my black panel/white text

Thanks for the link.  I tried it, but I'm not seeing anywhere to change the font down on my task bar to white.  Any suggestions as to what I'm doing wrong?

---

### Post by jryprt on 2008-04-21
> **Lantesh said:**
> Thanks for the link.  I tried it, but I'm not seeing anywhere to change the font down on my task bar to white.  Any suggestions as to what I'm doing wrong?

Go to gnome-color-chooser click on Panel look at screenshot  check the 2 top boxs & change the color .

---

### Post by Lantesh on 2008-04-21
jryprt, thanks man.  I'm such an idiot.  I was trying to do it where you change the font size, and font type.  I thought that color selection box was for the color of the bar itself, not the font.  Sometimes the answer is right in front of my face and I don't see it.  Anyway thanks I appreciate it!

---

### Post by Brii on 2008-04-21
> **featherking said:**
> here is a package for a program called gnome-color-chooser its basically a gui that creates the gtkrc file but also shows you each color you can change

i didnt write the program but ive had this package for so long i forget exactly where it came from, this is how i have always set up my black panel/white text

i downloaded the program and installed it with the packet installer but i can find it

---

### Post by Mchl923 on 2008-04-28
Brii, type 
 ```
gnome-color-chooser
```
in terminal

---

### Post by Mchl923 on 2008-04-28
tried gnome color chooser... no change

---

### Post by JackTheDipper on 2008-04-30
> **Mchl923 said:**
> tried gnome color chooser... no change

gnome-color-chooser (not "gnome color chooser") is the starting command. Else just use the starter at "System->Settings->GNOME Color Chooser". ;-)


[edit]
oh, should have read the previous posts..
@Mchl923: what do you mean with "no change"? Which theme and which panel are you using?
[/edit]

---

### Post by Mchl923 on 2008-04-30
When I change settings in color chooser, there is no change to the panel

---

### Post by Mchl923 on 2008-04-30
My bad... I just realized that there are different tabs, switching to panel tab helps a lot.  Now all I need is a good background image to use for the panel.

---


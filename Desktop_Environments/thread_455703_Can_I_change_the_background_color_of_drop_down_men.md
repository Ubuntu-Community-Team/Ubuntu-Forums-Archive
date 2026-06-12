---
title: "Can I change the background color of drop down menu's on the Gnome panel?"
date: 2007-05-26
forum: Desktop Environments
---

### Post by Hayesio on 2007-05-26
Hi guys, I'm a newbie to Ubuntu and this is probably a silly question, but can someone tell me how to change the background color of the Applications/Places/System drop-down-menu's in the gnome panel.  I would also like to change the text color if its possible.
 (Note: I'm not talking about the button color on the panel itself, this is simply the panel color).   

I'm running Ubuntu Feisty with Beryl installed - Emerald theme manager.

Any help would be greatly appreciated.

Hayesio

---

### Post by gavintlgold on 2007-05-27
I don't think the menu supports that. I've never heard of anything like that (though that would be quite cool)

---

### Post by culorut on 2007-05-27
[http://www.gnome-look.org/content/show.php/gnome-color-chooser?content=47349](http://www.gnome-look.org/content/show.php/gnome-color-chooser?content=47349)

You should be able to change the menu colors and a lot more with color chooser. I am running it right now but the only problem I have is it does not change the text color in Firefox.

Great app.

---

### Post by Hayesio on 2007-05-28
Thanx culorut, this is a really cool app but it doesn't seem to be able to change the menu color.  It says "Start menu not yet supported" under the panel tab.

Cheers

---

### Post by bimmerd00d on 2007-05-31
You'll need to create a file in your /home/username directory called .gtkrc-2.0

paste this in there and it will make your text whatever color is under the "my_color" hex data that i've highlighted in bold for you.  I forget where i got the color chart for hex codes, but you can find it on google pretty quick im sure.



 include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = **"#CCCCCC"**
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "000000"
widget_class "*ToolItem*" style "000000"
widget_class "*SeparatorMenuitem*" style "000000"
widget_class "*SeparatorToolitem*" style "000000"
widget_class "*ImageMenuitem*" style "000000"
widget_class "*RadioMenuitem*" style "000000"
widget_class "*CheckMenuitem*" style "000000"
widget_class "*TearoffMenuitem*" style "000000"

---

### Post by RudolfMDLT on 2007-06-02
Thanks for the file!

for hex colors

sudo apt-get install gcolor2

and then run it via alt+F2

---

### Post by lred_tree on 2007-12-04
Hey, I've edited the "my_color" style in .gtkrc-2.0 in this way:

style "my_color"
{
fg[NORMAL] = "#123CD8"
fg[SELECTED] = "#ff0000"
fg[ACTIVE] = "#ff0000"
fg[PRELIGHT] = "#ff0000"
fg[INSENSITIVE] = "#696DC2"
bg[SELECTED] = "#000000"
bg[ACTIVE] = "#000000"
bg[PRELIGHT] = "#000000"
}

This changes my panel text color, highlight color, etc.  However, I can't seem to figure a way to change the actual drop down menu background.  The only thing I can figure is that there is a specific widget or widget_class you can add that will change it.
Any widget experts out there? eh? eh?

---

### Post by lred_tree on 2007-12-11
Solved this one, check out my [**[COLOR="Red"]thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=637862").

---


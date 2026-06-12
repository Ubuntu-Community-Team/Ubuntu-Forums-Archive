---
title: "Changing font color of the panel"
date: 2005-09-18
forum: Desktop Environments
---

### Post by jozmak on 2005-09-18
Hi,

I've changed the panel color of my Gnome desktop to dark gray and would like to change the 'Applications, Places and System' as well as the 'Date'  font colors to white or light gray. How should I go about doing that?

Thanks,
J. Mak

---

### Post by Nasso on 2005-10-10
i have been looking for a solution to this too, anyone?

---

### Post by nosami on 2005-10-15
Check this [http://www.ubuntuforums.org/showthread.php?t=69723&highlight=font+color]("http://www.ubuntuforums.org/showthread.php?t=69723&highlight=font+color") page out

---

### Post by agapito on 2005-11-15
I have a faster way to do it. Try this:
In ~/.gtkrc-2.0 insert this line

include "/home/<user_name>/.gnome2/panel-fontrc"

then create the file panel-fontrc in .gnome2, which consists of the following lines:

style "my_color"
{
fg[NORMAL] = "#4353b6"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

and that's it. All you have to do is choose the color and do a killall gnome-panel. The second "widget" line affects only the applets and the first one does the rest.
To chose the color you can use the color select dialog in GIMP or, even better, use this:
[http://gcolor2.sourceforge.net/]("http://http://gcolor2.sourceforge.net/")
it allows you to pick colors from anywhare in the gnome desktop. It compiled smothly in Hoary.

Have fun! :smile:

---

### Post by nikolaiortiz on 2007-04-08
ok.. i made the file..
but nothing happens
please some help...:confused:

---

### Post by KittyChunk on 2007-10-22
Just a note - if .gtkrc-2.0 doesn't exist (as it didn't in my install of 7.10), you need to create it. There are a couple of other similar-looking .gtkrc-XXX files in the home dir, but using them won't work.

---


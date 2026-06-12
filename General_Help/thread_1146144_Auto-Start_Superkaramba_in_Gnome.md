---
title: "Auto-Start Superkaramba in Gnome"
date: 2009-05-02
forum: General Help
---

### Post by panzer77 on 2009-05-02
I spent a little time looking for a how-to on starting Superkaramba on login for Gnome.  I found lots of information posted for KDE, but couldn't locate one for Gnome.  Maybe I didn't look in the right place?  Here is what I did to get it running in Ubuntu 9.4  If you already have Superkaramba installed, skip to “Launching on start up” at the bottom.

[IMG]http://lh4.ggpht.com/everaldo.canuto/RoLwjwxKTSI/AAAAAAAAALQ/XDIfxz2JsPg/s400/glassy-green.jpg[/IMG]

**First you will need to install Superkaramba:**
Add/Remove Programs Install Option
1.From the “Applications” menu drop down, select “Add/Remove...”.
2.In the “Accessories” section, select “Superkaramba”, then “Apply Changes”.

Synaptic installer Option
1.From the “System” menu drop down, select “Administration/Synaptic Package Manager”.  (You will need to enter your password.)
2.In the Quick Search box (top right), enter “Superkaramba”. (no quotes)
3.Right click on the Superkaramba in the package and choose “Mark for Installation” and then press “Apply”.

Command line Install Option
1.From the “Applications” menu drop down, select “Accessories/Terminal”.
2.Type the follow commands:
sudo apt-get update (press enter)
<yourpassword>  (press enter)
sudo apt-get install Superkaramba (press enter)

At this point Superkaramba can run from the command (Press the Alt key and F2, then enter “Superkaramba).  

**Add the program to your applications menu:**
1.With your mouse over the ubuntu logo in the top left corner of the task bar, right click mouse and select “edit menus”.
2.Highlight or select one of the Application sub-directories (I selected the “Accessories” section).
3.Press the “New Item” button on the right side.
4.Enter the following:
Name: Superkaramba
Command: /usr/bin/Superkaramba
Comment: (This is optional)
5.Press “OK”

Now that you have Superkaramba installed, you can set up some Superkaramba themes and add them to your desk top.  I highly recommend “3D Desktop Clock” and “3DDDhorz” calendar.  If you have “Visual Effects” enabled, your will also get some nice desktop reflections!  Both of these you will have to get while on line in the “Get New Stuff” section.


**Launch on start up**
1.From the “System” menu drop down, select “Preferences/Startup Applications”.
2.Select the “Add” button.
3.Enter the following:
Name: Superkaramba
Command: /usr/bin/Superkaramba
Comment: (This is optional)
4.Press the “Add” button.
5.Select the “Options” tab, and check “Automatically remember running applications when logging out.

---


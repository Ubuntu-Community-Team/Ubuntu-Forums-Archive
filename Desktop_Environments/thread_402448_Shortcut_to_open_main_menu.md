---
title: "Shortcut to open main menu"
date: 2007-04-05
forum: Desktop Environments
---

### Post by Boule on 2007-04-05
Hi,

I would very much like to use the special key (otherwise known as the windows key) to open the menu in ubuntu, ideally the "Applications" section, and then be able to browse thru it using arrows...

If there's another keyboard shortcut I don't know about that does the job, it's also fine by me !

thanks

---

### Post by johnc4510 on 2007-04-05
Alt+F1

---

### Post by Boule on 2007-04-05
great, thx !

---

### Post by Scruffynerf on 2007-05-25
Is there a way to change it from Alt+F1 to the Windows key?

I've found lots of people asking it, but no answers.

---

### Post by mgmiller on 2007-05-26
> Is there a way to change it from Alt+F1 to the Windows key?


Yes there is.

Run Applications>System Tools>Configuration editor
It's easier if you make it full screen.

On the left side, navigate to:
apps/metacity/global_keybindings

You do this by clicking on the little triangles to make the list open up below it.

Once you get to the global_keybindings entry, left click it once to select it, then look on the right side for the key called 
"panel_main_menu"   Right click the entry and select "edit key"  The type should be string and the value you should change to Super_L

The change takes effect immediately.  I would suggest saving a bookmark to this spot to make it easy to get back to later.  Look at the top of the window and you will see a Bookmarks drop down.  Just click that and then add bookmark.  Simple!!

---

### Post by Scruffynerf on 2007-05-28
Excellent! - Very many thanks!

---

### Post by mgmiller on 2007-05-28
You're welcome.  ):P

---

### Post by Lord Illidan on 2007-05-28
I am not on Ubuntu at the moment, but isn't there an easier way through the Preferences menu? God help us if we have to change shortcut keys through the Configuration Editor..that's like using the Registry in windows!

---

### Post by mgmiller on 2007-05-28
You could try going to System>Preferences>Keyboard Preferences and then the Layout options tab and click the triangle next to Alt/Win key behavior and trying a few of the options there.  I have mine set as Default and used the configuration editor as I mentioned above, but this might be an easier way.  If you get it to work, please post back.

---


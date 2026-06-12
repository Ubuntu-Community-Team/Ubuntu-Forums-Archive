---
title: "How to assign key combo to app?"
date: 2009-01-03
forum: Desktop Environments
---

### Post by 5Toes on 2009-01-03
Hello World

I'm new to Ubuntu, and I'm running on Intrepid Ibex. I pretty much love Ubuntu, and barely use Windows. However, I'm used to the Ctrl+Alt+Del combo for the task manager.
My Question is: How can I assign Ctrl+Alt+Del to the Ubuntu System Monitor?

Thanks in advance :)

---

### Post by Ivo Moelans on 2009-01-03
Open Configuration Editor (*Applications&#8594;System Tools&#8594;Configuration Editor* or in terminal type *gconf-editor*).
Go to *apps/metacity/keybinding_commands*. In the right pane choose a command that is blank, click in the column *values* and type *gnome-system-monitor*.
In the left pane go to *global_keybindings*. In the right pane choose the corresponding *run_command_...*, click in the column *values* and type *<Control><Alt>Delete*.

That's it - of course the principle works for other applications/commands as well. (If you want to know the exact command for an application open *System&#8594;Preferences&#8594;Main Menu*, select the application and click on *Properties*.)

---

### Post by 5Toes on 2009-01-04
This worked [:)]

Thanks a lot Ivo!
*(Though I had to unbind the Logout command from Ctrl+Alt+Del first from Keyboard Shortcuts before I could use it!*

---

### Post by Ivo Moelans on 2009-01-04
Glad it worked for you.

> (Though I had to unbind the Logout command from Ctrl+Alt+Del first from Keyboard Shortcuts before I could use it!

Forgot about that; I did my configuration a few years ago... :) In the beginning I also modified Super+E (Win+E) to start nautilus as I was used to it in Windows to start explorer. Now I use Super+N and Shift+Alt+Ctrl+Delete for the system monitor.

---

### Post by paparozoumis on 2009-01-18
This is a great idea to match the Ctrl-Alt-Del to the System Monitor but I can't make it wor :O

I have Ubuntu 8.10 and I have done all those steps described as you can see in the attachments. 
Then I removed the combo from Keyboard Shortcuts as already said. 

Still, the combo doesn't work... Actually, there's no action at all when I hit Ctrl-Alt-Del... 
Anything extra I  have to do ?

---

### Post by Ivo Moelans on 2009-01-18
I've no idea. It *should* work. As
If you use compiz, you could check *System&#8594;Preferences&#8594;CompizConfig Settings*. Go to *General Options*, tab *Commands*. The two first sections have the same items as in *Configuration Editor* although they number the items slightly differently. In fact they communicate: what you change in one is automatically changed in the other. You could look if for some reason or other this hasn't happened.

Also, try to use */usr/bin/gnome-system-monitor* as the command.

Edit:

I forgot: log out & log in. This shouldn't be necessary, but you never know.

---

### Post by Ludachrispeed on 2009-01-18
@ paparozoumis

Does it work if you use a different key combo?  For example, try  <Alt>s  or something.

---

### Post by paparozoumis on 2009-01-18
> **Ludachrispeed said:**
> @ paparozoumis

Does it work if you use a different key combo?  For example, try  <Alt>s  or something.


No... No command or combination worked through gconf-editor. 
 

> **Ivo Moelans said:**
> I've no idea. It *should* work.
If you use compiz, you could check *System&#8594;Preferences&#8594;CompizConfig Settings*. Go to *General Options*, tab *Commands*. The two first sections have the same items as in *Configuration Editor* although they number the items slightly differently. In fact they communicate: what you change in one is automatically changed in the other. You could look if for some reason or other this hasn't happened.

Also, try to use */usr/bin/gnome-system-monitor* as the command.

Edit:

I forgot: log out & log in. This shouldn't be necessary, but you never know.


I   logged in and out and in and out but nothing came up,,, 
The command works through terminal. 

I followed your advice and did it  through Compiz. It worked right away without any logging in/out. 
Now I know how to handle a few ideas I have as I am quite new into the Ubuntu thing and I  feel  I  have A LOT to learn about it :lol

Thanks  all guys... Your advice is valuable :guitar:

---

### Post by mlnease on 2009-10-31
Thanks, Guys--worked a treat.

mike

> **Ivo Moelans said:**
> Glad it worked for you.



Forgot about that; I did my configuration a few years ago... :) In the beginning I also modified Super+E (Win+E) to start nautilus as I was used to it in Windows to start explorer. Now I use Super+N and Shift+Alt+Ctrl+Delete for the system monitor.

---


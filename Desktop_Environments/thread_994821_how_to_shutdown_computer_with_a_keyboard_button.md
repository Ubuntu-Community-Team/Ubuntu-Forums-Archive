---
title: "how to shutdown computer with a keyboard button"
date: 2008-11-27
forum: Desktop Environments
---

### Post by ekansdiuqil on 2008-11-27
Is there a way that I can shutdown the system by only pressing a keyboard button?

---

### Post by Keyper7 on 2008-11-27
If your computer has a power button, all you need to do is to go to the power management settings and assign "shutdown" to this button.

If you want to shutdown with an arbitray key, this might help:

[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

PS: it might take an entire day to check your reply to this, but I will

---

### Post by ekansdiuqil on 2008-11-27
Thanks alot. It seems that it will work. but when i press the buttons I assigned it says:

There was an error running "/home/mybox/shutdown.csh":
Failed to execute child process "/home/mybox/shutdown.csh" (No such file or directory).

The shutdown.csh is in my folder and I execute:

chmod 777 shutdown.csh at the correct place and all its permissions are enabled.

---

### Post by Keyper7 on 2008-11-28
That's strange... does putting a common command like, say, "firefox" work?

---

### Post by ekansdiuqil on 2008-12-01
It was a fault of mine with script. But now I have 2 different problems. First I cannot assign any keybinding command to numpad but in my project I don't have any buttons accept numpad that is I have to use numpad. Do you have any suggestions about this? 

Secondly I tried some commands like firefox chmod in my script they work fine but when I tried:
sudo -p mypassword -u root shutdown -h 0
it doesn't shutdown.

---

### Post by glotz on 2008-12-01
There are some suggestions. Some of them might be silly or outright dangerous though.
[http://www.google.com/search?q=non-root+shutdown](http://www.google.com/search?q=non-root+shutdown)

---

### Post by ekansdiuqil on 2008-12-01
Thanks. I tried one of them and now shutting down works fine without numpad. The last question is how can I assign this script to numpad ?

---

### Post by glotz on 2008-12-01
What key would you like to use?

The drill is here. Open a terminal and type in xev. A white little box should pop up. Move your mouse cursor into it. Now hit a key. You will then see in the terminal a log for the key down and key up events. There you'll see the name of they key, it's right there after the keysum, e.g. the plus on the keypad would be KP_Add. (Capitalization matters, like always.) Find out the name of they key you'd like to use. Then close the event tester, the white box and type into the terminal gconf-editor.

There navigate to /apps/metacity/global_keybindings/ and add the key combo to a run command. (You can add modifiers like Ctrl and Alt to the key.) Finally edit /apps/metacity/keybinding_commands/ to point to the shutdown command. :)

---

### Post by ekansdiuqil on 2008-12-01
thanks for all the replies. 
I wanted to use "-" key. KP_Subtract solved my problem, and for numbers only KP_#(KP_8 ) works.

---


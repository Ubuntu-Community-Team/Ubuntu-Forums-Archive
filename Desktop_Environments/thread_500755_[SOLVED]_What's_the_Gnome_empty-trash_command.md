---
title: "[SOLVED] What's the Gnome empty-trash command?"
date: 2007-07-14
forum: Desktop Environments
---

### Post by aysiu on 2007-07-14
Please don't say ```
rm -rf ~/.Trash/*
``` I've used that before, and I've read both [How To Empty the Ubuntu Gnome Trash from the Command Line](http://www.howtogeek.com/howto/ubuntu/how-to-empty-the-ubuntu-gnome-trash-from-the-command-line/) and [Empty Ubuntu Gnome Trash from the Command Line](http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html)

I already know how to do that.

That command empties the trash *immediately*

I don't want to empty the trash immediately. I want to know command that pops up this window (see attached screenshot), confirming that I want to empty the trash.

My ultimate goal is the creation of a keyboard shortcut for emptying the trash. I hate using the mouse and would prefer not having to move my mouse to the trash, right-click it, and select *Empty Trash*. It'd be much faster and more convenient to have a keyboard shortcut for emptying the trash. That's why I'm asking for the command. If someone knows a way to make a keyboard shortcut for it without knowing the command, that would be cool, too.

Thanks in advance for any help.

---

### Post by raja on 2007-07-14
aysiu, if all you want is a warning before the trash is emptied, why not just have a warning dialog with zenity and then the line as above in a script which you run with a shortcut?
Doesnt exactly answer your question, but serves the purpose I think.

---

### Post by aysiu on 2007-07-14
Hi, raja. Thanks for the suggestion. I'm not really familiar with Zenity. What steps would I take, exactly, to do that?

---

### Post by tomchuk on 2007-07-14
```

zenity --question --text="Are you sure you want to empty the trash?" && rm -rf ~/.Trash/*

```

---

### Post by raja on 2007-07-14
You  beat me to it, Tomchuk.

Yes, that or use zenity warning instead of question (maybe more appropriate here).

---

### Post by aysiu on 2007-07-14
I'll give that a try, tomchuk. Thanks!

**Edit**: That's awesome. It worked! Thanks to you both, for the idea and the execution.

To anyone who may stumble upon this thread and not know how to make this all happen (there were some blanks I filled in):

1. Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gksudo gedit /usr/local/bin/emptytrash
``` This will open up a file called *emptytrash* in the /usr/local/bin and bring it up in a text editor.

2. In the blank text document that appears, paste in this text: ```
#!/bin/bash
zenity --question --text "Permanently remove all items from the trash?" && rm -rf ~/.Trash/*
``` Save and exit the text editor called Gedit.

3. Paste these commands into the terminal: ```
sudo chmod +x /usr/local/bin/emptytrash
gconf-editor &
```

4. In the configuration editor window that appears afterwards, navigate to **Apps > Metacity > global_keybindings > run_command_1**. Right-click the value and select **Edit Key** and put in the keyboard shortcut you want ```
<Control><Shift>e
``` for example.

Then, go to **Apps > Metacity > keybinding_commands > command_1**. Right-click the value and select **Edit Key** and put in the command ```
emptytrash
```

Now, the keyboard shortcut Control-Shift-E should bring up the empty trash dialogue.

---


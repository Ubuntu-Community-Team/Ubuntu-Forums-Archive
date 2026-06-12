---
title: "gamepad screensaver script"
date: 2008-02-11
forum: Gaming &amp; Leisure
---

### Post by &amp;)ky#)^ on 2008-02-11
Here's a quick script I wrote a while ago that allows one to temporarily disable a screensaver.  Why would you want to do that?  I've found that while playing some emulators with a gamepad, the system doesn't count gamepad input like it does keyboard or mouse input to keep the screensaver from popping in.  I can't tell you how many lives I've lost from having to grab for the mouse to keep the screen from blacking out.

This simple script disables the default gnome screensaver before running your program and then enables it again when you close the program.  The way it works is like this example.  Just pass the program you want to run as well as any of its arguments as an argument to the script.

./noss.sh zsnes

Enjoy! :)

---

### Post by grossaffe on 2008-02-12
sorry, linux noob here; do i need to edit something in the script that makes it program-specific?

edit: and how do i make the script executable?

---

### Post by &amp;)ky#)^ on 2008-02-12
> **grossaffe said:**
> sorry, linux noob here; do i need to edit something in the script that makes it program-specific?

edit: and how do i make the script executable?
To make the script executable, right click on the file and choose **Properties**.  In the properties dialog window, choose the **Permissions** tab.  In that tab, check the check box that indicates **"Allow executing file as program"**.  Then, just click **Close**.

The script doesn't need to be edited in any way.  To launch an application using the script, just add the program name and its arguments to the script's arguments.

For example, let's say this is what you would normally run:
zsnes mariokart.zip

With the script, this is what you would run:
./noss.sh zsnes mariokart.zip

---

### Post by grossaffe on 2008-02-12
that's if i were to run the script in the terminal, isn't it?  if i wanted to get it to run as an executable wouldn't i have to replace something in there with the argument?  and maybe the shell would need to be placed in the folder with the program (zsnes in this case).

---

### Post by &amp;)ky#)^ on 2008-02-12
If zsnes is in your path, you shouldn't have to have the script in the same directory as the executable.  If you just wanted to run the script as an executable to run specifically one program, you could either replace "$*" in the script with the command to run the program or you could edit the default zsnes desktop entry file.

/usr/share/applications/zsnes.desktop [edited]
```
[Desktop Entry]
Encoding=UTF-8
Name=zsnes
Comment=A Super Nintendo Entertainment System (TM) emulator
**Exec=/home/user/noss.sh zsnes**
Icon=zsnes.xpm
Terminal=false
Type=Application
Categories=Application;Game;2DGraphics;Emulator
```

The bolded line is the only one I changed.  If you choose to change it, you should update it to reflect the location of my script.

---

### Post by grossaffe on 2008-02-12
> **bluej774 said:**
> If zsnes is in your path, you shouldn't have to have the script in the same directory as the executable.  If you just wanted to run the script as an executable to run specifically one program, you could either replace "$*" in the script with the command to run the program or you could edit the default zsnes desktop entry file.

/usr/share/applications/zsnes.desktop [edited]
```
[Desktop Entry]
Encoding=UTF-8
Name=zsnes
Comment=A Super Nintendo Entertainment System (TM) emulator
**Exec=/home/user/noss.sh zsnes**
Icon=zsnes.xpm
Terminal=false
Type=Application
Categories=Application;Game;2DGraphics;Emulator
```

The bolded line is the only one I changed.  If you choose to change it, you should update it to reflect the location of my script.
oh, ok.  I kept trying to replace "command" with the program.  I think i'm starting to get the hang of this stuff.  just need to learn the language.

---

### Post by grossaffe on 2008-02-13
ok, i've tried changing that line of the zsnes.desktop to direct it to the script, but i keep getting a permissions error

---

### Post by &amp;)ky#)^ on 2008-02-13
I forgot to mention that the desktop file is a protected file.  Try editing it by typing this into the command line:
gksudo gedit /usr/share/applications/zsnes.desktop

---

### Post by grossaffe on 2008-02-13
> **bluej774 said:**
> I forgot to mention that the desktop file is a protected file.  Try editing it by typing this into the command line:
gksudo gedit /usr/share/applications/zsnes.desktop

no, i didn't have a problem editing the file itself (well i did, i created my own work around, i copied the file into a non-protected folder, edited it, and then used the terminal to copy it over the old file).  what i meant was that when i try to run the edited file i get a permissions error.

---

### Post by &amp;)ky#)^ on 2008-02-13
Do you get the same error when you try to run it from a command line?
In other words, do you get a permission error if you run:
/path/to/noss.sh znes

What does this error say exactly?

What I'm trying to get at here is whether or not you have permissions for the script.  I know you have permissions to run zsnes and I know root has permissions to everything.  But, do you as a user have correct permissions for the script?

---

### Post by grossaffe on 2008-02-13
interestingly enough, i am not getting that error message anymore.  thanks for the script and the support. (now to test it to make sure it actually works ;) )

---

### Post by grossaffe on 2008-02-14
um... the no screen saver script isn't stopping the screen saver...

---

### Post by &amp;)ky#)^ on 2008-02-14
It should work.  It still works on my box and any Ubuntu box I've tried it on.

Try these commands in the terminal.
$ gnome-screensaver-command --exit
$ gnome-screensaver-command

After those commands, it should print the message "** Message: Screensaver is not running!" to the terminal.

Next, try this command.
$ gnome-screensaver
$ gnome-screensaver-command -q

Then, the terminal should print "The screensaver is inactive".

If your system behaves as I have described it and you haven't edited my script in any way except perhaps the line that has "$*", then there's no reason why it shouldn't work.  Otherwise, it's your box and not my script.

---

### Post by grossaffe on 2008-02-14
> **bluej774 said:**
> It should work.  It still works on my box and any Ubuntu box I've tried it on.

Try these commands in the terminal.
$ gnome-screensaver-command --exit
$ gnome-screensaver-command

After those commands, it should print the message "** Message: Screensaver is not running!" to the terminal.

Next, try this command.
$ gnome-screensaver
$ gnome-screensaver-command -q

Then, the terminal should print "The screensaver is inactive".

If your system behaves as I have described it and you haven't edited my script in any way except perhaps the line that has "$*", then there's no reason why it shouldn't work.  Otherwise, it's your box and not my script.

you think it could have something to do with my compiz settings?

---

### Post by acoustibop on 2008-02-14
Always disable Compiz if you're playing 3D games, grossaffe.

---

### Post by &amp;)ky#)^ on 2008-02-14
> **grossaffe said:**
> you think it could have something to do with my compiz settings?

I don't use compiz, so it could be possible.  However, gnome-screensaver is gnome-screensaver.  If that's the program that acts as your screensaver, I don't see how compiz could mess with that.  Either gnome-screensaver is running as a daemon or it's not.

However, I'm far from a compiz expert.

---

### Post by grossaffe on 2008-02-14
> **acoustibop said:**
> Always disable Compiz if you're playing 3D games, grossaffe.

well i hardly consider ZSNES 3d...

---


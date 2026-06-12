---
title: "Symbolic links rant"
date: 2005-06-24
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-24
..are different to regular links and i need them to get thunderbird lightning talking to the clock aplet (yep  :smile: )

Right click > create symbolic link. No. Again, I am refered to the command line. Now that's not normally a problem, but what if i make a typo? Things will not work, i will not know why. bla bla bla

Again, not a problem for a single link, but I'm going to be doing this alot.

"I suggest you learn command line" is not a valid answer. I don't want to learn the damn ins and outs of the whole OS just yet. I would just like to have things working reasonably and sort the rest of my life out before pouring hour after hour into setting something up to do the world's simplest task, which in any other OS would be on right click by default.

Now, i am very pleased with ubuntu and linux, and soon i wont be needing windows for anything other than occasional power tasks. but the damn effort that everything is now! I mean.... have you seen the thread on how to install OOo2b ? It's 13 pages long!

---

### Post by skoal on 2005-06-24
[QUOTE=Dave_is_sexy]"I suggest you learn command line" is not a valid answer. I don't want to learn the damn ins and outs of the whole OS just yet. I would just like to have things working reasonably and sort the rest of my life out before pouring hour after hour into setting something up to do the world's simplest task, which in any other OS would be on right click by default.[/QUOTE]
I agree with you 101%.  However, from time to time I hop back on a Win box and find certain tasks as equally difficult or time consuming.  Granted, I've been using Linux *exclusively* for almost 7 years now, but (to be perfectly blunt) I'd probably need you to explain to me how to create a symlink (shortcut?) on the windows desktop.  Seriously.  

I think the image Linux has as an "unfriendly uber geek OS" comes predictably from our potty training on Windows.  Imagine a world where we all migrated from Unix to Windows instead.  I can, since I did.  Point and click just frustrate me.  In that same vein, I would imagine those raised on velcro straps would find the adjustment to shoe laces rather difficult...

\\//_

---

### Post by cwaldbieser on 2005-06-24
I am not sure how it works on a Mac, but on Windows, you cannot just right click to make a symbolic link.  You can create a shortcut to an application or folder by right clicking in Windows, but cannot create symbolic links (called junction points in Windows lingo) without writing a program to do it for you.  This makes the command line in Linux actually look pretty user friendly by comparison.

---

### Post by WAM on 2005-06-25
[QUOTE=cwaldbieser]I am not sure how it works on a Mac, but on Windows, you cannot just right click to make a symbolic link.  You can create a shortcut to an application or folder by right clicking in Windows, but cannot create symbolic links (called junction points in Windows lingo) without writing a program to do it for you.  This makes the command line in Linux actually look pretty user friendly by comparison.[/QUOTE]
 Are you sure? From what I can tell you still just right click (on folder/application) > create shortcut...

I'm too lazy to reboot into Windows to verify, but from what I can remember it's that simple.

---

### Post by miscz on 2005-06-25
This are simple shortucts that are treated like a files. They are opened by Explorer to show original location, but you cannot open C:\symlink\something that was in original folder\pikachu.jpg.

---

### Post by crashtest on 2005-06-25
[QUOTE=Dave_is_sexy]
"I suggest you learn command line" is not a valid answer. I don't want to learn the damn ins and outs of the whole OS just yet. I would just like to have things working reasonably and sort the rest of my life out before pouring hour after hour into setting something up to do the world's simplest task, which in any other OS would be on right click by default.

[/QUOTE]
Sorry Dave, I know you don't want to hear this, but using the command line is often (usually?) much easier than doing things with a gui.  

The command 'ln -s' creates a symbolic link to a file.  'ln -s file1 file2' creates a symbolic link named file2 that points to file1.  Pretty simple.

If you're trying to create the symlink in a directory where regular users do not have write permission, just stick the word 'sudo' in front: 'sudo ln -s file1 file2'

A nice easy tutorial on the command line can be found here: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Anyway, if you really REALLY don't want to learn the command line, but still want the power  and stability of UNIX, nothing beats Mac OS X.  In my opinion, Apple makes the only UNIX based OS that you can use without EVER opening a command line. I'm still not sure if that's a 'good' thing.

Linux can, for the most part, be used without learning the command line, but in the long run it is actually more work, and you won't understand the OS as well.  Sorry to preach at you, but I'm really trying to help.

---

### Post by cwaldbieser on 2005-06-25
[QUOTE=WAM]Are you sure? From what I can tell you still just right click (on folder/application) > create shortcut...

I'm too lazy to reboot into Windows to verify, but from what I can remember it's that simple.[/QUOTE]
 This link has a pretty good explanation of the difference between a sym-link and a shortcut on Windows:

[http://www.pearlmagik.com/winbolic/](http://www.pearlmagik.com/winbolic/)

---

### Post by cwaldbieser on 2005-06-25
I will further observe that at least in Kubuntu, there is a simple way to create symbolic links uing the GUI.  Open up konqueror.  Split the file explorer window into 2 panes.  drag the file you want to link into the destination pane.  When the context menu pops up, choose "Link here".

This seems pretty simple to me.

---

### Post by crashtest on 2005-06-25
[QUOTE=cwaldbieser]I will further observe that at least in Kubuntu, there is a simple way to create symbolic links uing the GUI.  Open up konqueror.  Split the file explorer window into 2 panes.  drag the file you want to link into the destination pane.  When the context menu pops up, choose "Link here".

This seems pretty simple to me.[/QUOTE]

How does konqueror handle it if you try to make a symlink in a directory owned by root?  Nautilus just pops up an error message "You do not have permissions to write to this folder"  Is there a way to do this in a gui?  I'm guessing there must be, but I still maintain that doing it from the command line will be MUCH quicker.

---

### Post by cwaldbieser on 2005-06-25
You would have to have root permissions, which means you would have to open one konqueror window with kdesu.  I have seen some distributions that use KDE have a menu item for opening a root konqeror explorer window and give it a red border to serve as a warning that root powers are active.

I have observed that competence with either GUI or command line is possible in this regard.  I choose to use the CLI or GUI because I find it more accessible or convenient, depending on circumstances.  Sometimes, the choice is arbitrary.

---


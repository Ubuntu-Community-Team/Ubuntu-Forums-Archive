---
title: "I really want to use the Terminal . . ."
date: 2009-01-28
forum: General Help
---

### Post by crimlaw on 2009-01-28
The terminal scares the crap out of me.  Why, I am not really sure, could be all of the code that pops up when I enter a command someone gives me, and I don't understand any of it.  Could be because I have no idea what to type. Or, it could be because nothing ever seems to work for me when I do try to type something.  

So, my question.  Where is the best, easily explained guide to learning the terminal?  Is it the same as command line?  What is the terminals full potential?  Is there a reason I need to use the terminal if I don't already know how?  

Thanks!!!

---

### Post by indytim on 2009-01-28
For those robust in terminal use, they will probably tell you it is at least as good as, if not better than the GUI.  There are certain situations within the Lx environment where the terminal is the best way to go.  My advice with respect to learning terminal commands is to frequent the "man" pages.  The next time you come across a terminal command, before blindly executing it, consult the man pages for a full description of the command all of the variances to it (flags).

The "man" pages are accessed by (you guessed it) the terminal!.  At the terminal prompt, simply type man <command> for a full description.  

For commonly used terminal commands, consult your preferred search engine and start with bash or bash commands.

IndyTim

---

### Post by jerome1232 on 2009-01-28
This should give you some basics (how to find your way around and such)

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by mkrahmeh on 2009-01-28
command lines are so fun to use once you get your hands on them..sometimes they are more useful than the GUI..

> **jerome1232 said:**
> This should give you some basics (how to find your way around and such)

[http://linuxcommand.org/](http://linuxcommand.org/)

+1
excellent choice

you may also refer to this [_fun-to-read tutorial_]("http://ubuntuforums.org/showthread.php?t=73885")

---

### Post by Iowan on 2009-01-28
Careful... once you start using terminal commands, regularly, you'll start wondering why the GUI is really necessary.  Then you'll build a server - just to work via CLI... (been there).

---

### Post by crimlaw on 2009-01-28
alright, here is a stupid question.  Can you explain a GUI with an example?  I understand that the GUI is something that allows me to access the shell (?), I hope I understand that much, but what is an example?  Is all of ubuntu a GUI?  Is the terminal window a GUI?

I am looking at [http://linuxcommand.org](http://linuxcommand.org).  Thanks for the suggestion.  

Wait, I lied, I have one more question.  Do I "do" command line in the terminal?  Or do I need to use another program?

---

### Post by blackened on 2009-01-28
> **crimlaw said:**
> alright, here is a stupid question.  Can you explain a GUI with an example?  I understand that the GUI is something that allows me to access the shell (?), I hope I understand that much, but what is an example?  Is all of ubuntu a GUI?  Is the terminal window a GUI?

I am looking at [http://linuxcommand.org](http://linuxcommand.org).  Thanks for the suggestion.  

Wait, I lied, I have one more question.  Do I "do" command line in the terminal?  Or do I need to use another program?

GUI stands for "Graphical User Interface". If you use the mouse to run your machine via pretty (or sometimes not, ahem XP default) pictures, then you're likely looking at one right now.

If your terminal is surrounded by window borders, then yes, it is part of the GUI. The "terminal" you're talking about, if you're using Gnome, is likely "gnome-terminal". There are many other interfaces to the commandline available, including booting (or "dropping") to the CLI (Command Line Interface).

---

### Post by crimlaw on 2009-01-28
> **blackened said:**
> GUI stands for "Graphical User Interface". If you use the mouse to run your machine via pretty (or sometimes not, ahem XP default) pictures, then you're likely looking at one right now.

I think I am getting it.  So, an OS like Vista, XP, Ubuntu, what I see on my screen, all of the windows, the menus, the icons, are all part of the GUI.  Right?

---

### Post by jerome1232 on 2009-01-28
GUI - Graphical User Interface

A gui is just that, an interface to the computer with pretty pictures and symbols. Pretty much everything you use is a gui. Firefox is a gui, the menu's you use to open programs are gui's, the programs you use are "gui's".

Ubuntu uses the Gnome Desktop Enviroment which is sort of a collection of GUI applications. (Rhythmbox, firefox, transsmission etc... are all gui applications.)

Ubuntu comes with gnome-terminal as it's default terminal emulator, you can open it by clicking Applications-Accessories-Terminal. You should be given a bash prompt where you can follow along at that site I linked to.

If you want to get a pure command line enviroment then hit ctrl+alt+f1, you'll land at a text based login, press ctrl+alt+f7 to get back into your x session.

---

### Post by albinootje on 2009-01-28
> **crimlaw said:**
> I think I am getting it.  So, an OS like Vista, XP, Ubuntu, what I see on my screen, all of the windows, the menus, the icons, are all part of the GUI.  Right?

Yes.

Here's another page about the terminal :
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by cdtech on 2009-01-28
Here is some more reading that may interest you:
[http://www.network-theory.co.uk/docs/bashref/](http://www.network-theory.co.uk/docs/bashref/)

---

### Post by crimlaw on 2009-01-28
Thanks Jerome, I got it now.  I am currently running through that website.  Good stuff.  It suggests that I should not use the terminal while in superuser all of the time.  Do I have to do something to place myself as the superuser?  Is that when I type "sudo" <command> and then enter my password?  

If I am already in Superuser, just by opening the terminal, then I need to "create a user account for myself."  How do I do that?

---

### Post by DGortze380 on 2009-01-28
Just to confuse you some more (sorry)...

GUI (Graphical User Interface)

In linux, the operating system 'is' (for lack of a better term) the terminal (CLI). When you click a button in the GUI, it cause a corresponding CLI command.

Windows is a little different, the terminal in Windows is actually an emulation, the Graphical Interface 'is' the operating system. Entering a command in the terminal causes and action in the graphic interface.


That's an oversimplified explanation, but it should give you an idea of the power of the command line in linux.

(in case you were wondering, OS X is sort of somewhere in between. The terminal is fully functional and not an emulation, but it's tightly integrated with the GUI)

---

### Post by jerome1232 on 2009-01-28
Your not a super user by default, using sudo escalates your privilages to that of the superuser (root).

So in other words if you didn't type sudo first then your fine, your just a regular user that can only destroy his own account, not the rest of the system :)

---

### Post by DGortze380 on 2009-01-28
> **crimlaw said:**
> Thanks Jerome, I got it now.  I am currently running through that website.  Good stuff.  It suggests that I should not use the terminal while in superuser all of the time.  Do I have to do something to place myself as the superuser?  Is that when I type "sudo" <command> and then enter my password?  

If I am already in Superuser, just by opening the terminal, then I need to "create a user account for myself."  How do I do that?

Ubuntu disables to root account ('superuser') by default. Sudo allows you to execute particular command with root privileges.

---

### Post by The Cog on 2009-01-28
The "terminal" and "command line" are pretty-much synonymous. The terminal (or console) is where the command prompt is that you type the command into. You could argue that the bottom line of the terminal is the command line,.

The word "console" is usually taken to mean the black&white text screen that you get pressing Ctrl-Alt-F1 through Ctrl-Alt-F6.

---

### Post by crimlaw on 2009-01-28
well Jerome . . . that is reassuring.;)

Thanks again for everyone who as explained things to me in stupid terms, I am getting it.  Now to just read through these cites, I hope to be using my terminal and command line in no time.

---

### Post by albinootje on 2009-01-28
> **crimlaw said:**
> Do I have to do something to place myself as the superuser?  Is that when I type "sudo" <command> and then enter my password?  

Yes. See also here : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by antmenj on 2009-01-28
**Read all this before you try it**

Now if you really want to "scare the crap out of your self:p" and see what its like with no GUI at all hit

alt control F2

[COLOR="Red"]To get the GUI back alt control F7   [/COLOR]  Remember this one;)

---

### Post by crimlaw on 2009-01-28
hmm, yeah, my luck I won't be able to get it back.  I will take your word for it.  I hit ctr+alt+f1 and scared myself enough.  And that didn't even do anything.

---

### Post by albinootje on 2009-01-28
> **crimlaw said:**
> hmm, yeah, my luck I won't be able to get it back.  I will take your word for it.  I hit ctr+alt+f1 and scared myself enough.  And that didn't even do anything.

Try ctl alt at the same time, then also press F1

---

### Post by crimlaw on 2009-01-28
ok, I hit ctr+alt+f1 and now my skydome is all screwed up.  How do I get it back?  Do I have to restart my computer?  Will that do it?

---

### Post by albinootje on 2009-01-28
> **crimlaw said:**
> ok, I hit ctr+alt+f1 and now my skydome is all screwed up.  How do I get it back?  Do I have to restart my computer?  Will that do it?

You should see what is called a "virtual console". Do you see a login prompt or not ?

Hit ctl and alt, and then also F7 to get back into your desktop.

---

### Post by crimlaw on 2009-01-28
When I hit all three keys, the screen when white for a second, then came back to normal, except that my skydome was messed up.  So, I went into compiz and reloaded the pic, looks great.  No problems at this point.

---

### Post by kelean on 2009-01-28
If you want to learn the power of the command line try INX linux.  It is based on ubuntu and has many tutorials on how to use the command line.  There are some pretty cool apps.  It is liveCd and here is the link.

[http://inx.maincontent.net/]("http://inx.maincontent.net/") 

INX is worth checking out.

---

### Post by crimlaw on 2009-01-30
I ran through most of the website that Jerome provided and it was a great intro to the terminal.  However, when it started to talk about Shell Scripts I began to lose interest, because I can't see much use for Scripts with what I do.  What I would like to do with the terminal is control my computer as if I did not have a mouse.  I understand that I can control my computer through keyboard commands like ctr, alt, and combinations, but I was under the impression that I could do such things with the terminal through command line.  

Any good sites for explain how to do that?

Thanks!!!

---

### Post by albinootje on 2009-01-30
> **crimlaw said:**
> What I would like to do with the terminal is control my computer as if I did not have a mouse. 

alt-F2 fires up the "run command" window.
You must surely know alt-tab already. And from a terminal you can start applications if you know their name, e.g. :
```

firefox &
gimp &

```

---

### Post by crimlaw on 2009-01-30
yeah, I see now.  I don't think I had a proper understanding of command line and what it was used for.  I will continue to read websites just to gain knowledge of the terminal and its potential. 

Thanks again for all of your help.

---

### Post by jerome1232 on 2009-01-30
That depends what do you want to do exactly?


There are tons of cli app's out there. for example w3m is a cli based web browser, finch is a cli based pidgin, mocp is a great cli based audio player, apt-get and apttitude are the command line package managers, 
rtorrent is a great cli based torrent program. vim is an advanced cli text editor.

I'm not sure what you mean by control your system.

---

### Post by crimlaw on 2009-01-30
I am not sure I really know either, that is why I am being confusing I guess.  Let's use the example of running an openoffice document.  If I use a mouse, I double click on my jump drive, find the folder, double click, find my document, and double click.  

When I think of command line, I think of being able to open that document simply by typing a command in the terminal.  Then my document would open in openoffice, I would do what I needed to do, then use another command line command to close openoffice.  

The closest thing I have found to this is to open the terminal, type openoffice, its opens, use a ctr + O, then find my document, and edit.  However, when I try to "kill" from the terminal, it does not work.  I thought the website you suggested was going to go in this direction with its instructions, but it didn't.

Does that make more sense?

---

### Post by albinootje on 2009-01-30
> **crimlaw said:**
>  When I think of command line, I think of being able to open that document simply by typing a command in the terminal.  Then my document would open in openoffice, I would do what I needed to do, then use another command line command to close openoffice.  

The closest thing I have found to this is to open the terminal, type openoffice, its opens, use a ctr + O, then find my document, and edit.  However, when I try to "kill" from the terminal, it does not work.


```

oowriter /media/your_usb_drive/your_document.odt

```
Then e.g. :
```

ps auxw|grep soffice.bin
killall -9 soffice.bin

```

oowriter will probably "detach" itself from the terminal after being started, but quite some programs will keep on running from the terminal.
With ctl-c you can "kill" it, and with ctl-z you can "suspend" it into the background.
With "fg" you can push it to the foreground again, and if you use ctl-z with more than one command, then the command "jobs" can be useful to look up the job number.
With "kill %1" <enter> you can kill the first job in the background.

I just tested the whole thing (while writing this comment down), and it was interesting to see that starting oowriter from the command line will actually end up running soffice.bin with the -writer parameter, perhaps useful to know when you want to use the "ps" command or "killall" command to shut down the OpenOffice writer.

---

### Post by gjoellee on 2009-01-30
Knowing how to use the terminal is crusial to become a Linux user that can stand for him/herselves without getting much support from other then yourself.

---

### Post by jerome1232 on 2009-01-30
> **crimlaw said:**
>  I thought the website you suggested was going to go in this direction with its instructions, but it didn't.

Does that make more sense?

Yeah I understand a bit better now, that website is about the barebone basics, alot of people don't understand how to get around in a cli (cd, pwd, ls and etc)

I think albinootje covered your specific example rather well.

---

### Post by mikemac on 2009-01-30
Follow this link:
[http://ubuntuforums.org/showthread.php?t=1054271&highlight=ubuntu+pocket+guide]("http://ubuntuforums.org/showthread.php?t=1054271&highlight=ubuntu+pocket+guide")

It will bring you to a site where you can either download this excellent pocket guide (as a .pdf), or alternatively buy a print copy.  It is an excellent resource and well written by Keir Thomas.  I would guess you'd need pretty big pockets for the print version - it's a 170-page pdf.

Hope this helps some.  I've been going through the book and it's excellent.

---

### Post by crimlaw on 2009-01-30
the explanation from albinootje was great and is exactly what I am looking to do.  So, where do I learn to do this myself?  I am going to take a look at the pdf in the last post.  I imagine that once I get the basic commands learned, a guide like that pdf will come in handy whenever I know what I want to do but not sure what to type.

---

### Post by albinootje on 2009-01-30
> **crimlaw said:**
> the explanation from albinootje was great and is exactly what I am looking to do.  So, where do I learn to do this myself?  

I learned the ctl-z and "fg" and "kill %1" from my first Linux book I read (somewhere in 1996 or 1997 I think).

You should play around with this, try experimenting a bit.

Try this to see the difference between using "&" and without :
```

gedit &
baobab

```

See also here : [http://tldp.org/HOWTO/DOS-Win-to-Linux-HOWTO.html](http://tldp.org/HOWTO/DOS-Win-to-Linux-HOWTO.html)
Very very old, but perhaps useful.
Disclaimer : using chmod 777 and chmod 666 should be frowned upon, don't use that when it is not needed!
Skip the "4.6 Running Programs on Remote Computers" section, that's really insecure! Use "ssh -X" instead.

---

### Post by albinootje on 2009-01-30
Now I remember the example from the book again.
First open a terminal, and start the "yes" command :
```

yes

```
This will start an "endless" amount of output :)

Then press ctl-z
After that type in :
```

kill %1

```
and press <enter> twice.
If all went well the yes command was terminated.

Perhaps one can argue that the ctl-z command is not very useful in nowadays life, but if you're comfortable with the command line, I can tell you that when you are in a big hurry to finish something, then ctl-z can be faster to do "something in between running another process from the terminal" instead of hitting ctl-shift-t to open another terminal tab in the gnome terminal.
This is just an example. 
You can also use ctl-z during a compilation process to temporarily stop it.

---

### Post by kelean on 2009-01-31
Ctrl c-stops the command yes and brings you back to the prompt.

I still say that INX linux can show you a great deal about the cli.  The interactive tutorials will give you the basics and show you where to go from there.

---


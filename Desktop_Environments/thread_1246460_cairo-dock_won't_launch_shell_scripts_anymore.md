---
title: "cairo-dock won't launch shell scripts anymore"
date: 2009-08-21
forum: Desktop Environments
---

### Post by v1nsai on 2009-08-21
I've been using a shortcut on cairo-dock to launch Bluej for a while, but now all of a sudden all it does is open the script in a text editor.  I haven't made any changes to it and I don't think it has been updated (using the repo version).

I went to Properties > Open With and deleted all the programs it wanted to open the script with, but now nothing happens when I click on it in cairo-dock -_- .  

I've also tried running 'sudo chmod +x' on it but that hasn't affected it either.  What the heck can anyone recommend something?

---

### Post by anthw27 on 2009-08-21
I tried cairo-dock under jaunty here and had so many stability problems I now use Awn.

It is far more stable and has some nice applets too.

Now I know it doesn't solve your problem but I can tell you that awn is stable and so far has not let me down.

---

### Post by fabounet on 2009-08-22
which version ?
I don't have any stability problem with Cairo-Dock.
is your script executable ?
what is the command of the launcher ? try to run it into a terminal.

---

### Post by v1nsai on 2009-08-22
> **fabounet said:**
> which version ?
I don't have any stability problem with Cairo-Dock.
is your script executable ?
what is the command of the launcher ? try to run it into a terminal.

It's definitely executable, I can run it from nautilus no problem, but running it from cairo-dock either opens the script in a word processor or does nothing.

When I drag and drop the shell script to cairo, it creates a launcher with the command 'file:///home/v1nsai/bluej/bluej', which does not execute in a terminal.  It says the file does not exist.  I tried launching '/home/v1nsai/bluej/bluej' and that worked from the terminal, but still nothing from cairo-dock.  Strange.

[QUOTE=anthw27]I tried cairo-dock under jaunty here and had so many stability problems I now use Awn.

It is far more stable and has some nice applets too.

Now I know it doesn't solve your problem but I can tell you that awn is stable and so far has not let me down. 
[/QUOTE]
Oh I'm well aware, I use awn as my taskbar.  Cairo-dock is my launcher ;)

I just don't believe in mixing the two, can't tell what the hell is going on when your launchers are mixed with your open programs.  Yes yes I know you can separate them but it's still a mess in my eyes.

Cairo has had stability problems since I first heard of it, but damned if it doesn't look good when it decides to work.

---

### Post by fabounet on 2009-08-24
if you drag and drop the script into the dock, a shortcut to the file will be made, independantly of the file's type.
what you want is a launcher with the command
/path/to/your/script
so right-click -> add a manual launcher, then give it a name, an image, and fil the command with the path of your script.
that should work.

by the way, you can have 2 main docks in Cairo-Dock.
just edit a launcher, and in the "container" option, enter a name (let's say "dock2" for instance). A 2nd dock will be created with your launcher inside.
mode this dock where you want, and move your other launchers into it.
Now the first main dock is used for taskbar, and the 2nd one for launchers :-)
you can even have a 3rd one for applets on another side of your screen.

---

### Post by v1nsai on 2009-08-24
> **v1nsai said:**
> I tried launching '/home/v1nsai/bluej/bluej' and that worked from the terminal, but still nothing from cairo-dock.  Strange.


I have also tried changing the command to '/home/v1nsai/bluej/bluej.sh' and 'sh /home/v1nsai/bluej/bluej' and other combinations of 'sh' and '.sh' but neither have opened it.  Some do nothing while others open the file as a text document.

And thanks for the tip, but cairo-dock and awn both have different apps and uses, I like having both.


EDIT:
When I tried '/home/v1nsai/bluej/bluej' the first time, I just went to the launcher that was created when I dragged the file to the dock, and changed the command.  I tried creating a new manual launcher, and entering the exact same command and it worked!  Strange, but hell, it was fixed.  Thanks fabounet!

---

### Post by anthw27 on 2009-08-25
> **fabounet said:**
> which version ?
I don't have any stability problem with Cairo-Dock.
is your script executable ?
what is the command of the launcher ? try to run it into a terminal.

Sorry Fab, 

Yeah Under Jaunty it seems unstable, but it turns out its not Cairos fault.
I think it has something to do with Compiz. The Dock always launches but the effects settings are screwed up severly.

I think it happened after an update that has caused some drama's, seems there's been an increase in problems with compiz in here of late.

---

### Post by fabounet on 2009-08-26
ok
@v1nsai : it's not strange, it's because the launcher you created was a shortcut to the file you dropped into the dock
you can't modify a launcher just by editing manually the command.
sorry for the confusion ^_^
I guess that the dock should probably not consider .sh files as any "normal" files but rather as launcher.

---


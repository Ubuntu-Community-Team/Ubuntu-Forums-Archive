---
title: "Helpful nautilus scripts"
date: 2005-12-10
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-10
I had a "files" directory with 20 files in it and I needed each of the 20 files to go to 20 different locations. Rather than right-click a file, choose cut, surf to the target directory, right-click, choose paste, go back to the source directory and repeat all of that for the remaining 19 files, I wrote some scripts that perform these steps much faster.

**Nautilus script explanation**
A nautilus script is just an executable shell script (usually bash) that is placed in a special scripts directory so that the Nautilus graphical shell can find it. This is a really neat function of Nautilus, because it allows you to extend the functionality the the file browser to do just about anything. Scripts are invoked by selecting a file or group of files, and right-clicking with the mouse, to bring up a 'Context' menu. One of the options of this menu is the 'Scripts' submenu (this option only appears once you have at least one script in the scripts directory), which allows you to select a script to invoke on the selected files.

For a script to appear on the script menu, it must:
1. be placed in your scripts directory (~/.gnome2/nautilus-scripts), and
2. be executable (with chmod a+x filename)

If you place an executable script in your scripts directory, its name will not necessarily appear on the scripts menu immediately. You first must visit the scripts directory with Nautilus - which can be done using the last option in the scripts menu. Once the directory is visited, Nautilus will know about which scripts you have, and you will be able to use them.

**Now, on to the Copy To and Move To scripts.**

**The Copy To script:**
Place the following code in a new file, give it a filename of copyto and make it executable with chmod a+x copyto. Move the new file to the ~/.gnome2/nautilus-scripts/ directory, open nautilus and you'll find a new right-click menu item entitled "Scripts" with a submenu that has an item that quickly copies a file to any directory you desire.

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e $location/$arg ];then
   zenity --question --title="Conflict While Copying" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  cp $arg $location ;;
   esac
else
   cp $arg $location
fi
done

```

**The Move To script:**
Place the following code in a new file, give it a filename of moveto and make it executable with chmod a+x moveto. Move the new file to the ~/.gnome2/nautilus-scripts/ directory, open nautilus and you'll find a new right-click menu item entitled "Scripts" with a submenu that has an item that quickly moves a file to any directory you desire.

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e $location/$arg ];then
   zenity --question --title="Conflict While Moving" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  mv $arg $location ;;
   esac
else
   mv $arg $location
fi
done

```

As you can see, nautilus scripts allow you to extend nautilus to do almost anything. I have put my entire Gnome Applications menu in my nautilus/desktop right-click menu so I don't even use my gnome menu much anymore.

For instance, you can put the below code into a new text file, give it a name of terminal or something like that, make it executable and move it to ~/.gnome2/nautilus-scripts/Terminals or ~/.gnome2/nautilus-scripts/Apps or whatever suits you, and you'll have a right-click menu item to open gnome-terminal. This can be done with any app, whether you need to use sudo or not.

```

#!/bin/sh
gnome-terminal


```

Basically, the "gnome-terminal" part of the above code is simply the cli command to start gnome terminal. You can use the gnome menu editor to find the proper commands for all the apps in the Applications menu.

More information, scripts and tutorials for nautilus scripts can be found [here]("http://g-scripts.sourceforge.net/").

---

### Post by mustang on 2005-12-10
Cool cool cool man! Thanks a lot. Both scripts work like a charm. Thanks for the guide and the good read. This will certainly come in handy.

---

### Post by ardchoille on 2005-12-10
[QUOTE=mustang]Cool cool cool man! Thanks a lot. Both scripts work like a charm. Thanks for the guide and the good read. This will certainly come in handy.[/QUOTE]
You're welcome. Glad to help :)

---

### Post by mustang on 2005-12-10
Sorry I should have asked this earlier:

Is there anyway to edit the scripts so that it prompts the user for the password when he/she is moving/copying a file to a restricted area only root has access to? Kinda like the prompt synaptic gives you once you first open it?

I know I could just modify my nautilus launcher so that it executes "gksudo nautilus" but then it doesn't start up with my default home directory.

Thanks m8!

---

### Post by ardchoille on 2005-12-10
[QUOTE=mustang]Sorry I should have asked this earlier:

Is there anyway to edit the scripts so that it prompts the user for the password when he/she is moving/copying a file to a restricted area only root has access to? Kinda like the prompt synaptic gives you once you first open it?

I know I could just modify my nautilus launcher so that it executes "gksudo nautilus" but then it doesn't start up with my default home directory.

Thanks m8![/QUOTE]
Hmm.. that's a good question. I haven't ever used these scripts to copy anything to a dir outside my $HOME, but I suppose you could modify the various instances of "cp" or "mv" (copy and move) to read "gksudo cp blah blah" or gksudo mv blah blah" and that would prompt you for the root password.

Or, you could even have a seperate set of scripts for root use, Copy As Root, and Move As Root, and have those scripts contain the gksudo cp and gksudo mv commands.

---

### Post by anil_robo on 2005-12-11
I vote this thread a FIVE STAR, and strongly recommend it to be implemented in all Ubuntu versions by default!

---

### Post by ardchoille on 2005-12-11
Anyone know how to get hold of the Ubuntu dev team?

---

### Post by anil_robo on 2005-12-11
I guess you could pm some moderators... their names are listed at homepage bottom... in red font I guess. They should be able to guide your properly.

---

### Post by everdred on 2005-12-11
[QUOTE=ardchoille]I have put my entire Gnome Applications menu in my nautilus/desktop right-click menu so I don't even use my gnome menu much anymore.[/QUOTE]


Could you please post this script? I've been looking for a way to do just this.

---

### Post by 4linux on 2005-12-11
> **ardchoille]I had a "files" directory with 20 files in it and I needed each of the 20 files to go to 20 different locations. Rather than right-click a file, choose cut, surf to the target directory, right-click, choose paste, go back to the source directory and repeat all of that for the remaining 19 files, I wrote some scripts that perform these steps much faster.

**Nautilus script explanation**
A nautilus script is just an executable shell script (usually bash) that is placed in a special scripts directory so that the Nautilus graphical shell can find it. This is a really neat function of Nautilus, because it allows you to extend the functionality the the file browser to do just about anything. Scripts are invoked by selecting a file or group of files, and right-clicking with the mouse, to bring up a 'Context' menu. One of the options of this menu is the 'Scripts' submenu (this option only appears once you have at least one script in the scripts directory), which allows you to select a script to invoke on the selected files.

For a script to appear on the script menu, it must:
1. be placed in your scripts directory (~/.gnome2/nautilus-scripts), and
2. be executable (with chmod a+x filename)

If you place an executable script in your scripts directory, its name will not necessarily appear on the scripts menu immediately. You first must visit the scripts directory with Nautilus - which can be done using the last option in the scripts menu. Once the directory is visited, Nautilus will know about which scripts you have, and you will be able to use them.

**Now, on to the Copy To and Move To scripts.**

**The Copy To script:**
Place the following code in a new file, give it a filename of copyto and make it executable with chmod a+x copyto. Move the new file to the ~/.gnome2/nautilus-scripts/ directory, open nautilus and you'll find a new right-click menu item entitled "Scripts" with a submenu that has an item that quickly copies a file to any directory you desire.

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e $location/$arg ] said:**
> ;then
   zenity --question --title="Conflict While Moving" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  mv $arg $location ;;
   esac
else
   mv $arg $location
fi
done

```

As you can see, nautilus scripts allow you to extend nautilus to do almost anything. I have put my entire Gnome Applications menu in my nautilus/desktop right-click menu so I don't even use my gnome menu much anymore.

For instance, you can put the below code into a new text file, give it a name of terminal or something like that, make it executable and move it to ~/.gnome2/nautilus-scripts/Terminals or ~/.gnome2/nautilus-scripts/Apps or whatever suits you, and you'll have a right-click menu item to open gnome-terminal. This can be done with any app, whether you need to use sudo or not.

```

#!/bin/sh
gnome-terminal


```

Basically, the "gnome-terminal" part of the above code is simply the cli command to start gnome terminal. You can use the gnome menu editor to find the proper commands for all the apps in the Applications menu.

More information, scripts and tutorials for nautilus scripts can be found [here]("http://g-scripts.sourceforge.net/").

Well, the oddest thing; It works on some files but not others. For instance I have a folder with a bunch of jpgs. With some of them the copyto or moveto script works, on others it does not...just nothing happens. Got me scratching my head.  

Same with some other files and folders too.

I'll keep playing with it to see if I can find out more.

---

### Post by ardchoille on 2005-12-11
[QUOTE=everdred]Could you please post this script? I've been looking for a way to do just this.[/QUOTE]
It isn't a single scripts. It is a set of scripts.. one for each app on the Applications menu. It only takes about 15 minutes to write all the scripts. I have added a screenshot of what my desktop right-click menu looks like.

---

### Post by everdred on 2005-12-11
[QUOTE=ardchoille]It isn't a single scripts. It is a set of scripts.. one for each app on the Applications menu. It only takes about 15 minutes to write all the scripts.[/QUOTE]

Ah, alright. Thanks anyway.

---

### Post by bvc on 2005-12-12
[QUOTE=4linux]Well, the oddest thing; It works on some files but not others. For instance I have a folder with a bunch of jpgs. With some of them the copyto or moveto script works, on others it does not...just nothing happens. Got me scratching my head.  

Same with some other files and folders too.

I'll keep playing with it to see if I can find out more.[/QUOTE]I've had the same prob.

[Here's a script...audio convert]("http://freshmeat.net/projects/audio-convert")

Oh, and why is it that we can't have the menu scripts?

---

### Post by ardchoille on 2005-12-12
[QUOTE=bvc]I've had the same prob.

[Here's a script...audio convert]("http://freshmeat.net/projects/audio-convert")

Oh, and why is it that we can't have the menu scripts?[/QUOTE]
I have attached a tarball of all of my nautilus Applications scripts. However, these are simply bash scripts that call an app and some of them won't work on your system.. unless you have the pertinent apps installed - i.e. the script that calls graveman won't work if you don't have graveman installed. You can, however, open these scripts in a text editor to learn how to make your own scripts. See the attachment.

---

### Post by everdred on 2005-12-12
Thanks for posting the scripts. I'll give them a try.

Even though it takes a little work, I think this way might be preferable to having the entire apps menu in the right click... it's a bit cluttered as it is. :)

---

### Post by ardchoille on 2005-12-12
[QUOTE=everdred]Thanks for posting the scripts. I'll give them a try.

Even though it takes a little work, I think this way might be preferable to having the entire apps menu in the right click... it's a bit cluttered as it is. :)[/QUOTE]
You're welcome :)
Keep in mind that some of the scripts which won't work may just need a little tweaking in a text editor.

---

### Post by drotter on 2005-12-12
Thanks for posting these scripts.  I have one question though.
KDE has a nice function where you can "open terminal here" which opens a prompt in the current directory of the file manager.  Its the one thing in KDE that i like better then gnome.  Is there any way to make a script that can do the same function?

thanks

---

### Post by ardchoille on 2005-12-12
[QUOTE=drotter]Thanks for posting these scripts.  I have one question though.
KDE has a nice function where you can "open terminal here" which opens a prompt in the current directory of the file manager.  Its the one thing in KDE that i like better then gnome.  Is there any way to make a script that can do the same function?

thanks[/QUOTE]
There is a package that you can sudo apt-get install from universe that does exactly what you are talking about. The name of the package is nautilus-open-terminal. Enable universe, then install it with:

```
sudo apt-get install nautilus-open-terminal
```

---

### Post by drotter on 2005-12-12
That was exactly what i was looking for.
thanks

---

### Post by ardchoille on 2005-12-12
[QUOTE=drotter]That was exactly what i was looking for.
thanks[/QUOTE]
You're welcome. I had actually written a nautilus script for that functionality and then I found nautilus-open-terminal.. but the open-terminal package is better in my opinion.

---

### Post by computerbs on 2005-12-12
[QUOTE=4linux]Well, the oddest thing; It works on some files but not others. For instance I have a folder with a bunch of jpgs. With some of them the copyto or moveto script works, on others it does not...just nothing happens. Got me scratching my head.  

Same with some other files and folders too.

I'll keep playing with it to see if I can find out more.[/QUOTE]


I haven't tried the script myself, but does it handle spaces in filenames?  Maybe 

mv $arg $location

needs to be:

mv "$arg" "$location"

??

Or does nautilus automatically escape the spaces (e.g., ' ' becomes \' ')?  Just a thought...

---

### Post by computerbs on 2005-12-12
[QUOTE=computerbs]I haven't tried the script myself, but does it handle spaces in filenames?  Maybe 

mv $arg $location

needs to be:

mv "$arg" "$location"

??

Or does nautilus automatically escape the spaces (e.g., ' ' becomes \' ')?  Just a thought...[/QUOTE]


I love answering myself :-)  I ran a simple test and it appears the two scripts have problems with filenames with spaces.

Here are modified versions of the same 2 scripts that work with spaces:

copyTo:

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location/$arg" ];then
   zenity --question --title="Conflict While Copying" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  cp "$arg" "$location" ;;
   esac
else
   cp "$arg" "$location"
fi
done

```

moveTo:

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location/$arg" ];then
   zenity --question --title="Conflict While Moving" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  mv "$arg" "$location" ;;
   esac
else
   mv "$arg" "$location"
fi
done

```

---

### Post by 4linux on 2005-12-12
Thank you, I shall try it :)

---

### Post by 4linux on 2005-12-12
> **computerbs]I love answering myself :-)  I ran a simple test and it appears the two scripts have problems with filenames with spaces.

Here are modified versions of the same 2 scripts that work with spaces:

copyTo:

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location/$arg" ] said:**
> ;then
   zenity --question --title="Conflict While Moving" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  mv "$arg" "$location" ;;
   esac
else
   mv "$arg" "$location"
fi
done

```

Works great on file with and without spaces in file names.  Thanks!


Now, how about a script that does the same with folders, (move to  & copy to)?  ;)

---

### Post by bvc on 2005-12-13
Thx for posting them!
Concerning the open terminal script...heh, I still use one from over a year ago. There's many diff ways to do it, so I can't see that one would be better than another if they all work.```
#!/bin/bash
cd $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
gnome-terminal
```

---

### Post by ardchoille on 2005-12-13
[QUOTE=4linux]Works great on file with and without spaces in file names.  Thanks!


Now, how about a script that does the same with folders, (move to  & copy to)?  ;)[/QUOTE]
After testing them on folders I have found they work fine.

---

### Post by ardchoille on 2005-12-13
> **computerbs]I love answering myself :-)  I ran a simple test and it appears the two scripts have problems with filenames with spaces.

Here are modified versions of the same 2 scripts that work with spaces:

copyTo:

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location/$arg" ] said:**
> ;then
   zenity --question --title="Conflict While Moving" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  mv "$arg" "$location" ;;
   esac
else
   mv "$arg" "$location"
fi
done

```

Thanks a lot! I have made these changes to my scripts. I love these forums!

---

### Post by 4linux on 2005-12-13
[QUOTE=ardchoille]After testing them on folders I have found they work fine.[/QUOTE]
Strange, I tested some more and it seems the copyto does not work for me with folders. (works for files though) :confused: 

The moveto is working fine for both files and folders.

---

### Post by paul555 on 2005-12-19
for me copy-to and move-to aren't working for folders.Anyway great job :)

---

### Post by poptones on 2005-12-19
0  )  cp "$arg" "$location" ;;

Ain't gonna work with folders.

0  )  cp -r "$arg" "$location" ;;

---

### Post by cowlip on 2005-12-26
wow thank you computerbbs and poptunes, those posts fixed my problem witht eh scripts

---

### Post by ardchoille on 2005-12-26
Thank you all for the posts and the fixes for the scripts. I never had any problems with the scripts because I never create files whose filenames that contain spaces.

---

### Post by bluevoodoo1 on 2006-06-06
I just found this thread and I must say it is great! Thank you very much ardchoille.

---

### Post by H.E. Pennypacker on 2006-06-29
This idea of editing context menus is exactly what I am looking for, but it shouldn't require the use of copying and pasting and all that.  I'd much rather go to a GUI and specificy what I want the context menu to do.

There's something similar to this named Nautilus Actions.  Check it out at:

[http://www.grumz.net/?q=taxonomy/term/2/9](http://www.grumz.net/?q=taxonomy/term/2/9)

---


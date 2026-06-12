---
title: "sending terminal commands from text file"
date: 2009-03-28
forum: General Help
---

### Post by tjk on 2009-03-28
I've been a Linux (Ubuntu) convert for several years now.  I've accepted that I do need to use the terminal from time to time -- and the terminal often is a useful tool for using Linux.  I am constantly learning new uses and commands -- but it's a slow process...

I know that you can use the up/down arrow to select recent commands in the terminal, but I always have some commands that I forget -- and I have to look them up.  I have developed a considerably large text file, which contains commands and their uses (complete with my comments).  What I would like is: 
[INDENT]1) to just open my text file, 
2) select my command, 
3) right click for a pop-up menu, 
4) select "send to terminal", and that's it...
[/INDENT]the terminal would auto open and the command would be processed.  Isn't this a great idea?  :)
[B]
Here's my question:[/B] *Is is there anything like this?  And does anyone have similar ideas or know of an application that can perform this kind of procedure?*

---

### Post by dhughes on 2009-03-28
> **tjk said:**
> I've been a Linux (Ubuntu) convert for several years now.  I've accepted that I do need to use the terminal from time to time -- and the terminal often is a useful tool for using Linux.  I am constantly learning new uses and commands -- but it's a slow process...

I know that you can use the up/down arrow to select recent commands in the terminal, but I always have some commands that I forget -- and I have to look them up.  I have developed a considerably large text file, which contains commands and their uses (complete with my comments).  What I would like is: 
[INDENT]1) to just open my text file, 
2) select my command, 
3) right click for a pop-up menu, 
4) select "send to terminal", and that's it...
[/INDENT]the terminal would auto open and the command would be processed.  Isn't this a great idea?  :)
[B]
Here's my question:[/B] *Is is there anything like this?  And does anyone have similar ideas or know of an application that can perform this kind of procedure?*


 They're called shell scripts, a very common thing to do but not quite the way you want.

---

### Post by sgosnell on 2009-03-28
You can make a shell script that does what you want.  You'll need to do a little more studying to learn how to do all of it, though.  It ain't rocket science.

---

### Post by tjk on 2009-03-29
> **sgosnell said:**
> You can make a shell script that does what you want.  You'll need to do a little more studying to learn how to do all of it, though.  It ain't rocket science.

I was kinda hoping for something already made...  I imagined a two pane window, the top had the commands (and can concatenate commands by clicking on multiple commands), and the bottom had the terminal.  Krusader has a similar feature -- with it's separate terminal pane (but it has far too many other features).

Well, maybe I'll have to check into programming something or try to make a simple script...

---

### Post by mb_webguy on 2009-03-29
If it's a single command, you can make an alias.  Open your .bashrc file for editing with "gedit ~/.bashrc".  At the bottom of the file, add something like the following:```
alias *name*='*command*'
```
Where *name* is the name you want to give the *command* -- something easy to remember.  For example, I edit system files often enough that I got tired of typing "gksudo gedit *file*" every time, so I added the alias:```
alias sudit='gksu gedit'
```Keep in mind that an alias is just simple substitution.  As long as any options can be added at the end of the command, such as in my example of "gksu gedit", then you're ok.  If you need to change some information within the command, you need to use a script.  Scripts are actually pretty easy.  Here's an example:```
#! /bin/sh

echo "Hello!"
```The first line of the script tells the computer what to use to interpret the script, which is usually "/bin/sh", the basic shell.  You could also use "/bin/bash" if you want, which is the shell you use in the terminal.  There's really not much difference, except that bash has some additional features that make it better for interactive use (i.e. for you using it in the terminal), but slower for running scripts.

The rest of the script is essentially just a list commands.  For example, suppose I wanted a script to convert a video to an avi using mencoder.  The command to do this (at a bitrate of 1000kbps) has the following syntax:```
mencoder -o *output_file* -ovc xvid -xvidencopts bitrate=1000 *input_file*
```Since I don't want to have to remember that, I could create the following script:```
#! /bin/sh
mencoder -o $2 -ovc xvid -xvidencopts bitrate=1000 $1

```The "$1" and "$2" are placeholders for the arguments passed to the script.  For example, if I saved this script as "conv2avi", then I could convert the file "oldvid.flv" to "newvid.avi" using the command "conv2avi oldvid.flv newvid.avi".

If you create a directory called "bin" in your home directory and save your scripts there, you can use them in the terminal just like ordinary commands.  Just make sure to make them executable using the command "chmod +x *filename*".

---

### Post by hyper_ch on 2009-03-29
(1) the shebang line should be
```

#!/bin/....

```

(2) define the shell you want to us.
"sh" is not a shell but it is linked to one. On ubuntu I think it links by default to dash while root cron uses bash and that can cause problems. So better to use
```

#!/bin/bash

```
or
```

#!/bin/dash

```
or whatever shell you want.

---

### Post by darksideforge on 2009-03-29
> **tjk said:**
> I've been a Linux (Ubuntu) convert for several years now.  I've accepted that I do need to use the terminal from time to time -- and the terminal often is a useful tool for using Linux.  I am constantly learning new uses and commands -- but it's a slow process...

I know that you can use the up/down arrow to select recent commands in the terminal, but I always have some commands that I forget -- and I have to look them up.  I have developed a considerably large text file, which contains commands and their uses (complete with my comments).  What I would like is: 
[INDENT]1) to just open my text file, 
2) select my command, 
3) right click for a pop-up menu, 
4) select "send to terminal", and that's it...
[/INDENT]the terminal would auto open and the command would be processed.  Isn't this a great idea?  :)
[B]
Here's my question:[/B] *Is is there anything like this?  And does anyone have similar ideas or know of an application that can perform this kind of procedure?*

This might sound over-the-top, but have you considered downloading AnjutaIDE and Ubuntu_Customization_Kit and simply designing your own Desktop Environment?

---

### Post by ghostdog74 on 2009-03-29
> **tjk said:**
> but I always have some commands that I forget -- and I have to look them up. 
if you forget commands, you can always look it up using man. 
```

man -k <your keyword>

```

---

### Post by PhrankDaChickenGeek on 2009-03-29
Sounds like you could just open a terminal and your text file and have the same results:
1) to just open my text file,
2) select my command,
3) middle-click in the terminal, pasting the command
4) hit enter

You might also check out the "External Tools" plugin in Gedit, if that's what you use for text viewing/editing.

---

### Post by tjk on 2009-07-28
> **PhrankDaChickenGeek said:**
> Sounds like you could just open a terminal and your text file and have the same results:
1) to just open my text file,
2) select my command,
3) middle-click in the terminal, pasting the command
4) hit enter

You might also check out the "External Tools" plugin in Gedit, if that's what you use for text viewing/editing.

I was just reviewing my old threads and realized that the above suggestion is pretty much the method that I've adopted...  I discovered that kate is useful for this purpose. (I think it can also be done with gedit.) I have a quicklink to a specific kate file, which contains explanations of various commands; at the same time, when kate opens, there is a shortcut view (where I put my commands in); then I just highlight the command in the shortcut portion of the window, middle click in the terminal portion of kate, and hit enter.  I find it's a pretty good all-in-one system that works for me.

---


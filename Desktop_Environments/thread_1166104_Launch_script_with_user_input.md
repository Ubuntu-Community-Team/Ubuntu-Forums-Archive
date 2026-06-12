---
title: "Launch script with user input"
date: 2009-05-21
forum: Desktop Environments
---

### Post by aristotelian on 2009-05-21
Dear All,

  this is really a two part question concerning using something like latexmk (a perl script for latex). The first concerns how to call it from the desktop. There may be a second part about how to write the appropriate backend.

Here's what I'd like to be able to do. Have a launcher on a desktop panel that prompts me for an input, such as a .tex file (alternatively, being able to click on a tex-file in a file-browser window). That starts a script that does the following things.

[LIST]
[*]start the terminal
[*]changes into the directory containing the file selected
[*]takes the file as argument of a command, such as latexmk [options] filename
[/LIST]
I'd be grateful for any suggestions.

Cheers,
Bernhard.

---

### Post by kpkeerthi on 2009-05-21
This should help you get started:

```

#! /bin/bash

selected_file=$(zenity --file-selection --open)
latexmk $selected_file

```

---

### Post by aristotelian on 2009-05-21
Thanks a lot for the reply; I'm afraid that it was a little bit above my paygrade, though. Could you tell me what kind of file I save this code as, and then how to connect it to something on the desktop. I'm a linux noob, just moving over from an apple where I did a lot of stuff like this with apple-script, and I'm unclear on how to translate that stuff to the (to me new) ubuntu environment.

Cheers,
Bernhard.

---

### Post by Freelance Physicist on 2009-09-15
Essentially, kpkeerthi is showing you the beginnings of a BASH script, which you can think of as a list of commands to be executed.  Once you learn a few commands you can input into a terminal, you'll be ready for scripts.  Going by your first post, here's what I would do:

1) Open gedit (Applications -> Accessories -> Text Editor) and copy the following into the new file
```
#!/bin/bash

file="$(zenity --file-selection)" # the program zenity opens the file selection dialog so 
                                  # you can pick a file and assigns the full path name
                                  # to the variable 'file'

cd "$(dirname "$file")"        # change to the directory of the selected file

latexmk "$(basename "$file")"  # compile file with latexmk: 
                               # you can edit this line 
                               # with the options you need

read -s     # pauses the program until you press enter so you can examine the output

exit  # at the end of the program the terminal window will close
```

2) Save the file to your home folder.
3) Open your home folder from the Places menu.
4) Right-click on the file you just created and click on Properties.
5) Under the Permissions tab, check the box next to "Allow executing file as program"

To create Launcher:

6) Right-click anywhere on the desktop and click "Create Launcher..."
Under Type, select Application in Terminal
Write anything you want in Name and Comment
Click the Browse button and select the file you containing the code above.

Now you'll have an icon on your desktop that you can double click to choose a latex file to compile.

Download this pdf for a better introduction to bash scripting:
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)

---


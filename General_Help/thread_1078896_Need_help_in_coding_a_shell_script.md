---
title: "Need help in coding a shell script"
date: 2009-02-23
forum: General Help
---

### Post by HACKER1993 on 2009-02-23
I want to write a shell script and hoped i could get some help 

make a script to convert .txt to wav using text2wave but i would like prompts to ask the user for the name and location of the input txt file preferably in nautlis same with  the output file

would be greatful if some code was shown to point me in the right direction
can anyone help me because i am useless at shell scripts

Thanks HACKER1993

---

### Post by snova on 2009-02-23
You could use zenity. To get the input file, you could use:

[PHP]input_file="`zenity --file-selection`"[/PHP]

Zenity, with that option, will pop up a file selection dialog. When the user selects a file, it will print out its name- which is captured by the backticks and assigned to $input_file. It's quoted in case there is a space.

Similarly, Zenity can prompt for an output file:

[PHP]output_file="`zenity --file-selection --save`"[/PHP]

You might also want to question the user if they select a file that already exists, in which case, use the --confirm-overwrite option:

[PHP]output_file="`zenity --file-selection --save --confirm-overwrite`"[/PHP]

Zenity has many useful dialogs available.

---

### Post by HACKER1993 on 2009-02-24
How would I incorporate text2wave into the shell script e.g drag hi.txt on to a launcher on my desktop with the shell script loaded into the launcher then zenity pops up asks for input then where to save output

thank for your reply

---


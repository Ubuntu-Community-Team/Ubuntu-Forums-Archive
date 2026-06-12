---
title: "bash to give option"
date: 2009-04-15
forum: General Help
---

### Post by mrsmither on 2009-04-15
hi can anyone tel me how to either ask the user to input a letter in a textbox and have a if statment that goes alog the line of if the string is "r" then exicicute a command.Or just have a option box or two with a command.
all of this in a bash code.
a would prefer the second option if posible.

thanx in advance!
mr smither

---

### Post by silentrebel on 2009-04-15
If your script will be running from the terminal, and if the user can (in this application) enter his choice as the script is being activated, this solution would be best:
```
if [ $1 == "r" ]  # $1 designates the first argument
	<code>
fi
```
The user would have to use such syntax to activate the script from the terminal:
> script_name argument
Does anyone know how to implement *exactly *what *mr smither* is asking?

---

### Post by sedawk on 2009-04-15
bash doesn't have GUI elements like check boxes, radio boxes, buttons, etc.

For text-based "GUIs" you would have to implement something using ncurses
or you would have to use something like Tcl/Tk for "GUI-scripts".
(or use perl or python with some GUI library).

With bash you can read lines with the read command, e.g.
"read LINE" will read one line of input from keyboard into
variable LINE.
This can be evaluated like described in the script above.

---

### Post by silentrebel on 2009-04-15
> **sedawk said:**
> 
For text-based "GUIs" you would have to implement something using ncurses or you would have to use something like Tcl/Tk for "GUI-scripts". (or use perl or python with some GUI library).

If you are very attached to the idea of a dialogue box, follow the link below.  It is a learn-by-example wxPython tutorial for building such GUI structures.  I guess you could copy and paste the code that is closest to what you like and change it to fit your needs (fret not, Python is extraordinarily easier to read and understand than traditional programming languages).  You'll then be able to call your Python script from your Bash script.  

You'll have to learn a bit of Python to succeed in returning a value (such as the user's choice) to the Bash script from Python.

If their code does not work on your Ubuntu, you may have to download wxPython (there should be something in the repositories) (it isn't difficult).  I am pretty sure that Ubuntu comes installed with Python and wxPython libraries. 

[http://www.zetcode.com/wxpython/dialogs/](http://www.zetcode.com/wxpython/dialogs/)

---

### Post by kaibob on 2009-04-15
> **mrsmither said:**
> hi can anyone tel me how to either ask the user to input a letter in a textbox and have a if statment that goes alog the line of if the string is "r" then exicicute a command.Or just have a option box or two with a command. all of this in a bash code. a would prefer the second option if posible....

If you want a GUI, then zenity is one option. A zenity "List Dialog" appears closest to the "option box" that is your first preference.

[http://library.gnome.org/users/zenity/2.24/zenity.html](http://library.gnome.org/users/zenity/2.24/zenity.html)

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

As mentioned by sedawk, you may also want to consider a read command:

[http://linuxcommand.org/man_pages/read1.html](http://linuxcommand.org/man_pages/read1.html)

An example of a simple read command is:

```
#!/bin/bash

read -p "Enter response: " RESPONSE

if [ "$RESPONSE" = a ] ; then
	echo "You pressed the "a" key!"
elif [ "$RESPONSE" = b ] ; then
	echo "You pressed the "b" key!"
else
	echo "You did not press a valid key!"
fi
```

---

### Post by silentrebel on 2009-04-15
I'm asking out of curiosity for what the *-p* option is.  I'm not at home in front of my computer so I cannot check myself.

---

### Post by kaibob on 2009-04-15
From the Bash Reference Manual:

> -p prompt
Display prompt, without a trailing newline, before attempting to read any input. The prompt is displayed only if input is coming from a terminal. 

---

### Post by mrsmither on 2009-04-15
thanx so mutch i'v got it!!!!

---


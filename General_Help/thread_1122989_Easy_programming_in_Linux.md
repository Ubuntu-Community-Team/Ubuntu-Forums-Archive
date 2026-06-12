---
title: "Easy programming in Linux?"
date: 2009-04-11
forum: General Help
---

### Post by Blackdragon1400 on 2009-04-11
Hey guys, I'm kinda new to writing scripts so I dont know if if would be esier to use a programming language or not. What I would like to be able to do is prompt for a few vars. ex.
A="user defined imput"
B="user defined imput"
C="user defined imput"

these would receive user imput, and then the script would put these vars into a command line based application. So lets say we want to do one for "ls". My script would use the command "ls" as a base and the imput (lets just use one var for now) would be "A". For "A" as the imput the user would put something like "-l" or "-A". 

Can you see where I would like to go with this?

Thanks!

---

### Post by kaivalagi on 2009-04-11
Sounds like you should just stick with a shell based approach, using sh or bash would do it. It doesn't sound like there is any need to learn conventional programming languages to me, just shell scripting.

zenity would help with the GUI part of the process too...you should find it installed by default but if not "sudo apt-get install zenity" will get it installed

From "man zenity":

```
       zenity  is a program that will display GTK+ dialogs, and return (either
       in the return code, or on standard output) the users input. This allows
       you to present information, and ask for information from the user, from
       all manner of shell scripts.

       For example, zenity --question will return either 0 or 1, depending  on
       whether  the  user  pressed OK or Cancel. zenity --entry will output on
       standard output what the user typed into the text entry field.

```

Try this link to get you started with Zenity: [http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

If you do plan on start learning a language I would recommend Python...but that's just me, others will have there own opinions on this too. So wait for more responses and make your own choice :)

Have fun

---

### Post by ibuclaw on 2009-04-11
> **Blackdragon1400 said:**
> Can you see where I would like to go with this?

Not really. Could use describe the context of which you want to use it in?

An example of how you would like to run your script...along with the output it may produce as a result?

Regards
Iain

---

### Post by Blackdragon1400 on 2009-04-11
so (without time to play around with it yet) with zenity i could use the commands --Width --height --Title for the window. Do you know a good place to get some general info on the formats of scripts, like a general usage guide or something of that sort?

Also, how do you set something to run directly in a virtual terminal in a script?

---

### Post by kaivalagi on 2009-04-11
You need to do some googling and have a read...also there are plenty of shell scripts in your OS install which can help...you could look (**_not edit_**) at init (/etc/init.d/...) scripts for example....again search to find out more, google is your friend

Found this for example: [http://www.hsrl.rutgers.edu/ug/shell_help.html](http://www.hsrl.rutgers.edu/ug/shell_help.html)

---

### Post by Blackdragon1400 on 2009-04-11
Thanks alot!

---


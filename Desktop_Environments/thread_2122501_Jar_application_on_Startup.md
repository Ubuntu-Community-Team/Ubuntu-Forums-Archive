---
title: "Jar application on Startup"
date: 2013-03-05
forum: Desktop Environments
---

### Post by IJselflearner on 2013-03-05
Hi all,

I am trying to figure out how can I add a jar program to startup. I've tried installed application to run on startup, it worked out fine, but my jar application would not appear on start up.


Help please anyone.


Thanks in advance!

Fr: Ubuntu newbie

---

### Post by cortman on 2013-03-05
You may need to write a script that calls the jar-

```
[COLOR=#000000][FONT=Ubuntu Mono]java -jar /path/to/your/jar[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[FONT=trebuchet ms]Save the script in ~/bin, and add the script to your startup programs.[/FONT][/FONT][/COLOR]

---

### Post by IJselflearner on 2013-03-05
Hi cortman,

Thanks for the reply!
This is what I am looking for, in addition I need to make the script executable from the terminal command, ~# chmod 777 /bin/<the script>.

Thanks so much!

:D

---

### Post by slickymaster on 2013-03-05
The easiest way to run it would be to add it to the file **/etc/rc.local**. 

(Assuming the jar is in your home folder) Make a script like the following and save it in your home folder (let's call myapp.sh, for example):
```
#!/bin/sh
java -jar /your_home_folder/your_app.jar [optional arg if any]
```
Make it executable:
```
chmod u+x myapp.sh
./myapp.sh
```
So now you'll have to open **/etc/rc.local** to add a call to your script. In order to do it just run the following:
```
gksudo geany /etc/rc.local
```(You'll have to use the text pad you have installed on your computer)

And just before the line **exit 0**, add the the call to your script:
```
sh /your_home_folder/myapp.sh
```

---

### Post by IJselflearner on 2013-03-05
Hi slickymaster,

Thanks for the reply.
The first one worked, surely I will also try your solution.

Thanks! :D

---

### Post by cortman on 2013-03-05
Glad it's working- please mark the thread [SOLVED].
Good luck!

---

### Post by Morbius1 on 2013-03-05
I guess it depends on what this jar file does but can't you just add it to your start up applications:

Select the Dash thingy ( I'm a XFCE user sorry ) > Startup Applications > Add:
[ATTACH=CONFIG]239802[/ATTACH]
No need to make it executable.

---

### Post by IJselflearner on 2013-03-05
Hi All,

Thanks for your kindness.
Is it also possible to add a script that when I close the application user will automatically be logged off from the system?

Thanks so much!

-IJ-

---

### Post by cortman on 2013-03-05
> **IJselflearner said:**
> Hi All,

Thanks for your kindness.
Is it also possible to add a script that when I close the application user will automatically be logged off from the system?

Thanks so much!

-IJ-

It is possible, you'd have to run the script constantly, as a daemon. [Here's]("http://askubuntu.com/questions/264230/what-is-the-proper-way-to-logout-a-profile-when-a-certain-program-is-closed") maybe one idea.

---

### Post by IJselflearner on 2013-03-08
Hi cortman,

Thanks for the link.
By the way, here's what i added in the script and it worked, :D

gnome-session-quit --no-prompt

what it does is to automatically sign off the user upon closing the application.

Thanks so much.

---

### Post by cortman on 2013-03-08
> **IJselflearner said:**
> Hi cortman,

Thanks for the link.
By the way, here's what i added in the script and it worked, :D

gnome-session-quit --no-prompt

what it does is to automatically sign off the user upon closing the application.

Thanks so much.

Great, good for you for figuring it out! :)

---


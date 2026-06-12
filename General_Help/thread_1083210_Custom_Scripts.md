---
title: "Custom Scripts"
date: 2009-02-28
forum: General Help
---

### Post by mikedmor on 2009-02-28
I have made 2 custom script that i need to run when a program starts and another to run before/after my program closes. How would i go about doing this? here are the two codes:

Run when app starts:
```
sudo killall avant-window-navigator
killall compiz.real
xfwm4
```

Run before/after app closes:
```
engage -b 70707099 -R 1 -Z 2 -d 0.32 -i 1 -I 1 -T
```

i know it has something to do with pointing the shortcut to the file that has these commands. but i just dont know how to do this exactly.

thanks 

-mike

---

### Post by prinny42 on 2009-02-28
There might be a more elegant solution, but what I generally do is just combine them into one large script.  For instance, I might do like this:
```

#!/bin/bash
# blah - a script to blah

sudo killall avant-window-navigator
killall compiz.real
xfwm4
blahcommand
# this part below checks the exit status and, if it is zero
# (that is, if the program has ended successfully) it executes
# I'm not too sure of all the technical details, but it works
# for me
if [ "$?" = "0" ]; then
     engage -b 70707099 -R 1 -Z 2 -d 0.32 -i 1 -I 1 -T
fi
exit 0
```

---

### Post by mikedmor on 2009-02-28
ok so i would have this script start as soon as i start the app. and it would run in the background. as soon as the app closes it knows from the processes currently running and closes. So here is the question. what do i have to add to the end of my application shortcut to tell it to run this script, and how exactly do i need to fill out the:

```
if [ "$?" = "0" ]; then
```

part. im assuming that "$?" is where i would put the process but what is needed there exactly? is the $ needed to be there. and how would the process be formated. for an example lets say i want it to start when i run the Chess game. in the system monitor it list that as /usr/games/glch so would it look like

```
if [ "$/usr/games/glch" = "0" ]; then
```

Sorry if this is a noob question. im very new to linux. i actually found that code online, and im trying to get this to work when ever i start a wine game. the last post i submitted about this never got a reply.

---

### Post by prinny42 on 2009-03-01
I believe you can do it by doing something with launchers, but I don't know what it is and don't really like launchers, so I'm explaining the way I know, which is by putting it in a script.

But anyway, it's my fault for not being clear enough.  Let me elaborate.

The "$?" part just remains as it is; this refers to the environment variable of exit status.  When a program ends it sends an exit status (that's why the end of the script had "exit 0"); if it's zero, it was successful, and if it's any other number (usually one), it was unsuccessful.

You can see this illustrated with the commands "true" and "false," which do nothing but send an exit status of zero or one, respectively, and you can see the exit status of the last command with the command "echo $?".

But yeah, I generally use scripts to run games with Wine as well.  For instance, a game called *Perfect Cherry Blossom* changes my resolution to fit it when it runs, but doesn't change it back later.  Also, I always hate having to switch all the way to its directory to run it.  So I run it with this script, which I can use like any other command by simply typing its name:

```

#!/bin/bash
# th07 - a script to run Perfect Cherry Blossom and set the resolution back afterwards

cd "~/.wine/dosdevices/c:/Program Files/Perfect_Cherry_Blossom"
wine "~/.wine/dosdevices/c:/Program Files/Perfect_Cherry_Blossom/Th07.exe"
if [ "$?" = "0" ]; then
        xrandr -s 1024x768 -r 60
fi
exit 0

```

What that's saying is "change to the game's directory, execute the game with Wine, and if the exit status is zero (if the game ends), change the resolution to 1024x768 with a refresh rate of 60.  Then end successfully.

By the way, if you didn't know already, you should put scripts in ~/bin ("~" is an abbreviation for "/home/[user]").  If you don't already have it, just make the directory and restart your computer (so that bash can check for it).  And when you make a script, you should set its permissions when you're done; the most common way would be:

```
chmod 755 (script goes here without parentheses)
```

That would give you permission to do anything with the script, and everyone else permission to read it and execute it, but not to modify it.

So if I needed to run *Perfect Cherry Blossom* with the commands you're specifying, I would make a script like this in my home folder's bin:

```

#!/bin/bash
# th07 - a script to do some stuff, run Perfect Cherry Blossom, and do some other stuff

sudo killall avant-window-navigator
killall compiz.real
xfwm4
cd "~/.wine/dosdevices/c:/Program Files/Perfect_Cherry_Blossom"
wine "~/.wine/dosdevices/c:/Program Files/Perfect_Cherry_Blossom/Th07.exe"
if [ "$?" = "0" ]; then
     engage -b 70707099 -R 1 -Z 2 -d 0.32 -i 1 -I 1 -T
fi
exit 0
```

Then I would issue the command

```
chmod 755 th07
```

After that, I could run it anytime by just typing "th07" in the same way that I might type "gedit" or "vim".  Alternatively I could create a launcher for it by creating a launcher with the command "th07".

If you'd like to learn more about scripting, I would recommend [LinuxCommand]("http://www.linuxcommand.org/writing_shell_scripts.php") as a good starting point.

---

### Post by mikedmor on 2009-03-01
Thank you very much. i will give your way a shot. Also thanks for the website. im still trying to convert over to linux but i WAS a learning windows programmer, the switch has been a little difficult but im enjoying the process at the same time.

Let me clairfy one thing though. The script was named th07 when asked to save it. no extentions?

---

### Post by prinny42 on 2009-03-01
Indeed, just name it what you want the command that calls it to be.  In Linux, file extensions are for the convenience of humans and for the computer to know what program to default to when trying to use a file.  But ultimately, they don't matter; you could remove the extensions from all your .ogg files and they would still play as long as you specified what program to play them with, for instance.

---

### Post by mikedmor on 2009-03-01
ok one more question about this code

```
wine "~/.wine/dosdevices/c:/Program Files/Perfect_Cherry_Blossom/Th07.exe"
```

That part mine would look like this for counter-strike source

```
wine "~/.wine/dosdevices/c:/Program Files/Steam/steamapps/mikedmor/counter-strike source/Th07.exe"
```

but the Th07.exe file. does this mean that i save the code twice? once inside the bin folder in ~ and another time in that destination except with the extention .exe? or do i just need to point that to that directory and not do anything else?

---

### Post by prinny42 on 2009-03-01
Oh no, you need to direct it to the executable for the game you want to run.  It might be something like css.exe; it should be somewhere in the game's directory (although I don't know when it comes to Steam; I'm not exactly sure how it handles things).  Th07.exe is just the executable file for *Perfect Cherry Blossom*; it stands for **T**ou**h**ou **07**, the seventh game in the Touhou series.  Sorry about that.

---

### Post by mikedmor on 2009-03-01
oh! wait nevermind. i see what was going on. lol i missed that the first one cd'ed to the directory and the second one started was the game. ok i understand now. thanks alot!

---


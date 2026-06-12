---
title: "Automate a .sh script"
date: 2011-08-11
forum: Desktop Environments
---

### Post by Trubbelgum on 2011-08-11
Hi! I'm new here and I'm wondering how to automate a kind of script I have done (with .sh as file extension). The script is based on the features in scanmem. The problem is that the script doesn't continue after scanmem has opened and started (after this line):
```
sudo scanmem -p $(pidof plugin-container)
```I'm wondering what I shall add after this line, so the script can continue. Is there any simple way to do this?

Here is the script:
```
sudo apt-get install scanmem
y
sudo scanmem -p $(pidof plugin-container)
1154221576722516516
set 1154221576722319908
reset
-8778627313621546964
set -8778627313621683412
reset
-3734597221320194516
set -3734597221320325076
reset
-5247808792060906708
set -5247808792060852180
reset
-4094887278864124628
set -4094887278864318932
reset
-6688959624847440084
set -6688959624847260116
reset
290344280678655
set 290344117872383
reset
exit
Finnished!
```

If I do this manually, I can paste everything at the same time, and that works.
That I want, is a script that can do this automatically.

Thanks beforehand!

---

### Post by Trubbelgum on 2011-08-12
Maybe I have been a bit unclear. That I want, is to put some commands into a executable text file, which works exactly as if I had copied and pasted the text inside the file.

So I want to do a executable file containing this commands:
```
sudo apt-get install scanmem
sudo scanmem -p $(pidof plugin-container)
1154221576722516516
set 1154221576722319908
reset
-8778627313621546964
set -8778627313621683412
reset
-3734597221320194516
set -3734597221320325076
reset
-5247808792060906708
set -5247808792060852180
reset
-4094887278864124628
set -4094887278864318932
reset
-6688959624847440084
set -6688959624847260116
reset
290344280678655
set 290344117872383
reset
Finnished!
exit
```The problem is that a simple .sh-file containing the commands above, doesn't work as if I had copied-pasted the commands directly into the terminal.

---

### Post by ofnuts on 2011-08-12
> **Trubbelgum said:**
> Maybe I have been a bit unclear. That I want, is to put some commands into a executable text file, which works exactly as if I had copied and pasted the text inside the file.

So I want to do a executable file containing this commands:
```
sudo apt-get install scanmem
sudo scanmem -p $(pidof plugin-container)
1154221576722516516
set 1154221576722319908
reset
-8778627313621546964
set -8778627313621683412
reset
-3734597221320194516
set -3734597221320325076
reset
-5247808792060906708
set -5247808792060852180
reset
-4094887278864124628
set -4094887278864318932
reset
-6688959624847440084
set -6688959624847260116
reset
290344280678655
set 290344117872383
reset
Finnished!
exit
```The problem is that a simple .sh-file containing the commands above, doesn't work as if I had copied-pasted the commands directly into the terminal.

Your basic misunderstanding is that all programs your start just "read"  the script like they read the console. This isn't correct. Only one instance of the bash shell  reads it. You have to put your input to scanmem in a separate file (say, scanmem.cmds) (check access rights, if using through sudo) and give it to scanmem sing input redirection:

```

sudo scanmem -p $(pidof plugin-container) < scanmem.cmds

```

If you wan to keep all your scnamem commands in the script, you can use a "here document"  which is basically an input file made on-the-fly from the script contents when starting the command: see [http://www.gnu.org/software/bash/manual/bashref.html#Redirections](http://www.gnu.org/software/bash/manual/bashref.html#Redirections)

---

### Post by Trubbelgum on 2011-08-12
Thank you very much ofnuts! Your post was so helpful!

I did the script like this now:
```
sudo apt-get install scanmem
sudo scanmem -p $(pidof plugin-container) <<[-]word
1154221576722516516
set 1154221576722319908
reset
-8778627313621546964
set -8778627313621683412
reset
-3734597221320194516
set -3734597221320325076
reset
-5247808792060906708
set -5247808792060852180
reset
-4094887278864124628
set -4094887278864318932
reset
-6688959624847440084
set -6688959624847260116
reset
290344280678655
set 290344117872383
reset
Finnished! 
exit
delimiter

```

---

### Post by ofnuts on 2011-08-12
> **Trubbelgum said:**
> Thank you very much ofnuts! Your post was so helpful!

I did the script like this now:
```
sudo apt-get install scanmem
sudo scanmem -p $(pidof plugin-container) <<[-]word
...
290344280678655
set 290344117872383
reset
Finnished! 
exit
delimiter

```

Will not work that way... 

The redirection is either "<<" or "<<-" (this is what the [] indicates) and although it's not too clear in the referenced doc, the string immediately after is arbitrary (but it shouldn't appear in the input) and shoul dbe used to mark the end of the input lines, where your script continues.  So you code should look more like:

```
sudo apt-get install scanmem
sudo scanmem -p $(pidof plugin-container) **[SIZE=4]*[COLOR=Red]<< x_x_x[/COLOR]*[/SIZE]**
1154221576722516516
set 1154221576722319908
reset
-8778627313621546964
set -8778627313621683412
reset
-3734597221320194516
set -3734597221320325076
reset
-5247808792060906708
set -5247808792060852180
reset
-4094887278864124628
set -4094887278864318932
reset
-6688959624847440084
set -6688959624847260116
reset
290344280678655
set 290344117872383
reset
**[SIZE=4]*[COLOR=Red]x_x_x[/COLOR]*[/SIZE]**
echo Done! 
exit

```

Btw, I don't see the purpose of  installing scanmem each time.

---

### Post by Trubbelgum on 2011-08-13
> **ofnuts said:**
> Will not work that way... 
Actually it did worked that way (Maybe it won't work on all ubuntu's though)
But I've changed it as you said, so the script will be more compatible.

I have one more question, though. Is there any way to do a "5 seconds delay" between two commands? I'd like xmacro to start arround 5 seconds after that firefox have started.

```

firefox file:///home/a/Documents/XXX.htm
***-- I want a 5 seconds delay here --***
cat ~/Documents/PR2/Script/X.macro| xmacroplay -d 100 :1
sudo scanmem -p $(pidof plugin-container) << START/STOP
...
START/STOP
Finnished!

```

---

### Post by ofnuts on 2011-08-13
> **Trubbelgum said:**
> Actually it did worked that way (Maybe it won't work on all ubuntu's though)
But I've changed it as you said, so the script will be more compatible.

I have one more question, though. Is there any way to do a "5 seconds delay" between two commands? I'd like xmacro to start arround 5 seconds after that firefox have started.

```

firefox file:///home/a/Documents/XXX.htm
***-- I want a 5 seconds delay here --***
cat ~/Documents/PR2/Script/X.macro| xmacroplay -d 100 :1
sudo scanmem -p $(pidof plugin-container) << START/STOP
...
START/STOP
Finnished!

```

There is  a "sleep" command: sleep 5

---

### Post by Trubbelgum on 2011-08-14
> **ofnuts said:**
> There is  a "sleep" command: sleep 5
Thanks! 

I have one question more and I hope this is my final too. When I start firefox from the terminal, I can't enter other commands before firefox has been closed again. 

```
firefox file:///home/a/Documents/XXX.htm       **//The script can't continue after this**
sleep 5
echo Delay 5 MotionNotify 400 400 ButtonPress 1 ButtonRelease 1 | xmacroplay -d 100 :0
sudo scanmem -p $(pidof plugin-container) << START/STOP
...
START/STOP
Finnished!
```Any ideas?

---

### Post by ofnuts on 2011-08-14
> **Trubbelgum said:**
> Thanks! 

I have one question more and I hope this is my final too. When I start firefox from the terminal, I can't enter other commands before firefox has been closed again. 

```
firefox file:///home/a/Documents/XXX.htm       **//The script can't continue after this**
sleep 5
echo Delay 5 MotionNotify 400 400 ButtonPress 1 ButtonRelease 1 | xmacroplay -d 100 :0
sudo scanmem -p $(pidof plugin-container) << START/STOP
...
START/STOP
Finnished!
```Any ideas?
Standard answer: postfix the command with "&", that will "detach" it and the parent process can continue:
```

firefox &

```
If that starts the whole firefox (no other FF windows already up, and if this makes you code wait it is likely the case) this can make your FF process a child of your terminal window, and it will be killed without warning when you close the terminal window, including other FF windows you started....

So the real answer is to start Firefox as a desktop application so that its parent is the desktop. If running KDE use 
```

kstart firefox&

```

There is likely a Gnome equivalent to this.

---

### Post by Trubbelgum on 2011-08-15
Thanks for all help ofnuts! I have finnished my script now.

```
sudo apt-get install scanmem
sudo apt-get install xmacro
kstart firefox http://www.xxq.site40.net/pr2/ &
echo Delay 10 MotionNotify 400 400 ButtonPress 1 ButtonRelease 1 MotionNotify 400 400 ButtonPress 1 ButtonRelease 1 | xmacroplay -d 100 :1 &
echo Delay 10 MotionNotify 400 400 ButtonPress 1 ButtonRelease 1 MotionNotify 400 400 ButtonPress 1 ButtonRelease 1 | xmacroplay -d 100 :0
sudo scanmem -p $(pidof plugin-container) << START/STOP
1154221576722516516
set 1154221576722319908
reset
-8778627313621546964
set -8778627313621683412
reset
-3734597221320194516
set -3734597221320325076
reset
-5247808792060906708
set -5247808792060852180
reset
-4094887278864124628
set -4094887278864318932
reset
-6688959624847440084
set -6688959624847260116
reset
290344280678655
set 290344117872383
reset
exit
START/STOP
echo MotionNotify 520 540 ButtonPress 1 ButtonRelease 1 | xmacroplay :0
Finnished!
```

---


---
title: "Create a launcher for a shell program"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Locomotion on 2006-10-04
Hello!
In the first place, sorry about my english, but its not my 1st language! :D
This is my 3rd day in linux


So, I'm hosting a Shoutcast Server.
And everytime I reboot the computer, I need to go to console and type: 

> cd Shoutcast\ Streamer
./sc_trans_linux
[IMG]http://img175.imageshack.us/img175/1636/streameroe3.png[/IMG]


And than, another console with:

> cd Shoutcast\ Server
./sc_serv
[IMG]http://img175.imageshack.us/img175/2549/serverjr3.png[/IMG]


Both programs need to stay open!

So here is the problem, I can't create a "shortcut" to a shell program!
If I go to "Create Launcher" and try to make a normal shortcut, all I get when I open is a shell that open and close.
Even adding the option "execute in terminal" I still getting this problem.

The big question is: How to create a shortcut to a shell program that need to execute a code and STAY open?



**EDIT:** And just another question... I want to create a program, with 2 buttons, START APACHE, and CLOSE APACHE, just to see how is the linux programing.

I wont ask how to make this program, but I will ask what I should search in Internet! Like what programs, what language, anything...

And I have a little experience with Vbasic and Delphi.

---

### Post by Kateikyoushi on 2006-10-04
You could create a startup script and put it in/etc/init.d/ symlinking it to a runlevel.

---

### Post by Locomotion on 2006-10-04
But it would run in background or i will see the shells?

It will be better if I can see it :P

---

### Post by kwalo on 2006-10-04
The terminal gets closed, because the program, that runs in it had exited, so what you need is a terminal emulator, that stays open after the it's child exits.

Xfce4-terminal has an --hold option which doesn't destroy terminal, when child process exits. I did't see that option in gnome-terminal, so you should install xfce4-terminal, or any terminal, that supports --hold option (maybe Eterm ?)

1. Create a launcher for a xfce4-terminal program (or any terminal you like).
2. Right click on Properties of that launcher.
3. Change command from```
xfce4-terminal
```to something like```
xfce4-terminal --hold -x command_you_want_to_run
```

Now you see terminal, even if process , that was running inside it exited.

If you start your shoutcast server every time you log in, maybe you should add commands that start it to your session. In GNOME go to System->Preferences->Sessions. Click 'Startup Programs' tab and add commands, that run your server. You won't be able to see how they run, but, the'll run as long, as you're logged in. You can run xfce4-terminal in session, which will run your commands and hold.

---

### Post by Locomotion on 2006-10-04
hm, it only works if i go to console and type
[B]
cd Shoutcast\ Streamer[/B]

question: how can I add this to my launcher?, i mean, i want a launcher with 2 lines:

[B]
cd Shoutcast\ Streamer
xfce4-terminal --hold -x ./sc_trans_linux[/B]

[B]
EDIT:[/B]
Aff, this is very weird ](*,) 

If I type:

> cd Shoutcast\ Streamer
xfce4-terminal --hold -x ./sc_trans_linux

in a terminal.
It works.

But how can I create a launcher with 2 lines?

**EDIT2:** Can I create a shell shortcut? Like if I type **shoutcast_streamer**, it would be the same thing for

> cd Shoutcast\ Streamer
./sc_trans_linux

So I could create a launcher for **shoutcast_streamer**

---

### Post by aidanr on 2006-10-04
xfce4-terminal --hold -x "~/Shoutcast\ Streamer/sc_trans_linux"

should do it

---

### Post by Locomotion on 2006-10-04
my problem is simply

I created a file.sh
> #!/bin/sh

echo "Hello, world."

If I execute this in console, I will get a Hello, world message.
But if I execute by double clicking and choosing to execute in terminal, I terminal will open and close.

This is the same "problem" I have with the launcher.
So, will be the same solution.

**BIG QUESTION:** What I need to do, to when I execute the file.sh I get a terminal with a hello world message, not a blank terminal closing?

---

### Post by axial_net on 2006-10-04
I believe that your problem is that the terminal is closing as soon as the program has finished executing.  To see your "file.sh" script in your terminal window you may wish to change it to:

[INDENT]#!/bin/sh

echo "Hello, world."
sleep 5[/INDENT]

What is most likely preventing your "ShoutCast Streamer" script from running is that the terminal opens in the wrong directory.  This causes the launched program to fail and then exit (causing the terminal to close).

To get it to run you could create a script that changes to the correct directory, then runs the "ShoutCast Streamer" program.  Lets call the script "run-shoutcast.sh"

[INDENT]#!/bin/sh
cd ~/Shoutcast\ Streamer
./sc_trans_linux
[/INDENT]

Then make sure the "run-shoutcast.sh" script is executable:

[INDENT]chmod 755 run-shoutcast.sh[/INDENT]

Once you have done that you can go to "Create Launcher" and set the "Command" to 'ruh-shoutcast.sh' and select the option "execute in terminal".  I think that should have the desired effect.

As for your question regarding creating a program that could have both a start and a stop button for apache, it could be written in C, Perl, Python, Mono, and probably many other things.

I hope that helps.

---

### Post by axial_net on 2006-10-04
Your question regarding a "shell shortcut" is probably best answered by the "[functions]("http://tldp.org/LDP/abs/html/functions.html")" and "[aliases]("http://tldp.org/LDP/abs/html/aliases.html")" chapters in the [Advanced Bash Scripting Guide]("http://tldp.org/LDP/abs/html/").

---

### Post by Locomotion on 2006-10-04
1st of all, thanks =]

I want to make 3 shorcuts
1 for shoutcast server, other for shoutcast streamer and other for no-ip

The shoutcast streamer is OK, I did almost like you said, i created a **streamer.sh** with:
> #!/bin/sh

cd  /home/locomotion/Shoutcast\ Streamer
./sc_trans_linux

CHMOD to executable, and I can run normally

But the shoutcast server did not work.
server.sh
> #!/bin/sh

cd /home/locomotion/Shoutcast\ Server
./sc_serv

When I try to open (after chmod) i'm getting the same problem, it open a blank terminal and it close.
the strange thing is:
If i type this in a terminal, it works! But if I put in server.sh and try t o open, it doesnt work

Same thing with noip.sh
If i type **no-ip -c** in terminal, i get a message
But if I make a no-ip.sh it doesnt work

**[SIZE="4"][COLOR="Red"]BIG EDIT:[/COLOR][/SIZE]** I downloaded XFCE4-TERMINAL, and selected to open those files with it, now server.sh and streamer.sh are working, but no-ip.sh is not

---

### Post by Locomotion on 2006-10-04
and **axial_net**

do you recommend any IDE for start programing? :cool:

---

### Post by axial_net on 2006-10-05
In terms of IDE on linux, many peole like [eclipse]("http://www.eclipse.org"), although others prefer  [Emacs]("http://www.gnu.org/software/texinfo/manual/texinfo/emacs.html") as it is more flexible (but it's not really an IDE).  There is also [J-Builder]("http://www.borland.com/us/products/jbuilder/index.html") for java programs.  But I'm the worst person to ask as I write almost everything with cat.

In terms of your scripts not running, probably the best way to test them is to run the scripts within terminals to see if they produce an error.  In the terminal window you would run either:

> ./no-ip.sh

or

> /home/locomotion/no-ip.sh

(or whatever the full path to the script is).

With your "no-ip.sh" script you might want to add the line "sleep 10" to the end of it, this way it should pause for 10 seconds before finishing.  That way you should see any error messages that appear when launching it from an icon in Gnome.

---

### Post by kwalo on 2006-10-05
> **axial_net said:**
> I write almost everything with cat.Sorry for going off-topic, but cat is used for reading files. It prints to stdout. How can you write with that? Maybe you're using some other cat program?

---


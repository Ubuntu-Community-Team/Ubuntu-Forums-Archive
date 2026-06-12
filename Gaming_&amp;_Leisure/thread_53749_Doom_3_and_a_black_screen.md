---
title: "Doom 3 and a black screen"
date: 2005-08-02
forum: Gaming &amp; Leisure
---

### Post by umdzig on 2005-08-02
I installed doom 3 (finally) and i start it and all i get is a black screen that i cant get out of and i am forced to press <ctrl> <alt> backspace. Kind of reminds of windows...blah. I have the updated driver for my at radeon 9600 graphics card. Any help?

---

### Post by Mishura on 2005-08-02
Do this... run Doom3 from a terminal such as Konsole or Gnome Terminal.  When doom3 does the same thing, hit <CTRL> <ALT> <F2>, login and type:

killall doom3.x86

or "killall doom3"

Hit <CTRL> <ALT> <F7> to get back to your desktop.  Post the output of your terminal (The one you used to launch Doom3) here.

Also, post what kind of ATi drivers you have, whether they are the commercial or Fglx (or whatever they're called) drivers.

Note, that I can't help you if its a ATi problem, since I've never used those cards (Nvidia man), but if its a doom3 issue, then thats more up my alley.

---

### Post by umdzig on 2005-08-02
I tried what you said to do, however the killall doom3.x86 and doom3 was not the correct command to kill the app. I have the demo version and i cant figure out how to kill the app to finish what you said to do.

---

### Post by Mishura on 2005-08-02
Do a "ps -A | more" instead, and look through the list of processes.  I remember now that the demo wasn't doom3 (more like doom3-demo) but I can't remember off-hand what it is.  When you find the correct process name, kill that instead.  Also:

killall **-9** process

works too, but I can't figure out what the -9 does, other than that I read about that somewhere..

---

### Post by Mishura on 2005-08-02
Upon reading deeper into this forum, I notice that you are not the first person with this problem.

[http://ubuntuforums.org/showthread.php?t=53347](http://ubuntuforums.org/showthread.php?t=53347)

---

### Post by endy on 2005-08-02
```

       Signal     Value     Action   Comment
       -------------------------------------------------------------------------
       SIGHUP        1       Term    Hangup detected on controlling terminal
                                     or death of controlling process
       SIGINT        2       Term    Interrupt from keyboard
       SIGQUIT       3       Core    Quit from keyboard
       SIGILL        4       Core    Illegal Instruction
       SIGABRT       6       Core    Abort signal from abort(3)
       SIGFPE        8       Core    Floating point exception
       **SIGKILL       9       Term    Kill signal**
       SIGSEGV      11       Core    Invalid memory reference
       SIGPIPE      13       Term    Broken pipe: write to pipe with no readers
       SIGALRM      14       Term    Timer signal from alarm(2)
       SIGTERM      15       Term    Termination signal
       SIGUSR1   30,10,16    Term    User-defined signal 1
       SIGUSR2   31,12,17    Term    User-defined signal 2
       SIGCHLD   20,17,18    Ign     Child stopped or terminated
       SIGCONT   19,18,25            Continue if stopped
       SIGSTOP   17,19,23    Stop    Stop process
       SIGTSTP   18,20,24    Stop    Stop typed at tty
       SIGTTIN   21,21,26    Stop    tty input for background process
       SIGTTOU   22,22,27    Stop    tty output for background process

```

Taken from "man signal" :D


EDIT: Actually the kill manual page probably has a more relevent description, type "man kill" for more information :)

---

### Post by umdzig on 2005-08-03
typing killall doom3-demo does not kill the app. I am still left with doing the <ctrl><alt><backspace>. any ideas on how to figure what the correct process name is so i can kill it? I use doom3-demo to start it but that will not kill it.

---

### Post by Mishura on 2005-08-04
Did you read post #5 on this thread and click the link?  Does that pertain to you?  I'm not sure since I don't have your computer specs. (Note:  read my sig for an example.)

If not, I could grab the demo and find out myself, how to kill it.  The console output of Doom3 would help alot more, since just your explaination alone doesn't really tell me anything.  :???: 

If anyone knows how to get the console output for Doom 3 a different way (Mine's a hack),  let us know.

---

### Post by Mr_J_ on 2005-08-04
try out a combo of these commands!
**ps**

and

**grep**

you can do this using the **|**

like

**#ps -aux | grep *doom***

Ctrl+Alt+[F1]...[F7] are ur, normal shells, which I'm non too sure of the number, so just go from [F1] and [F7] should be your normal GUI...

To get more help on ur commands, you can use [(command) --help] or [Man (command)] to get a detailed explanation on the **Man**ual...
Also! I find this one usefull if I can't remember the full name of a command...
Just
$A
then hit **Tab **twice and it should show all commands starting with the letter A. If you use more letters it will restrain to those beggining letters!




[SIZE=2]If you want to get more knowledge on the linux shell commands I really recomend an O'Reilly book on Linux Shell commands, which I believe is called Linux... It's pocket sized and; to my liking; a concentrated version of those bigger more bloated books on shell commands![/SIZE] :grin: I got one! \\:D/

---

### Post by Mishura on 2005-08-04
> **Mr_J_]try out a combo of these commands!
**ps**

and

**grep**

you can do this using the **|**

like

**#ps -aux | grep *doom***

Ctrl+Alt+[F1]...[F7] are ur, normal shells, which I'm non too sure of the number, so just go from [F1] and [F7] should be your normal GUI...

To get more help on ur commands, you can use [(command) --help] or [Man (command)] to get a detailed explanation on the **Man**ual...
Also! I find this one usefull if I can't remember the full name of a command...
Just
$A
then hit **Tab **twice and it should show all commands starting with the letter A. If you use more letters it will restrain to those beggining letters!




[SIZE=2]If you want to get more knowledge on the linux shell commands I really recomend an O'Reilly book on Linux Shell commands, which I believe is called Linux... It's pocket sized and said:**
>  :grin: I got one! \\:D/

Niiiice.  I didn't know some of those.

Also, on most distros that I used (Suse, Mepis, Fedora and Kubuntu).. [CTRL] + [ALT] + [F7] will bring you back to your GUI.  F1-F6 are consoles.  F1 is the console that you see when you boot up.  These are VERY useful.  (Like, play a game and switch over to another console, run mpg321 on a directory of MP3s or ogg123 on a directory of Ogg vorbis files.  CTRL+C to switch tracks.  Very fun, and very very lightweight.  These players will not suck up resources like amaroK or even Xmms will!)

---


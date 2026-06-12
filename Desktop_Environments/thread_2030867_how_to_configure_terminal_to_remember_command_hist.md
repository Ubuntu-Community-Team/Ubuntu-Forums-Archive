---
title: "how to configure terminal to remember command history from previous session."
date: 2012-07-21
forum: Desktop Environments
---

### Post by GwibberFooey on 2012-07-21
For example: Yesterday I run command 

mplayer -playlist /home/foo/SongsList.ascii -shuffle

but eventually I turn off the computer.  Today I restart the computer and I want to run the same command. But I don't want to retype the command.  

In previous versions of Ubuntu I could open Terminal and simply press the Up arrow key and the most recent command would appear.  But in Ubuntu 12.04 Terminal can not recall the last command from previous session.  

How can it be reconfigured to recall commands from previous sessions ?

---

### Post by dcsoldschool53 on 2012-07-21
> **GwibberFooey said:**
> For example: Yesterday I run command 

mplayer -playlist /home/foo/SongsList.ascii -shuffle

but eventually I turn off the computer.  Today I restart the computer and I want to run the same command. But I don't want to retype the command.  

In previous versions of Ubuntu I could open Terminal and simply press the Up arrow key and the most recent command would appear.  But in Ubuntu 12.04 Terminal can not recall the last command from previous session.  

How can it be reconfigured to recall commands from previous sessions ?

Open a terminal, click Edit > Profile Preferences > Scrolling.  What are your setting, set to in there?

---

### Post by sudodus on 2012-07-21
> **GwibberFooey said:**
> In previous versions of Ubuntu I could open Terminal and simply press the Up arrow key and the most recent command would appear.  But in Ubuntu 12.04 Terminal can not recall the last command from previous session.  

The command history is available as you describe in my installations of [LX]Ubuntu. It should be running directly without any tweaking. Have you changed anything?

---

### Post by kibaya on 2012-07-21
> **GwibberFooey said:**
> For example: Yesterday I run command 

mplayer -playlist /home/foo/SongsList.ascii -shuffle

but eventually I turn off the computer.  Today I restart the computer and I want to run the same command. But I don't want to retype the command.  

In previous versions of Ubuntu I could open Terminal and simply press the Up arrow key and the most recent command would appear.  But in Ubuntu 12.04 Terminal can not recall the last command from previous session.  

How can it be reconfigured to recall commands from previous sessions ?



You can create a launcher on the desktop instead if you run that command often and even put it on the start up list so that you don't have to run it at all

---

### Post by GwibberFooey on 2012-07-23
Hi. Thanks for the responses.  I use Ubuntu 12.04. And I opted to use Gnome Classic desktop so that I could avoid Unity desktop.  In terminal, the "Default" profile has the following configuration:  
Scrollbar is: On the right side
Scrollback: 512; lines
Scroll on output: NO
Scroll on keystroke: YES
Use keystrokes to scroll on alternate screen: YES

I would still like to have the ability to retain command history  in Terminal from previous sessions.

---

### Post by sudodus on 2012-07-23
I don't understand. It should work by default :confused:

- What happens when you run the terminal command ```
history
```

It lists 506 commands for me (including old commands).

- What happens when you close a terminal window and open a new one without logging out? Will it remember the history?

- What happens when you close the terminal window, log out, log in again without rebooting? Will the history survive?

- And finally, what happens when you close the terminal window, and reboot the computer? Will the history survive?

- Does it make a difference if you close the terminal window in a nice manual way (for example with the command exit), or if you reboot with the terminal window open? (I think it should not make a difference, the history should be preserved.)

---

### Post by asmoore82 on 2012-07-23
+1 for the `history` command, also...

It's the BASH shell itself and not any particular terminal app that remembers the history for you.

It's a simple hidden text file ".bash_history" in your $HOME directory.

double check permissions and then check BASH history settings...

```
ls -ld $HOME
ls -l $HOME/.bash_history
shopt | grep hist
echo $HISTFILE
echo $HISTCONROL
```

as soon as you get your history working again, you can fall in love with ctrl+r :D.

---

### Post by GwibberFooey on 2012-07-23
Every time I close Terminal it looses the command history. This is true regardless if I type "exit" or press "Ctrl + D " or is I use the mouse to click on the "X" at the top of the window, or if I press "Alt + F4" or if I shut down the whole machine.

If I close the terminal window, log out, log in again without rebooting then the command history does not survive.

And if I close the terminal window, and reboot the computer then the command history does not survive.

When I run the terminal command "history" then it lists all commands that occurred since the current terminal window was opened but none from any previous Terminal window.  

The following is a printout of the commands and their output that you (@ asmoore82) listed 

foo@computer:~$ ls -ld $HOME
drwxr-xr-x 31 foo foo 4096 Jul 23 14:51 /home/foo
foo@computer:~$ ls -l ~/.bash_history
-rw------- 1 root root 13 May 23 20:37 /home/foo/.bash_history
foo@computer:~$ shopt | grep hist
cmdhist            on
histappend         on
histreedit         off
histverify         off
lithist            off
foo@computer:~$ echo $HISTFILE
/home/foo/.bash_history
foo@computer:~$ echo $HISTCONTROL
ignoreboth


I looked at the file ~/.bash_history and it consisted of just two lines:
drivers
exit


Basically, what I would like to accomplish is to have the ability to retain command history in Terminal from previous sessions.

---

### Post by oldfred on 2012-07-23
It looks like root took over your bash file.

```
fred@fred-Precise:~$  ls -l ~/.bash_history
-rw------- 1 fred fred 18316 Jul 23 18:44 /home/fred/.bash_history
fred@fred-Precise:~$ echo $HISTCONTROL
ignoredups:ignorespace
fred@fred-Precise:~$ 

```

Which then leads to a question of how did it get changed and are other files in /home owned by root?

sudo chown $USER:$USER ~/.bash_history

---

### Post by GwibberFooey on 2012-07-24
Thanks oldfred. Because of the command "sudo chown $USER:$USER ~/.bash_history", I can now recall the command history from previous Terminal sessions.

---

### Post by Lucutus of Borg on 2012-07-24
> **dcsoldschool53 said:**
> Open a terminal, click Edit > Profile Preferences > Scrolling.  What are your setting, set to in there?
Hi

Try to open your terminal, click Edit > Profile Preferences > Scrolling >  Scrollback....
I typically select "Unlimited".

To see your history, type "history" in terminal. Just remember though, when you issue a command in sudo, you will see sudo history and if you drop out of sudo, you will see your user mode history :-)

Lucutus of Borg

---


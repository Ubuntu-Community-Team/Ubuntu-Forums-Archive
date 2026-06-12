---
title: "I need help writing a script to launch a server inside tmux &lt;3"
date: 2020-08-22
forum: Gaming &amp; Leisure
---

### Post by cosmic2910 on 2020-08-22
He guys, i'm an admin/owner of a local hosted server, hosting 2 LinuxGSM servers one csgo and one Minecraft, then a modded minecraft 1.12.2 server, not with linuxGSM. i don't want all the servers to be launched at once i was looking for a way to run a sh bash file that would launch tmux as the servers user . then run the start command which for the gsm servers is "./mcserver start" and "./csgoserver start" . and then the launch parameters for the modded minecraft server is "java -Xms8G -Xmx8g -jar forge-1.12.2-14.23.5.2854.jar --port 25567 nogui" . if anyone knows how to make a good script for both starting and stopping each server individually in separate tmux session. 

I'd appreciate any help, advice or concerns <3 
thanks guy

---

### Post by TheFu on 2020-08-22
Take everything you are typing and put those commands into a file.  That is a script.

Do that as your first draft.  Does it work?

Creating a "good script" s highly subjective. It takes years to get good at scripting.  Really, most scripts just need to be good enough, no more.
There are hundreds of example scripts on your Linux computer already, if you need examples to follow.

The "Beginning Bash Scripting Guide" and "Advanced Bash Scripting Guide" are worth a quick look too.

I don't think tmux has anything to do with the script. I don't use tmux.

---

### Post by cosmic2910 on 2020-08-23
the problem is getting the script to work, i know how to make the bash script, but every script i make doesn't work XD and i can log into tmux with as the server's user but i can't run any commands in tmux from the script

---

### Post by TheFu on 2020-08-23
> **cosmic2910 said:**
> the problem is getting the script to work, i know how to make the bash script, but every script i make doesn't work XD and i can log into tmux with as the server's user but i can't run any commands in tmux from the script

Please post the script, if you'd like help.
Also, show the **ls -l **for that script file.

Any please, please, please, please, use code tags. Otherwise, it will be too hard to read, so few people will.

---

### Post by mastablasta on 2020-08-24
from [https://minecraft.gamepedia.com/Tutorials/Setting_up_a_server](https://minecraft.gamepedia.com/Tutorials/Setting_up_a_server)
> [h=4]On macOS, Linux, and FreeBSD[/h][FONT=&quot]All these systems use a common scripting language called the "POSIX shell script" on the command line. Create a text file in the folder where you put the jar as "start.sh" and write the following in:[/FONT]
```
[FONT=&quot][COLOR=#408080]*#!/bin/sh*[/COLOR]
[COLOR=#008000]cd[/COLOR] [COLOR=#BA2121]"[/COLOR][COLOR=#008000]**$(**[/COLOR]dirname [COLOR=#BA2121]"[/COLOR][COLOR=#19177C]$0[/COLOR][COLOR=#BA2121]"[/COLOR][COLOR=#008000]**)**[/COLOR][COLOR=#BA2121]"[/COLOR]
[COLOR=#008000]exec[/COLOR] java -Xms1G -Xmx1G -jar server.jar --nogui
[/FONT]

```[FONT=&quot]Now save the file. Run chmod a+x start.sh (or path to wherever you put the script) to make it executable. You can now run the file by double-clicking or by running ./start.sh in the folder (or using a whole path from outside there).[/FONT]
[FONT=&quot]If you want to add a pausing part like the Windows example, remove the [/FONT][FONT=&quot]exec[/FONT][FONT=&quot] word, and add a line of [/FONT][FONT=&quot]read -n 1 -p "Waiting..."[/FONT][FONT=&quot] to the end. This is useful if you are running the script by double-clicking on the GUI[/FONT]

then you can install screen to run it in background. or to run multiple servers in background at the same time.

---


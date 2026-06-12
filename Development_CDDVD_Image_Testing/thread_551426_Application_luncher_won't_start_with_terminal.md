---
title: "Application luncher won't start with terminal"
date: 2007-09-15
forum: Development CD/DVD Image Testing
---

### Post by pPrdrm on 2007-09-15
[COLOR="White"]__[/COLOR]I've made a luncher at my desktop for a program (**blender**). I haven't installed the one in the repositories. What I did is I've downloaded the  **tar.bz2** file from blender's site, extract it in my home folder and made a luncher for it at my Desktop. If i choose to start it as an application it works fine, but if I choose to start it with a terminal it gives me a message "**... -x" (No such file or directory)**". Also if I open a terminal first and then execute **blender** from there it also works O.K.. **Blender** gives information in the terminal from which it was executed, so running it without one is not an option.
[COLOR="White"]___[/COLOR]I don't know if this has something to do with it, but I am running **Gutsy Gibbon** from an external USB hard drive. I have also installed all the latest updates. Has anyone came across with something like this?

---

### Post by cadamr on 2007-09-18
I'm having a similar problem. Just recently all launchers using the option to launch "application in terminal" have stopped working. I click the launcher but nothing happens. I can start a terminal and run the script manually and everything works fine. I think they stopped working after I installed compiz fusion, but switching to metacity doesn't help. I'm using feisty.

---

### Post by pPrdrm on 2007-09-19
Hi Cadamr,

I don't thing that it has something to do with compiz fusion because I also have it installed in my Feisty and works fine. It doesn't work though in Gutsy Gibbon.  For now, what works for me is to make a text file with the command line that I use in order to execute my program, right click on it &#8594; Properties &#8594; and on the Permissions tab I check "Execute" To allow a file to be run as a program. Then in a Nautilus window I choose Edit &#8594; Preferences &#8594; Behavior and at Executable text files I select "Ask each time". Then I click on the text file containing the command line and at the dialog that appears I choose "Run in Terminal". It's an extra step but it works as a workaround.

---

### Post by cadamr on 2007-09-20
Thinks for the workaround idea. 

I looked at your post a little closer, and it looks like you just mixed up some options in the command. What is the exact command you are using in the launcher?

---

### Post by pPrdrm on 2007-09-21
The command I use is this: "**/home/user/.blender-2.44/blender -w -p 0 25 1270 945**". The **-w** option is to have blender windowed and the **-p 0 25 1270** option is to make the window appear with a fixed size and position (By the way, I want it to start maximized but I don't know if there is an option for that. That's why I use the **-p** one.). When I choose to start it as an app it works O.K.. If I choose to start it with a terminal that's when the message appears with this **-x **option (or whatever it is). I don't use a **-x** in my command. I think that this** -x** must have something to do with the terminal.

---

### Post by pPrdrm on 2007-10-02
I don't know what is happening but this problem also appeared in my Feisty partition. It was working fine and suddenly the error message came up. But I've found this thread: [[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=561610&highlight=launcher+problem[/COLOR]]("http://ubuntuforums.org/showthread.php?t=561610&highlight=launcher+problem") and it gave me the solution. It looks like something happened in the program that creates the launchers and it doesn't give the correct command anymore. If only someone knew what causes it and how to fix this...:-(
Anyway, because this is just a workaround should I mark this thread as solved or not?

---

### Post by pPrdrm on 2007-10-02
I think I've found out what was the problem. That **-x** that was appearing in the command line was what was bothering me. Looking at my **System -> Preferences -> Preferred Applications** in the **System** tab I noticed in the **Execute flag** field there was a **-x** option in it. I erased it and **Bingo!!!**. Problem solved! It works for both new and old launchers.

---

### Post by cadamr on 2007-10-09
pPrdrm, you're comment lead me in the right direction. It seems like the problem is with my gnome-terminal. Like you said, the "application in terminal" launcher uses the "gnome-terminal -x" command by default. when I execute "gnome-terminal -x 'echo testing'" in bash, i get an error message: "There was an error creating the child process for this terminal". Changing the preferred terminal to "x-terminal-emulator -e" fixes the problem, but I'd still like to know what is wrong with gnome-terminal.

I have no idea why getting rid of -x works for you... oh well, don't fix what isn't broken.

---

### Post by pPrdrm on 2007-10-10
Well, I don't have a clue either. But I think that the **-x** parameter must be for the **gnome-terminal** command to start a program in terminal. From the man file of gnome-terminal: "** -x, --execute        Execute the remainder of the command line inside  the  terminal.**". I don't know if the** -x** is there by default, but if it isn't and some other program put it there for some reason, if I make a launcher with the choice to run in terminal then the **-x** parameter must be given twice. If that is what's happening then this is what confuses the **gnome-terminal**. Someone with a clean install please check if the** -x** parameter exists in your **System -> Preferences -> Preferred Applications** in the **System tab**.

---

### Post by monsanto on 2008-10-15
Hi

I check if the -x parameter exists in a clean install and exist.

Monsanto

---


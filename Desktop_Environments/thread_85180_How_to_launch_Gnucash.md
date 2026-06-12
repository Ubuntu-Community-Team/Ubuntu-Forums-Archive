---
title: "How to launch Gnucash?"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Darrin on 2005-11-01
I downloaded it through synaptic, Im not even sure where it is installed at. I found a folder called Gnucash at /usr/share. But cant figure out how to even launch it. Anyone know?

---

### Post by Iandefor on 2005-11-01
Open up a terminal and type in "man gnucash" and read the manual. If that doesn't work, open up Synaptic. Go to GnuCash. Right-click, select Properties and go to the "Installed Files" tab. Look for a file installed to /usr/bin. That should be the executable.

---

### Post by SickTwist on 2005-11-02
Like landefor mentioned, all you need to know is the name of the executable if Gnucash didn't create a menu icon. It's probably just "gnucash" (without quotes) but I'm not positive about that.

You can start the program by typing the name of it in a terminal, pressing ALT+F2 and typing it there, or by creating a launcher for it on the panel/menu. (The menu editor is under Applications -> System Tools -> Menu Editor).

In Linux you usually do not need to use the complete path of the program like you would in Windows. You can just use the name of the executable by itself and Linux will automatically search all of the directories in the PATH system variable for it.

---

### Post by Darrin on 2005-11-02
So, I noticed the properties of a SH file shows its a shell script. Is that what an executable is? Same as a .exe file in windows? Still trying to learn the lingo :). 

> Right-click, select Properties and go to the "Installed Files" tab. Look for a file installed to /usr/bin.
Thanks. Nice tip. Was wondering how I would know what was installed and where.

> In Linux you usually do not need to use the complete path of the program like you would in Windows. You can just use the name of the executable by itself and Linux will automatically search all of the directories in the PATH system variable for it.
Thats great. I was going to put the full path of the file. This is much easier way.

---

### Post by Darrin on 2005-11-02
Got it launched now. Thanks for the help.

---

### Post by Darrin on 2005-11-02
One last question on this. I have it added to my applications menu, but where can I find a proper icon for it?

---

### Post by Darrin on 2005-11-02
I have it added to my applications menu, but where can I find a proper icon for it?
**EDIT: Nevermind got it**

---

### Post by Iandefor on 2005-11-02
[QUOTE=Darrin]So, I noticed the properties of a SH file shows its a shell script. Is that what an executable is? Same as a .exe file in windows? Still trying to learn the lingo :). [/QUOTE]

Let's see... if you're familiar with the Windows/DOS platform, a shell script is similar to a batch file. If you're not familiar with Windows/DOS platform, it's not an executable like .exe, it's a list of commands to give the shell, with a little extra functionality. In Linux, executables aren't necessarily marked by a file extension like .exe. Hope this helps a little with learning "The Lingo" :)

---

### Post by rplantz on 2005-11-02
[QUOTE=Iandefor]In Linux, executables aren't necessarily marked by a file extension like .exe.[/QUOTE]

In fact, most executable programs (in the sense of .exe files) don't have extensions. Execute the commands:
```

ls /bin
ls /sbin

```
and you will recognize that a lot of the "commands" you use are actually programs. They are stored in machine code.

You can see a lot of script files with the commands:
```

locate *.sh
locate *.pl

```
The script files are stored in text format. You can read them with an editor.

Half the battle in any discipline is learning the lingo.  :-)

Bob

---

### Post by faithsnathan on 2006-10-21
Can anyone help a noob with this?

I could probably create a shortcut to my desktop for Gnucash if I could only find whatever file it takes to launch the stupid program.  I can launch it in the terminal, but would like a shortcut for my wife's desktop (and it'd be easier for me to put one on mine, too).  

Also, I'm unable to create a shortcut to my panel (like XP's Quicklaunch is what I'm wanting) for programs.  When I do, it comes up with the following error:
Could not launch application

Details: Text ended before matching quote was found for '. (The text was '/home/nathan/Desktop/Nathan's Documents/Bills 2006.ods')

With something so simple, surely I'm missing something!

Any help would be appreciated.

---

### Post by Aggienator on 2006-10-21
I have just installed via Synaptic (on Edgy) and it has appeared on the menu under Applications > Office.

Good Luck

---


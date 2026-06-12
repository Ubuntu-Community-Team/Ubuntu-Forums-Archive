---
title: "Make Desktop Icons Easier"
date: 2013-10-13
forum: Gaming &amp; Leisure
---

### Post by gerowen on 2013-10-13
I've written another little tool to make my life a little bit easier, and thought I'd share it with you guys.

So I noticed in newer versions of Ubuntu that when you double click a .sh file, you are no longer presented with a dialog asking "Run, Run in Terminal, View", even if the file is marked as executable.  They always open in a text editor without asking.  I play a few video games via emulator, and some of them use different emulators, different options, etc.  However, even with writing scripts to automate launching the games with the appropriate software and settings, I "still" had to open up a terminal and manually execute the script.  I wanted it to be like I'd installed the games and just have an icon on my desktop that I could double click and go.  So I sat down, opened up Geany and started hashing out some python code.  I'm not an expert programmer, but in an hour or two I managed to knock out something that is functional and allows me to generate valid .desktop files that point to the icon and executable files of my choice.  You can use it for purposes other than gaming obviously, but that was my primary motivator.  Another problem I had was that I play a few Nintendo 64 games via emulator, but I haven't been able to find a decent user interface for Mupen64Plus since the default one started getting removed from newer Linux distros.  CuteMupen was the best I could find with one major issue.  The Glide video plugin works best for me, but using Glide, if you have a game open and hit escape, the game dies and you can go to the main interface to launch another one, but the window stays open.  Not a huge issue, unless you want to play fullscreen, because then escape doesn't get you out of fullscreen, it just kills the game and leaves you at a black screen with nothing but a mouse pointer.  However, using the same plugins, if you launch the game with Mupen64Plus manually from the terminal without using CuteMupen, it all works fine.  So anyway, because I'm lazy, I wrote a program that helps me make desktop icons to launch my games automatically with my own scripts.

If you'd like to check it out for yourself, feel free to download, modify, redistribute, etc.  I uploaded it to my sourceforge account at: 

[https://sourceforge.net/projects/linuxlaunchermaker](https://sourceforge.net/projects/linuxlaunchermaker)

It's all in plain text format so if you want to examine what's going on before-hand you can open all the files in a text editor.  The python file for me worked using both Python 2.7 and Python 3.3 on Linux, and on Python 3.3 on Windows 8 (In case you have all the details about where files are located and for whatever reason want to generate them in Windows)

---

### Post by Mateusz Stachowski on 2013-10-13
I've recently upgraded 13.04 to 13.10 and then the dialog asking "Run, Run in Terminal, View" disappeared. I thought that smething broke but it turns out that only the setting in Nautilus the file manager has been reset to default. If you want to get the dialog back go to Preferences of Nautilus and on the second tab named "Behavior" change the option for "Executable text files" to "Ask everytime".

---

### Post by gerowen on 2013-10-13
Thanks for that, :-)

At least I got to practice my python a little bit.

---


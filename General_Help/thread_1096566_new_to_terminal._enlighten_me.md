---
title: "new to terminal. enlighten me"
date: 2009-03-15
forum: General Help
---

### Post by kingaj on 2009-03-15
my teacher says that the terminal is where ubuntu really shines. but im new to it and i don't really see whats so god about the terminal. like can i download an album or a video really fast through the terminal or something?

---

### Post by martrn on 2009-03-15
Yea you can download an album through the terminal - eg :

```
wget "http://agsinger.com/music/Adam-Singer-Gradient-Sound_(2009-CreativeCommons).zip"
```
*Album Released under Creative Commons 3.0 License. All tracks written, produced and mastered by Adam Singer, and he plays piano and am an avid electronic musician. *

As long as you know where to find it and that.

It might mean you know where to find your file like typeing this in a terminal :

```
find . -type f -exec grep -il "foobar" {} \;
```

will find all your files with "foobar" in it.  (Maybe incase you forget where to put your albums and that).

---

### Post by 3rdalbum on 2009-03-15
Not quite. You're not thinking "big picture". Also, your download speed is limited by your internet connection speed, so your choice of software will not help.

There are a lot of programs on Linux that have more functionality when you use them from the terminal, than when you use them from the GUI. I mean, you only have so much screen space to add controls and buttons and things for different options. On the terminal, you can specify (up to) a massive number of options for any task you could possibly need.

The terminal is also useful for automation. You can string together a couple of easy commands to accomplish a task. For instance, you could put together a couple of commands that download an album in MP3 format, convert it to WAV, and burn it to audio CD. You can start this sequence going at night, and by the time you wake up in the morning you will have a freshly burned CD. If one of the steps fails (for instance, the conversion), it will not continue (and waste a CD). Or it will - it's your choice.

Another good use for the terminal is to control your computer remotely. I have a friend with an Ubuntu computer who occasionally asks me for help with her computer, and I'm also entrusted to apply software updates for her. Through the Internet, I can access a command-line on her computer, and I can perform all sorts of remote maintanance on her Ubuntu system just from the command-line. The Windows alternative is "remote desktop", but on ordinary Internet connections there is just not enough bandwidth to stream a full desktop across the Internet; so the command-line works very well. You can do remote desktop on Linux as well, or even just use one GUI program remotely.

If you want to move all the JPEG pictures of aircraft from one folder to another, you can open a file browser and manually keep scrolling down and selecting JPEG files with the word "plane"... but what if there are 1,000 files in the folder and some 700 are photos? You could use the following command:

> mv *plane*.jpg "Aircraft Pictures/"

Which says "move all files that contain the word 'plane' and end with '.jpg' to the 'Aircraft Pictures' folder".

I've seen some very clever examples of this sort of thing; it might take one minute to write the command and ten seconds to run, but it could save you ten minutes of tedious work!

The other good thing I like about the terminal is that it can often be quicker to do something in the terminal than to use a GUI. If I want to install some software that I know the name of, it's quicker to just type a "sudo apt-get install" line than to open Synaptic, do a search for the package I want, right-click it and click Mark For Installation, click Apply and click Ok.

---

### Post by konqueror7 on 2009-03-15
its just that, in the terminal, you can do a lot more things than using a GUI front-end...

oh, and i think its good to download from the terminal because it uses less memory...:D

---

### Post by lovinglinux on 2009-03-15
> **3rdalbum said:**
> The terminal is also useful for automation. You can string together a couple of easy commands to accomplish a task. For instance, you could put together a couple of commands that download an album in MP3 format, convert it to WAV, and burn it to audio CD. You can start this sequence going at night, and by the time you wake up in the morning you will have a freshly burned CD. If one of the steps fails (for instance, the conversion), it will not continue (and waste a CD). Or it will - it's your choice.

I would like to complement the comment above with something about shell scripts. When you write a complex command or a series of commands that you could reuse in the future, you can save them as a shell scripts (usually bash script). Then, when you need to run the commands, all you have to do is type the name of the shell script file in the terminal and all those commands are executed. 

When I first started to use Ubuntu (just 6 months ago), I didn't like the idea of using commands to do stuff, but now I'm loving it. If you click my signature you will find a media center extension for Firefox that I'm developing. This extension has 142 shell scripts with lots of commands inside. They control everything the extension does* by interacting with a database and performing several automated tasks (*record TV series automatically every week, play videos, create playlists with tags, import programme schedules from xmltv files, automatically update several things...).

Another example I like is about upgrading the OS. When I was Windows user I had to format the HD and reinstall Windows every 6 months, then get the updates and install all the stuff again. But now, if I need to do a clean install (not really necessary), I just run a command that save a list with all installed applications. After the clean install, all I have to do is run another command that get this list of applications, download and install ALL OF THEM automagically. It's really fantastic.

---

### Post by x33a on 2009-03-15
terminal lets you do really complex tasks with a few commands. if you are a keyboard lover, you can increase your productivity by a huge margin through the terminal. it is really low on resources. you become a real geek :popcorn:

---

### Post by zvacet on 2009-03-15
@ 

Look [this]("http://www.linuxcommand.org/learning_the_shell.php") and play with it for sometime and you will get picture what you can do with terminal.

---


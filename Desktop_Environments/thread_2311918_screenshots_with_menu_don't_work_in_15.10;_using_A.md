---
title: "screenshots: with menu don't work in 15.10; using Alt+PrntScrn; saving in ~/Pictures"
date: 2016-01-31
forum: Desktop Environments
---

### Post by anotherChris on 2016-01-31
Here's the long story short (see below for the long story/explanation):

I wanted to take a screen shot with a menu open and couldn't.  So I looked and found out how to do this in Lubuntu with a scrot delay.  At the same time, I figured out how to save my screenshots in the Pictures directory (where they logically belong) rather than in the Desktop directory.

**My question:**
1- Can someone give a non-technical explanation of why, from 11.10 to 15.10, the ability to take a screen shot with a menu open was not implemented?  Is there no demand, or would doing bloat the LXDE, or what?

Thanks.


**_Long story, or how to take screenshots in Lubuntu 15.10 with a menu open and save them in the Pictures directory, below..._**

I wanted to take a screen shot while hovering over the wi-fi icon in my panel with the wi-fi menu open.  Screenshot would not work.  So, I found the following:

[http://askubuntu.com/questions/184618/taking-screenshots-in-lubuntu-11-10](http://askubuntu.com/questions/184618/taking-screenshots-in-lubuntu-11-10)
and
[http://ubuntuforums.org/showthread.php?t=2185294](http://ubuntuforums.org/showthread.php?t=2185294)

These both indicated that what I wanted to do was not possible in 11.10 and 13.10, so it's probably not possible in 15.10, either.  I wonder why this hasn't been implemented?  Anyhow...

The second thread pointed me to this link:
[http://askubuntu.com/questions/252281/how-do-i-take-screenshots-with-a-delay](http://askubuntu.com/questions/252281/how-do-i-take-screenshots-with-a-delay)

From these three resources, I was able to figure out how to configure Lubuntu's screenshots to do what I'd like... i.e., take a photo of everything on the desktop and save it in the Pictures directory...

In Lubuntu 15.10...

(1) open your Home Folder **/home/username**, then select **View -> Show Hidden**
(2) open** .config/openbox**
(3) open the file called **lubuntu-rc.xml** with a simple text editor and save a backup (I called it **lubuntu-rc.xml.backup**).
(4) in lubuntu-rc.xml, find...
```
 <!-- Take a screenshot of the current window with scrot when Alt+Print are pressed -->
    <keybind key="A-Print">
      <action name="Execute">
        <command>**lxsession-default screenshot window**</command>

```and
```
   <!-- Launch scrot when Print is pressed -->
    <keybind key="Print">
      <action name="Execute">
        <command>**lxsession-default screenshot**</command>

```
(5) change the bolded text as follows...
```
 <!-- Take a screenshot of the current window with scrot when Alt+Print are pressed -->
    <keybind key="A-Print">
      <action name="Execute">
        <command>**scrot -b -d 5 ~/Pictures/screenshot_%Y:%m:%d:%H:%M:%S.png**</command>

```and
```
   <!-- Launch scrot when Print is pressed -->
    <keybind key="Print">
      <action name="Execute">
        <command>**scrot -b ~/Pictures/screenshot_%Y:%m:%d:%H:%M:%S.png**</command>

```
What you just did was change the Prnt Scrn button so that it takes a screenshot and puts it in your Pictures directory and change Alt+Prnt Scrn so that it does the same thing after a 5 second delay.  This 5 second delay allows you time to open a menu in case you want to take a screenshot with a menu open.  *Note that Alt+Prnt Scrn no longer takes a screen shot of the current window, which was its original function.*

(6) Open a terminal and run 
```
[COLOR=#111111][FONT=Consolas]openbox --reconfigure[/FONT][/COLOR]
```
To quote from the source: "[(You won't see anything happen and you'll get back your prompt if you haven't messed up anything. If you have messed up something, you'll get an error. That's when the back-up comes handy.) Running the command is a necessary step to ensure that your edits to lubuntu-rc.xml are now active.]("http://askubuntu.com/questions/252281/how-do-i-take-screenshots-with-a-delay")"

Finished!  I just did this on Lubuntu 15.10 and it worked.

---

### Post by mr-tin-man on 2016-02-08
Have you tried the program "Take ScreenShot" it has a option to put in a delay for the purpose you were talking about with no tweaks or scripts. I'm sure it's in the Ubuntu Software Center.



mr_tin_man

---

### Post by sammiev on 2016-02-08
> **mr-tin-man said:**
> Have you tried the program "Take ScreenShot" it has a option to put in a delay for the purpose you were talking about with no tweaks or scripts. I'm sure it's in the Ubuntu Software Center.



mr_tin_man

+1 I have added Screenshot to Lubuntu before with no issues.

---

### Post by vasa1 on 2016-02-08
What's the name of the executable? I'm guessing "Take ScreenShot" is the .desktop name?

I'm asking because of this _on Lubuntu 14.04_:```
07:38 AM ~ $ acse screenshot | grep take
gtk-vector-screenshot - takes screenshots of applications as PDF or SVG files
07:39 AM ~ $ 
```

*acse = apt-cache search*

Is that the "Take ScreenShot" program?

> **mr-tin-man said:**
> Have you tried the program "Take ScreenShot" it has a option to put in a delay for the purpose you were talking about with no tweaks or scripts. I'm sure it's in the Ubuntu Software Center.
...
Hi, the point of that Ask Ubuntu QnA was to get delayed screenshots *using default applications* (= those that are part of the distro) and not to install additional software.

Of course, it all depends on one's requirements. Some heavily into graphics will want more fully-featured software.

---

### Post by mr-tin-man on 2016-02-14
The program "Take ScreenShot" was, and is part of my Ubuntu-Mate, I also run Lubuntu on another machine, I looked there and, it is not a part of their installed default programs.  I looked in the Lubuntu Software Center, and did not see it.  I loaded the Synaptic Package Manager, and searched there.  It's Called Gnome Screenshot there, that's the same program that is installed by default with Ubuntu-Mate..

I figured if your trying to get a job done, you'd want to take advantage of what was there for your needs, whether it was a default installed program or not..

mr tin man

---

### Post by vasa1 on 2016-02-14
> **mr-tin-man said:**
> ... Gnome Screenshot ...

I figured if your trying to get a job done, you'd want to take advantage of what was there for your needs, whether it was a default installed program or not..

mr tin man
The default installed program in Lubuntu, scrot, has the provision to take delayed screenshots and to get the stated job done.

---

### Post by mr-tin-man on 2016-02-15
Glad to know that, I'll take a look see.  I don't use that machine much, just keep it updated.  I like lubuntu, as well as k, and mate.  My full time machine is running mate now, and I've grown kinda fond of it.  Thanks for the info, i'll put in on my desktop..

Again thanks, mr tin man

---


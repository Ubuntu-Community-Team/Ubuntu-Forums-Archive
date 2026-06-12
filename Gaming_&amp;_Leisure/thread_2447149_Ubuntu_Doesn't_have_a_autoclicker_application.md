---
title: "Ubuntu Doesn't have a autoclicker application?"
date: 2020-07-13
forum: Gaming &amp; Leisure
---

### Post by wiisanen15 on 2020-07-13
Okay i been looking every where for a good working autoclicker for linux ubuntu and i cant seem to find a working up to date script i need it for a game and asking anyone out there if they could help me with this problem that would be great im new to linux so i have very little linux smarts but im getting there

---

### Post by deadflowr on 2020-07-13
What's autoclicker and what does it do?

---

### Post by wiisanen15 on 2020-07-13
An auto clicker is a type of software or macro that can be used to  automate clicking. They can be triggered to generate input that was  recorded earlier or generated from various current settings. Auto clickers can be as simple as a program that simulates mouse clicks.

basically auto clicks ur mouse for you and some even record mouse movements and will play and copy everything u did but yeah i'm not able to find one

---

### Post by TheFu on 2020-07-13
xdotool for simple needs.  I use this hundreds of times every day and don't really think about it.  I have keyboard accel keys setup to perform a number of different tasks - mostly to launch programs with specific options, constraints, from specific directories. Pretty much anything can be automated - like I run Chromium with a specific webcam, specific microphone, at a specific zoom level for some video conferences. No worries that I changed something in Pulse and screwed up the settings.

Also look for Xnee for [https://xnee.wordpress.com/](https://xnee.wordpress.com/) and look for X11 testing tools.  These testing tools can ensure exactly the correct object, not just by screen location, get the desired event.  

Webapp testing tools can get really elaborate.  [https://en.wikipedia.org/wiki/Comparison_of_GUI_testing_tools](https://en.wikipedia.org/wiki/Comparison_of_GUI_testing_tools) is a list.  I've used Selenium.

There are screen text recorders used for CLI presentations that record just the text entered and the delays for the next point when text needs to be entered. [https://www.tecmint.com/record-and-replay-linux-terminal-session-commands-using-script/](https://www.tecmint.com/record-and-replay-linux-terminal-session-commands-using-script/) 

If you want to go hard-core, use Tk/TCL via **expect**.  The killer application for expect was changing passwords on 50-200 different system passwords back when we didn't use NIS, NIS+, LDAP and NFS on the networks.  Since ssh-keys became a thing, expect just hasn't been needed.  I have a calendar entry to remind that changing out my keys are needed every year, but I keep the old key files around a few yrs. Hummm. I should script the migration from the old ssh-key to the new ones.

Some DEs may get in the way for some of these tools, but I know xdotool works fine with openbox and fvwm. I have no idea if they work with Gnome3 or when using non-X11 like Wayland. Probably should work fine, but until you try, you won't know.

BTW, good for asking this question.  Unix has been around a very long time and there are some solutions for pretty much anything that would have been dont 10, 20, 30, 40 yrs ago. Also, most of the old stuff still works, but has been forgotten.

Instead of thinking "autoclicker", think "automated key input."  Key input events can be directed to a specific widget, whereas doing that with a mouse will be less exact and much more hassle to setup.

---

### Post by wiisanen15 on 2020-07-16
thanks guys this helped thanks everyone for replying!

---

### Post by bahamida47 on 2021-05-14
hi, use [Max Auto clicker]("https://maxautoclicker.blogspot.com") is available for linux ubuntu and windows

You can find how to install it here :
[URL="https://maxautoclicker.blogspot.com/2021/05/mouse-auto-clicker-for-ubuntu-linux.html"]https://maxautoclicker.blogspot.com/2021/05/mouse-auto-clicker-for-ubuntu-linux.html
[/URL]
and the download link :
[https://sourceforge.net/projects/maxautoclicker/](https://sourceforge.net/projects/maxautoclicker/)

---

### Post by juxwillx on 2021-06-02
Autoclicker is only available for windows and MacOS.

---

### Post by QIII on 2021-06-02
RIP, dear old thread.

---


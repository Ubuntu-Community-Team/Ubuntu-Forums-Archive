---
title: "xfce and Ubuntu"
date: 2008-01-05
forum: Desktop Environments
---

### Post by blackenedbloodx on 2008-01-05
Hey guys. Here's the deal. I had installed many different Linux distros and I have come to like Ubuntu the best. It has the best feel, look, and it's easiest to learn for me. My only problem is the computer i have at the moment. It does have many upgrades but unfortunately it still has a Pentium 4. Hopefully I will be getting another computer with an Athelon, but thats only if i sell this one. Anyway I kinda liked the Xfce environment. The fact that it is less power dependant was a big help. And i liked how I could adjust the panels to be smaller and free transform. Anyone know how to get these two features on Ubuntu?

---

### Post by vambo on 2008-01-05
Try Xubuntu - Ubuntu with XFCE DE.

---

### Post by PeterJS on 2008-01-06
Or you could just install the Xubuntu-Desktop on top of your existing install.

---

### Post by tdrusk on 2008-01-06
I love my xubuntu. Its the best imo.

---

### Post by bharadwaj on 2008-01-06
> sudo apt-get install xubuntu-destop and then in the login windows cange the session before going any further

---

### Post by blackenedbloodx on 2008-01-06
Thanks guys, and yes I do like Xubuntu, but i just didn't "click" with it as much as ubuntu. And I don't really like to keep reinstalling operating systems. lol. I have messed up and had to reinstall Windows numerous times until i finally switched over to Linux. And then i had to keep reinstalling this because of that fake chmod for the virtual box. I am downloading the Xubuntu desktop now and I'll be back if i need any more help, or just a thanks.

EDIT: Ok yeah, need BIG help.
A) In Xubunu, can't get compiz to work
B) Can't add launchers to panel
C) Can't change theme other than the base themes (can't install any from the net).
D) Can't connect via wireless, I have to connect in Ubuntu in order to get internet in Xubuntu.
(In Ubuntu)
A) Why is it now 800x600? What happened to my 1440x900!? (640x840 in Xubuntu)
B) Now my compiz won't work in Ubuntu. Every time I go to change to "Custom Effects" there is a popup saying that it could not be enabled.

Again thanks. Any help is greatly appreciated.
(And yes, I am a complete Noob at Linux.)

PS. All i really wanted was for my system resources to be less worked and the cool panels and icons like i see around the net similar to the Mac dashboard. Oh, and the ability to minimize the windows like in Xubuntu with the little arrow to just show the browser bar. I guess i could just use Xubuntu but I need the help previously mentioned.

---

### Post by tdrusk on 2008-01-06
> **blackenedbloodx said:**
> 
EDIT: Ok yeah, need BIG help.
A) In Xubunu, can't get compiz to work
[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/)
B) Can't add launchers to panel
This is where XFCE sort of lacks. You have to make launchers. Right click on the bar and add new item and choose launcher.
C) Can't change theme other than the base themes (can't install any from the net).
I dunno, I don't mess with themes.
D) Can't connect via wireless, I have to connect in Ubuntu in order to get internet in Xubuntu.
right click network manager and click your connection.
(In Ubuntu)
A) Why is it now 800x600? What happened to my 1440x900!? (640x840 in Xubuntu)
post your lspci.
B) Now my compiz won't work in Ubuntu. Every time I go to change to "Custom Effects" there is a popup saying that it could not be enabled.
i dunno

Again thanks. Any help is greatly appreciated.
(And yes, I am a complete Noob at Linux.)

PS. All i really wanted was for my system resources to be less worked and the cool panels and icons like i see around the net similar to the Mac dashboard. Oh, and the ability to minimize the windows like in Xubuntu with the little arrow to just show the browser bar. I guess i could just use Xubuntu but I need the help previously mentioned.


Try to stick with Xubuntu. It's well worth it.

---

### Post by mali2297 on 2008-01-06
> **blackenedbloodx said:**
> 
A) In Xubunu, can't get compiz to work

Copy/paste the following into the terminal
```

pkill xfwm4 && sleep 5 && compiz &

```
Do you get any errors?

> 
C) Can't change theme other than the base themes (can't install any from the net).

Say that you have downloaded a theme example.tar.gz to your desktop, then unpack it to the hidden directory **.themes**. From the terminal, you can do that with the commands
```

cd ~/.themes
tar -xvzf ~/Desktop/example.tar.gz

```
Then it should be available in the settings manager.

If you haven't got a .themes directory in your home folder, create it:
```

mkdir ~/.themes

```

---

### Post by blackenedbloodx on 2008-01-06
thanks guys its all grood now.

---


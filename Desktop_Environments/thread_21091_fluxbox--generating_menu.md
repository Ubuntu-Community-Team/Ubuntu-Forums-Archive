---
title: "fluxbox--generating menu"
date: 2005-03-20
forum: Desktop Environments
---

### Post by Brunellus on 2005-03-20
I'm running ubuntu warty, and have just successfully apt-getted fluxbox.   It appears very nicely in my session-type menu in GDM, and it runs very very fast indeed...

The trouble is that, in order to run any programs, I'm having to run them from terminal windows.  My initial experience with fluxbox was from using Damnsmall Linux, where a right-click had brought up a fairly comprehensive menu of the various applications..

After googling, I found that ```
fluxbox-generate_menu
``` was the command to use;  but when I type this into the terminal, all I get is an error:  ```
bash: fluxbox-generate_menu: command not found
```.  I don't know what to do from here.

Any fluxbox gurus want to help me out here?

---

### Post by kb00heda on 2005-03-20
I'm no guru, but I had Fluxbox running on my old SuSE system. I remember I first installed fluxbox using apt-get, and then I started it, i.e., I left KDE and went Fluxbox.

Now a .fluxbox folder was created in my home directory. I copied that one to /root

"sudo cp -r /home/kb00heda/.fluxbox /root"

because I otherwise had problems installing fluxconf. That I did next

"sudo apt-get install fluxconf"

and I added the packages fbdesk, fbpager, and fluxter as well. At least I think fluxconf is essential. Check in Synaptic (or via apt-cache search) if you want to know more. 

Now I ran

"fluxconf"

and changed the Menu File Location to my home directory 

"/home/kb00heda/.fluxbox/menu"

Afterwards I executed "fluxbox-generate_menu". It worked fine. Try it. At least it was OK on my SuSE 9.2 machine. Perhaps you missed out on the fluxconf package?

The nice thing about the menu is that it is quite easy to customize it precisely the way you want it, e.g., which programs to appear, and in what order. I will stay with GNOME for a while, however, just to get the feeling of it.

Good luck!

/David

---

### Post by Brunellus on 2005-03-20
bump/update:

thanks to thoreauputic on #ubuntu, I was able to get things running nicely.  The fluxbox package in the warty repositories is *ancient* and did not include the fluxbox-generate_menu script.  A more recent .deb ( v. 0.9.12) runs fine.

Now I'm tweaking.  I'd like to run some dockapps in the fluxbox slit at startup.  I understand that I'd have to edit .xinitrc as shown [here](http://www.fluxbox.org/docbook/en/html/app-setup.html) to make this happen.  Question:  will this affect the behaviour of any other desktop environments/window managers I decide to run on this system?  That is, will this break GNOME 2.8?

second question:  from fluxbox, how does one take a screenshot?

---

### Post by Brunellus on 2005-03-22
bump/update 2:


I've finally gotten fluxbox 0.9.12 up and running nicely.   In order to have dockapps load at the beginning of the fluxbox session, it   it is necessary to edit  /usr/share/xsessions/fluxbox.desktop --I changed the Exec= line to read

```
Exec= /usr/local/bin/startfluxbox
``` 

This executes "startfluxbox," which, when run for the first time, creates a startup file in ~/.fluxbox .  editing ~/.fluxbox/startup in order to run dockapps when the fluxbox session begins is trivial--the file which was generated automatically is well-commented with the directions for doing so.

---


---
title: "Starting GNOME desktop from BASH?"
date: 2011-04-14
forum: Desktop Environments
---

### Post by javajames97 on 2011-04-14
i need to make this clear that this was my error, not the computers. I went into the log in menu options (System>Administration>Login Screen) and i was having a fidle around, and at the bottom there are options on how you want the computer to boot, i selected the second one down, (the one with nothing to do with my GUI - gnome), this i found to be the stupidist mistake i have ever made in computing. because when it started up again, all i got was BASH shell, in terminal, no GUI no nothing - i should have seen it coming. i have looked around and no one seems to know how to turn it back, can someone please, help, if you have ubuntu and gnome can you help? i want to be able to restore my gnome desktop.

---

### Post by g00f on 2011-04-14
startx

At least that is what it used to be.

---

### Post by 23dornot23d on 2011-04-14
If you want to fix it properly from a desktop environment - first of all install another desktop manager

sudo apt-get update
sudo apt-get install kdm

choose kdm to boot into ..... when it asks you

Then reboot

You will now have a kdm login screen ...... 
(let me know when you have done this successfully)

You can change back - 'whatever it was that you changed in the first place' ..... and then
we will re-install it back to boot from  gdm

---

### Post by javajames97 on 2011-04-14
i have tried startx, that doesn't seem to work, i have also tried ctrl-alt-f7, but that doesn't work either, startx says there is some sort of server problem, i will try and find out what that problem is, and post it, see if anyone knows...

---

### Post by javajames97 on 2011-04-14
OK, that did sound reasonable, but my computer has not connected to the internet, (im running this on windows); i know this because it can't access the archives containing the updates and installs you suggested. How can i connect, bear in mind i can run my applications as long as i know their names.

---

### Post by 23dornot23d on 2011-04-14
Try this first by typing .....

sudo gdm

It might run the gnome desktop manager .....

---

### Post by javajames97 on 2011-04-14
ok, im on the internet, i tried sudo gdm, no luck, i installed kdk like you said, and it worked, but i accidentally pressed to boot gdm, instead of kdm, it didn't work, and it boots into bash again, when i try to run kdm again (with sudo kdm) it comes up with loading and then it just brings me back to bash. Is there a different way to run kdm like i did at first if not, how do you uninstall it, so that i can reinstall it (sorry if i sound like a complete bash novice, it's because i am.

---

### Post by 23dornot23d on 2011-04-14
sudo apt-get remove kdm

then

sudo apt-get install kdm

This time choose ' kdm '

and reboot

( we will get you your gdm login back once you can get kdm running )

---

### Post by javajames97 on 2011-04-14
right, i don't know my username, (i have got to kdm login), but no worries, i just need a way back to x-term, (the bash thing i was stuck in), then if i put in exit, i can get to the gnome login screen - this doesn't leyt me log in to gnome but it will let me view my username. from there i will note of my username, and go back and repeat steps, i hope im not bothering you to much

---

### Post by 23dornot23d on 2011-04-14
do ctrl+alt+f1 ....... to get to a terminal screen .... from the kdm menu

see what your username is ..... and  then ctrl+alt+f7

to get back to the kdm login screen ...

---

### Post by javajames97 on 2011-04-14
that doesn't work, it brings me to terminal login, is there any other way to find my username?? maybey a default account that i could login to to find my username. In the mean time i am going to boot up one of my previous ubuntu updates from grub, if kdm doesn't start up in them i may be in luck

---

### Post by el_koraco on 2011-04-14
sudo service gdm start

---

### Post by javajames97 on 2011-04-14
thank you for all your help, i have come back to gnome desktop and i think all is well, all my applications are there (and i can finally use google chrome again), but generally thanks, it looks like its in gnome desktop, will it boot like it use to or do i need to change things? it wont seem to unlock the settings for login screen (thats where it all went wrong) but the bar that i wanted to change appears to be correct: 'GNOME (this session logs you into GNOME)'   :D :D

---

### Post by el_koraco on 2011-04-14
can you post a screenshot?

---

### Post by javajames97 on 2011-04-14
errr.... image coming soon, (how to upload directly to this site???) but im still loging in through kdm???

---

### Post by javajames97 on 2011-04-14
here

---

### Post by javajames97 on 2011-04-14
> **23dornot23d said:**
> sudo apt-get remove kdm

then

sudo apt-get install kdm

This time choose ' kdm '

and reboot

( we will get you your gdm login back once you can get kdm running )

how do i get my gdm login back?

---

### Post by el_koraco on 2011-04-14
When you got booted to bash, did you get a black screen with the first prompt being 

```
login (your user name):
```or was there a blue and red screen presenting several options? And when you say you solved things, does that mean you booted into one of the older entries in the grub menu? How did you get to the desktop?

---

### Post by javajames97 on 2011-04-14
i am an only user, so i have it auto login, so it automatically logged into bash in the same way as when you go to applications>accessories>Terminal:

```
james@james-laptop:~$ 

```

which meant i could access all the applications (if i knew their names), and i would get gui for each of these apps, but no multitasking and no gnome desktop

---

### Post by el_koraco on 2011-04-14
Open a terminal and type 

> less /etc/gdm/custom.conf >> ~/Desktop/gdm.txt

This will make a file on your desktop called gdm.txt. Post it back here inside the code brackets.

---

### Post by javajames97 on 2011-04-14
```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=james
TimedLoginEnable=false
TimedLogin=james
TimedLoginDelay=10
DefaultSession=xterm
```

Bear in mind it still logs in through kdm

---

### Post by 23dornot23d on 2011-04-14
how do i get my gdm login back?     

> 
i need to change things? it wont seem to unlock the settings for login screen (thats where it all went wrong)
[COLOR=Red][B]

You still need to sort this out[/B][/COLOR] .......( it wont seem to unlock the settings for login screen )

otherwise when I give you the instructions to put GDM back again ......

You will be in the same position as you were before booting to a terminal .....

( once you are ready to go back to gdm login ...... just remove kdm as we did earlier )

[B]sudo apt-get remove kdm

and then choose gdm[/B]  ........ 

( but only remove kdm after you sort the login from the GUI otherwise we will end up going around in circles )

---

### Post by javajames97 on 2011-04-14
GUI login? i will go ahead and remove kdm probably, after whats his nam explained it it doesn't take too long to run kdm, unless you have any objections?

---

### Post by javajames97 on 2011-04-14
> **javajames97 said:**
> GUI login? i will go ahead and remove kdm probably, after whats his nam explained it it doesn't take too long to run kdm, unless you have any objections?

ok, it appears you were right, kdm doesnt want me to remove it, because im running it (looks awfully like gnome to me), anyhow, how do i sort this out so it boots into gnome desktop like it used to

---

### Post by 23dornot23d on 2011-04-14
You have not sorted the problem out yet ..... 

[COLOR=Red]**You still need to sort this out**[/COLOR] .......( it wont seem to unlock the settings for login screen )

how did you do it before ..... I have a feeling you used a password to unlock it .... 
( have you forgotten your password ? )

GUI is Graphic User Interface ....
its what lets you work easily and see things graphically to change them ....

If you remove your kdm login ...... you will end up back at a terminal

Your username is james ........

You probably forgot the password ..... or have CAPS LOCK on .....

kdm will take you into your normal Gnome Desktop ...... 

just as GDM would .....

Its just basically a different startup sequence ....... to get you to your Gnome Desktop

and nothing will look different because we have not altered anything in that .......

---

### Post by el_koraco on 2011-04-14
james, what you did, obviously, was choose a different login session. There are several things you can try, cuz you're obviously gonna have to reboot at some point. The file i asked you to post was meant to clarify everything a little. 

There are two things you can try if the above advice does not work. 

First, boot into bash, login with your username and password, and run the command 

```
sudo service gdm start
```This command does what startx used to do. You should get to your desktop, or to gdm. If not, try clicking CRTL ALT F7. You can then to to the login screen and choose Ubuntu Desktop Edition as your default session. 

If that doesn't work, we'll be editing the /etc/gdm/custom.conf file, which is just the CLI version of the "Login screen" utility. 

What you will do is, and you might wanna write this down on a piece of paper, enter 

```
sudo nano /etc/gdm/custom.conf
```and change your settings to say 

> AutomaticLoginEnable=true 
AutomaticLogin=james 
TimedLoginEnable=false 
TimedLogin=james 
TimedLoginDelay=10 
DefaultSession=**gnome**
Basically, you'll just be changing the last entry. You'll then hit CTRL O (the letter, as in orange), enter and CRTL X. Then you'll run sudo shutdown -r now and we'll see how it goes.

---

### Post by javajames97 on 2011-04-14
> **23dornot23d said:**
> You have not sorted the problem out yet ..... GUI is Graphic User Interface ....
its what lets you work easily and see things graphically to change them ....

If you remove your kdm login ...... you will end up back at a terminal

Your username is james ........

You probably forgot the password ..... or have CAPS LOCK on .....

but kdm will take you into your normal Desktop ...... just as GDM would .....

its just basically a different startup sequence .......

i know what GUI is and i know my password, but how do i change it so that it starts up in gnome start up, the login screen options menu wouldnt respond when i pressed unlock, it didn't even give me my usual box to start unlock  administration. the question is how to make my computer boot the way it used to?

---

### Post by javajames97 on 2011-04-14
> **el_koraco said:**
> james, what you did, obviously, was choose a different login session. There are several things you can try, cuz you're obviously gonna have to reboot at some point. The file i asked you to post was meant to clarify everything a little. 

There are two things you can try. First, boot into bash, login with your username and password, and run the command 

```
sudo service gdm start
```This command does what startx used to do. You should get to your desktop, or to gdm. If not, try clicking CRTL ALT F7. You can then to to the login screen and choose Ubuntu Desktop Edition as your default session. 

If that doesn't work, we'll be editing the /etc/gdm/custom.conf file, which is just the CLI version of the "Login screen" utility. 

What you will do is, and you might wanna write this down on a piece of paper, enter 

```
sudo nano /etc/gdm/custom.conf
```and change your settings to say 



Basically, you'll just be changing the last entry. You'll then hit CTRL O (the letter, as in orange), enter and CRTL X. Then you'll run sudo shutdown -r now and we'll see how it goes.

can i run these commands through terminal in my desktop? (the one about editing the CLI)?

---

### Post by javajames97 on 2011-04-14
can i use gedit, to edit that conf file?

---

### Post by el_koraco on 2011-04-14
> **javajames97 said:**
> can i run these commands through terminal in my desktop? (the one about editing the CLI)?

Yes, you can. But first try to follow the above advice, you guys are having a write up of your own. I edited my post above with instructions on how to proceed. I gotta go, will be back later to check on progress.

---

### Post by el_koraco on 2011-04-14
> **javajames97 said:**
> can i use gedit, to edit that conf file?

You can do that as well, I was giving you instructions for when you're booted into bash, obviously :D

---

### Post by javajames97 on 2011-04-14
> **el_koraco said:**
> You can do that as well, I was giving you instructions for when you're booted into bash, obviously :D

thanks, all is working now, i rebooted and it went into gnome, :D and now i know a little bit more about xterm for the future.

---

### Post by el_koraco on 2011-04-14
> **javajames97 said:**
> thanks, all is working now, i rebooted and it went into gnome, :D and now i know a little bit more about xterm for the future.

keep the /etc/gdm/custom.conf file in mind, since you're logging in automatically, our dear friend gnome keyring might give you trouble in the future.

+ mark the tread as solved.

---

### Post by javajames97 on 2011-04-14
> **el_koraco said:**
> You can do that as well, I was giving you instructions for when you're booted into bash, obviously :D

x-term allows you to use applications - even if they have their own  GUI - so gedit would have worked :D

---


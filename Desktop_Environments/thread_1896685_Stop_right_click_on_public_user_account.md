---
title: "Stop right click on public user account"
date: 2011-12-17
forum: Desktop Environments
---

### Post by GaryMac on 2011-12-17
Hi

I posted on an old thread - without reply ..
[http://ubuntuforums.org/showthread.php?t=1176963](http://ubuntuforums.org/showthread.php?t=1176963)
I will try my luck starting anew.

A little background ..
I am a twenty years Windows user ..  being chased by Microsoft Watchdogs for not having a Rental Rights License in our Internet Cafe.   We use Windows XP Home on the PCs - and not only do we need Rental License but also need Professional Windows ..  so looking at 2,000 euro  to "get legal" ...    Yeah right.

So I have turned to Ubuntu ..  and am installing 10.04 on all our PCs .. so as not to shock our old timer customers too much with a complete new (Unity) system ..  maybe next year.

So to the question :  

Trying to impose a few restrictions on the public user account ..  including disable the right click.

Have tried the following 

xmodmap -e "pointer = 1 2 99"
This only works for one session = on restart - back to normal ..  

**Is there a permanent fix for this ... on the one public account ?  **


====================

Tried this ...

put the part in quotes into ~/.Xmodmaprc to have it run automatically
 
 Which did not work either.

====================

  I have tried running  ...      xmodmap -e "pointer = 1 2 99"  
Then   ...    xmodmap -pke > .Xmodmap  
(it creates a files called .Xmodmap in your home directory)

Then you have to create a file called **.xinitrc** in your home directory where you put this commandline xmodmap .Xmodmap

I found these instructions here > [http://askubuntu.com/questions/24916...p-certain-keys]("http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys")


On re-start I got a box asking if I wanted to run xmodmap  =   check ok

But the right click was still available.

---

### Post by GaryMac on 2011-12-20
OK ..  if this is not possible with a single command line entry ..

Is it possible to run this command in the terminal every time the PC starts  ??

xmodmap -e "pointer = 1 2 99"


If so .. how can I do this ..  
Please help I have tried to learn but I cannot find a solution ..

---

### Post by Lars Noodén on 2011-12-20
> **GaryMac said:**
> OK ..  if this is not possible with a single command line entry ..

Is it possible to run this command in the terminal every time the PC starts  ??

xmodmap -e "pointer = 1 2 99"


If so .. how can I do this ..  
Please help I have tried to learn but I cannot find a solution ..

If you need it to run as root when the machine starts, then it can go in [font=Courier New]/etc/rc.local[/font].  If you need it to run as a specific user, then it can go in [font=Courier New].xsession[/font] in that user's home directory.

There are several way to make kiosks.  You might look around on the net for other solutions to.  Some of them might complement what you are already trying to do, others might be a better way.

---

### Post by dargaud on 2011-12-20
As already stated, there are better ways to make kiosks, but about the mouse button removal, you can read my little writeup about [mouse button *addition* ]("http://www.gdargaud.net/Hack/Linux.html#Mouse")and adapt it...

---

### Post by GaryMac on 2011-12-20
I am so obviously out of my depth here.
But the past 8 weeks cannot be in vain.

Regarding Kiosk solutions .. the biggest hurdle to overcome is the Cyber Control Software .. and I have one which will work on Ubuntu  ..  so this is the direction I chose.

Lars you say ..
If you need it to run as root when the machine starts, then it can go in [FONT=Courier New]/etc/rc.local[/FONT].  If you need it to run as a specific user, then it can go in [FONT=Courier New].xsession[/FONT] in that user's home directory.

I cannot find .xsession in the users home directory.

But I found .xsession in /etc/X11/   when looking at dargauds writeup  - which at this stage in my Ubuntu learning - looks a little too complex for me.

Thanks guys.

**But the question remains ..**
Is it possible to run this command in the terminal every time the PC starts  ??

xmodmap -e "pointer = 1 2 99"       (I know this works - but is lost on re-start)

If so .. how can I do this ..

---

### Post by sudodus on 2011-12-20
0. Have a look at Webconverger, an open-source and free linux kiosk. It can probably be customized for a reasonable fee by the guy developing it.

1. But have another try with Ubuntu

If you enter gnome-terminal (or another command line terminal program) into the group of start-up programs, the file [FONT=Courier New][SIZE=3].bashrc[/SIZE][/FONT] will be automatically run when logging in.  So enter your command line (as the last iine of [FONT=Courier New][SIZE=3].bashrc[/SIZE][/FONT])

```
xmodmap -e "pointer = 1 2 99"
exit
```Good luck

---

### Post by GaryMac on 2011-12-20
Thanks sudodus   -  but

If you enter gnome-terminal (or another command line terminal program) into the group of start-up programs, the file [FONT=Courier New][SIZE=3].bashrc[/SIZE][/FONT] will be automatically run when logging in.  So enter your command line (as the last iine of [FONT=Courier New][SIZE=3].bashrc[/SIZE][/FONT])

I have done a search for [FONT=Courier New][SIZE=3].bashrc [/SIZE][/FONT] ..  no success 
bash.bashrc
dot.bashrc
bash.bashrc
dot.bashrc

---

### Post by sudodus on 2011-12-20
If you are in your home folder look for .bashrc
```
ls .bashrc
```If it is not there, create it! It will be discovered and used :-)

```
cd             # go to your home folder
nano .bashrc   # start editing
```

---

### Post by GaryMac on 2011-12-20
PERFECT ..

sorry to be a pain ...
The file was there ...  I am stupid.

Thanks  ..  sudodus

---

### Post by sudodus on 2011-12-20
You are welcome :KS
and good luck :-)

... and when you have tested that it works, please mark your thread SOLVED

---

### Post by pastalavista on 2011-12-20
It seems to me the Ubuntu 'Guest Session' would be perfect for a kiosk session. Nothing can be saved if there's no USB or SD card ports for external drives.

---

### Post by GaryMac on 2011-12-20
Just to clarify ..   for anyone else searching for this.

The solution works .. perfectly.

But when the Terminal is run on the "public" account it closes automatically.

Obviously this can be temporarily fixed by removing the lines added to  .bashrc

Note : to reverse the right click disable ..   
enter xmodmap -e "pointer = 1 2 3"  in Terminal


Anyway ..   it is fine & dandy ..   as far as I am concerned.
Thanks once again sudodus
Marked as solved.

@ pastalavista   I now have two machines set up how I wanted them ...  
now for the big install process & time will tell how it goes.

---

### Post by Lars Noodén on 2011-12-20
> **GaryMac said:**
> Lars you say ..
If you need it to run as root when the machine starts, then it can go in [FONT=Courier New]/etc/rc.local[/FONT].  If you need it to run as a specific user, then it can go in [FONT=Courier New].xsession[/FONT] in that user's home directory.

I cannot find .xsession in the users home directory.

You can make [FONT=Courier New].xsession[/FONT] if one does not exists.

---

### Post by eishv on 2013-04-26
None of the above worked as a perm solution for me. On Zorin 6 lite LXDE I did:

create ~/.config/autostart/custom.desktop with contents:

[Desktop Entry]
Name=Chromium
Exec=/home/kiosk/.xmodmap
X-Ubuntu-Gettext-Domain=gdm

Then create .xmodmap in users home dir with contents:

/usr/bin/xmodmap -e "pointer = 1 2 99"

Made it executable and reboot. The custom.desktop file I reused I just changed the Exec=

---

### Post by wildmanne39 on 2013-04-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


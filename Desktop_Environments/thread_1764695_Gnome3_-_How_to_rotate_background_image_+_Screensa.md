---
title: "Gnome3 - How to rotate background image + Screensavers?"
date: 2011-05-22
forum: Desktop Environments
---

### Post by maverick280857 on 2011-05-22
Hi,

I'm running Gnome3 on a Ubuntu 11.04 x64 box. I have a whole bunch of jpeg images in my Pictures folder, and I'm wondering if it is possible to iterate over the background images somehow.

In other words, I want to pick a jpeg file at random from $HOME/Pictures, and set it as the background image for 'x' seconds, before transitioning to another randomly selected image.

I have found Perl-based scripts elsewhere on this forum, but they don't work with Gnome3 (or at least I haven't been able to get them to work). It seems these solutions are for Gnome2.

Secondly, is it possible to add screensaver support to Gnome3?

I would appreciate any inputs or ideas on these issues, especially the desirable rotating background feature.

**EDIT**: As of May 25, 2011, this problem has been solved. Please refer to [http://ubuntuforums.org/showpost.php?p=10858322&postcount=8](http://ubuntuforums.org/showpost.php?p=10858322&postcount=8) for a solution.

**EDIT (June 02, 2011)**: How to change the theme and background picture in GDM 3.x - [http://ubuntuforums.org/showpost.php?p=10892454&postcount=194](http://ubuntuforums.org/showpost.php?p=10892454&postcount=194)

---

### Post by cbowman57 on 2011-05-22
> **maverick280857 said:**
> Hi,

I'm running Gnome3 on a Ubuntu 11.04 x64 box. I have a whole bunch of jpeg images in my Pictures folder, and I'm wondering if it is possible to iterate over the background images somehow.

In other words, I want to pick a jpeg file at random from $HOME/Pictures, and set it as the background image for 'x' seconds, before transitioning to another randomly selected image.

I have found Perl-based scripts elsewhere on this forum, but they don't work with Gnome3 (or at least I haven't been able to get them to work). It seems these solutions are for Gnome2.

Secondly, is it possible to add screensaver support to Gnome3?


I would appreciate any inputs or ideas on these issues, especially the desirable rotating background feature.

Try desktopnova for the wallpaper changer.  Not sure about the screensaver.

---

### Post by maverick280857 on 2011-05-22
> **cbowman57 said:**
> Try desktopnova for the wallpaper changer.  Not sure about the screensaver.

Desktopnova does not work for Gnome3. I already tried it.

---

### Post by cbowman57 on 2011-05-22
> **maverick280857 said:**
> Desktopnova does not work for Gnome3. I already tried it.

Yeah, I gave it a go too.  Guess it can't display through mutter yet.

---

### Post by maverick280857 on 2011-05-22
Okay so I'm thinking about how one changes the background by hand. You right click on the desktop, select 'Change desktop background', select something from the drop down menu (in my case 'Pictures Folder') and finally pick an image, and then *close* this window.

So

1. What is the command I'd have to issue to open the Background window?
2. How do I design a backend script which

(a) picks a random jpg file from $HOME/Pictures (or any folder) and stores it in STRING
(b) opens the Background window, somehow "selects" the icon correspdonding to STRING, and then closes the Background window.

I know this is a crude way of thinking about the problem: Gnome3 obviously stores the background setting somewhere in the xml framework (I am only just beginning to understand this, so please bear with my ignorance).

---

### Post by cbowman57 on 2011-05-22
I'm no scripting wiz, hopefully somebody will come up with an answer.  Shouldn't be that difficult for somebody with skills.

---

### Post by maverick280857 on 2011-05-23
I don't know much about it either. But from the looks of it, there aren't very many active threads on this issue for Gnome3/Gnome-Shell. I should probably check how the Fedora and SUSE folks have gotten it to work (if at all)..

EDIT: I'm keeping this thread active and 'unsolved'. If I find anything useful/interesting, I'll post it here.

---

### Post by maverick280857 on 2011-05-24
Just as I was trying to write a script to change stuff using the info at [http://stackoverflow.com/questions/4928738/shell-script-copy-and-paste-a-random-file-from-a-directory](http://stackoverflow.com/questions/4928738/shell-script-copy-and-paste-a-random-file-from-a-directory),

```

files=(Pictures/*)
filecount="${#files[@]}"
randomid=$((RANDOM % filecount))
filepick="${files[$randomid]}"
echo $filepick
gsettings set org.gnome.desktop.background picture-uri 'file://$filepick'

```

I encountered

[https://bbs.archlinux.org/viewtopic.php?pid=933248](https://bbs.archlinux.org/viewtopic.php?pid=933248)

which solves the problem. The script is

```

# Credits: https://bbs.archlinux.org/viewtopic.php?pid=933248
#!/usr/bin/perl -w
use strict;
use warnings;

my $searchPath = '~/Pictures/';   # Set to the directory you want to have searched for photos
my $switchTime = 30;               # Edit to the number of seconds between photo switches

my @photos = `find $searchPath -type f | grep [jJ][pP][eE]*[gG]`;             
chomp(@photos);
my $photo;

while(1)
{
    $photo = $photos[rand($#photos)];
     `gsettings set org.gnome.desktop.background picture-uri "file:///$photo"`;
    sleep($switchTime);
}
```

First do

```
chmod +x shifter
```

To execute the script, use

```
shifter &
```

I am marking this thread **SOLVED** as the screensaver is unlikely to arrive anytime soon.

Hope this helps.

Creating a file by the name shifter.desktop under $HOME/.config/autostart/ with the following lines, makes the script run at startup.

```

[Desktop Entry]
Type=Application
Exec=/home/username/shifter &
Hidden=false
X-GNOME-Autostart-enabled=true
Name[en_US]=shifter
Name=shifter
Comment[en_US]=Rotate wallpaper
Comment=Rotate wallpaper

```

Note: The ampersand is important otherwise multiple processes seem to get spawned. I am not sure if the script is terminated when I log out, but that is a minor problem which I am sure can be solved..

Dynamic wallpaper in Gnome3! Yay! :)

**EDIT**: For some users, the script may continue to run after they log off. If you see multiple processes running when you issue the command

```
ps -ef |grep shifter
```

then you need to make an addition to the script /etc/gdm/PostSession/Default, to kill the instance of the script you initiate when you log into the shell. This can be done by adding the line

```
kill -9 $(pgrep shifter)
```

to /etc/gdm/PostSession/Default, before 'exit 0'. After this addition, the script on my system looks like this:

```

#!/bin/sh

kill -9 $(pgrep shifter2)

exit 0

```

---

### Post by 23dornot23d on 2011-05-24
> 
Hope this helps.

Now I just have to figure out how to start this script automatically in  every gnome session. Adding it to gnome-session-properties did not help  btw.     

I like it ...... just set it up ...... superb ty ..... 

It also picks out of any folders in there too .... home/Pictures/....

---

### Post by maverick280857 on 2011-05-24
You're welcome. I just posted a fix for how to get this script to auto-execute. I would like to know from you and others if it continues to run after you log out. This can be checked by logging in and out a couple of times and checking the process using

```
ps -ef |grep shifter
```

You should see only one instance of it running, synchronized nearly with the time you logged in (give or take a few seconds of course). If you see multiple processes, we have to figure out a way to stop the script when one logs off.

---

### Post by maverick280857 on 2011-05-24
For every login session, one instance of the perl script starts and keeps running indefinitely, because of the infinite loop. The ampersand has nothing to do with it (I just checked).

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> For every login session, one instance of the perl script starts and keeps running indefinitely, because of the infinite loop. The ampersand has nothing to do with it (I just checked).

Nice, haven't run it yet but just set it up.

---

### Post by 23dornot23d on 2011-05-24
keith@keith-Aspire-7730ZG:~$ ps -ef |grep shifter.perl
keith    14065 14005  0 05:03 pts/0    00:00:00 grep --color=auto shifter.perl
keith@keith-Aspire-7730ZG:~$ 


Just one entry ..... but its weird ..... log out and log in again and its stopped .....
I tried creating a launcher for it too ..... 

( but then I do get multiples and it does not appear to run through the pictures as before .....  )

---

### Post by maverick280857 on 2011-05-25
> **23dornot23d said:**
> keith@keith-Aspire-7730ZG:~$ ps -ef |grep shifter.perl
keith    14065 14005  0 05:03 pts/0    00:00:00 grep --color=auto shifter.perl
keith@keith-Aspire-7730ZG:~$ 


Just one entry ..... but its weird ..... log out and log in again and its stopped .....
I tried creating a launcher for it too ..... 

( but then I do get multiples and it does not appear to run through the pictures as before .....  )

There is no entry corresponding to the script, so it's not running. You may have some problems with the executability. I don't think it matters, but you could try renaming the file to shifter (the extension is irrelevant, because of the first line in the file, which tells you how the file has to be executed). Then run

```
chmod +x shifter
```

What does your $HOME/.config/autostart/shifter.desktop look like?

Are you able to run the script from the terminal manually?

```
./shifter &
```

Finally, I hope you don't have SELinux or something which is killing the execution of the Perl script?

---

### Post by 23dornot23d on 2011-05-25
I have now renamed it to shifter (no extension) //// .... still no luck now ....
and it is executable ..... too .... 
( it ran once I had the file named with the extension but I also put that into the
shifter.desktop file too ........ and now it does not run .... edited the files and its just shifter
now ........ plus the main script is just shifter too .... )

[IMG]http://img3.imageshack.us/img3/7544/shifter1.jpg[/IMG]


Here is the script ...

[IMG]http://img593.imageshack.us/img593/4151/shifter2.jpg[/IMG]


I made a launcher on the desktop so that it could be run just when I want it to too ..... but that is not working
anymore .... not sure what happened .... not done any upgrades yet on this machine,

---

### Post by maverick280857 on 2011-05-25
Is the file named shifter.desktop~ or shifter.desktop? It's the latter you want. Offhand, I can't think of a reason why you're facing this problem. If the attributes are set correctly, you should be able to execute the script using

```
shifter &
```

the perl -w in the first line instructs the shell that this is a Perl script. Of course as I said before you need to do

```
chmod +x shifter
```

first. So the question is, can you run the script manually, from a terminal window?

I just did a fresh install of Natty and Gnome3 on my desktop, and am successfully using the script on it. I had earlier been using it on my laptop. So, maybe it has to do with permissions on your system...

PS -- In the shifter.desktop file, try getting rid of the ampersand:

```
Exec=/home/keith/shifter
```

Does that help?

Otherwise, get rid of the desktop file, and use gnome-session-properties (this did not work for me though).

---

### Post by 23dornot23d on 2011-05-25
It runs if I do

perl shifter &

So the script is fine and it does execute ..... maybe I need 

perl 

infront to get it to work properly ..... or does this cause a problem ..... that I cannot see yet .......

But it works fine now am watching it change again .... quite nice too .... may I add  ;)

I will try your recommendation too .... ty

[IMG]http://img685.imageshack.us/img685/6867/screenshot7tf.jpg[/IMG]

Exec=/home/keith/shifter

[IMG]http://img7.imageshack.us/img7/3235/screenshot8gl.jpg[/IMG]


So much wasted space ..... ;)

---

### Post by maverick280857 on 2011-05-26
> **23dornot23d said:**
> infront to get it to work properly ..... or does this cause a problem ..... that I cannot see yet .......

No problem that I'm aware of..it is (should be) redundant if you make the file executable, because it already has a 'perl -w' sticking out on the first line, which instructs the shell to use Perl to execute it. But maybe not on your system, for some reason.

Anyway, glad to know that it works.

---

### Post by maverick280857 on 2011-06-05
A fix added to prevent multiple instances of the dynamic wallpaper script from starting, in post #8: [http://ubuntuforums.org/showpost.php?p=10858322&postcount=8](http://ubuntuforums.org/showpost.php?p=10858322&postcount=8). This used to happen if you would log out and log back in (or at least it happened for me).

---


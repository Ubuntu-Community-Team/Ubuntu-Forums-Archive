---
title: "zsnes help"
date: 2007-01-11
forum: Gaming &amp; Leisure
---

### Post by valke on 2007-01-11
I compiled from source zsnes. it worked great for three hours, and ever since i tried to change the resolution it up and died. what i mean by that specifically is that no matter how i start it, from shortcuts, and even from terminal, it flashes up on the screen and dissapears. in the system monitor, it just blinks for a second. zsnes is crashing i think. please do help.:confused:

---

### Post by po0f on 2007-01-11
valke,

Which version did you compile?  The new 1.5.0 or 1.4.2?

You can manually change which resolution zsnes starts out at by editing ~/.zsnes/zsnesl.cfg.

---

### Post by valke on 2007-01-11
uhh, thats a good question, it is 1.50. also, i cannot find that file.

could you walk me through how to do this?

```
valke@valke-laptop:~$ ~/.zsnes/zsnesl.cfg.
bash: /home/valke/.zsnes/zsnesl.cfg.: No such file or directory
valke@valke-laptop:~$ 

```

---

### Post by po0f on 2007-01-11
valke,

If 1.50 is the same as 1.42, all your configuration data resides in ~/.zsnes.  Open up Nautilus and from your home directory ('~' for short), right-click and choose "Show hidden files".  A bunch of stuff should now be visible, hopefully among them, a '.zsnes' directory.  Double-click on it.  There should be a file called 'zsnesl.cfg' in there.  You can open it up in GEdit and change the resolution.  It's well commented, so you shouldn't have any problems figuring out what to do from here.

[EDIT]

Ok, can you cd to ~/.zsnes and post what `ls` says?
```
[font="Courier New"]$ cd ~/.zsnes
$ ls -l[/font]
```

---

### Post by valke on 2007-01-11
edit:```
total 76
-rw-r--r-- 1 valke valke  8192 2007-01-10 21:17 BahamutLagoon.srm
-rw-r--r-- 1 valke valke  8192 2007-01-10 21:14 ff6.srm
-rw-r--r-- 1 valke valke  8192 2007-01-10 21:14 ffv.srm
-rw-r--r-- 1 valke valke  8192 2007-01-11 00:07 romancing.srm
-rw-r--r-- 1 valke valke   241 2007-01-11 00:06 rominfo.txt
-rw-r--r-- 1 valke valke  2048 2007-01-10 21:14 Super Mario World.srm
-rw-r--r-- 1 valke valke  8105 2007-01-10 20:43 zfont.txt
-rw-r--r-- 1 valke valke  3317 2007-01-11 01:30 zinput.cfg
-rw-r--r-- 1 valke valke  2439 2007-01-11 01:30 zmovie.cfg
-rw-r--r-- 1 valke valke 16958 2007-01-11 01:30 zsnesl.cfg

```

---

### Post by po0f on 2007-01-11
valke,

There is no .zsnes directory in your home dir?  That is weird.  I haven't yet compiled 1.50, but now I am.  I'll report back.

Considering this is a new version, you might have run into a bug.  Just a thought.

[EDIT]

The file zsnesl.cfg is the one you want to edit.

---

### Post by valke on 2007-01-11
it DOES say its there... huh? i don't know why i can't edit it then.

edit [www.zsnes.com](www.zsnes.com) is where i got it from. there is a message board there that tells you how to compile.

---

### Post by po0f on 2007-01-11
valke,

In Nautilus, hit Ctrl+L to open up the location bar (IIRC).  In there, type in "/home/valke/.zsnes".  Then double-click on the file.  It should open up in GEdit.

---

### Post by valke on 2007-01-11
ok, poof, and all i do is click save after i have made the changes right?

edit: so far so good, just searching other posts now.

---

### Post by valke on 2007-01-11
did not work, how do i uninstal and start over? or do i need to re "make" it? advice is greatly appreciated.](*,)

---

### Post by po0f on 2007-01-11
valke,

Honestly, I would just stick with 1.42 as it's in the repos.  Any special reason you want to compile 1.50 from source?

---

### Post by valke on 2007-01-11
no, honestly not really. is it in synaptic? and just to remove 1.50 i delete the folder zsnes right? i thank you so much for helping me.:KS

---

### Post by po0f on 2007-01-11
valke,

Yes, you can install it through Synaptic if you have the multiverse repos enabled.  I'm sorry, I would have suggested this earlier if I knew you weren't just wanting to test out 1.50.

How did you install zsnes 1.50?  Which options did you pass to ./configure, and did you `make install` it?

---

### Post by valke on 2007-01-11
belive it or not all i did was this:

```
sudo apt-get install build-essential nasm autoconf automake libsdl1.2-dev zlib1g-dev libpng12-dev subversion mesa-common-dev
cd ~
rm -rf zsnes
svn co https://svn.bountysource.com/zsnes/trunk/ zsnes
cd zsnes/src
./autogen.sh
make
sudo make install 
```

it was so easy and quick, now mind you i have absolutely no experience with terminal or its language, nor do i know anything about ubuntu. i have only had ubuntu for three weeks. i love it though.

---

### Post by po0f on 2007-01-11
valke,

Before you install zsnes from the repos, what does this command output?
```
[FONT="Courier New"]$ which zsnes[/FONT]
```
You should be able to just delete whatever file it spits at you to uninstall zsnes 1.50.  After that, `rm -rf ~/.zsnes` to get rid of the old config files, and install zsnes from the repos.

---

### Post by BoyOfDestiny on 2007-01-11
> **po0f said:**
> valke,

Honestly, I would just stick with 1.42 as it's in the repos.  Any special reason you want to compile 1.50 from source?

Erm,

[http://forums.emulator-zone.com/showthread.php?t=8371](http://forums.emulator-zone.com/showthread.php?t=8371)

Tremendous change log...

Anyway, Valka, don't give up man.

open up a terminal

type

rm  ~/.zsnes/zsnesl.cfg

Give it a go. :)

---

### Post by po0f on 2007-01-11
BoyOfDestiny,

Yes, I do realize that it has a tremendous changelog, so big that I didn't bother reading it.  1.42 works perfectly for me though (perfectly as in no issues whatsoever), so why upgrade?

---

### Post by valke on 2007-01-11
```
/usr/local/bin/zsnes
```

thats what it tells me.

---

### Post by BoyOfDestiny on 2007-01-11
> **po0f said:**
> BoyOfDestiny,

Yes, I do realize that it has a tremendous changelog, so big that I didn't bother reading it.  1.42 works perfectly for me though (perfectly as in no issues whatsoever), so why upgrade?

Well 3 only are meaningful for me. 
1 is it keeps the ratio for for widescreen (meaning I get two vertical bars instead of distortion)

2) No funky white line bug on the top of the screen in super metroid.

3) Multiple ips softpatching.

If it works for you, and you don't need the new features, keep it. But to discourage someone just because the older package is there... I'd rather they give it a shot... Didn't mean any harm by it.

---

### Post by valke on 2007-01-11
hey its all good, no worries. ok so now what?

---

### Post by BoyOfDestiny on 2007-01-11
> **valke said:**
> hey its all good, no worries. ok so now what?

Well if you're going for zsnes 1.42

Just go ahead and install from the repo, should hopefully override your old one if I'm not mistaken.

Make sure to remove the config files from ~/.zsnes You can keep your srm (save ram files)

Or if you are sticking with 1.50. Do the command I posted to remove the config. And try launching zsnes

*you can launch from terminal with the command)
zsnes

See if it works, or if you have any error messages?

---

### Post by valke on 2007-01-11
access denied.

how to i get into root mode? is that why it is saying that?:confused:

---

### Post by BoyOfDestiny on 2007-01-11
> **valke said:**
> access denied.

how to i get into root mode? is that why it is saying that?:confused:

hmm, can you paste what you are typing and terminal output?

---

### Post by valke on 2007-01-11
nevermind, synaptic was still running.

---

### Post by valke on 2007-01-11
erm, does this look right?

```
valke@valke-laptop:~$ rm ~/.zsnes/zsnesl.cfg
valke@valke-laptop:~$
```:-k

---

### Post by BoyOfDestiny on 2007-01-11
Yup.

---

### Post by valke on 2007-01-11
```
valke@valke-laptop:~$ znes
bash: znes: command not found
valke@valke-laptop:~$ 

```

---

### Post by BoyOfDestiny on 2007-01-11
> **valke said:**
> ```
valke@valke-laptop:~$ znes
bash: znes: command not found
valke@valke-laptop:~$ 

```

zsnes :)

A hint for commandline

you can press tab to complete commands and filenames

try typing
zsn then hit tab to see what I mean...

---

### Post by valke on 2007-01-11
um i think i have it. ok andria's dumb question time...

how do i make a shortcut in my applications drop down list?

edit: oh wow thats really cool! it worked! tab IS good for something!

---

### Post by BoyOfDestiny on 2007-01-11
> **valke said:**
> um i think i have it. ok andria's dumb question time...

how do i make a shortcut in my applications drop down list?

Well the gui way.

Right click on applications

Choose Edit menu

Click Games (or make a new menu I guess)

click new item

from name put ZSNES (or whatever)

and command zsnes

If you click "no icon"

you can select a nice zsnes icon, which came with the source code you got. Not sure where you have it but should be something like zsnes/src/icons

EDIT: Yep commandline is cool, a few other commands I really like are history and grep

for example

type

history | grep zsnes

It will list all the commands you've typed with the word zsnes in it...

---

### Post by valke on 2007-01-11
thanks so much for your help. both of you.:KS

---

### Post by BoyOfDestiny on 2007-01-11
> **valke said:**
> thanks so much for your help. both of you.:KS

No problem. Have fun!

---

### Post by valke on 2007-01-11
out of sheer curiousity, do you know about changing the icon of the trash can? i added you to my buddy list. btw.

---

### Post by BoyOfDestiny on 2007-01-11
> **valke said:**
> out of sheer curiousity, do you know about changing the icon of the trash can? i added you to my buddy list. btw.

Thanks, I'll add ya too.

Hmm the trash can in the lower right bar (or do you have the icon on the desktop)

From what I can tell, it's tied to the Theme. (System -> Preferences -> Theme) You can choose just to modify the icon set by going to custom. 

I'm not sure it's more flexible than that...There might be a way to change using gconf-editor... Maybe start another thread in a different section... (Sorry I wasn't much help on this question)

---


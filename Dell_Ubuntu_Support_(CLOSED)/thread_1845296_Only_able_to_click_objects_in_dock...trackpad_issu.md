---
title: "Only able to click objects in dock...trackpad issue?"
date: 2011-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mister.v on 2011-09-16
So I recently installed Natty Narwhal on an old Dell Inspiron B130 laptop I had lying around. 
For the first week or so it was great--certainly zippier than the original XP install-- but then it started to not let me minimize/maximize windows. 

This problem soon progressed into not letting me click any buttons. However, it does let me right-click on things and select programs from the dock. It also lets me click into text entry fields. 
It's not as if clicking itself is the option; when I roll the mouse over buttons, they don't change colour as usual. 

Somehow, though, I can use key commands to open/close windows and tabs without the use of the trackpad, so I reckon it's a driver issue of some sort. I tried plugging in a Logitech wired mouse to see if that would do anything, but it didn't register.

Anyway, thanks for your time. I hope I can get an answer! :)

---

### Post by mister.v on 2011-09-17
shameless self bump

---

### Post by Lisiano on 2011-09-17
First thing first. I'm not a Dell expert of ANY sort.
Does the touchpad work normally before you log in?
Can you remember installing some software or changing some settings before this started?
Try installing xinput (Not sure if it's pre-installed) ```
sudo apt-get install xinput
``` then type ```
xinput list
``` before you connect a mouse then connect one, wait a few seconds and do it again, post the output here.

---

### Post by mister.v on 2011-09-18
> **Lisiano said:**
> First thing first. I'm not a Dell expert of ANY sort.
Does the touchpad work normally before you log in?
Can you remember installing some software or changing some settings before this started?
Try installing xinput (Not sure if it's pre-installed) ```
sudo apt-get install xinput
``` then type ```
xinput list
``` before you connect a mouse then connect one, wait a few seconds and do it again, post the output here.

The last thing I tried to install was Sun Java. And since I have it set to auto login, I couldn't say, nor would it let me go in to change that, on account of the original problem.
Oddly enough, when I booted up to do the xinput thing, it did let me make new tabs in FF and change between them, though it still refused to let me click buttons in system dialogs or move/close/whatever windows. 

When I did that, I got the same result regardless of the mouse being plugged in:
> 
Virtual core pointer id=2 [master pointer (3)]
    -> Virtual core XTEST                        id=2 [slave pointer (2)]
    -> SynPS/2 Synaptics TouchPad        id=10 [slave pointer (2)]
Virtual core keyboard                             id=3 [master keyboard (2)]
    -> Virtual core XTEST keyboard         id=5 [slave keyboard (3)]
    -> Video Bus                                     id=6 [slave keyboard (3)]
    -> Power Button                                id=7 [slave keyboard (3)]
    -> Sleep Button                                 id=8 [slave keyboard (3)]
    -> AT Translated Set 2 Keyboard       id=9 [slave keyboard (3)]


Is it worth trying a clean install, or do you think the problem will crop up again?

Thanks!

---

### Post by mister.v on 2011-09-19
can anyone help me or should I just do a clean install and hope it doesn't happen again?

EDIT: Actually, I just reinstalled Ubuntu and the problem still happens. I plugged in a different mouse and the same problem was produced. I'm thinking it has something to do with the laptop itself, now?

---

### Post by Lisiano on 2011-09-20
The USB mouse thing... Well it looks like it's because of the laptop itself, maybe booting with the mouse already connected might help.
After re-reading it a few times, do you by any chance use Compiz?
you can check if it's running by copy pasting this command
```
ps aux | grep compiz | grep -v compiz
```

---

### Post by mister.v on 2011-09-21
> **Lisiano said:**
> The USB mouse thing... Well it looks like it's because of the laptop itself, maybe booting with the mouse already connected might help.
After re-reading it a few times, do you by any chance use Compiz?
you can check if it's running by copy pasting this command
```
ps aux | grep compiz | grep -v compiz
```

Well booting with the mouse pre-connected seems to solve the problem. Still not sure if it's a driver issue or the trackpad dying of old age, though. And running that code in terminal does nothing.

---

### Post by Lisiano on 2011-09-22
Sorry. I mistyped the command.
It should have been this
```
ps aux | grep compiz | grep -v grep
```
ps tells us what processes are running
grep finds a specific line containing compiz
2nd grep removes any entry with the word grep since it is shown in ps.
That time I mistyped the command so that it removed any entry with the word compiz, thus empty. Try running this one, if this comes out empty, this means you aren't using compiz, if not, you are.

---


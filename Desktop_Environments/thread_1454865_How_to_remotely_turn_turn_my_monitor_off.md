---
title: "How to remotely turn turn my monitor off"
date: 2010-04-15
forum: Desktop Environments
---

### Post by bobdobbs on 2010-04-15
Hi guys.

I'd like to know if, given ssh access, I can turn off the signal to the screen of my desktop workstation's monitor.

My remote machine is running ubuntu 9.10, and I have have ssh access to it.

It's all the way over at my desk, perhaps three metres away. I'm in bed with my laptop, and I don't want to have to go all the way over there to turn it off before I go to sleep.

The screen is constantly flashing because it my browser is open and showing javascript animations that I've been working on.

I could ssh in and kill my browser, but this is a second-best solution.

Any suggestions ?

---

### Post by mcduck on 2010-04-15
At least when you are running X you can use the following command:

```
xset dpms force off
```

---

### Post by nothingspecial on 2010-04-15
I don`t know how turn actually turn the monitor off, but I have these 2 aliases in my laptop`s .bashrc to lock and unlock the screen of the main pc
```

alias lock="ssh -X user@address \"export DISPLAY=:0; gnome-screensaver; gnome-screensaver-command -l;\""
alias unlock="ssh -X user@address \"export DISPLAY=:0; gnome-screensaver; gnome-screensaver-command -d;\""
```

So I just type ```
lock
``` when I`m being a mean old dad, and ```
unlock
``` when I am being a gracious and benevolent father.

The screen will go dark.

---

### Post by bobdobbs on 2010-04-17
> **mcduck said:**
> At least when you are running X you can use the following command:

```
xset dpms force off
```


This command returns this:
```
xset:  unable to open display "0"
```

My guess is that this command works best locally.

---

### Post by bobdobbs on 2010-04-17
> **nothingspecial said:**
> I don`t know how turn actually turn the monitor off, but I have these 2 aliases in my laptop`s .bashrc to lock and unlock the screen of the main pc
```

alias lock="ssh -X user@address \"export DISPLAY=:0; gnome-screensaver; gnome-screensaver-command -l;\""
alias unlock="ssh -X user@address \"export DISPLAY=:0; gnome-screensaver; gnome-screensaver-command -d;\""
```

So I just type ```
lock
``` when I`m being a mean old dad, and ```
unlock
``` when I am being a gracious and benevolent father.

The screen will go dark.

Thats a pretty nifty trick, niftily employed.

Unfortunately, I can't figure out how to adapt the commands for my case.
If I ssh into my target host and issue "gnome-screensaver", I get this:

```
** (gnome-screensaver:32277): WARNING **: Cannot open display: 
```

I find X really confusing, so I'm not sure what this means.
But I'm guessing that this tells me that this command can't be issued remotely.

---

### Post by mcduck on 2010-04-17
Try using the "-Y" option with the ssh command, that should sort the display problem automatically for you.

Alternatively you could try exporting the DISPLAY variable, like in the command nothingspecial suggested.

export DISPLAY=*remote machine name*:0; xset dpms force off

---

### Post by bobdobbs on 2010-04-17
> **mcduck said:**
> Try using the "-Y" option with the ssh command, that should sort the display problem automatically for you.

Alternatively you could try exporting the DISPLAY variable, like in the command nothingspecial suggested.

export DISPLAY=*remote machine name*:0; xset dpms force off

Alas, these remedies don't seem to work.
This is what I'm doing:
```
ssh -Y remotehost
```
```
export DISPLAY=0
```
```
gnome-screensaver
```

And then I still get this:
```
** (gnome-screensaver:4901): WARNING **: Cannot open display:
```

Then I try gnome-screensaver, and I get this:
```
** (gnome-screensaver:4901): WARNING **: Cannot open display:
``` 

What am I missing ?

---

### Post by nothingspecial on 2010-04-18
Sorry to ask the obvious, but is your remote machine running a default Ubuntu install with gnome-screensaver installed?

---

### Post by bobdobbs on 2010-04-18
> **nothingspecial said:**
> Sorry to ask the obvious, but is your remote machine running a default Ubuntu install with gnome-screensaver installed?

Not quiet a default installation.
It's ubuntu studio, based on ubuntu 9.10.

Ubuntu studio is pretty much just ubuntu with some extra packages installed for multimedia production.

It does indeed have gnome-screensaver installed.

---

### Post by vol7ron on 2010-04-28
I'm trying to learn Linux for work and found this thread interesting.  Although we're not using Ubuntu at work, I've installed it at home (I know all Linux versions are not created equal) to learn more and understand how the different shells operate.

I could see this being useful, especially with iPhone SSH integration.

Does it help if you change "export DISPLAY=0" to "export DISPLAY=:0" (with the colon)?

vol7ron

---

### Post by jasonnur on 2010-04-28
Yea of course...

---

### Post by jasonnur on 2010-04-28
Yea of course...




  [ colour   copying]("http://www.thecolorcopystore.com/store/storePage.aspx?id=937") | [ colour prints]("http://www.thecolorcopystore.com/store/storePage.aspx?id=937")

---

### Post by nothingspecial on 2010-04-28
I realize copying and pasting stuff you randomly find on the internet (and then adapting it to your personal want) can be a bad idea.

But if you are uncomfortable with it then you have to research it fully and type it correctly.

No offence meant, to anyone, but ............

---


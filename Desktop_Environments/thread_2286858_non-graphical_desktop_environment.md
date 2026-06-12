---
title: "non-graphical desktop environment?"
date: 2015-07-15
forum: Desktop Environments
---

### Post by ashley-a on 2015-07-15
Hello All!
I am new to these forums (but not to Ubuntu), and I would like to know if there is a desktop environment I can get (preferably with the apt-get command) that opens something like the alt-ctrl-F1, alt-ctrl-F2, etc. command windows...but on alt-ctrl-F7?

Thanks!

---

### Post by sudodus on 2015-07-15
Welcome to the Ubuntu Forums :-)

Do you want a simple Ubuntu based system without a graphical user interface, or do you want a system that can switch the user interface on 'alt-ctrl-F7' between a graphical user interface and a text user interface?

And how do you intend to use this feature?

---

### Post by ashley-a on 2015-07-15
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Do you want a simple Ubuntu based system without a graphical user interface, or do you want a system that can switch the user interface on 'alt-ctrl-F7' between a graphical user interface and a text user interface?

And how do you intend to use this feature?

Wow! Thanks for the quick reply!

I'm going to expand on my original post...It should answer your question in doing so...

What I need, is either:
a) A lightweight desktop interface that brings up something the same as, or equivalent to the alt/ctrl/F1-F6 stuff when I login, or
b) An option in my GRUB boot menu to boot to a linux command line. 

To clarify option B, I need it to boot with the "/" directory on my Ubuntu "/" directory, so it has to be a part of Ubuntu, or some sort of add-on.

Now for how I intend to use this:

I have found, and then edited to suit my needs, a program that will run my linux server's commands (which I need on my laptop, as I have no screen on my server), for my home business. Unfortunately, this program is extremely laggy after my modifications, and even if I'm running it on alt/ctrl/F1 with openbox in the background, as oppose to unity (which is very slow on my ancient laptop), it still lags. If I can have a command-line, without a graphical environment, it should free my system resources for this Ram/SWAP hogging program.

Hope this answers your questions!
I apologize for any spelling errors. I am typing in haste!

---

### Post by sudodus on 2015-07-15
If you add the [boot option](https://help.ubuntu.com/community/BootOptions) **text** the computer will boot into a text screen.

```
$ grep text /etc/default/grub
GRUB_CMDLINE_LINUX="text"
```

Run ```
sudo update-grub
``` to make it active.

After doing the heavy server stuff you can start the graphical desktop environment (or if you wish a simple window manager - openbox) with a command.

I have a small script 'x' in my bin directory,

```
$ cat ~/bin/x
#!/bin/bash

ans="$(ps -A|grep \ lightdm$)"
res=$?
if [ "$res" == "0" ]
then
 echo "x (lightdm) is already running"
else
 echo "x will be started:"
 echo "sudo service lightdm start"
 sudo service lightdm start
fi
```

---

### Post by grahammechanical on 2015-07-15
As far as I know, what we get when we hit Ctrl+Alt+F1 (tty1/console 1) is the Linux Command line. Linux loads on tty 1 and Ubuntu runs on tty 7 (Ctrl+Alt+f7). This "lag" could be cause by the data download rates of the network connection or the simple effect of managing a server over a network.

I do not know anything about that. But I do know that when I hit Crtl+Alt+F1 or +F2 through to +F6 I am at a Linux command line and I have to log in. And by hitting Ctrl+Alt+F7 I get back to the graphical desktop environment.

Regards.

---

### Post by ashley-a on 2015-07-15
> **sudodus said:**
> If you add the [boot option]("https://help.ubuntu.com/community/BootOptions") **text** the computer will boot into a text screen.

```
$ grep text /etc/default/grub
GRUB_CMDLINE_LINUX="text"
```

Run ```
sudo update-grub
``` to make it active.
Hmm...That hasn't seemed to have worked for me. I did ```
sudo gedit /etc/default/grub
``` and edited it from there. Will test it soon...

> **sudodus said:**
> After doing the heavy server stuff you can start the graphical desktop environment (or if you wish a simple window manager - openbox) with a command.

I have a small script 'x' in my bin directory,

```
$ cat ~/bin/x
#!/bin/bash

ans="$(ps -A|grep \ lightdm$)"
res=$?
if [ "$res" == "0" ]
then
 echo "x (lightdm) is already running"
else
 echo "x will be started:"
 echo "sudo service lightdm start"
 sudo service lightdm start
fi
```
Your 'x' script worked...as far as I can tell...but it keeps bringing up 'permission denied' or 'command not found' when I run with sudo. This is because I am running from tty1 instead of through your first lot of code, yes?

Ok. Have tried rebooting...no luck. The ```
GRUB_CMDLINE_LINUX="text"
``` had no effect. Is there something I am not understanding?

---

### Post by ashley-a on 2015-07-15
> **grahammechanical said:**
> As far as I know, what we get when we hit Ctrl+Alt+F1 (tty1/console 1) is the Linux Command line. Linux loads on tty 1 and Ubuntu runs on tty 7 (Ctrl+Alt+f7). This "lag" could be cause by the data download rates of the network connection or the simple effect of managing a server over a network.
I had thought this too, so I connected my server to my laptop directly over a single LAN cable, just to see if there was an improvement. There was an improvement, but not a dramatic one. Once I get (if I get) this non-graphical mode going on my laptop, I'll look more deeply into that.

---

### Post by sudodus on 2015-07-16
> **ashley-a said:**
> Hmm...That hasn't seemed to have worked for me. I did ```
sudo gedit /etc/default/grub
``` and edited it from there. Will test it soon...


Your 'x' script worked...as far as I can tell...but it keeps bringing up 'permission denied' or 'command not found' when I run with sudo. This is because I am running from tty1 instead of through your first lot of code, yes?

Ok. Have tried rebooting...no luck. The ```
GRUB_CMDLINE_LINUX="text"
``` had no effect. Is there something I am not understanding?

This advice is actually copying what I do in one of my computers, and it works for me.

Did you run ```
sudo update-grub
``` before rebooting?

I type ***x*** [and press the Enter key]. There is sudo 'inside' the script x. Did you make the script executable?

```
chmod ugo+x ~/bin/x
```

What is the problem with sudo? Are you running a user ID, that has no sudo permissions? Check with the following command and edit the file accordingly, if necessary when booted from a live drive with ubuntu or lubuntu or ... (to have the permissions)

```
$ grep ^sudo: /etc/group
sudo:x:27:nio,sudodus
```

(*Your* user IDs should show up there.)

-o-

All these commands are intended to be run locally (not remotely via ssh).

---

### Post by ashley-a on 2015-07-16
Ok, Sudodus. I did forget to make it executable...got through that with ```
sudo chmod
``` and then ran 'x' on tty1 and got this output: ```

/bin/x: 6: [: 0: unexpected operatorx will be started:
sudo service lightdm start
start: Job is already running: lightdm

```
I take it that means it works.
Now I just need to get the GRUB thing to boot with text. It still won't work. I did update the grub file previously. Any ideas?

---

### Post by sudodus on 2015-07-16
Check during booting:

At the grub menu, press ***e*** to view and edit the command line. Check the line starting with linux (it might be wrapped if too long for the screen). Near the end, you should find the boot option **text**. If it is not there, write it there


```
linux ... text --
```

And then press ***ctrl + x***

---

### Post by ashley-a on 2015-07-16
Going to type this post play-by-play.
I'm currently in the ctrl+e GRUB, and there is no 'text' tag. Will put that on...
Ok, ctrl+x...it's booting (no quiet splash. Disabled that long ago).
Ok, I think it worked. I have tty1 up there...Going to test a connection to my server, see if this has done anything...
It worked, and is less laggy. I will still try to get a smaller network, to reduce the lag like grahammechanical said, but this has really helped! Thanks sudodus!
The only problem I've got now is:
If I reboot, I'm going to not have the ```
 text -- 
``` after the Linux stuff, will I? Ill have to do it each time, won't I?

---

### Post by sudodus on 2015-07-17
> **ashley-a said:**
> Going to type this post play-by-play.
I'm currently in the ctrl+e GRUB, and there is no 'text' tag. Will put that on...
Ok, ctrl+x...it's booting (no quiet splash. Disabled that long ago).
Ok, I think it worked. I have tty1 up there...Going to test a connection to my server, see if this has done anything...
It worked, and is less laggy. I will still try to get a smaller network, to reduce the lag like grahammechanical said, but this has really helped! Thanks sudodus!
The only problem I've got now is:
If I reboot, I'm going to not have the ```
 text -- 
``` after the Linux stuff, will I? Ill have to do it each time, won't I?

If your local system is an ***installed*** system and you do the what is described below locally (not remotely via ssh), it ***should*** put the boot option **text** to that place 'behind' the grub menu, and it should work. Please try again. You can refer to the following link:

[Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

> **sudodus said:**
> If you add the [boot option](https://help.ubuntu.com/community/BootOptions) **text** the computer will boot into a text screen.

```
$ sudo nano /etc/default/grub
```
Edit the file, so that the line containing **GRUB_CMDLINE_LINUX=** will look like this:
```
GRUB_CMDLINE_LINUX="text"
```
and save it.

Run ```
sudo update-grub
``` to make it active.


---

### Post by ashley-a on 2015-07-17
Ok, Sudodus, that one worked.
I went back through the forum, and found this post:

> **sudodus said:**
> If you add the [boot option]("https://help.ubuntu.com/community/BootOptions") **text** the computer will boot into a text screen.

```
$ grep text /etc/default/grub
GRUB_CMDLINE_LINUX="text"
```

Run ```
sudo update-grub
``` to make it active.



In that post, you told me to > **sudodus said:**
>  ```
$ grep text /etc/default/grub
GRUB_CMDLINE_LINUX="text"
```  and that did nothing. Then, in your previous post, you told me to > **sudodus said:**
>  ```
[COLOR=#000000]*$ sudo nano /etc/default/grub *[/COLOR]
```
[COLOR=#000000]*Edit the file, so that the line containing *[/COLOR]**GRUB_CMDLINE_LINUX= **will look like this:
```
[B]
GRUB_CMDLINE_LINUX="text" [/B]
```
and save it.

The commands you told me to do were different. The second one works, nevertheless.
Thankyou, Sudodus! You have helped me more than you know!

---

### Post by sudodus on 2015-07-17
Sorry for the confusion. I realized that it was a bad explanation in post #4, and tried to explain it better in post #12. I'm glad that it works for you now :-)

If you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

-o-

Here is an explanation of the first command (in post #4): ```
grep text /etc/default/grub
``` displays the following line ```
GRUB_CMDLINE_LINUX="text"
``` when the text option is there - if it is not there you have to edit the file (which I should have explained). ***grep*** is 'only' a command to search for a string in a file (in this case for the string **text**).

---

### Post by ashley-a on 2015-07-17
> **sudodus said:**
> Sorry for the confusion. I realized that it was a bad explanation in post #4, and tried to explain it better in post #12. I'm glad that it works for you now :-)

If you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

-o-

Here is an explanation of the first command (in post #4): ```
grep text /etc/default/grub
``` displays the following line ```
GRUB_CMDLINE_LINUX="text"
``` when the text option is there - if it is not there you have to edit the file (which I should have explained). ***grep*** is 'only' a command to search for a string in a file (in this case for the string **text**).
Ok. Understood.
Thanks again, sudodus!

---


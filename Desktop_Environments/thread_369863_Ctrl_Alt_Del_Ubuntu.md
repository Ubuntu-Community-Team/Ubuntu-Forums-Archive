---
title: "Ctrl Alt Del Ubuntu"
date: 2007-02-25
forum: Desktop Environments
---

### Post by frog3764 on 2007-02-25
Greetings to the Group - Quite some time ago while testing PCLinux?, a few programs or applications would lock up once in a while.  Probably  due to something I did and shouldn't have been doing as a newbie.  Anyway, I couldn't get out of them and had to re-boot.  What is the counterpart CTRL ALT DEL in Ubuntu to get some sort of program manager to unlock a program that is "hung up" or frozen?  I don't want to re-boot if it happens here as I have Ubuntu set up the way I want and will just add new things as I get comfortable with it.  One time I had to re-install the PCLinux because I screwed up something I did and shouldn't have done.  All help will be appreciated.

Thanks,
The Frog

---

### Post by highneko on 2007-02-25
When a program's running really slow and can't be closed or something I usually do this:
```
[COLOR="DimGray"]# This will enter a full screen terminal called tty1:[/COLOR]
ctl+alt+f1
[COLOR="DimGray"]# Then find the program you wanna kill:[/COLOR]
ps -e | grep programname
[COLOR="DimGray"]# Then when you find the program name kill it:[/COLOR]
killall programname
[COLOR="DimGray"]# Then go back to your display manager using terminal:[/COLOR]
ctl+alt+f7
```
When changing tty just remember ctl+alt+f7 is the one you wanna get back to.

---

### Post by frog3764 on 2007-02-25
Hey thanks Highneko - I tried it to see what it looked like.  After entering my sign on, I got a prompt $.  What do I enter there?  Don't the programs that are running show up so you can select one?  If I need the name, it's too late after it locked up because I won't know the exact name then.  What does this line call  for ps -e | grep?  

The Frog

---

### Post by RedSquirrel on 2007-02-25
> **frog3764 said:**
> Greetings to the Group - Quite some time ago while testing PCLinux?, a few programs or applications would lock up once in a while.  Probably  due to something I did and shouldn't have been doing as a newbie.  Anyway, I couldn't get out of them and had to re-boot.  What is the counterpart CTRL ALT DEL in Ubuntu to get some sort of program manager to unlock a program that is "hung up" or frozen?  I don't want to re-boot if it happens here as I have Ubuntu set up the way I want and will just add new things as I get comfortable with it.  One time I had to re-install the PCLinux because I screwed up something I did and shouldn't have done.  All help will be appreciated.

Thanks,
The Frog

In Ubuntu, press Alt-F2 and then enter the following command:

```
xkill
```That will give you a skull-and-crossbones mouse cursor. Then all you have to do is put the cursor over the program you want to terminate and **click**.

Alternatively, if it's just an application program that has stopped responding and you can switch to another workspace, open up a terminal and follow the instructions highneko gave.

---

### Post by RedSquirrel on 2007-02-25
See "EDIT" at the end of this post. :)

> **frog3764 said:**
> Hey thanks Highneko - I tried it to see what it looked like.  After entering my sign on, I got a prompt $.  What do I enter there?  

Just type in the commands highneko gave.

> Don't the programs that are running show up so you can select one?  They will if you run 

```
ps -e
```> If I need the name, it's too late after it locked up because I won't know the exact name then.  
You don't need to know the *exact* name, just the name of the program you were using that is now locked up.

> What does this line call  for ps -e | grep?  You need to provide a *program name* to search for (firefox, for example).

By the way, are you familiar with the terminal? If not, have a look at this page:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

That whole site ([http://www.psychocats.net/ubuntu]("http://www.psychocats.net/ubuntu/terminal")) is a good starting place for new users.

For future reference, when you don't know what a command is, you can look it up in the man pages (manual pages -  an online manual) using a terminal:

```
man ps
```and

```
man grep
```Here is what those commands had to say:

[I]ps - report a snapshot of the current processes (and the "-e" option is: Select all processes. )
[/I] 
* grep - print lines matching a pattern*

so, 

```
ps -e | grep <program-name>
```will search the list of processes for <program-name>.

If you were trying to shutdown a program like firefox, you would do:

```
ps -e | grep firefox
```and the result would be something like:

```
 5544 ?        00:13:59 firefox-bin

```and you would then do:

```
killall firefox-bin
```[This is just an example, of course. Firefox tends to shutdown all by itself when it runs into trouble.]

That was probably quite a lot to digest, but don't worry. Learning how to terminate processes in linux is *different* from what you may be used to, but you'll get used to it.

Every process (essentially, a program running on your system) has what is known as a pid (process ID). You can terminate (kill) individual processes as well.

The pid in the example above is 5544. So I could use 

```
kill 5544
```If you do

```
ps -e
```the last few items in the list will be things you have run recently, so you can get the pids from there.

Feel free to ask more questions if there's something you don't understand.

EDIT: well, after typing all that and then re-reading your first post, you may be more comfortable (initially) with xkill or there is something called the *Process Manager. *It's in the menus somewhere, but I don't use GNOME anymore so I'm not sure what menu it's in. Shouldn't be too hard to find. 

Knowing how to do things using the terminal is a real bonus, though, IMO.

---

### Post by frog3764 on 2007-02-27
Thanks RedSquirrel, that's a lot to digest, but I will definitely keep it as I know I will need it in the future.  This Ubuntu is definitely a KEEPER!  Windows is on it's way out anyway, according to The Man.  He said Vista is the last Windows OS.  I think from what I've read, that everything will be on the Internet,  like Google Live, Windows or MS Live etc.  Sorry, I got carried away.

Take Care,
The Frog

---

### Post by RedSquirrel on 2007-02-27
> **frog3764 said:**
> Thanks RedSquirrel, that's a lot to digest, but I will definitely keep it as I know I will need it in the future.  This Ubuntu is definitely a KEEPER!  Windows is on it's way out anyway, according to The Man.  He said Vista is the last Windows OS.  I think from what I've read, that everything will be on the Internet,  like Google Live, Windows or MS Live etc.  Sorry, I got carried away.


No worries. I got carried away too! :)

Glad to hear you're enjoying Ubuntu. The great thing is that you can use mostly the graphical stuff initially and then later on, if you're interested, you can learn other concepts like using the terminal and maybe even some programming.

I think it will be a while before *everything* is on the internet, but that day may be coming. We're already seeing some of that, even with Ubuntu, since the basic stuff you need is on **one** CD, and you can get the rest from the internet. Pretty cool.

---


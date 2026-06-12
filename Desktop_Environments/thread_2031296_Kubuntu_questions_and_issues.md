---
title: "Kubuntu questions and issues"
date: 2012-07-21
forum: Desktop Environments
---

### Post by Gikoskos on 2012-07-21
p, li { white-space: pre-wrap; }  [COLOR=#000000][FONT=Ubuntu]Hi all.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu]Most recently I installed Kubuntu 12.04 on my desktop PC, mostly because of the stability of the KDE but i started experiencing some small issues with it.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu]First of all, when i reboot or log out some plasma widgets with buttons appear weird ( the buttons only) and i have to resize the widget for the buttons to look normal again.:confused:[/FONT][/COLOR]

Secondly, during many situation ( expecially when i am surfing the web) the kde panel freezes for some seconds, and as a result i can't choose any other open window from it;
only if i use the Alt+Tab to change windows.


I have only installed apps from the Muon Software Center, except from VLC player which i added from ppa.


Another question i have is why when i open a program the cursor loads and the program 's entry appears on the task manager for many seconds. I have this issue with almost every application, especially Firefox; when i open a link from an external source, even if firefox is open, the link open in another tab but on the panel appears a second firefox loading only to dissappear in a couple of seconds. This proves to be confusing most of the times because when i open a KDE app, i wait some minutes for it to load, only to find that the app has already loaded on the tray.


Lastly, how can i make some keyboard buttons (e.g. the mute button) to work while i am playing a game?

Thanks:P

---

### Post by Gikoskos on 2012-07-22
Bumb hours ago.

---

### Post by smcrossman on 2012-07-23
I'm sorry I don't have any real answers. Except to say that when properly set up Kubuntu is very stable. I think getting it set up is a lot of work.

Also some of your issues aren't so much Kubuntu as on or more modules of KDE (several of which have the fixes set up and ready for release 5.0...no mention on bugzilla whether they are going to put them into releases for the current system).

If no one else can help, and IF you are using PLASMA then you might try changing your type of desktop.  Generally there is a odd little tab on you desktop that says desktop. A simple left click gives you a menu. Choose whichever says something about desktop settings. It should give you a new menu with several options. They all work a little different and on my system only 1 or 2 is stable and consistent.

Now for the non-opening programs. I've had this issue with Ubuntu since upgraded earlier in the year. That seems to be that some programs don't install as executable so it simply isn't going to run.  In my KDE apps it often means the module has crashed or it is set to open minimized (which puts it into an icon on the bar). I have found one or two that my dependencies were not satisfied so again it couldn't run.

Wish I could help more. Do you have the link for the KDE or the Kubuntu forum in case you need it? I haven't done the Kubuntu yet, but KDE was helpful, more like this one was a couple of years ago when I started.

---

### Post by QIII on 2012-07-23
Remember that we are all her voluntarily, on our own time and the person with a good answer may not be right there to help.  A 24 hour bump cycle is appropriate.

 Also, many will read a "laundry list" post and move on.  It is difficult to respond to several questions at once and the thread can become confusing.

My recommendation would be to pick the problem that you most want to have help with and create a single thread for a single problem at a time.

---

### Post by Gikoskos on 2012-07-24
Well KDE sometimes needs just a reboot to fix these minor (to insignificant) problems.
At least its stability is guaranteed on contrary with the totally unstable Unity desktop on Ubuntu.

---

### Post by QIII on 2012-07-24
Unity works just fine for me on my BOINC machine and on my Quantal test machine.

It is definitely different, but that does not mean unstable.

---

### Post by PaulW2U on 2012-07-24
> **Gikoskos said:**
> Most recently I installed Kubuntu 12.04 on my desktop PC, mostly because of the stability of the KDE but i started experiencing some small issues with it.

None of your problems have been noted here which is one reason why I didn't reply.

A lot of KDE bugs were fixed before Kubuntu 12.04's release and I can honestly say that all of the annoying crashes and bugs that I was experiencing during the development cycle were fixed. I'm sure there are many more fixes to come although an upgrade to Kubuntu 12.10 or later may become necessary.

> **QIII said:**
>  Also, many will read a "laundry list" post and move on.


As did I. The original contents of post #2 probably didn't help either.

> **Gikoskos said:**
> 
At least its stability is guaranteed on contrary with the totally unstable Unity desktop on Ubuntu.

I run Unity on a netbook with very limited resources. It works fine.

---

### Post by Jakin on 2012-07-25
I must be one of those persons who didnt setup Kubuntu-desktop correctly, because the entire desktop crashes at times. Im newish to KDE 4, (on 4.8.4) i installed Kubuntu-desktop on top of ubuntu 12.04 amd64.
Even with those desktop crashes though, i still find it far more usable than unity... just gotta log back in.

---

### Post by Teunis on 2012-07-26
I'm mostly following Kubuntuforums.org and find your problems unusual.
A first question would be what hardware, especially what video card are you using?
And when ATI or nVidia did you install the drivers for it?
Did you enable the 3D or desktop effects?

---

### Post by BigCityCat on 2012-07-26
A clean install is recommended if your new to Linux. I don't recommend upgrading unless you can handle a few hiccups.

---

### Post by Jakin on 2012-07-27
I definitely agree with clean install rather than upgrade, it has always poised better stability, and far less issues in my experience. 
Its not hard to backup important files and settings; but i can see why some would rather upgrade and forgo the reinstallations of all their programs and tools.

As far as the stability of kubuntu-desktop, its definatly better (in my opinion) to use a kubuntu CD/DVD rather than install it over a ubuntu distro- i tried just that today- wasn't ever gonna use Unity again anway. Far more stable!
I have had one crash so far, as opposed to 5-6 crashes a day, but i think its because the gnome/gtk intended program i was using wasn't playing nice with KDE.(considering it hasnt happened again, and i have not used said app)

---

### Post by BigCityCat on 2012-07-27
I never get crashes. I'm using Intel hardware though and there are no proprietary drivers on my system.

---

### Post by Jakin on 2012-07-28
Could be that amd64 version isn't as stable as i386. The main problem is i can never seem to recreate the crash, by doing (what i think is) the exact same thing- multiple times. The crashing seems more random..
It's not too big an annoyance when it happens, the desktop comes back, with all windows prior to crash- albeit resized somewhat. I have thought perhaps it is the propietary ATI driver.. 
The crash handler (admittedly i dont understand the readings well) always says the traceback has very little important info to help- but i submit the info regardless...

I would love to have a system as stable as you say yours has been- but i can live with it. As someone already mentioned, lets hope KDE 4.9 fixes many bugs, and issues that may be related to my problem.



If someone would like to take the time to check my readings, please have at it. [https://dl.dropbox.com/u/58975533/plasma-desktop-crash.zip](https://dl.dropbox.com/u/58975533/plasma-desktop-crash.zip)

---


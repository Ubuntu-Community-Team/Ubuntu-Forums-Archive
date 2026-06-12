---
title: "Boot up 90 seconds normal?"
date: 2009-04-19
forum: General Help
---

### Post by Camilia on 2009-04-19
I got ubuntu uploaded in windows. It takes 15 seconds to get into windows.
It takes 90 seconds to get into ubuntu. Is this normal?  
Is there anything I can do to speed it up?

---

### Post by s.fox on 2009-04-19
Hi,

90 seconds sounds rather long time to me.  [This]("http://digg.com/d1CBJB") guide should help you speed things up, though I must admit I have not tried it.

Hope this helps.

-Ash R

---

### Post by ajgreeny on 2009-04-19
> **Camilia said:**
> I got ubuntu uploaded in windows. It takes 15 seconds to get into windows.
It takes 90 seconds to get into ubuntu. Is this normal?  
Is there anything I can do to speed it up?
I assume you mean using wubi by "uploaded in windows"  Is that correct?
Is the 90 secs from power-on to a usable desktop, and is the 15 secs for windows also from power-on, or are you talking of from login to desktop?
That seems incredibly fast to me for windows, which in 15 seconds on my machine has not got a lot further than the POST, grub, and the windows logo appearing, though that includes 4 seconds in the grub-menu in my case, with a dual boot system.  90 seconds is about how long my machine takes from power-on to the usable desktop in ubuntu.  In windows it is considerably longer with all the services starting (zone-alarm, AVG virus checker, etc etc) before I can actually do anything, though the desktop appears in about the same 90 secs.

EDIT:
I have just installed bootchart and found that my machine takes 32 secs to boot according to that, and that is just to the gdm screen, I think.  Gnome then takes a bit more time, but if you mean 90 secs to the gdm login screen, then I agree, it is far too long.  Install bootchart and see if it gives you any clues from the chart you'll find in /var/log/bootchart

For you info I have a AMD sempron 2400+ with 1GB ram, which is now slow and old compared to many, I accept, but is still perfectly acceptable for many desktop users, I would have thought.

---

### Post by Camilia on 2009-04-20
Timed it with phone timer and got:
  3 seconds to screen with windows and ubuntu choice.
 17 seconds for the gold bar to appear
 41 seconds for splash screen to appear
 70 seconds for main screen to appear.
131 seconds to get to main screen

Pasted sudo apt-get install bootchart in terminal.
I can't figure out how to access it. I read the info at link given. Tried sudo apt-get bootchart and search for it in home file. Tried search in home files for /var/log/bootchart.
 
How do I access it?

---

### Post by boof1988 on 2009-04-20
> **Camilia said:**
> Pasted sudo apt-get install bootchart in terminal.
I can't figure out how to access it. I read the info at link given. Tried sudo apt-get bootchart and search for it in home file. Tried search in home files for /var/log/bootchart.
 
How do I access it?

Barring any problems with the installation...  The images (.png IIRC) are in:
```
/var/log/bootchart
```

and not in your home directory.

One way to view the images is described next.

If you have Ubuntu installed you can type the following (in *Applications* -> *Accessories* -> *Terminal*) and then press <Tab> (i.e. Use *Tab* completion) to get the actual image-file you want to view.  If you press <Tab> twice, I think it brings up all the files listed in the current-working-directory.  In this case it is */var/log/bootchart/*.

```
eog /var/log/bootchart/
```

eog is Eye-Of-Gnome.  Also see (in *Applications* -> *Accessories* -> *Terminal*)...

```
man eog
```

---

### Post by Camilia on 2009-04-20
Okay I see something when I post those commands in sudo but what they mean or what to do.

---

### Post by boof1988 on 2009-04-20
> **Camilia said:**
> Okay I see something when I post those commands in sudo but what they mean or what to do.

When you use (in *Applications -> Accessories -> Terminal*) ...
```
man eog
```
...if you have Eye-Of-Gnome installed, it will show the *man-page* for it.  I forgot to mention it, but you can exit out of the *man-page* by pressing "q" (for quit).  The man-pages give you information on how to use the application.  In this case we are looking for information on how to use eog ([Eye-Of-Gnome](http://projects.gnome.org/eog/)).

When you type in...
```
eog /var/log/bootchart/
```
... you need to either type in the actual filename after the last "/" or press <Tab> twice to display the possible files located in */var/log/bootchart/* and then you have to finish typing in the filename from the options (or sometimes it can auto-complete the whole filename for you).

So, for instance, if the image file we want to view is called *file.png* and it is located in */var/log/bootchart/*, then we use (to open the .png image in Eye Of Gnome)...
```
eog /var/log/bootchart/file.png
```

If there are any problems (or errors) with permissions of viewing this file, then you may need to precede the above command with gksu (or equivalent).

---

### Post by Camilia on 2009-04-20
> **boof1988 said:**
> 

Well I pasted ```
eog /var/log/bootchart/
```then pressed tab and nothing happened.
 
I pasted```
eog /var/log/bootchart/file.png
``` and got no image viewable.

[QUOTE=boof1988;7108395]
If there are any problems (or errors) with permissions of viewing this file, then you may need to precede the above command with gksu (or equivalent)

Where in the command```
eog /var/log/bootchart/
``` do I paste gksu?

I am at loss as to what to do.

---

### Post by boof1988 on 2009-04-20
Can you open *Applications -> Accessories -> Terminal*, type the following and post the results?

```
ls -al /var/log/bootchart 
```

If bootchart has been installed (barring errors), the previous command should display the files located in the */var/log/bootchart* directory.  If there is no */var/log/bootchart* directory, then I don't know what else to look for.

Another question... Have you rebooted since you installed *bootchart*?  The system may have to go through a (first) boot process for the */var/log/bootchart* directory to be created.

---

### Post by Camilia on 2009-04-20
> **boof1988 said:**
> Can you open *Applications -> Accessories -> Terminal*, type the following and post the results?

```
ls -al /var/log/bootchart 
```

Pasted command and got this:
total 404
drwxr-xr-x  2 root root   4096 2009-04-20 16:16 .
drwxr-xr-x 14 root root   4096 2009-04-20 16:16 ..
-rw-r--r--  1 root root 129597 2009-04-20 14:27 intrepid-20090420-1.png
-rw-r--r--  1 root root 129121 2009-04-20 14:44 intrepid-20090420-2.png
-rw-r--r--  1 root root 129801 2009-04-20 16:16 intrepid-20090420-3.png

Now will reboot and see if anything changes.
No change.

---

### Post by boof1988 on 2009-04-20
> **Camilia said:**
> Pasted command and got this:
total 404
drwxr-xr-x  2 root root   4096 2009-04-20 16:16 .
drwxr-xr-x 14 root root   4096 2009-04-20 16:16 ..
-rw-r--r--  1 root root 129597 2009-04-20 14:27 intrepid-20090420-1.png
-rw-r--r--  1 root root 129121 2009-04-20 14:44 intrepid-20090420-2.png
-rw-r--r--  1 root root 129801 2009-04-20 16:16 intrepid-20090420-3.png

Now will reboot and see if anything changes.
No change.

Okay...  It looks like there are three bootcharts here.  If the system is not adding any more files to the */var/log/bootchart* directory, than something is wrong and [bootchart](http://www.bootchart.org/) is not making any more charts.  It usually makes a chart for each boot process but there is probably some way to change this.

If eog is installed (it should be if you are using ubuntu), then the following should display the first bootchart (listed above) in the */var/log/bootchart* directory...

```
eog /var/log/bootchart/intrepid-20090420-1.png
```

...if that doesn't work, try...

```
gksu eog /var/log/bootchart/intrepid-20090420-1.png
```

...and let me know what happens.  When it asks for the password in the terminal, it will not display the password (or any symbols while typing it), but this is fine.  Go ahead and type your password and press enter.

---

### Post by Camilia on 2009-04-20
Doing both just give me the itrepid-20090420-1.png image. I don't know what to do with it.

---

### Post by boof1988 on 2009-04-20
> **Camilia said:**
> Doing both just give me the itrepid-20090420-1.png image. I don't know what to do with it.

Sorry... I have reached the limits of my knowledge.  I was just trying to help you figure out where the bootchart images are located and to make sure that they are being generated.

I hope someone else chimes in and can help you figure out why your system is booting in this time-frame.

EDIT:
Maybe post the bootcharts (in this thread) like the people are doing [here](http://ubuntuforums.org/showthread.php?t=531453).  Maybe someone else can help read it.

---

### Post by Slim Odds on 2009-04-20
> **Camilia said:**
> Doing both just give me the itrepid-20090420-1.png image. I don't know what to do with it.

Just run nautilus
Goto that directory
double click on one of the PNG files.

That will work.

---

### Post by boof1988 on 2009-04-21
Bump

---

### Post by Slim Odds on 2009-04-21
Bump what?

Read the messages

bootchart just creates an image file.

Doubleclick on it in Nautilus and you'll see it.

---

### Post by boof1988 on 2009-04-21
> **Slim Odds said:**
> Bump what?

Read the messages

bootchart just creates an image file.

Doubleclick on it in Nautilus and you'll see it.

The original question has not been answered yet.

So I'll repeat them here.

Is 90 seconds a normal boot time?
What are some things to do to speed it up?

> **Camilia said:**
> I got ubuntu uploaded in windows. It takes 15 seconds to get into windows.
It takes 90 seconds to get into ubuntu. Is this normal?  
Is there anything I can do to speed it up?

---

### Post by kamitsukai on 2009-04-21
> **boof1988 said:**
> The original question has not been answered yet.

So I'll repeat them here.

Is 90 seconds a normal boot time?
What are some things to do to speed it up?

1) 90 seconds? no

2) we don't know how to speed it up this is why we want you to upload you   bootchart so we can see why it is taking 90 seconds after this people will try to help you sort out any problems that can be seen in you bootchart;)

---

### Post by boof1988 on 2009-04-21
> **Camilia said:**
> Doing both just give me the itrepid-20090420-1.png image. I don't know what to do with it.

@Camilia...
You can upload it to this thread.  Ask how to do it if you are not sure.

> **kamitsukai said:**
> 1) 90 seconds? no

Yeah... I agree that 90 seconds is a bit long.  That's why I was trying to help Camilia find the bootchart files.

> **kamitsukai said:**
> 2) we don't know how to speed it up this is why we want you to upload you   bootchart so we can see why it is taking 90 seconds after this people will try to help you sort out any problems that can be seen in you bootchart;)

@Kamitsukai...
It is not me that needs the help.  It is Camilia who needs the help.

---

### Post by Camilia on 2009-05-06
Well, for some reason I didn't get notification of the new replies.  

Everything was getting slow.  It was slow opening documents etc. Thus scanned with Clam av.  Found 25 problems/viruses. Thus went into windows and scanned with superantispyware. Rescanned ubuntu with Clam av and found 60 problems/viruses. Many could not be quarantined. Thus I installed 
Ubuntu 9.04. I was going to wait a month but glad I didn't. I boots up faster now. 

With Ubuntu 8.04 I had to install it in windows. Thus windows would be first choice to boot up. With 9.04 I was able to upload in along windows. Now it is the first choice. First try didn't work. Got message unable to copy some files. Possibly do to some files being quarantined?  Second try it worked.

Problem no longer exist.

Now I am having problems with programs, document, crashing and not being able to recover them. Get message that there is no room. Thus rebooting with ubuntu CD. It will be the only OS program on my computer.

I will keep the info in mind for if things get slow again.

Thank you

---


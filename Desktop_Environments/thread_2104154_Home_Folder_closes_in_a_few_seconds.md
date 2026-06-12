---
title: "Home Folder closes in a few seconds"
date: 2013-01-12
forum: Desktop Environments
---

### Post by oakridge on 2013-01-12
This morning the Home Folder button has been closing within a few seconds of opening.  Everything else seems to work and I am having no trouble accessing files from the Windows boxes.

I can access files with the Terminal, but I am very rusty on the commands. Life is too easy these days.

I am using Ubuntu 12, hmmmm, cannot remember, but it is the latest update.  How do I find the version?

Thank you in advance.

Malcolm

---

### Post by ibjsb4 on 2013-01-12
In terminal:

```
nautilus
```

Get any errors?

---

### Post by oakridge on 2013-01-12
Ah, Nautilus, I must try and remember the name.

Yes, this is the error:

Segmentation fault (core dumped)

Thank you for your reply.

Malcolm

---

### Post by ibjsb4 on 2013-01-12
Try reinstalling it

```
sudo apt-get install --reinstall nautilus
```

---

### Post by oakridge on 2013-01-12
Thanks again ibjsb4.

Pretty well the same message:

Initializing nautilus-gdu extension
Segmentation fault (core dumped)

I did try a CD which opened normally, an extra pane went fine also but as soon as I clicked on 'HOME' Nautilus shut down again.

Malcolm

---

### Post by ibjsb4 on 2013-01-12
Try

```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by ibjsb4 on 2013-01-12
Im running across some old bug reports.  I think your running 12.04, but to be sure ..

```
cat /etc/issue
```

Also ran across a post stating "nautilus-open-terminal" is the cause.  Do you have that package installed?

---

### Post by oakridge on 2013-01-12
cat /etc/issue

Reported:

Ubuntu 12.04.1 LTS \n \l

Nautilus-open-terminal is not installed.

And this made no changes.

sudo dpkg --configure -a && sudo apt-get -f installMade

Thanks again.

Malcolm

---

### Post by ibjsb4 on 2013-01-12
Ok

```
rm -r ~/.config/nautilus && sudo apt-get purge nautilus && sudo apt-get autoclean && sudo apt-get install nautilus
```

---

### Post by oakridge on 2013-01-14
Thank you again for your help, but.......

rm ~/.config/nautilus && sudo apt-get purge nautilus && sudo apt-get autoclean && sudo apt-get install nautilus

Generates the message:

rm: cannot remove `/home/oakridge/.config/nautilus': Is a directory

The world is against me.

Malcolm

---

### Post by ibjsb4 on 2013-01-14
Nope, the world is not against you.  Just me and my typing :) made a typo, its fixed now (-r).  Go ahead and run it again.

---

### Post by oakridge on 2013-01-15
That line worked fine,ibsjsb4, but..... the problem has not gone away.

If I put in a CD that opens Nautilus and I can access everything on the list down the left-hand side with not problem, but if I click on Home/Oakridge it Nautilus shuts down and generates an error.

Malcolm

---

### Post by ibjsb4 on 2013-01-15
I have been digging through here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=nautilus+Segmentation+fault+%28core+dumped%29+precise+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=nautilus+Segmentation+fault+%28core+dumped%29+precise+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=nautilus-gdu+extension+precise+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=nautilus-gdu+extension+precise+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

And have come across suggestions, but seems that there is no one answer.

---

### Post by oakridge on 2013-01-16
Thank you for that.  I did not know about googlubuntu.  I will work through the references.  

Should I fail on Nautilus is their an alternative that I could try?

Malcolm

---

### Post by black veils on 2013-01-16
it doesnt seem like nautilus, but if you want to try another file manager, try Thunar.

```
sudo apt-get install catfish thunar thunar-volman thunar-archive-plugin

```you will need to add a startup entry for ```
Thunar --daemon
```when i installed catfish before thunar, it automatically added inbuilt search function, unless i had configs there already, was a while ago.

do you remember what you were doing the night before it stopped working preperly? had you installed something that day, or changed anything?

---

### Post by oakridge on 2013-01-17
Thank you for your reply 'black veils'.

This morning the problem has got much worse, but to answer your question first it happened during the day.  The machine is used largely as a file server apart from some scanning that I am doing at present.

The new problem is that this morning it is not accepting my login password.  Fortunately we can access the files from the PCs.  A Guest session was not set up.

Malcolm

---

### Post by black veils on 2013-01-17
if it were me, i would backup all data! then do hhd and memory scans to check hardware. if that was clear i would format the machine, though i dont know how feasible that would be for your setup.

---

### Post by oakridge on 2013-01-17
Is it possible to force a startup in command mode please?

Malcolm

---

### Post by black veils on 2013-01-17
you mean its stuck halfway through the boot process? 

you could try:

**pressing Ctrl + Alt + Del**

or

**sudo reboot**

if those dont work, you should do this instead of a force shutdown:

**hold Alt + PrtSc while slowly typing R E I S U B**  (it will shutdown the computer in a safer way and restart)

---

### Post by oakridge on 2013-01-20
There has been developments.

Between entering the password and it asking again this message flashes up:

Could not write bytes. Broken pipe
 
Stopping save kernel messages
 
Stopping anac(h) ronistin cron
Starting anac(h) ronistic cron
 
Stopping anac(h) ronistic cron
 
Checking battery state
Stopping system V runlevel compatability

Have you any ideas?

---

### Post by oakridge on 2013-01-22
Solved by re-installing Ubuntu, it must just have had a tantrum.  I have also fitted a 2nd 500Gb drive at the same time and everything is gradually going back together.

Thank you for all your help.

Malcolm

P.S. Is there a 'Solved' Button somewhere?

---

### Post by black veils on 2013-01-22
in **Thread Tools**, above the thread

---

### Post by oakridge on 2013-01-22
Thank you Black Veils.

---


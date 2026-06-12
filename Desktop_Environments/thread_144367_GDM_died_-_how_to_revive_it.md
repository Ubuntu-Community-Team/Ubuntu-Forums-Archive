---
title: "GDM died - how to revive it?"
date: 2006-03-14
forum: Desktop Environments
---

### Post by garretjax on 2006-03-14
Okay, so I've been using Ubuntu for a while now, and had no major problems; a few minor ones, but nothing outstanding.  Yesterday i patched my system with some recent updates, and it noted that one of them required a reboot [Kern 2.6.12-10] so when i was done my work i set it to reboot and wandered away. when i came back - i didn't see my usual login screen, instead i had been dumped to a terminal and was waiting for login.

i tried resorting to the previous kernel, same thing, i get dropped into terminal 1 instead of login.  It doesn't seem to be an X probelm, at least not directly, if i start and x session using startx - no problem, loads up gnome and away i go. I have tried manually starting gdm, but the system tells me its already running. running it might be, but it doesn't seem to be doing anything. if i kill it, and restart it, system just drops back to terminal 

What i don't know is where else to look for errors from GDM, and thus i have no idea what might have casued it to break.  
I didn't really look closely at the last batch of patches [i know, my own fault] so i really don't know if it was a recent patch that is causing it.  I would suspect if a patch breakin gdm came out, that we would be hearing about it on the forms, more than just my little post here.

Anyone with suggestions, please let me know - where i should be lookin for info on this or if you have had similar problme, how you fixed it.


Thanks

---

### Post by zi99y on 2006-03-14
Have you had a rummage through the log files in /var/log - maybe /var/log/messages ? 

One idea is to reinstall GDM using apt-get, I'm not sure of the exact command. OR you could install KDM which is kde's login manager, at least just to get something up and running...

These are just ideas as I'm not an uber linux jock yet

---

### Post by zi99y on 2006-03-14
Looking on my debian machine the GDM log files are in /var/log/gdm (surprise!) so there's a good place to start

---

### Post by garretjax on 2006-03-14
Thanks for the replies; I have thought about trying to reinstall gdm, or something else as you suggest, and i think that will be my last resort, I'd really like to find what the problem is, rather than make it disappear till it happens again.

I had check /var/log/gdm prior to posting, it has one log and thats from about a week and a half ago - lovely [though that was probably the last time the system was down and back prior to this]

Any other suggestions ? I'm really flying in the breeze on this one, not sure what is causing this.  tried reverting to an old Xorg.conf to see if it might have been something i changed recently that is causing problems; still nadda


T

---

### Post by zi99y on 2006-03-14
you could have a look here: [http://www.gnome.org/projects/gdm/docs/2.13/troubleshooting.html]("http://www.gnome.org/projects/gdm/docs/2.13/troubleshooting.html") 

there's a few things you could try, but apart from that I'm out of ideas...

---

### Post by Mustard on 2006-03-14
Are you using any specific graphics drivers?

Can you get to a command line and do this command?  You can try getting to a command line using the ctrl + alt + f1  through to f6 keys.

```
sudo dpkg-reconfigure xserver-xorg
```

If so you might be able to reconfigure you xorg.conf to use vesa drivers as a workaround until you find out what the issue is.

To restart X after reconfiguring use one of these commands..

```
startx
```

or

```
sudo /etc/init.d/gdm restart
```

---

### Post by garretjax on 2006-03-15
thanks guys 

Zi99y i'm gonna try some of what that link suggested; and if thats a no go i'll prolly apt-get gdm and see if that will make things go back to normal

Mustard, Thanks for the help, but i've established it is not the Xserver that is giving me the problem, as i can manually start X with the startx script

Thanks for the help guys - i'll post back later today if i find a solution off the above link

T

---

### Post by Sef on 2006-03-15
to reinstall gnome desktop:

sudo apt-get install gnome-desktop

---

### Post by garretjax on 2006-03-17
Gahh - sorry it took so long; but i finally got a chance to sit down and mess with this w/o interuptions.

We have obtained a shooting solution, though it was only after i realized half the problem was a ID10T error.  I had previously been triyng to set up a remote login for that computer- in doing so i must have messed up my gdm.conf file; there was no error messages becasue it was doing what it was told to, just not what i was thinkin it should.  Anyway, copied gdm.conf.factorydefault over gdm.conf and away we went.

I kinda feel silly, but this is what happens when you are working on something and don't reboot till like a week later, you don't remember all the things you had been working on.

Anyway, hope this helps if anyone else runs into the same problem.

---

### Post by zi99y on 2006-03-17
don't worry it happens to us all ;)

(doesn't it??!)

---


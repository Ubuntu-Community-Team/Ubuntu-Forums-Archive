---
title: "your session only lasted less than 10 seconds."
date: 2005-04-02
forum: Desktop Environments
---

### Post by nicholaspaul on 2005-04-02
I was installing a couple of things ( I think 'softbeep' was the last one) remotely, and when I restarted my Hoary Hedgehog, I got this after logging in - 

[SIZE=0]"your session only lasted less than 10 seconds. If you have not logged out yourself this could mean that here is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem. 

detail - (-/.xsessions-errors file)

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "nicholas"
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:8015): WARNING **: Unable to read ICE authority file : /home/nicholas/.ICEauthority"[/SIZE]

I humoured the message and deleted some ISO's, freeing up about 43% of my hard drive (oops) so its now 48% free (a whopping 6Gb in total). [ Oh, I managed to do this in failsafe terminal, the only mode that worked]

Anyone have any ideas?

BTW I haven't posted much on here, but I have read loads and lots. Fab resource, this is!

---

### Post by Dracontopes on 2005-04-02
I got the same problem yersterday. The .ICEauthortiy file has been altered to only root permissions, which is wrong. kassetra posted a workaround/fix:

Check the permissions:
 ```
ls -l /home/nicholas/.ICEauthority
``` 
If it's not owned by you:
 ```
sudo chown nicholas /home/nicholas/.ICEauthority
sudo chmod 600 /home/nicholas/.ICEauthority

``` 
Now restart GDM/X and it should be working :roll:

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=Dracontopes]I got the same problem yersterday. The .ICEauthortiy file has been altered to only root permissions, which is wrong. kassetra posted a workaround/fix:

Check the permissions:
 ```
ls -l /home/nicholas/.ICEauthority
``` 
If it's not owned by you:
 ```
sudo chown nicholas /home/nicholas/.ICEauthority
sudo chmod 600 /home/nicholas/.ICEauthority

``` 
Now restart GDM/X and it should be working :roll:[/QUOTE]
 If this doesn't work just remove the .ICEauthority This is what I do when it happens to me.

---

### Post by nicholaspaul on 2005-04-02
** Totally icebox. **
Thanks Guys, that worked like a charm. I'm back Ubuntuing with ease. 

Trouble was, I didn't know what the problem was related to so I didn't know how to search the forum for it. 

What on earth is .ICEauthority and how did it get maimed?

---

### Post by penvzila on 2005-05-26
[QUOTE=nicholaspaul]** Totally icebox. **
Thanks Guys, that worked like a charm. I'm back Ubuntuing with ease. 

Trouble was, I didn't know what the problem was related to so I didn't know how to search the forum for it. 

What on earth is .ICEauthority and how did it get maimed?[/QUOTE]

It can happen if you run a KDE program as root from GNOME, especially if that program puts a lot in (read: fills) /tmp.

---

### Post by saz on 2006-07-30
i get about the same error, but instead of the ICE file, i get this:

"error while loading shared libraries: libasound.so.2: cannot open shared object file: no such file or directory"

anyone can help?? :confused: :confused: :confused: :confused:

(i'm running ubuntu dapper)

---

### Post by Lord Illidan on 2006-07-30
> **saz said:**
> i get about the same error, but instead of the ICE file, i get this:

"error while loading shared libraries: libasound.so.2: cannot open shared object file: no such file or directory"

anyone can help?? :confused: :confused: :confused: :confused:

(i'm running ubuntu dapper)

Post a new thread, then. This forum is for Hoary users. Also, it is quite old..

---


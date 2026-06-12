---
title: "several problems after gnome crash"
date: 2006-03-26
forum: Desktop Environments
---

### Post by louis_nichols on 2006-03-26
hi everybody! today hasn't been a good day at all for me and my Linux :(

I am running Breezy Badger, with a Knome interface (you've probbably read the instructions on tips'n'tricks). It used to run smoothly, without crashes, only a few session-to-session issues (some settings wouldn't save, sessons weren't identical etc.) but nothing serious. But today it all went down the drain.

First thing that happened (I don't know if it's relevant...) was that on first boot today, the login sound wasn't there, although I hadn't changed anything in the sound settings anytime recently. No big thing, anyway. Then.... gnome crashed. probably because of the transparency issues. I wasn't there, just came back to see the login screen. After that... trouble. First, I wasn't able to login at all. Several attempts to restart X and delete some .lock files from home folder left me with a black screen with a couple of unreadable characters and no reaction to any input, so I had to do a hardware reboot.

Now, logins from gdm take forever (about 5 mins). Some app hangs, but I don't know which one. At first, the session was pretty screwed up, with gnome-panel transformed into somekind of bad taste puzzle, but that's gone now.

What is also bugging me is that in gdm I don't see the human cursor teme anymore (not that I want the exact one, but it's what I had before and was ok; thing is I never knew how to change cursors for the login screen), but the X black ugly one. The same cursor theme is shown when firefox loads pages, although I had previously solved this following instructions in a thread. I had made a file /usr/share/icons/default/index.theme and written 

[Icon Theme]
Inherits=Kubuntu

in it. Strangely, the file, along with the whole /usr/share/icons/default/ folder was gone. Finally, I see the same black cursor theme when I right-click on the desktop.

Anyways, I can take the ugly cursors (probably) but the long login time is killing me. Please help!

---

### Post by louis_nichols on 2006-03-26
anyone? any ideas?

is there a way to see a log of the login? to find out which app hangs for 5 minutes before giving the ok to the rest of the login?

---

### Post by louis_nichols on 2006-03-27
well... I managed to solve most of the problems. I deleted the folder ~/.gnome 2 and then remade the sessions. Still don't know what was going wrong, exactly. I had the cursors messed up for a while, but after uninstalling and re-installing themes, most stuff is ok.

ONLY ONE THING REMAINS NOW: gdm login screen only shows plain black ugly X cursors. I searched every config file I could find and googled intensly and didn't find where to set cursors for gdm.

anyone? anything?

edit: just noticed, and I think they are connected, but dunno how, that the same black cursor is displayed when synaptic loads the list and searches.

---

### Post by tpog on 2006-03-27
Not sure how much use this will be but I recently  messed up my gnome settings by upgrading my system and then remounting my /home partition which had all of my settings for a previous version of GNOME.
I ended up with similar problems to those you have described. I got round it by deleting all gnome configuration files and ended up with a default desktop. The tutorial here [http://yolinux.com/TUTORIALS/GNOME.html](http://yolinux.com/TUTORIALS/GNOME.html)  should give you a good idea of where to start. 

Hope this helps.

---

### Post by louis_nichols on 2006-03-28
thanks for the input! Indeed, I ended up doing the same thing (although not as elegantly as described in the link you posted).

I can't find how to setup gdm though. There seems to be nothing out there on this topic. :confused:  I thought settings for gdm login screen were borrowed in part from the root account, but my root account is working perfectly now, cursor-wise, yet gdm can only show the black X cursor theme. ](*,)

---


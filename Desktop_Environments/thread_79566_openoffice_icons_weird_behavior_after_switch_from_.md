---
title: "openoffice icons weird behavior after switch from kubuntu to ubuntu"
date: 2005-10-20
forum: Desktop Environments
---

### Post by makhand on 2005-10-20
I switched a laptop from ubuntu to kubuntu and also upgraded the kernel to 686. I have the weirdest problem with open office. For some reason, now when I start it up, all of the icons appear breifly, but disappear as i hover over them. In the end, as i hover all icons and menu items are invisible except for the one that i am directly over along with some other random ones. This is some crazy behavior. I've completely removed openoffice and reinstalled it with no luck. i'm not even sure its an openoffice problem... but dont really know what is going on. 

I'm attempting to attach some examples

Update:
Actually, I'm pretty sure its not just an openoffice issue because the logout dialog doesnt show any button borders or radio options. I can click on a selection, hear the event sount, but see no radio button selected.

---

### Post by makhand on 2005-10-20
for those that are feeling helpful, i have one new development. It seems that all of these problems go away when i create a new user, and login as that new user. So how do i rescue the old user, I've tried deleting a bunch of configuration directories in the home directory, what else can i/should i do?

---

### Post by lindt on 2005-11-02
Same problem here :confused: 

Did you find any solution?

---

### Post by makhand on 2005-11-02
After a while, I gave up trying. I just 
1. created a new user, 
2. transfered all the files i wanted to keep to that new user, 
3. deleted the old user and associated files, 
4. then recreated the old user and 
5. gave him/it the files back. 

The problem is obviously somewhere within some configuration files in your home directory. I was unable to find it. In the end it was faster to just make the new user. Just be sure to transfer ALL the files that you need. For example, its easy to forget '.gaim' and '.mozilla'. On the same note, dont transfer the files that may be causing the problem (eg .gnome). You'll end up with a clean desktop that you'll have to configure all over again.. but at least it will all work. Thats my solution

you may need to change owners and permissions of the files as you go along.

---

### Post by edoardo on 2005-11-02
same problem here SOLVED 

by removing from my ~
all the following (I went over the top and got my panel back to default) and then logsing in again

 .gconfd            .gtkrc-1.2-gnome2  .openoffice.org2  .thumbnails
..      .gnome2            .gtkrc-2.0         .qt
.gconf  .gtk_qt_engine_rc  .kderc             .themes

---

### Post by lindt on 2005-11-02
Tnx!!

After a few tryings, I solved it too.
I just deleted ~/.gtkrc-2.0 that was modified by KDE control center, under "GTK Styles and Fonts".

---


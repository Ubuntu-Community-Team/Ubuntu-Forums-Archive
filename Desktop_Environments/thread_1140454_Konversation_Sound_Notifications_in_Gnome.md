---
title: "Konversation Sound Notifications in Gnome"
date: 2009-04-27
forum: Desktop Environments
---

### Post by Tohe on 2009-04-27
Kia ora all

I'm running Konversation on the Gnome desktop and only seem to have 1 little problem...

I can't seem to get the sound/audio notifications to work...

I'm assuming it is possibly because it may be looking for the KDE sound drivers/library etc?

Is there any KDE packages I can install to make them work? Is there anything else I could try? Any help would be hugely appreciated!

---

### Post by Tohe on 2009-04-27
Apparently it's a bug ](*,)

[https://bugs.launchpad.net/ubuntu/+source/konversation/+bug/360965/](https://bugs.launchpad.net/ubuntu/+source/konversation/+bug/360965/)

And it doesn't look like it's going to be fixed :(

---

### Post by nucleuskore on 2009-07-05
Hi everyone

I am an old user of konversation. I particularly like the feature that enables notification when my nick is mentioned in any incoming message. Prevents the need to be near the pc or at the window all the time.

As mentioned above, it is a bug that's not going to be fixed because of problems related to aRTS. I got that while googling for a solution. However, there is a workaround. The moment I figured it out I thought I'll search the forums to see if anyone else had the same problem and share my solution. [img]http://s269.photobucket.com/albums/jj44/visio159/Unismilies/44large.png[/img]

This is what I did:
[list=1]
[*]Install mplayer and w32codecs if you don't already have it.
[*]Make a folder in your home directory, say **kon**
[*]copy the sound notification files to that folder
[*]open gedit and type the following line
**mplayer /home/*yourself*/kon/*sound.wav***
where you replace *yourself* with your login name and *sound.wav* with your sound

This is how my line looks
mplayer /home/neville/kon/WhistlePrettyGirl.wav

Click on file->save and save it as *something*.sh 
I save it as kon.sh

In Konversation, click on Settings->configure notifications
[[IMG]http://img179.imageshack.us/img179/1561/konversation1.th.png[/IMG]](http://img179.imageshack.us/i/konversation1.png/)

Select the event you want to enable sound for as I have
[[IMG]http://img179.imageshack.us/img179/5272/konversation2.th.png[/IMG]](http://img179.imageshack.us/i/konversation2.png/)

Click on Advanced
[[IMG]http://img198.imageshack.us/img198/5589/konversation3.th.png[/IMG]](http://img198.imageshack.us/i/konversation3.png/)

Select execute a program
[[IMG]http://img188.imageshack.us/img188/1438/konversation4.th.png[/IMG]](http://img188.imageshack.us/i/konversation4.png/)

and browse to kon.sh, select it and click Ok
[[IMG]http://img179.imageshack.us/img179/2694/konversation5.th.png[/IMG]](http://img179.imageshack.us/i/konversation5.png/)

Click Apply and then OK

You'll have to do this for each sound you want to enable. If you want to use a different sound file you will have to make a different .sh file for that.[/list]

---


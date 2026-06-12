---
title: "digiKam with Gimp?"
date: 2012-05-30
forum: Desktop Environments
---

### Post by Rallg on 2012-05-30
I now have 12.04 using WUBI on my otherwise-Windows XP machine. Not a newbie.

The digiKam program, which relies heavily on K-desktop, can be installed in non-K Ubuntu, BUT doing so will remove Gimp! It seems that one or more of the digiKam K-dependencies hates to see Gimp hanging around. I do not understand why.

I use Gimp frequently. In fact I obtained 2.8 before most other users, via Debian. And, I managed to compile 2.9.1 (don't ask how) in /opt. Certainly, I do not wish to run the risk of having digiKam disturb my Gimp installations.

Is there any way around this, other than using digiKam on Windows? Oddly, it works great there, by installing part of the K-desktop. Understand that I do not wish to switch to Kubuntu (I tried it separately) and in any case I intend to keep both versions of Gimp.

On another note, I have not been able to compile any recent version of Cinepaint, even though the Windows version works.

---

### Post by traditionalist on 2012-05-30
No idea why it shouldn't work. Both programs work fine for me on 12.04, here they are on the same desktop;

[[IMG]http://img52.imageshack.us/img52/7553/workspace1001f.th.png[/IMG]](http://img52.imageshack.us/i/workspace1001f.png/)

---

### Post by Rallg on 2012-05-30
Worked for you? Hmmm.

When I use Synaptic, any attempt to install digiKam demands that a number of my existing packages be removed. Among them is Gimp.

Further research indicates that it is one (or more) of digiKam's dependencies that demands removal of Gimp and some other things.

Same happens if I try it via apt-get.

My attempt at installing digiKam only began over this past weekend. Could it be that in the time since you installed both, there has been some update that breaks the dependency chain?

I looked around the Internet (not just on this forum) and I didn't see anything on the subject, as most discussions that use both "digiKam" and "Gimp" are comparing one to the other, without mentioning both together.

I suppose I could force install digiKam and all dependencies that do not demand removal of Gimp, and see what happens. But I didn't want to do that without seeking advice.

---

### Post by traditionalist on 2012-05-30
> **Rallg said:**
> Worked for you? Hmmm.

When I use Synaptic, any attempt to install digiKam demands that a number of my existing packages be removed. Among them is Gimp.

Further research indicates that it is one (or more) of digiKam's dependencies that demands removal of Gimp and some other things.

Same happens if I try it via apt-get.

My attempt at installing digiKam only began over this past weekend. Could it be that in the time since you installed both, there has been some update that breaks the dependency chain?

I looked around the Internet (not just on this forum) and I didn't see anything on the subject, as most discussions that use both "digiKam" and "Gimp" are comparing one to the other, without mentioning both together.

I suppose I could force install digiKam and all dependencies that do not demand removal of Gimp, and see what happens. But I didn't want to do that without seeking advice.


I used the Ubuntu software centre to install Digikam  and I got GIMP over a PPA ( I had the 2.8 release before it was available generally). I never had any problems with either program, and was not aware that there were any, and the installation just went ahead as normal. The last time I installed Digikam was a couple of days ago on another machine which already had GIMP 2.8 on it. No problems at all.

[[IMG]http://img692.imageshack.us/img692/7983/selection001mlo.th.png[/IMG]](http://img692.imageshack.us/i/selection001mlo.png/)


[http://www.webupd8.org/2012/05/gimp-28-stable-finally-available-for.html](http://www.webupd8.org/2012/05/gimp-28-stable-finally-available-for.html)

Also see here  [http://www.webupd8.org/2012/05/download-gimp-28-script-fus-pack-more.html](http://www.webupd8.org/2012/05/download-gimp-28-script-fus-pack-more.html)

---

### Post by Rallg on 2012-05-30
Thanks for your advice, traditionalist. Knowing that indeed both digiKam and Gimp could coexist on Ubuntu 12.04, I looked in detail.

I also have Gimp 2.8. But I also managed to compile Gimp 2.9.1, a somewhat secret development version (in my opt folder). While doing that, I obtained some dependencies from Debian Sid. That turned out to be the problem. In 12.04, digiKam wanted to install some packages that were not version-compatible with a couple of things from Sid. Unfortunately, that wasn't what Synaptic told me; instead it wanted to remove Gimp.

The solution was to re-enable the Sid repository, reload Synaptic, then get digiKam. This time, the packages aligned. Finally, I turned off Sid (I don't want everything upgraded to experimental!).

I originally put the question in the Desktop Environments category because I thought it might be some rivalry between the distinctively Gnome Gimp, and the distinctively K digiKam.

---

### Post by traditionalist on 2012-05-30
> **Rallg said:**
> Thanks for your advice, traditionalist. Knowing that indeed both digiKam and Gimp could coexist on Ubuntu 12.04, I looked in detail.
<SNIP>


My pleasure, glad to hear it helped. I am a more or less complete newbie to Linux, and you are obviously way beyond that. Sometimes a fresh look at things can work wonders though. Doubtless due to the lack of preconceptions.

---

### Post by fredshome on 2012-05-31
Just to add a couple things... 

Despite its name Gimp isn't part of Gnome, just a GTK application. And the KDE people (as well as the Gnome people) tend to be very careful to make sure their stuff plays well and if possible is interoperable, with that of other desktops (as long as it's opendesktop compliant). 
So your type of problem should only result from a packaging error or a bad repository mix and match. 

Cheers

---


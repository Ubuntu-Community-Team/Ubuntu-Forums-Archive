---
title: "Lubuntu and fonts"
date: 2012-07-16
forum: Desktop Environments
---

### Post by pangeh on 2012-07-16
Hi,

Apologies for the newbie question but any help is sincerely appreciated.

I'm not sure if this is the right place to post this. Have been looking for the Lubuntu forum but searching keeps sending me to ubuntu forum.

I switched over to Lubuntu 12.04 from Ubuntu 10.04 as I didn't want to use unity on the new Ubuntu. 

Was just setting up the system and did not know how to install fonts in Lubuntu. In Ubuntu I could open the ttf file and it would open up a window that described the font and gave me an option to install. 

In Lubuntu when I double click the ttf  file it asks me for a program to open the file with.

Have been searching google for Lubuntu how to install fonts and only got results for Ubuntu. 

Would somebody please advise how I could install fonts in Lubuntu or point me in the right direction as to where I could download documentation outlining this kind of basic stuff for Lubuntu. I have fonts that I use for work and need to get these working on my pc.

Thanks in advance for your kind assistance and guidance.

regards
p

---

### Post by MG&amp;TL on 2012-07-16
There isn't a utility for this as yet on Lubuntu. If you wanted that, you probably should have stuck to Ubuntu. Sorry. Although this was on the mailing list this morning, so cross your fingers.

Press Alt-F2 and type the following:

```
gksu pcmanfm /usr/share/fonts/truetype/
```which will open a file manager in /usr/share/fonts/truetype/. *Be careful, you're root in the file manager and therefore can delete anything.*

Then just drag and drop your ttf(s) into that folder. [I]Close your file manager to exit the root session.
[/I]
Then open a terminal and run:

```
sudo fc-cache -f -v
```to update the font cache.

As per:  [https://wiki.ubuntu.com/Fonts#Manually](https://wiki.ubuntu.com/Fonts#Manually)

---

### Post by pangeh on 2012-07-16
Thank so much for your reply MG&TL, 

It worked perfectly. 

Just so I understand it better is it a case that the underlying functions of Ubuntu and Lubuntu are the same and only the utillities and gui environments are different?

Then to increase my understanding if I learn the Ubuntu documentation of how it works/doing things manually would that give me a solid grounding in using Lubuntu?

I really liked Ubuntu 10.04 and the Gnome 2 environment. To my detriment however I just learnt how to use different utillities and only some of the underlying system. I would like to learn things in a bit more depth but want to make sure I am looking in the right place.

Thanks again for your assistance and invaluable advice.

Kind regards
P.

---

### Post by MG&amp;TL on 2012-07-16
> **pangeh said:**
> Thank so much for your reply MG&TL, 

It worked perfectly. 

Just so I understand it better is it a case that the underlying functions of Ubuntu and Lubuntu are the same and only the utillities and gui environments are different?

Then to increase my understanding if I learn the Ubuntu documentation of how it works/doing things manually would that give me a solid grounding in using Lubuntu?

I really liked Ubuntu 10.04 and the Gnome 2 environment. To my detriment however I just learnt how to use different utillities and only some of the underlying system. I would like to learn things in a bit more depth but want to make sure I am looking in the right place.

Thanks again for your assistance and invaluable advice.

Kind regards
P.

Awesome. :)

As for Ubuntu vs. Lubuntu:

-They are the same 'under the hood'. For instance, they both read fonts from /usr/share/fonts/.

-They come with different GUI utilities. Lubuntu has less, to try and make a lighter experience.

-Knowing the manual way to do it is often quicker (although not always) and will work on any *buntu (and, most of the time, on an Linux, and, some of the time, on any *nix.).

-Learning it is not necessary unless you do it regularly. The Ubuntu wiki is a fantastic resource, so if you need to something occasionally, just search for it there.

-As for 'a bit more depth'-poke around, ask 'why is that there', and see what you can do manually. Best advice I can give.

Hope that helps your problem a bit, and I'm please the fonts work.

---

### Post by pangeh on 2012-07-16
Thats great to know, really clears up alot of confusion. Will focus on the wiki from now on and learn the manual way of doing things first and foremost.

Thank you again for all of your invaluable advice and help with my questions.

All the best.

Kind regards
P.

---


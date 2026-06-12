---
title: "The development of Scilab and Octave"
date: 2007-01-30
forum: Education &amp; Science
---

### Post by Qtea on 2007-01-30
As we know, there always lies a great development capacity in the user community - I would now like to wake it up to improve the usability of Ubuntu among scientists and engineers. Scilab and Octave the most competent programs for numerical computing for Ubuntu but both of them are still lousy and unintuitive to use when compared with Matlab. 

I know that there is already a vivid developer group for Octave (which I personally am far less familiar with than with Scilab) but none for Scilab. This may depend on the Scilab licence which is not GPL-compatible, but however, I know there is at least a lot of user experience to share among us in blogs or forums, even if it is not possible to collectively improve Scilab documentation or contribute to Scilab Wiki. The [definition of a Scilab developer]("http://www.scilab.org/developers/index_developers.php?page=SVNdevelopers.html") seems to me a bit restricted :shock: .

Has anyone any better sights to the future development of Scilab and/or Octave? What are the possibilities for Octave to become a usable tool for DSP or Process Control - I guess Scilab is far ahead Octave at these areas? Scilab 5.0 with better GUI and some improved algorithms [will be out in October 2007]("http://www.scilab.org/developers/index_developers.php?page=roadmap.html") - what can we expect it to be like?

This is rather a small thing, but I'd like to give my two cents by completing the [avaible scilab.lang file]("http://www.scilab.org/contrib/displayContribution.php?fileID=326") (for syntax highlighting in Gnome editors, gedit for example) and somehow then getting it included to the some future Ubuntu release. I have also begun with a [small Scilab blog]("http://scilabilla.blogspot.com/") (in Finnish only), but that's about all I'm capable of.

What do you think would be the most crucial things to do in order to make Ubuntu more scientist- and engineer-friendly? How should the user experiences of Scilab and Octave be improved and what could be done by us Ubuntu users?

---

### Post by raja on 2007-02-05
Well, I dont have any answers, but hope with you that these develop to the stage where they form a true replacement for matlab. I do a lot of my work on Matlab and have experimented with both scilab and octave. But for various reasons, I havent found it easy to make the shift. 
What seems more promising to me of late is to use python with numpy and matplotlib - anyone has experience with that ?

---

### Post by LaserJock on 2007-02-05
Well, from my perspective as MOTU Science team lead, putting in some time to learn how to package and maintain science apps in Ubuntu is valuable. It's a pretty demanding task (we are "tracking" 450+ science package) but more people helping makes the load less. We also need bug testers and triagers. One of the most important things we can do is let the software authors know what bugs Ubuntu users are encountering so they can correct them for all Linux users. 

Besides the more technical aspects I can also imagine the following:
[LIST]
[*] an "Ubuntu Science" blog aggregator so scientific ubuntu  users can get the word out
[*] getting an official ubuntu-science mailing list for science discussion (we already have a mailing list for development/bug emails)
[*] make a real effort to use help.ubuntu.com/community/UbuntuScientists wiki space to put documentation, tips, etc.
[*] perhaps make an add-on CD full of scientific packages. I had wanted to use "Scibuntu" but that has already been taken.
[/LIST]

On the whole I think an essential "piece" that the Linux scientific software community is missing is integration and focus. Currently we have hundreds of independet projects, sometimes trying to provide essentially the same features, and often times they aren't very concerned about how their software integrates with the rest of the user's OS. I think Ubuntu is an excellent platform to work on this issue.

Just my $0.02USD

-LaserJock

P.S. As far as octave vs scilab goes, scilab's license has made it difficult in the past to get devs "excited" to work on it. Scilab also seems more difficult to maintain.

---

### Post by LaserJock on 2007-02-05
> **raja said:**
> Well, I dont have any answers, but hope with you that these develop to the stage where they form a true replacement for matlab. I do a lot of my work on Matlab and have experimented with both scilab and octave. But for various reasons, I havent found it easy to make the shift. 
What seems more promising to me of late is to use python with numpy and matplotlib - anyone has experience with that ?

I use scipy in my research and like it quite a bit. The only thing I have a hard time with is that scipy/numpy are being developed rapidly enough that sometimes my scripts have to be "tweaked" to work with newer versions. Of course this isn't all bad since they are adding in all kinds of other things too. :-) I think scipy/numpy/matplotlib are very cool tools and I hope to see them really taking over in the future.

-LaserJock

---

### Post by FredFirmo on 2007-02-06
I am physicist, and I have been using python, which is a lovely progamming language. More recentlyu I used Octave, because of some difficulties I had to install, matlab in Ubuntu. It works quite well, even if I had some work to translate my matlab files. I still don t know if Octave is faster or not, but at least is free.  Some benchmarks would help. From the other side, I did not suceed in installing Scilab in my amd64 Ubuntu, It seems that there is a bug in this 4.1. When Iask the scilab command, it comes out written, in some strange fonts. if anyone knows how to solve that, I would appreciate
Frederico Firmo

---

### Post by sylvestre on 2007-06-24
Hi

I only found this post 6 months after.

You will be happy to hear that Scilab 5 will have a new license (Opensource moreover) and a great work has been done to clean up the code and make it easier to understand (even if there is still some work on it).

@FredFirmo : do you still have your problem with fonts ?

@Qtea : your blog is dead ? :/

---

### Post by bestjobm on 2007-06-24
Qtea, Thanks your started this post. I learn alot. :)

---


---
title: "Few Questions, simple but important to me!"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Isoss on 2006-06-11
I went googling and couldn't find good answers. I am trying to free some space cuz I've got a lotta installed uneeded applications. 

Here are the question:

1. I started "Add/Remove Applications" to remove some uneeded programs. But some applications wouldn't be removed unless I remove it's dependencies. Like I wanted to remove Dictionary from Accessories so the software asked me to remove gnome-utils, gnome-utils depends on ubuntu-desktop! I don't wanna remove the gnome-utils or ubuntu-desktop! So what do u suggest? What should I do in the case of removing any application that has a dependency which I never want to remove?

2. I was checking some high-sized applications with synaptic and saw that ubuntu-docs occupy 33MB. I am not sure what these are, seem like help item or manual to me but I've never used it and never now how to use it. Fortunately it has no dependecy. So I think I will remove it since I dunno how to use it! I've been using linux for for more than 3 months now and have switched to it 100%, all the help and HOWTOs that I needed were easily available for me online, especially this forum. You can see that I have 290 posts and you can consider 99% of them as questions and solving problems. I can't wait untill I'm an expert so I can be helpfull and a benefit for others.;-)  and I guess the nearest linux user to me is a 100 miles away so the only help I can get is online ... so ... ummm what was my question?:rolleyes: aha ... The question is: Will removing ubuntu-docs be problem? What benefit can I get from them? are they the same the ones in [http://help.ubuntu.com/?](http://help.ubuntu.com/?)

3. Is there a "Easy Ubuntu" for Dapper? Cuz the one I have updates my repositories to breezy while I have dapper!

4. Does automatix work with dapper? You know since I found that easy ubuntu which also is one of the 3rd party projects didn't work, so before i try out I need to know.

5. What are exactly the packages like Paython2-.4-kde3 and paython-reportlab for? I mean I know that paython is a programming language but since I don't use it why do I need for example a reportlab library to create  PDF documents using paython? I am asking because they are installed and have dependencies like kubuntu-desktop which I also have it installed.

That's it ... I guess all are simple. Every body knows how to fry eggs, but how would you know if you've never seen your mom frying some for ur breakfast?;-)

---

### Post by ????? on 2006-06-11
Have you tried Synaptic? (System > Admin > Synaptic)

---

### Post by fluffington on 2006-06-11
> **Isoss]1. I started "Add/Remove Applications" to remove some uneeded programs. But some applications wouldn't be removed unless I remove it's dependencies. Like I wanted to remove Dictionary from Accessories so the software asked me to remove gnome-utils, gnome-utils depends on ubuntu-desktop! I don't wanna remove the gnome-utils or ubuntu-desktop! So what do u suggest? What should I do in the case of removing any application that has a dependency which I never want to remove?[/QUOTE]

As far as I can tell, gnome-dictionary is part of the gnome-utils package. And you can't uninstall just part of a package. As far as ubuntu-desktop goes, that's just a dummy package that depends on Ubuntu's default install said:**
> 2. I was checking some high-sized applications with synaptic and saw that ubuntu-docs occupy 33MB. I am not sure what these are, seem like help item or manual to me but I've never used it and never now how to use it. Fortunately it has no dependecy. So I think I will remove it since I dunno how to use it! I've been using linux for for more than 3 months now and have switched to it 100%, all the help and HOWTOs that I needed were easily available for me online, especially this forum. You can see that I have 290 posts and you can consider 99% of them as questions and solving problems. I can't wait untill I'm an expert so I can be helpfull and a benefit for others.;-)  and I guess the nearest linux user to me is a 100 miles away so the only help I can get is online ... so ... ummm what was my question?:rolleyes: aha ... The question is: Will removing ubuntu-docs be problem? What benefit can I get from them? are they the same the ones in [http://help.ubuntu.com/?](http://help.ubuntu.com/?)

The ubuntu-docs package is the official Ubuntu handbook, and it contains a lot of the stuff you get when you go to System > Help > System Documentation. Remove it if you like, but I'd leave it.


[QUOTE=Isoss]3. Is there a "Easy Ubuntu" for Dapper? Cuz the one I have updates my repositories to breezy while I have dapper![/QUOTE]

I don't know. Check out [the Easy Ubuntu forum](http://www.ubuntuforums.org/forumdisplay.php?f=86)

[QUOTE=Isoss]4. Does automatix work with dapper? You know since I found that easy ubuntu which also is one of the 3rd party projects didn't work, so before i try out I need to know.[/QUOTE]

[Yes](http://www.ubuntuforums.org/showthread.php?t=177646).

[QUOTE=Isoss]5. What are exactly the packages like Paython2-.4-kde3 and paython-reportlab for? I mean I know that paython is a programming language but since I don't use it why do I need for example a reportlab library to create  PDF documents using paython? I am asking because they are installed and have dependencies like kubuntu-desktop which I also have it installed.[/QUOTE]

First of all, it's Python (like the snake, no 'a'). Next, python2.4-kde is the KDE bindings package for python, and python2.4-reportlab is the reportlab bindings, which allows PDF creation. You may not use them, but I'm pretty sure there are some bits of KDE that wouldn't function without them.

EDIT: fixed a broken QUOTE tag

---

### Post by Isoss on 2006-06-11
hmmm .. first, thanks for the fast reply.
I think I will keep ubuntu-docs I may need them indeed although I prefere googling or posting in forums.

a lotta application depend on ubuntu-desktop ... I don't wanna remove ubuntu-desktop inorder to remove some needless application! There seem to be hundreds of application that have the same dependecy! What can I do in this case?

---

### Post by fluffington on 2006-06-12
[QUOTE=Isoss]a lotta application depend on ubuntu-desktop ... I don't wanna remove ubuntu-desktop inorder to remove some needless application! There seem to be hundreds of application that have the same dependecy! What can I do in this case?[/QUOTE]

It's the other way around; ubuntu-desktop depends on a lot of packages, specifically everything in the default install. Nothing depends on ubuntu-desktop (they shouldn't anyway). Removing ubuntu-desktop is perfectly safe and does absolutely nothing aside from making it possible to uninstall stuff that's part of the default install.

---

### Post by Isoss on 2006-06-12
Thanks. I thought by removing ubuntu-desktop I wouldn't be able to login again to a desktop environment, so it would just take me to something like the recovery mode. And that happened once for some other reason untill I had to reinstall ubuntu-desktop from the recovery mode.

So, correct me if I'm wrong, here is what I have just realized: when I install for example xubuntu-desktop, it's its dependencies and the related packages which are usually installed by default that setup the desktop invironment and not the xubuntu-desktop package itself! I noticed it's not a big-sized application. That really makes me more comfortable. Thanks a bunch my friend. :)

---


---
title: "Firefox can't automatic update. How shall I do it for automatic update?"
date: 2008-06-01
forum: Desktop Environments
---

### Post by aurora_consurgens on 2008-06-01
Hello, Everybody

I use Firefox but it can't automatic update. I try to _Help_ but _Check for updates_ is disabled. How shall I do it for automatic update?
And I use Gusty. Thank you...

---

### Post by Bubba64 on 2008-06-01
> **aurora_consurgens said:**
> Hello, Everybody

I use Firefox but it can't automatic update. I try to _Help_ but _Check for updates_ is disabled. How shall I do it for automatic update?
And I use Gusty. Thank you...

Are you try to update Gutsy or Firefox.

---

### Post by gootoo on 2008-06-01
It is clean.
he/she want ask how to update Firefox.

---

### Post by Bubba64 on 2008-06-01
> **gootoo said:**
> It is clean.
he/she want ask how to update Firefox.

If your saying it is clear what they want to do, the problem with giving advice on this is it appears that the poster doesn't know that FF2 in Gutsy is the final release for that distribution from the repositories. Consequently an update can be done easily to FF3 but it could be done wrong and the poster could lose the bookmarks and add ons and plugins, even though they are in the Mozilla file they may not be easy to just transfer from FF2-FF3 if a mistake is made. The upgrade in the preference section of Firefox is grayed out because it is a compiled version by the developers of Gutsy or Hardy.

---

### Post by trigsenior on 2008-06-01
i gues you are tying to update firefox if yes this is how i did in hardy ... should be same as gutsy i belive

open up a treminal and run this 

 sudo nano /etc/apt/sources.list

add this to list > deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main

ctr - x - y 

then in terminal sudo apt-get update

now go to synmatic package list and install latest version firefox 3:0

that worked for me , there is probally a easyer way though 

PS: all you bookmarks are not lost they go to new version

---

### Post by Bubba64 on 2008-06-01
> **trigsenior said:**
> i had the same problem , this is how i fixed it 

open up a treminal and run this 

 sudo nano /etc/apt/sources.list

add this to list > deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main

ctr - x - y 

then in terminal sudo apt-get update

now go to synmatic package list and install latest version firefox 3:0

that worked for me , there is probally a easyer way though 

PS: all you bookmarks are not lost they go to new version

Right I know I did the same thing in Hardy. and when I was using Gutsy I also installed the Hardy version of FF3 and had no problems but if you have noticed some people have not liked FF3 and have had problems although sa small amount in comparison of all the people using FF3,so advising this original poster without making sure they understand what they are doing is not a good Idea. The Launchpad update is easily found on the net. The question was why is the update grayed out I am assuming in the FF preferences. Just giving advice on something that can possibly cause problems is not what I am going to do.

---

### Post by trigsenior on 2008-06-01
yes , sorry should have been more clear , but i had to update because whenever i used flash in FF it used to crash . and have had no problems with new version as yet with new version.

---

### Post by Bubba64 on 2008-06-01
> **trigsenior said:**
> yes , sorry should have been more clear , but i had to update because whenever i used flash in FF it used to crash . and have had no problems with new version as yet with new version.

I am just concerned because the original poster has not responded yet. Your post is a good one that is the method and I thought of posting the same thing but was just concerned, due to whether they understood the compiling version in distributions, and that they were updated with the Gutsy version of FF.

---

### Post by Leed on 2013-04-04
I can strongly feel with the author. The Windows Version of Firefox automatically gets it's updates, the Ubuntu one seems to be stuck to the repository

---

### Post by oldos2er on 2013-04-04
Old thread closed.

---


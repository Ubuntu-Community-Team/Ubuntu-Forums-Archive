---
title: "Newbie here"
date: 2005-07-29
forum: Desktop Environments
---

### Post by theQmaster on 2005-07-29
Hi,

Great stuff going on in the linux area.  Liked the work (K)Ubuntu did/does.

As I said I'm new to Kubuntu and I'd like to know more about how to do stuff.

I've seen the ubuntu unofficial guide of Chua Wen Kiat  at
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Even though I know  that most of it will apply to Kubuntu there are stuff I couldn't find. For example it refers to gedit but gedit is not in Kubuntu. 

Are these two projects going to go in tandem or they'll separate ? It's a bit confusing. Sorry if the question was been addressed before, couldn't KDE and GNome be present in Ubuntu in the same time so Kubuntu would be Ubuntu ?

Thanks!
Q
http:\\[www.goodstockimages.com](www.goodstockimages.com)

---

### Post by phen on 2005-07-29
[QUOTE=theQmaster]Hi,

Great stuff going on in the linux area.  Liked the work (K)Ubuntu did/does.

As I said I'm new to Kubuntu and I'd like to know more about how to do stuff.

I've seen the ubuntu unofficial guide of Chua Wen Kiat  at
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Even though I know  that most of it will apply to Kubuntu there are stuff I couldn't find. For example it refers to gedit but gedit is not in Kubuntu. 

Are these two projects going to go in tandem or they'll separate ? It's a bit confusing. Sorry if the question was been addressed before, couldn't KDE and GNome be present in Ubuntu in the same time so Kubuntu would be Ubuntu ?

Thanks!
Q
http:\\[www.good.stockimages.com](www.good.stockimages.com)[/QUOTE]
 try kedit instead of gedit. they do the same i think. you can install gnome in kubuntu or kde in ubuntu. its just a matter of convienience for the user to have the two different distros.

i think you have to install ubuntu-desktop in kubuntu, to install the ubuntu gnome desktop!

(sudo apt-get install ubuntu-desktop)

cheers,

kai

---

### Post by theQmaster on 2005-07-29
Thanks for replying. Unfortunatelly I see no kedit.

Then I see no Knetworkconf even though I've run
*sudo apt-get install knetworkconf*

It's pretty frustrating no to find things that should be there. Do I need to use root to get that in there ?

Thanks and looking forward to here from you Masters,
Q
http:\\[www.goodstockimages.com](www.goodstockimages.com)

---

### Post by Xian on 2005-07-29
[QUOTE=theQmaster]Thanks for replying. Unfortunatelly I see no kedit.[/quote]
KDE Start Menu > Utilities > Simple Text Editor (KEdit)

[QUOTE=theQmaster]Then I see no Knetworkconf even though I've run
*sudo apt-get install knetworkconf*

It's pretty frustrating no to find things that should be there.[/QUOTE]
KNetworkConf is a KDE Control Center Module 
It lets you easily configure the settings of your network devices.

Accessible in the KDE Control Center > Internet & Network

---

### Post by theQmaster on 2005-07-29
I found the network connection and settings. Took me a while.

Now I'm looking for a console editor... Anyone ?

Q
[www.goodstockimages.com](www.goodstockimages.com)

---

### Post by theQmaster on 2005-07-29
I only could find KATE under utilities unless... I'm blind :)

---

### Post by Xian on 2005-07-29
[QUOTE=theQmaster]I found the network connection and settings. Took me a while.

Now I'm looking for a console editor... Anyone ?[/QUOTE]
KDE Start Menu > System > Terminal Program (Konsole)

[QUOTE=theQmaster]I only could find KATE under utilities unless... I'm blind :)[/QUOTE]
KDE Start Menu > Debian > Apps > Editors > Kate

---

### Post by c0rderr0y on 2005-07-29
what did was replace all the gedits and replaced them with vi..... but be prepared to learn how to use vi

---

### Post by Xian on 2005-07-29
[QUOTE=c0rderr0y]what did was replace all the gedits and replaced them with vi..... but be prepared to learn how to use vi[/QUOTE]
Heh. I admire a person with a large bite. 
Nice show.

Meanwhile, I'll still use gedit. :)

If you are using KDE pre-3.4.2 you'll need to use kwrite
in place of gedit in those command line examples
in the Starter Guide.

You can also use 'nano -w' if you like the terminal interface.
$ sudo nano -w /path/to/file

---

### Post by theQmaster on 2005-07-29
What I did was to install gnome :) or rather :(

I kept the kdm and it's okay I can start different session using but now I'm thinking maybe to uninstall it. Besides the space is there any "side efect" installing it ? ( does it takes extra extra resources (mem/cpu) to have it installed). 

How do I uninstall apps that I've installed ?

This machine I installed KU on is meant to be a server and I want to first configure it and then shutdown any other resourse consuming daemon/apps - from what you know is it there any way to start the machine in a "server mode" and then at startup to decide whether to start it in desktop mode or not ?


I've seen that KDE 3.4.2 was released yesterday. Anyone has any troubles installing it ?

Oh, one more thing - the fonts on kde destop are unbeareable large, how do I reduce them ?



Thanks all for quick, funny and prompt responses,
Q
http:\\[www.goodstockimages.com](www.goodstockimages.com)

---


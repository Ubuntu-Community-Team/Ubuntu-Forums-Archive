---
title: "Netflix Help!!!"
date: 2013-04-04
forum: Gaming &amp; Leisure
---

### Post by tsi25 on 2013-04-04
I figured this would go under "leisure" but i could be sorely mistaken. if i am i apologize, could you please refer me to the thread i should be in? 

so I'm running ubuntu 12.10, and ive been using netflix-desktop. i got it to work using the following procedure which was given to me on a website:


[LIST=1]
[*]Open a terminal window
[*]Issue the command sudo apt-get update
[*]Enter your sudo password
[*]Once the update completes, issue the command sudo apt-get upgrade
[*]Accept the updates
[*]If prompted (in case of a kernel upgrade), reboot the machine
[/LIST]

nextly


[LIST=1]
[*]Open up a terminal window
[*]Issue the command sudo apt-add-repository ppa:ehoover/compholio
[*]Hit Enter
[*]Issue the command sudo apt-get update
[*]Issue the command sudo apt-get install netflix-desktop
[/LIST]

lastly


[LIST=1]
[*]Open the Unity Dash
[*]Type *netflix*
[*]Click Install on the Wine Mono Installer (this is necessary for .NET)
[*]Click Install on the Wine Gecko Installer (this is necessary for embedded HTML to work properly)
[*]If you get an error, OK the error (I had this same thing happen on two machines — everything worked fine anyway)
[*]Allow the local installation to complete
[/LIST]

(this is courtesy of the tech republic)

netflix desktop was working fantastically until about yesterday evening (March 3rd, 2013) when i learned there had been a Silverlight update. i tried to just click the download button provided me in the window but it just popped up with a .exe and i couldnt get it to do anything useful.

does anyone know, or have access to an updated way to get netflix streaming up and running again?

(p.s. netflix still opens, and i can select something to watch, but rather than streaming the video it tellls me that i need to update silverlight. i have tried uninstalling and reinstalling netflix-desktop using the procedure above but it was ineffectual.)

---

### Post by breezypt on 2013-04-04
That ppa bricked my whole OS. I had to do a complete wipe afterwards.

---

### Post by tsi25 on 2013-04-04
i experienced no adverse effects from it. maybe we have different distributions of linux? or different versions of ubuntu?

---


---
title: "[SOLVED] Problems installing Xfce on Dell subnotebook"
date: 2007-07-07
forum: Desktop Environments
---

### Post by atomic_turtle on 2007-07-07
Hi,

my problem is actually somewhere inbetween this category, the "General Help" and "Ubuntu Dell Support".
I have a Dell Latitude C400 currently running Kubuntu Dapper. Yesterday I tried to install Xfce and upgrade to Feisty to make it run a little faster.
When I installed xubuntu-desktop via synaptic, it downloaded most of the packages, then hung at "Preparing packages" and didn't move forward. Using top, I could see it was working, but not particularly much, and it definitely wasn't going anywhere. I killed it in the end.
The next day, I tried using the console and "sudo aptitude install -f xubuntu-desktop". That went reasonably quick as most of the packages were already there. From that point, I could log into Xfce - but then, the screen with the hamster representing the loading process would show for a while and then the screen would go blue, end of story. Using a Knoppix Live-CD, I had discovered a while ago that it is possible to boot from the external drive, so I thought a fresh installation of Xubuntu Feisty would be easier than trying to fix it and then upgrading which carries a risk. 
So I downloaded and burned a Xubuntu Feisty Desktop-CD, checked the MD5-sum and tried that. It bootet all right, I got the menu, but when I selected "Start/ Install Xubuntu" or any other, for that matter, it would go "Loading, please wait", and then black screen, end of story. 
I can still log in to KDE now, but that's not exactly where I wanted to go.
Does anybody have an idea why the installation from CD didn't work? I still think installing a new copy would be easier than first fixing this and then upgrading. However, any other tips are also more than welcome.
Thanks a million!
Regards,

atomic_turtle

---

### Post by bapoumba on 2007-07-07
Did you install kubuntu with the dapper live CD? Depending on you computer specs, you may want to try out the alternate CD (using the text mode debian installer).
On my very old laptop, I installed text mode, with no desktop environment, then I installed xubuntu-desktop.

---

### Post by atomic_turtle on 2007-07-07
Hi bapoumba,

I didn't install it myself at all in the first place. The guy I bought it from told me the notebook couldn't boot from the external CD - now I think it can, it worked with a Knoppix anyway, but I don't have the "original" CD-drive - and there was Ubuntu Breezy. I merely upgraded to Dapper and put another Desktop on - first Xfce and then KDE.
I know the alternate CD, I can get one for Xubuntu Feisty, no problem. I only don't know a thing about the text-mode installer. Is that on the Alternate CD?
Regards,

atomic_turtle

---

### Post by bapoumba on 2007-07-07
Hello :)

Yes, it's an option on the alternate CD.
The difference with the desktop install is that the install process does not run through a GUI, so you have no mouse. To go from one option to the other, use <tab>, to select an option, either press <enter> or use <space> (when you have to select in a list for ex, and mark your selections with a *).

Its all pretty intuitive. The only step to be careful is the partition menu. Select your root partition (/), your /home (if separate) and a swap. The final partition option is to validate all your changes.
Please check here for screenshots:
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by atomic_turtle on 2007-07-07
Hello bapoumba,

okay, I'll download an Alternate CD now and try that.
There's only one thing that confuses me now, pretty basic: I understand that Ubuntu, Kubuntu, Xubuntu or whateverbuntu are all the same system - Ubuntu - only with different GUIs? So when I download a Xubuntu Feisty Alternate CD now and do that text-mode install, there should be no real difference from if I used a Kubuntu Alternate CD because the text-mode install has no GUI. All the applications and tools come with the GUI, right?
Regards,

Qbuntschuh

---

### Post by bapoumba on 2007-07-08
Yes :) I actually installed from a regular (gnome) ubuntu alternate CD, because I had one handy after installing on a desktop. I did try gnome, tough, on my old laptop, but it was all very slow.

---

### Post by atomic_turtle on 2007-07-09
Thanks for the help, bapoumba!
I have installed Xubuntu Feisty now and it's working, so I guess this thread is closed. Of course, one solved problem instantly gives birth to more, but I'll make new threads for those ;-)
Regards,

atomic_turtle

---

### Post by bapoumba on 2007-07-09
You're welcome.
In the thread tools, there should be an option for you to mark the thread as [Solved] (or close) ;)

---


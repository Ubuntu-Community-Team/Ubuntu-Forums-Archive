---
title: "Howto remove Kubuntu desktop"
date: 2012-10-07
forum: Desktop Environments
---

### Post by malel on 2012-10-07
I am running Ubuntu 12.04 and decided to try  Kubuntu desktop. I didn't like so tried to remove it but it has left a lot of KDE appliances still on the machine . I used 'aptitude' to install and aptitude to remove it . Although it now says that Kubuntu is no longer installed there are plenty of stuff left over . For instance the Startup screen, and desktop will not go back to the original ubuntu screen . It seems to be very screwed up . I have tried what others have said in the forums but aptitude does not work fro me in removing kubuntu .

Ubuntu 12.04 64 bit 1Gb ram

---

### Post by PaulW2U on 2012-10-07
kubuntu-desktop is only a meta package.

See [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu) for instructions on how to remove everything that kubuntu-desktop installed. Good luck.

---

### Post by oldos2er on 2012-10-07
Try [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by malel on 2012-10-07
Thanks folks . I already said that I had tried these thingsw but they just don't work for me. I don't think you should be pointing people to something that does not work ,

---

### Post by robtygart on 2012-10-07
I had the exact same problem, but I was using Kubuntu and I put Ubuntu Desktop on it, it was a very bad idea. 

If you want it to have the "Kubuntu" desktop, I think you should be looking for KDE (Kubuntu should come with a full set of KDE flavored applications.)

I should have put on a Gnome Desktop... I think "gnome-fallback"??


EDIT:

To fix mine I just did a fresh install.

---

### Post by malel on 2012-10-07
Thankyou Robygart it looks like I may have to do that also . May have to run a Fedora OS

---

### Post by PaulW2U on 2012-10-07
> **malel said:**
> I don't think you should be pointing people to something that does not work

Well, it's worked for me in the past and for others after I've told them about the site.

To be fair you weren't very specific about what you had already tried.

---

### Post by ajgreeny on 2012-10-07
> **malel said:**
> Thanks folks . I already said that I had tried these thingsw but they just don't work for me. I don't think you should be pointing people to something that does not work ,
Are you sure it didn't work?

Have you chosen the correct ubuntu version to remove all of the kubuntu-desktop dependencies?  What error message do you get when you run that ```
sudo apt-get remove akonadi-backend-mysql akonadi-server------&& sudo apt-get install ubuntu-desktop
```command?

---

### Post by bra|10n on 2012-10-07
If you are familiar with 'Aptitude' as opposed to 'Apt' then you could look into using the *rdepends *option to list all of the packages brought in by kubuntu-desktop.
This will isolate packages you want to be rid of...

There would still be some 'massaging' involved though, eg resetting to GDM, plymouth etc

---

### Post by oldos2er on 2012-10-08
> **malel said:**
> Thanks folks . I already said that I had tried these thingsw but they just don't work for me. 

Can you post the terminal output (inside code tags, please) so we can see exactly what doesn't work?

---

### Post by Frogs Hair on 2012-10-08
I used the posted method to remove the Kubuntu desktop and though it was a long process it did remove the login screen but there was some cleanup to do in synaptic. I will install kubuntu if want to try again.

---

### Post by skinnerc1989 on 2012-12-31
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

(remember to keep scrolling and copy/paste the whole code (ending with "&& sudo apt-get install ubuntu-desktop" as without this last bit you are left with no desktop environment, and nothing more than a tty shell to work with on reboot))

always works for me, make sure to either:

reboot or:

ctrl+alt+f1 to enter tty1
login with user and pass


then enter in tty:

sudo service lightdm stop
sudo service lightdm start


just to make sure everything goes back to the way its supposed to.

---


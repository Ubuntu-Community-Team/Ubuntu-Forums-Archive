---
title: "32-bit prog is a meanie on 64-bit Kubuntu"
date: 2014-02-15
forum: Desktop Environments
---

### Post by Tom_ZeCat on 2014-02-15
I'm having an awful time installing a French verb conjugation application named Le Conjuguer ([http://leconjugueur.lefigaro.fr/uktelechargelinux.php](http://leconjugueur.lefigaro.fr/uktelechargelinux.php)).  I use it on my Lenovo laptop with Kubuntu 13.10.  On that laptop I had originally installed Kubuntu 13.04 and later upgraded.  When it was still 13.04 I installed Le Conjuguer and had some troubles getting it to run, which I documented in case I ever needed to install it again.  It's been running flawlessly on my Lenovo for months.  On my Asus netbook that I just bought, the debian package installed, but the application won't run.  

According to my notes: 

> Le Conjuguer is a 32-bit program. If your Linux distro is 64-bit, you need this package for it to run: 
ia32-libs-multiarch 

sudo apt-get install ia32-libs

When I try to run that, I get a message saying the package has been obseleted, but that … 
> However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0

So I installed those in Synaptic, but LC still won't run.  Annoying.  I had documented exactly what worked last time to get the thing to run, but that failed.  I googled around to learn that others have been having the same problem.  Turns out in Ubuntu/Kubuntu 13.10 they've dropped support for that package those tree new packages that replace it don't run LC. Frustrating.  

I thought I found the solution here: 
[http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10](http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10)

It suggests: 

> Install Synaptic from terminal window
1. sudo apt-get install synaptic
2. Launch synaptic and goto “settings > Repositories”
3. click “other software > add”
4. insert this line in the box "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse"
5. click ok and close synaptic
6. in terminal “sudo apt-get update”
7. in terminal “sudo apt-get install ia32-libs”

I did that, but when I try to do the last step, installing ia32-libs in the terminal, I get the same message about it being obsoleted and replaced by "lib32z1 lib32ncurses5 lib32bz2-1.0".  

On another page, someone suggested recompiling the program so that it's dependent on the current 32-bit files, not the old one.  However, I find no source code on LC's site.  

But obviously this thing is running on my Lenovo laptop.  It's also a Kubuntu 13.10 computer, the difference being that it started as 13.04 and this problem was solved back when it was the older Kubuntu.  

I nearly istalled the 32-bit version of Kubuntu onto this netbook.  It's only got 2 GB of RAM, which cannot be upgraded, and therefore doesn't need the 64-bit version.  However, I chose the 64-bit version because I want to run FreeFileSync.  That program only has a 64-bit version.  

I've done what I know to do and I've searched the net and tried what I've found, but I'm hitting a brick wall.  It's time to reach out for help.  What can I do to get this thing to run?  Can I somehow take the needed packages from my Lenovo and transfer them over?  

Le Conjuguer is a far better program than the French verb conjugator available in the repositories (Verbiste).  

Ideas?

---

### Post by tgalati4 on 2014-02-15
A decision was made, I don't know by who, but a poll was conducted on this forum asking about the effects of completely dropping 32-bit support.  This apparently makes the 64-bit code cleaner and easier to support.  I don't know if there is a work-around.  Perhaps you could load a virtual machine with 13.04 just to run your conjugator.

Perhaps ask the developer to recompile for 64-bit?

---

### Post by kostkon on 2014-02-16
> **Tom_ZeCat said:**
> I did that, but when I try to do the last step, installing ia32-libs in the terminal, I get the same message about it being obsoleted and replaced by "lib32z1 lib32ncurses5 lib32bz2-1.0".
Yes, ia32-libs has been obsoleted, and it isn't available anymore in the 13.10 repos, more info [here]("https://help.ubuntu.com/community/MultiArch"). You don't need to install any additional packages yourself. But if an application during installation (or even during runtime) asks for the 32bit version of some packages/libs, you install them like this
```
sudo apt-get install package_name:i386
```

What happens when you try to install or if you have managed to install it, do you get any output coming from the app in question when you run it from the terminal?

---

### Post by Tom_ZeCat on 2014-02-16
> **kostkon said:**
> Yes, ia32-libs has been obsoleted, and it isn't available anymore in the 13.10 repos, more info [here]("https://help.ubuntu.com/community/MultiArch"). You don't need to install any additional packages yourself. But if an application during installation (or even during runtime) asks for the 32bit version of some packages/libs, you install them like this
```
sudo apt-get install package_name:i386
```

What happens when you try to install or if you have managed to install it, do you get any output coming from the app in question when you run it from the terminal?

Success!  Thanks to your information I was able to figure it out.  I'll document here what worked so that others doing searches may benefit.  

When I attempted to run Le Conjugueur in the terminal, I got this: 

```
leconjugueur: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

So using the info you gave me, I installed it like this: 

```
sudo apt-get install libgtk2.0-0:i386
```

And voilà!  It runs now.  I very much appreciate the both of you for your help.  I would have been seriously bummed if I had had to give up using LC when using my netbook.  It has a lot of features that Verbiste does not.  I do think I'll write to the developer requesting an update so that others can use this terrific tool.  He hasn't developed the Linux version since Ubuntu 8.04 .  Hopefully my French is up to the task.

---

### Post by oldos2er on 2014-02-16
Tom_ZeCat, could you please mark the thread as 'Solved' under Thread Tools? It will help others having the same problem. Thanks.

---

### Post by Tom_ZeCat on 2014-02-16
> **oldos2er said:**
> Tom_ZeCat, could you please mark the thread as 'Solved' under Thread Tools? It will help others having the same problem. Thanks.

Done.  Thanks for the heads up.

I'm also reproducing here the letter I wrote to the programmer since it might help French speakers who are searching the Internet for a solution (though I make no guarantees of perfect French).  Here it is.  An English version follows.  

> Depuis plusieurs mois j'ai le plaisir d'utiliser votre logiciel de conjugaison française, Le Conjugueur, sur mon ordinateur Kubuntu Linux.  Pourtant quand j'essayais de l'installer sur un nouvel ordinateur, j'ai rencontré des difficultés.  J'ai résolu le problème et maintenant il fonctionne.  Je vous fournis les informations afin de peut-être aider d'autre utilisateurs de Linux, au cas où vous souhaiteriez les publier sur votre site internet.  

J'utilise la version 64 bits de Kubuntu 13.10.  Malheureusement, au début de la version 13.10 de toutes les variétés de Ubuntu (Kubuntu y compris), le support pour le paquet 32 bits nécessaire pour exécuter Le Conjugueur a été abandonné.  Votre paquet d'installation Debian a quand même installé l'application sur mon ordinateur, mais il pouvait pas s'exécuter puisque le paquet 32 bits "libgtk2.0-0" n'était pas présent.  A partir d'Ubuntu 13.10, voici la ligne de commande pour installer ce paquet: 

sudo apt-get install libgtk2.0-0:i386

Après avoir exécuté cette commande, j'ai eu le plaisir de constater que Le Conjugueur marchait.  C'est une excellente application que j'aurais regretté de ne plus pouvoir utiliser. J'espère que cette information vous sera utile.  Merci.  

> For several months I've enjoyed running your French verb conjugation software, Le Conjugueur,on my Kubuntu Linux computer. However, when I attempted to get it to run on a new computer, I ran into difficulties.  I've solved the problem and it now runs.  I'm writing with the information for you so that perhaps it can help other Linux users should you wish to include it on your web page.  

I'm using the 64-bit version of Kubuntu 13.10.  Unfortunately, starting with version 13.10, all varieties of Ubuntu (including Kubuntu) have dropped support for the 32-bit package needed to run Le Conjuguer.  Your Debian install package still installed the application to my computer, but it would not run since the 32-bit package &#8220;libgtk2.0-0" was not there.  Starting with Ubuntu 13.10, the terminal command with which to install it is as follows: 

sudo apt-get install libgtk2.0-0:i386

After I ran this command in the terminal, I was pleased that Le Conjuguer would run.  It's an excellent application that I would miss if I did not have it.  I hope this information has proven useful.  Thank you.  

---


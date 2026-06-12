---
title: "I want to get back gnome"
date: 2006-06-25
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-06-25
I am using KDE on ubuntu dapper. I can't login to gnome. How can I winback gnome ? Please help

---

### Post by Winblowz on 2006-06-25
Do "sudo apt-get install ubuntu-desktop" if you don't have Gnome installed already. Then, do "sudo apt-get remove kubuntu-desktop" to get rid of KDE (Kubuntu).

---

### Post by aysiu on 2006-06-25
Actually ```
sudo apt-get remove kubuntu-desktop
``` won't get rid of anything except a pointer to Kubuntu's default packages (not the packages themselves).

When you say you can't log into Gnome, can you be more specific? Does Gnome not appear in the sessions menu? Have you already installed Gnome? Do you appear to be able to select it, but you get some kind of error when you actually try to log in?

Please provide as many details as you can.

---

### Post by krypto_wizard on 2006-06-25
Well, I had breezy on my laptop with both gnome and kde running fine. I was testing kde for a short time. When I tried loggin in to gnome it takes me to the main screen of gnome but I cannot play application in gnome. I then upgraded to dapper thinking that it would remove such problems. But the problem is persisting.

Now when i login, sometimes gnome session hangs while booting ( when gnome  session is starting), sometimes it starts but i cannot start any application. Looks like its seriously corrupted.

I tried sudo apt-get install ubuntu-desktop

I dont want to remove kde since i am not too sure if gnome would work fine if I remove kde.

I have to do some coding with python and wxPython. In KDE the looks are not clean because its built on qT. I want to go back to gnome.

I don't know how to get it back. Will installing gnome help my cause.

Please help,

Every help is greatly appreciated.





[QUOTE=aysiu]Actually ```
sudo apt-get remove kubuntu-desktop
``` won't get rid of anything except a pointer to Kubuntu's default packages (not the packages themselves).

When you say you can't log into Gnome, can you be more specific? Does Gnome not appear in the sessions menu? Have you already installed Gnome? Do you appear to be able to select it, but you get some kind of error when you actually try to log in?

Please provide as many details as you can.[/QUOTE]

---

### Post by aysiu on 2006-06-25
Can you try this from KDE? ```
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old
mv ~/.gnome ~/.gnome.old
mv ~/.gnome2 ~/.gnome2.old
mv ~/.icons ~/.icons.old
mv ~/.metacity ~/.metacity.old
mv ~/.nautilus ~/.nautilus.old
mv ~/.themes ~/.themes.old
``` Then log out and try to log into Gnome again?

---

### Post by krypto_wizard on 2006-06-25
I tried this, but it still hands while booting into gnome. Any other clues as to what is going wrong with gnome ?

One more thing I wanted to tell. When sometimes it can get into gnome it cant start any application.
If I Try to run anything from command line I get an error mesage

GTK Accessibility Modile Intialized
Segmentation Fault

And I get the command prompt again.

thanks for your help.

[QUOTE=aysiu]Can you try this from KDE? ```
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old
mv ~/.gnome ~/.gnome.old
mv ~/.gnome2 ~/.gnome2.old
mv ~/.icons ~/.icons.old
mv ~/.metacity ~/.metacity.old
mv ~/.nautilus ~/.nautilus.old
mv ~/.themes ~/.themes.old
``` Then log out and try to log into Gnome again?[/QUOTE]

---

### Post by aysiu on 2006-06-25
Does it have something to do with *at-spi*?
[https://launchpad.net/products/at-spi/+bug/31157](https://launchpad.net/products/at-spi/+bug/31157)

---

### Post by krypto_wizard on 2006-06-25
I think I have pretty much the same thing as explained in that post....IS there a way to fix this ?

[QUOTE=aysiu]Does it have something to do with *at-spi*?
[https://launchpad.net/products/at-spi/+bug/31157](https://launchpad.net/products/at-spi/+bug/31157)[/QUOTE]

---

### Post by aysiu on 2006-06-25
I don't know. ```
sudo aptitude remove at-spi
``` maybe?

---

### Post by krypto_wizard on 2006-06-26
It partially helped. Atleast some apps are starting now like synaptic. The icons in my panel above are all lost..dont know why. 

will installing gnome fix it ? Any other clues ...

Your help has been great for me till now. Thanks

[QUOTE=aysiu]I don't know. ```
sudo aptitude remove at-spi
``` maybe?[/QUOTE]

---

### Post by krypto_wizard on 2006-06-26
I did a 

sudo apt-get install ubuntu-desktop after removing at-spi and I think it seemed to fix the problem.

Thanks for all your help. I really appreciate this.

Thanks

---


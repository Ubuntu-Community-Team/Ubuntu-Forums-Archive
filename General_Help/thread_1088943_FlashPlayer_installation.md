---
title: "FlashPlayer installation"
date: 2009-03-06
forum: General Help
---

### Post by mark bower on 2009-03-06
newcomer - Ubuntu 8.10.  in synaptic pkg mgr i select "flashplugin-non free 10.0.22.87" for installation, and select apply.  says it is installed.  i go to applications/graphics and it does not show.  and it appears it is not installed when i go to a site that demands flashplayer.  what am i doing wrong?

mark bower

---

### Post by thtrgremlin on 2009-03-06
if you go to youtube.com, and you click 'get flashplayer' it sends you to a site to download a .deb. The directions there are reasonable to follow.

Did you try that route?

---

### Post by jwbrase on 2009-03-06
Are you using Firefox? Are you running 64-bit Ubuntu?

---

### Post by wpshooter on 2009-03-06
My suggestion would be that you first go back to Synaptic and uninstall the flash plugin.

And then do a Google search on Adobe and then make sure that you are at the "REAL" Adobe site and once you are there find and download and then install the full Linux version of Flashplayer.  If you are not familar on how to do this you may want to request some further detailed instructions on how to do the installation before you start.

---

### Post by mark bower on 2009-03-06
@jwbrase
firefox, yes.  how do i determine whether i am running 32 or 64 bit Ubuntu 8.10?

@wpshooter/thtrgremlin, no, i do not know how to install after a download from a site.  i will uninstall and try the utube idea since you indicate instructions there for me, i assume instructions might be generic for other downloads?

---

### Post by mark bower on 2009-03-06
o.k.

i uninstalled in syn pkg mgr.  then went to adobe.com (you tube did not seem to work - got into a charge thing so aborted utube) and did 2 things with the Ubuntu 8.04+ ver 10.0.22.87 ver: 1) downloaded flashplayer to the desktop, and 2) selected "GDeb: Pkg Installer" and presumably installed.  Flashplayer does not show in Apps/Graphics and is not functional with test at website which demands it.  So now what please, and again, how do i determine if Ubuntu is running on 32 or 64 on my machine?  in fact, is it selectable or is it a function of the distribution.

---

### Post by zvacet on 2009-03-06
To find what is your version 

```
uname -a
```

For installing flash plugin add this line in your source list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

if you are runing Intrepid then replace hardy with intrepin in above line

Save and close.

```
sudo apt-get update
```

After that go to the synaptic and uninstall flashplugin-nonfree and install **adobe-flashplugin**.

---

### Post by mark bower on 2009-03-06
@zvacet

uname -a shows i686 which i have read means 32 bit, settled.

1)unfortunately, i am too new to know what the add to source list process is, ie, i need verbose instructions please.  

2)i do know how to operate on the cmd line so i can do the apt get update, althoh i believe i have already done an update a few days ago by some sort of prompt i received - just can't remember.

3)then, i assume you mean after removal of the non-free version with syn pkg mgr, reload using syn pkg mgr the adobe-flashplugin. and not the flashplayer i downloaded from adobe to the desktop?

---

### Post by entr3p on 2009-03-06
***_Installing Adobe Flash Player_***
If you just recently installed Ubuntu, you may have noticed that if you go to a website using Flash, such as YouTube that it will tell you to get the latest Flash player to watch the content. There are three ways to do this in Ubuntu and their all extremely fast and easy to do.

Through Firefox: Simply visit a website using Flash and a yellow bar will appear on the top telling you that you're missing a plugin.
Click on &#8220;Install Missing Plugins...&#8221; and choose &#8220;Adobe Flash Player&#8221;.

Through &#8220;Add/Remove Applications&#8221;:  In the search box type in &#8220;Macromedia&#8221; and click on the check box next to the program &#8220;Macromedia Flash plugin&#8221;. Once you're ready click on &#8220;Apply Changes&#8221; and the program will be installed.


Through The Terminal: Type &#8220;sudo apt-get install flashplugin-nonfree&#8221; in the Terminal.

Note: You will have to restart your web browser after installing the Flash plugin for you to use Flash.

---

### Post by SuperSonic4 on 2009-03-06
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by mark bower on 2009-03-06
tried sudo apt -get ..., says i do not have apt installed.  is there an equivalent for Ubuntu 8.10?

---

### Post by mark bower on 2009-03-06
o.k.  my syntax was wrong, i had a space between "apt" and "-get"

i downloaded at the cmd line, saw the streaming code coming in, and it said installed.  however, when i go to the website of interest, still begs for Flashplayer 7 or later.  i am going to reboot, then return here.

---

### Post by thadacto on 2009-03-06
Have a read of my install guide for AMD 64 Hardy. I'm sure that the basics are the same for the 32 bit and Ubuntu 8.10

---

### Post by mark bower on 2009-03-06
o.k. got it.  thanks to multiple players for hanging in with me on this one.

here is essentially what worked to get FlashPlayer working in 8.10:

1)uninstall flashplayer-nonfree in syn pkg mgr
2)cmd line:  sudo apt-get install flashplugin-nonfree
3)reboot computer - and voila

i will record in my notebook all three options for installing given by entr3p.

thanks again all.

---

### Post by entr3p on 2009-03-06
> **mark bower said:**
> o.k. got it.  thanks to multiple players for hanging in with me on this one.

here is essentially what worked to get FlashPlayer working in 8.10:

1)uninstall flashplayer-nonfree in syn pkg mgr
2)cmd line:  sudo apt-get install flashplugin-nonfree
3)reboot computer - and voila

i will record in my notebook all three options for installing given by entr3p.

thanks again all.

Glad to see everything worked out. I have finished the guide on how to install the FLash plugin and when my website [www.learningubuntu.com](www.learningubuntu.com) is set up it will be there for your use anytime :D.

---

### Post by mark bower on 2009-03-07
again thks.  i'll look for your site.

---


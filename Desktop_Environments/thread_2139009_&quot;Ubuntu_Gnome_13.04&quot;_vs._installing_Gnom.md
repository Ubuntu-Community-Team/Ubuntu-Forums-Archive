---
title: "&quot;Ubuntu Gnome 13.04&quot; vs. installing Gnome over regular Ubuntu 13.04"
date: 2013-04-25
forum: Desktop Environments
---

### Post by dandaman96 on 2013-04-25
Now that Gnome has an official Ubuntu flavor, I have what might be a silly question.  

What is the difference between installing the Ubuntu Gnome 13.04 distribution vs. installing Ubuntu 13.04 and then installing Gnome from the repositories?  

Does the Ubuntu Gnome dist use the same repositories as regular old Ubuntu?  Are there really any differences between the two methods of getting Gnome on your system?  

Again, sorry if this is a dumb question.  Just looking for the cleanest Gnome install on my Ubuntu box.

---

### Post by Frogs Hair on 2013-04-25
The Gnome release is stand alone(No Unity) and installing on Ubuntu would be adding second Desktop. I can't tell you if there are many different default applications but , having the shell installed I know it is set up ti work with Evolution mail and not Thunderbird. I cant speak to other differences. Updates come from the Ubuntu repositories.

---

### Post by markbl on 2013-04-25
It's not a dumb question at all. I have been asking for a definitive answer to this myself for a while.

I have always just installed the standard desktop ubuntu then immediately just "apt-get install gnome-shell". Apart from minor aesthetics and default packages I don't think there is any difference. I prefer GNOME Shell but like to have Unity installed also so I can try it out occasionally, to see if any desktop/X bugs exist there also, etc. I happen to prefer the default GNOME Shell theme you get with the Ubuntu install, rather than the default GNOME theme. The theme and default packages are trivial to change yourself anyhow so I don't see this as a practical difference.

I also add the gnome team ppa but I know this is not included by default on Ubuntu GNOME either. I don't really see the point of all the work done to create Ubuntu GNOME when a user can effectively get it via that short one line command I quote above. What I am missing?

Can an expert Ubuntu GNOME developer please explain why we should install the official flavor instead?

---

### Post by markbl on 2013-04-26
I just installed ubuntu-13.04-desktop-amd64.iso guest in Virtualbox, added gnome-shell + gnome 3 team ppa. Then for comparison, I installed ubuntu-gnome-13.04-desktop-amd64.iso in another guest, added gnome 3 team ppa. Applied all current updates to both guests. I ran them in parallel in adjacent 27" screens on my host. By default, the Ubuntu + shell installation looks *much* better using Ubuntu fonts etc, otherwise they seemed the same. I stuffed around installing light-themes to get the Ubuntu ambiance theme into Ubuntu GNOME, used gnome-tweak-tool to tweak the fonts, etc and had the Ubuntu GNOME installation looking much like the standard one. However it still had the ugly GNOME scroll bars etc. My personal conclusion is that I am going to install the normal ubuntu ISO and add gnome-shell for my main PC installation as it just looks better.

---

### Post by rrich1974 on 2013-04-26
i also have installed gnome shell over ubuntu in 12.04 and i can tell, in my opinion, unity is more polished than gnome-shell. 
and also noticed a strange fact while using stellarium:
unity...i get 13 fps 
gnome-shell ......i get 9 fps. 
why is that? i can't explain!

---

### Post by grahammechanical on 2013-04-26
> [COLOR=#000000]Just looking for the cleanest Gnome install on my Ubuntu box.[/COLOR]

Then install Ubuntu Gnome.

[http://ubuntugnome.org/](http://ubuntugnome.org/)

[http://cdimage.ubuntu.com/ubuntu-gnome/releases/13.04/release/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/13.04/release/)

Why does everything in open source have to come down to "I win. You lose" type of situation? Let us just except that there are a great variety of tastes and developers are free to use their time and skills in the directions of their choice. And we benefit by getting choice.

I installed Ubuntu Gnome when it was still a Remix. I prefer Ubuntu Unity. I shall be using the Ubuntu development branch because I want to experience Unity changing into Unity Next and then Unity Touch as the convergence policy is completed. It will also be interesting to see how the other Ubuntu flavours deal with the situation. 

Regards.

---

### Post by dandaman96 on 2013-04-26
I should have explained in the original post, my box was already running 12.10 w/ Gnome installed.  If there were significant differences in underlying components, I would have done a clean install of "Ubuntu Gnome".  

Since this post, I went ahead and updated Ubuntu to 13.04.  From there, I added the Gnome PPA and upgraded to Gnome 3.8.  After playing around with some of the information found in the link - [http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html](http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html) - I had to downgrade back to Gnome 3.6 from the 13.04 repositories.  I have a hand full of extensions that I rely upon to create my version of the perfect Gnome desktop and there were issues with these extensions (beyond updating metadata.json) in 3.8.  

As a side note, I also found that I really didn't want the cleanest Gnome install possible.  After removing ubuntu-settings and replacing it with ubuntu-gnome-default-settings, I found I liked the appearance of Gnome over Ubuntu more so than 100% gnome.  

So, until the extensions catch up to 3.8, I'm pretty set where I am.  

Thanks to those who provided input.

---

### Post by markbl on 2013-04-27
> **dandaman96 said:**
> 
As a side note, I also found that I really didn't want the cleanest Gnome install possible.  After removing ubuntu-settings and replacing it with ubuntu-gnome-default-settings, I found I liked the appearance of Gnome over Ubuntu more so than 100% gnome.
I agree completely. Removing the ubuntu-settings package changes to the default gnome fonts and theme etc which IMHO look very ugly compared to the Ubuntu settings for gnome shell. Luckily, reinstalling ubuntu-settings puts them all back. I only use one extension (media player indicator) which seems to work fine so I am staying on 13.04 + gnome 3 ppa. However there are a few annoying bugs, such as message tray icons disappearing etc. Occasionally gnome-shell seems to restart. My system often hangs on shutdown, etc. I should have followed my regular advice to delay installing a new ubuntu release for the first month. :(

---

### Post by cerotu0 on 2013-10-14
The problem I am running into is wanting to install Ubuntu-GNOME on top of an existing server and maintaining the software RAID I have on the machine.  This can only usually be accomplished using an Alternate-Install iso.  The problem I am having is that there seems to be no Alternate-Install iso for Ubuntu-GNOME 13.04, nor for the newly released 13.10RC.  I guess I will try using an Alternate-Install of the regular Ubuntu desktop and installing GNOME on top of it.  I haven't liked the experience in the past, but maybe it will work for me - unless anyone has any other ideas.

---


---
title: "ubuntu classic + compiz + cairo-dock = NIGHTMARE"
date: 2011-06-19
forum: Desktop Environments
---

### Post by phonky on 2011-06-19
First of all, I don't blame anybody. I blame myself. For upgrading on my production laptop.

I've been using ubuntu since edgy, and linux since SuSe 4.x (1997).

I was running a smooth 10.04, until I decided I would upgrade to 11.04.
What a mistake.

Of course, unity is a question of taste. I simply don't like it. But what I really was surprised to find out was that the supposedly alternative with classic gnome just does not work for me. Compiz crashes frequently, I loose window decorations when I click on an item in the cairo-dock, and everything just feels unstable. I dumped emerald in the hope it would help, no joy.

It's ok for ubuntu to try a new layout. But it should not leave users in the void who would try to stick with their old layout.

Repeat: I blame myself first. But I won't install another ubuntu anymore. I feel I have been left out. What a shame, ubuntu's ideals greatly resonated with me. I lost my weekend trying to fix it. :(

---

### Post by bkratz on 2011-06-19
I had very similar experiences with the newest version--loved 10.04 ended up trying xubuntu 11.04 and think it is ok. I left one system with 10.04 and changed the other.

---

### Post by ajgreeny on 2011-06-19
I'm with you, phonky, I tried unity on my desktop, and I simply do not like it at all, and that is after using the 2D version, as the default 3D version will not run on my computers at all.  I agree with bkratz that xubuntu may be one way to go, though I am also trying Lubuntu with the lxde desktop.  It is very fast and in many ways very like, or can easily be made to look like gnome 2 in terms of its layout on screen, if that is what you want.

For those who don't like or can not run unity, or gnome 3 when it comes, either Xubuntu or Lubuntu seem to be an island of calm in the stormy seas of unity.  They do not have the same apps as gnome2/3 but all the same apps are available in the repos and can be installed, eg libreoffice, nautilus, gimp, etc etc.

Give them both a try and you may be surprised.

---

### Post by phonky on 2011-06-19
well my real problem now is that my system is actually well-configured with all apps and servers I need, only my DE is not running fine...

no time to install a new DE/?ubuntu flair.

I guess I need to stick to unity until I find the time to migrate... :( :(

---

### Post by phonky on 2011-06-19
To unity's and ubuntu's defense I should add that my graphics card is an ATI Radeon HD 5000 series. I've seen a few comments about problems with fglrx here and there, but no clear hints that I should be affected.

Wondering if the open source drivers could help, but seriously, I'm not keen on another experiment...

---

### Post by ajgreeny on 2011-06-19
> **phonky said:**
> To unity's and ubuntu's defense I should add that my graphics card is an ATI Radeon HD 5000 series. I've seen a few comments about problems with fglrx here and there, but no clear hints that I should be affected.

Wondering if the open source drivers could help, but seriously, I'm not keen on another experiment...
I think you can forget the open source drivers for unity with that ati card, but it is just possible that with that newer card than mine, an ati 9200SE from about 8 years ago, there is a chance that you might be lucky.  Try it by disabling the driver in whatever way that is done in 11.04, then logout and login again.

---

### Post by wildmanne39 on 2011-06-20
> **phonky said:**
> First of all, I don't blame anybody. I blame myself. For upgrading on my production laptop.

I've been using ubuntu since edgy, and linux since SuSe 4.x (1997).

I was running a smooth 10.04, until I decided I would upgrade to 11.04.
What a mistake.

Of course, unity is a question of taste. I simply don't like it. But what I really was surprised to find out was that the supposedly alternative with classic gnome just does not work for me. Compiz crashes frequently, I loose window decorations when I click on an item in the cairo-dock, and everything just feels unstable. I dumped emerald in the hope it would help, no joy.

It's ok for ubuntu to try a new layout. But it should not leave users in the void who would try to stick with their old layout.

Repeat: I blame myself first. But I won't install another ubuntu anymore. I feel I have been left out. What a shame, ubuntu's ideals greatly resonated with me. I lost my weekend trying to fix it. :(
Hi, see if this link fixes your problem, I think it will.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by phonky on 2011-06-23
Hey @wildmanne39

thank you very much for this link!
I indeed believe it will solve the problem.

However, I am now not willing to change immediately, as the desktop is running fine for now, albeit not looking the way I want it.
So I might leave it for that for a while, not wanting to risk to get to an unstable system again...

hope to be able to test your solution soon though.
thanks again

---

### Post by Elline on 2011-06-23
I'm affected with this too.

Nevertheless, I am using open source drivers and Unity can work with them. 

As for **wildmanne39** solution, thank you, I shall consider it.

---

### Post by FormatSeize on 2011-06-23
> **phonky said:**
> Of course, unity is a question of taste. I simply don't like it. But what I really was surprised to find out was that the supposedly alternative with classic gnome just does not work for me. Compiz crashes frequently, I loose window decorations when I click on an item in the cairo-dock, and everything just feels unstable. 
This might be partly because Gnome-Classic is a less stable version of traditional Gnome. But if it were me, I would mostly blame Compiz as well. Just last night I was tweaking around with my most stable desktop environment, and I decided to enable Compiz. Soon after, as usual, it became a case of Things Going Wrong. First by top panel disappeared, then went the window borders. I could only be upset with myself though, because I knew that it would happen, and I don't know what made me think otherwise.

---

### Post by wildmanne39 on 2011-06-24
> **FormatSeize said:**
> This might be partly because Gnome-Classic is a less stable version of traditional Gnome. But if it were me, I would mostly blame Compiz as well. Just last night I was tweaking around with my most stable desktop environment, and I decided to enable Compiz. Soon after, as usual, it became a case of Things Going Wrong. First by top panel disappeared, then went the window borders. I could only be upset with myself though, because I knew that it would happen, and I don't know what made me think otherwise.Hi, To get the cube working in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed. This is if you are using unity and not logged in as classic. I have the cube and many effects and they are working great in natty, but I to failed at my first attempt and had to reset unity.

---


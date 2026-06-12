---
title: "Mate or gnome 3 instead of unity"
date: 2013-10-04
forum: Desktop Environments
---

### Post by priestnot on 2013-10-04
I was a user of Ubuntu till 10.04 after that because of unity I changed to debian6.
Now I want to change back to Ubuntu but I still do not like the unity desktop, so I was wondering if there are any problems in installing and using Gnome 3 or Mate as a Desktop manager with Ubuntu.

Do I lose any of the functionality? Is there any software that depends on Unity to work?

---

### Post by ajgreeny on 2013-10-04
How about adding xubuntu-desktop, or xfce4, instead of gnome?  It's gtk based and can be made to look and feel very like gnome 2, but is more up to date, very stable, and unlike MATE, is not a fork of the old gnome 2 libraries etc etc.

Xuubuntu 12.04 was my refuge when Lucid lost GUI support for gnome, and I now wonder why I didn't move earlier, as I now love Xubuntu and doubt that I'll move away from it, unless, of course, xfce4 does what gnome 2 did!

---

### Post by priestnot on 2013-10-04
I do not like very much xfce4 :s, but I can give it a try.

Does any one else know if there are problems with instaling another Desktop Manager like Gnome 3 or Mate?

---

### Post by grahammechanical on 2013-10-04
You need to understand something. It is necessary for clarity. Ubuntu uses Gnome 3. It uses the Gnome 3 desktop environment. It does not use the Gnome 3 shell. If you do not like Unity then you should not like Gnome 3 shell. They are based upon similar principles.

The old desktop environment (Gnome 2) and its user interface (Gnome panel) are no longer being developed by the gnome organisation. Gnome switched desktop environments and user interfaces and so did Ubuntu. All that happened was that the two organisations had a different vision regarding user interfaces.

This being open source there are alternatives. It is your choice according to your taste.

Regards.

---

### Post by priestnot on 2013-10-04
What I do not understand is how you can say that "If you do not like Unity then you should not like Gnome 3 shell. They are based upon similar principles." because to me they very different. First off all unity does not let me move the dock from the left side. And the like mac menu bar it is a good idea but does not work like on a mac because the applications are not made to work like that.

The (in my umbel opinion) perfect desktop environment was gnome 2 (hence me asking about mate). Call me old fashion but it worked perfectly the top and botom bars did not take a lot of space from the desktop and we could fit all the information and shortcut that we need on them.  But this is not the point I want to get to.

"This being open source there are alternatives. It is your choice according to your taste."
Yes that is one of the biutiful things I like on linux, and that is wy I am asking about changing from Unity or to gnome3 or to Mate. Obviously I prefer Mate to Gnome3 but I can manage with gnome3.

So again is there any problem with any application that comes with Ubuntu that might stop working (any dependencies) if I use Mate or Gnome3?

---

### Post by ibjsb4 on 2013-10-04
I have not used Mate, so no help there.  But I do use gnome-classic in 12.04, which looks like the 10.04 desktop.  To install it in 12.04:

```
sudo apt-get install gnome-session-fallback
```

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by priestnot on 2013-10-04
Oh that sounds good. I migth use ubutu 12.04 because of the LTS.

But can I do it on the latest ubuntu?

---

### Post by ibjsb4 on 2013-10-04
> **priestnot said:**
> But can I do it on the latest ubuntu?

Yes you can, with the same command.  My understanding is this will change in 13.10 to flashback instead of being called fallback.

12.04 will be supported till 2017.  All versions in between LTS releases are supported for 9 months.

---

### Post by deadflowr on 2013-10-04
You can do what I do everytime, which is to install gnome-tweak-tool, which pulls in the gnome desktops, both gnome-shell and gnome classic(or whatever name it goes by now).

That a-way you can manipulate settings for stuff like themes, out of the gate.
And control shell extensions.

---

### Post by buzzingrobot on 2013-10-04
Mate works fine on every Ubuntu I've installed it on, which is 12.04 thru 13.10.

As far as I know, there's nothing in Mate that prevents anything already installed  on Ubuntu from working. Obviously, you can't use Unity or Unity-specific tools inside Mate because Unity isn't running. 

Follow the install guidance at mate-desktop.org.

Mate is the best -- only real -- option for someone looking for the classic Gnome 2 interface.

---

### Post by frank18 on 2013-10-04
> **priestnot said:**
> Oh that sounds good. I migth use ubutu 12.04 because of the LTS.

But can I do it on the latest ubuntu?


Hi guys. I use Ubuntu12.04 LTS also and like it too, but i use Gnome Classic for the simple Fact of the Minimize Button that minimizes  the pages to the task bar and in Unity or Gnome 3 the minimize button do not  work same,

---

### Post by buzzingrobot on 2013-10-04
Unity and Gnome 'minimize' to the icon in their respective docks.  That effect, and what you see in all cases, including minimizing to a panel in GNome 2/Mate, is just a visual metaphor.

---

### Post by dusanyu on 2013-10-04
If you want mate without any of the Gnome 3 stuff to go with it give an ubuntu derivitive a shot. I personaly use Mint to get a Ubuntu based distro with mate as the default desktop.

---

### Post by WinRiddance on 2013-10-05
> **ajgreeny said:**
> 
Xuubuntu 12.04 was my refuge when Lucid lost GUI support for gnome, and I now wonder why I didn't move earlier, as I now love Xubuntu and doubt that I'll move away from it, unless, of course, xfce4 does what gnome 2 did!

Same here. Part of why I switched to Linux was the total freedom & control that I had, to make my desktop look like anything that I wanted to. This freedom was "taken away" from me with Unity and Gnome3 ... so I switched to Xubuntu and haven't looked back since. I've tried about 7 or 8 different distros in the past 3 years but I'm always coming back to XFCE. Gotta love it .... :D
(easier on the resources too)

.

---

### Post by Buntu Bunny on 2013-10-05
+1 Xubuntu, although I admit an interest in Mate. There do seem to be a lot of support requests on the Forums involving Mate, so perhaps a look at those would be in order to see what kinds of problems folks are having.

---

### Post by kurt18947 on 2013-10-06
I believe a difference between Unity & Gnome-shell is that Gnome 3/gnome-shell was designed to allow user modifications such as extensions, Unity was not.  I don't find Gnome-shell satisfactory "out of the box".  A few additions make it quite usable without impacting stability.  There is a recent extension that adds a bottom task switcher along with some other handy bits.  It does not yet support autohide so I'm continuing to use tint2 panel which does support autohide.

---

### Post by buzzingrobot on 2013-10-06
> **Buntu Bunny said:**
> +1 Xubuntu, although I admit an interest in Mate. There do seem to be a lot of support requests on the Forums involving Mate, so perhaps a look at those would be in order to see what kinds of problems folks are having.

The Mint 15 XFCE and Mate releases are very similar in appearance and usage. Their XFCE might appeal to someone who is on the fence abou Mate.

---

### Post by priestnot on 2013-10-07
Thank you for all the answers...

---

### Post by frank18 on 2013-10-08
Add one more to Xubuntu Desktop,i just installed Xubuntu- desktop to my main PC and workes almost same way as gnome Classic, but it's more eye Candy. has more options out of the box. I already knew Xubuntu,i have it installed  in my old vaio laptop  from scrach and has been 
there and i love it too, i also like LXDE but is short of stuff if they do same in LXDE as they do in XFCE4 or gnome3 but keep what LXDE Has it would be the best Desktop.

---

### Post by frank18 on 2013-10-09
> **buzzingrobot said:**
> Mate works fine on every Ubuntu I've installed it on, which is 12.04 thru 13.10.

As far as I know, there's nothing in Mate that prevents anything already installed  on Ubuntu from working. Obviously, you can't use Unity or Unity-specific tools inside Mate because Unity isn't running. 

Follow the install guidance at mate-desktop.org.

Mate is the best -- only real -- option for someone looking for the classic Gnome 2 interface.


Today i gave Mate 1.6 Desktop a try,added it to Ubuntu  and i must say that i'm impressed,so much so that i'm gonna give it a try for awhile and see,if it stays stable and doesn't give me any glitches ,i'm going to keep it cause it looks good and has many easy features,

---

### Post by frank18 on 2013-10-10
Well today i don't know what i did, the taskbar page tab dissapear and don't know how to get it back,also xubuntu desktop i lost the second 
display i'm not able to get it mirrored, So i ended to go back to Gnome Classic.

---


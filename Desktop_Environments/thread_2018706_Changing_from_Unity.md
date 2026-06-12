---
title: "Changing from Unity"
date: 2012-07-06
forum: Desktop Environments
---

### Post by LinXNut on 2012-07-06
I was wondering if it is possible to change from Ubuntu Unity desktop to GNOME **safely**? I really miss the old GNOME look and feel. Does anyone have a method of doing this?

Thanks!

---

### Post by oldfred on 2012-07-06
I find gnome-panel or fallback to be almost the same. Some things are in slightly different places but manageable.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

# same thing for pre12.04 Unity versions with gnome2
sudo apt-get install gnome-session-fallback
sudo apt-get install gnome-tweak-tool
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)
Open the Ubuntu Software Centre and search for ‘gnome-panel’, hit install and log out.

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

Others prefer one of the many desktop environments. But I have not tried them.

---

### Post by VMC on 2012-07-06
Yes, "gnome-panel" is very good. Like Fred said, it works almost the same as the old gnome2.

---

### Post by lolpenguin on 2012-07-07
MATE desktop environment. It is a fork of good old GNOME 2, resolving all conflicts with GNOME 3 and can be used side-by-side. I'm sure someone has set up a PPA for it.

---

### Post by black veils on 2012-07-07
or you might like to use the xfce desktop ```
sudo apt-get install xubuntu-desktop
``` choices for the panels are: amount, size, images, transparency, plugins. there are many general settings also.

---

### Post by vasa1 on 2012-07-07
> **black veils said:**
> or you might like to use the xfce desktop ```
sudo apt-get install xubuntu-desktop
``` choices for the panels are: amount, size, images, transparency, plugins. there are many general settings also.

I suspect that Xfce is more stable than either Mate or Cinnamon. The documentation is pretty decent as well.

---

### Post by black veils on 2012-07-07
> **vasa1 said:**
> I suspect that Xfce is more stable than either Mate or Cinnamon. The documentation is pretty decent as well.

yes, it is very nice and stable (from my experience anyway), easy to use, and is lighter.

---

### Post by codingman on 2012-07-07
you can also try LXDE:

```
sudo apt-get install lubuntu-desktop
```

(I find the lubuntu desktop much more stable than the regular plain old LXDE)

---

### Post by msammels on 2012-07-07
We're doing one of these? :D OK here we go:

```
sudo apt-get install kubuntu-desktop
```

Haha :D

---

### Post by 3Miro on 2012-07-08
Just to clarify, Unity works on top of Gnome 3, thus Unity is Gnome.

When you say Gnome, you ma refer to the new Gnome interface and WM known as Gnome-shell or the old interface known as Gnome-classic or fallback. You can install both Gnome-shell and Gnome-fallback fairly easy from the Software Center.

The Gnome-fallback isn't quite the same as the old Gnome that you remember from Ubuntu 10.04. If you want something similar to it, you should look at Mate or Cinnamon (Gnome 2 ports) or XFCE, which is pretty similar (if you spend some time to make it similar). You can also look at KDE or LXDE, you may or may not like those.

Here is a way to switch different environments:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by Overcast32 on 2012-07-08
I'm torn if I want to try and upgrade to Ubuntu 12.x or just finally move on. I really detest Unity - and it's not about change, it's just that I don't want a big SmartPhone for a desktop and that's how it feels.

Still have 10.04 installed... 

I do suppose I'd bid this wonderful community farewell really. 

It's not about change - heck, this will require even more change!
But some of us - really don't want SmartPhone desktops.

---

### Post by kansasnoob on 2012-07-08
> **Overcast32 said:**
> I'm torn if I want to try and upgrade to Ubuntu 12.x or just finally move on. I really detest Unity - and it's not about change, it's just that I don't want a big SmartPhone for a desktop and that's how it feels.

Still have 10.04 installed... 

I do suppose I'd bid this wonderful community farewell really. 

It's not about change - heck, this will require even more change!
But some of us - really don't want SmartPhone desktops.

Did you even bother to look at [post #2]("http://ubuntuforums.org/showpost.php?p=12081530&postcount=2") and check out those links?

---

### Post by AlbertJB on 2012-07-08
I personally work with Gnome Classic no effects and despite some little bugs It's almost the same experience as in Gnome 2.x (IMHO). And I can switch from Gnome Classic to Gnome Shell or Unity and the Desktop remains the same, with same icons, same configuration.. (as 3Miro said, Unity is on top of Gnome3, and gnome classic i the fallback mode of Gnome 3).

Although, to be honest, I am a little confused with the concepts. I know there's a gnome-panel package with a lot of bugs which I am subscribed to, but I don't receive any updates for gnome-panel, just updates for unity or gnome shell... No changes, no improvements to my gnome classic interface... :(

---

### Post by kansasnoob on 2012-07-08
> **Gosset Inofensiu said:**
> I personally work with Gnome Classic no effects and despite some little bugs It's almost the same experience as in Gnome 2.x (IMHO). And I can switch from Gnome Classic to Gnome Shell or Unity and the Desktop remains the same, with same icons, same configuration.. (as 3Miro said, Unity is on top of Gnome3, and gnome classic i the fallback mode of Gnome 3).

Although, to be honest, I am a little confused with the concepts. I know there's a gnome-panel package with a lot of bugs which I am subscribed to, but I don't receive any updates for gnome-panel, just updates for unity or gnome shell... No changes, no improvements to my gnome classic interface... :(

I'm curious about the specific bugs you're having trouble with. Please feel free to add a comment here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by kd4dii on 2012-07-08
Hello
     I have found that the Gnome fork Mate is very good.  If you Google for the Mate Desktop their web page has the repos and instructions for the version of Ubuntu you are running.  They have set ups for 11,1 and 12.04  I have tried it on both and it works good for me.

Bob

---

### Post by 3Miro on 2012-07-08
> **Gosset Inofensiu said:**
> 
Although, to be honest, I am a little confused with the concepts. I know there's a gnome-panel package with a lot of bugs which I am subscribed to, but I don't receive any updates for gnome-panel, just updates for unity or gnome shell... No changes, no improvements to my gnome classic interface... :(

The original plan form Gnome was to keep Gnome-panel as only a deprecated feature and to stop all development. Eventually they found some developers to keep working on Gnome-panel, however, development is very slow. Basically, everything in Gnome-classic is getting very little if any love from the Gnome project. Needless to they, they are not getting much from Ubuntu either.

---

### Post by AlbertJB on 2012-07-09
@3Miro Actually it was one developer who ported Gnome-panel to gtk3, I encountered this link some time ago: [http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel](http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel)! 

Thanks for the reply, though.

---

### Post by Myrddin Emrys on 2012-07-09
> **kd4dii said:**
> I have found that the Gnome fork Mate is very good.  If you Google for the Mate Desktop their web page has the repos and instructions for the version of Ubuntu you are running.  They have set ups for 11,1 and 12.04  I have tried it on both and it works good for me.

I find the same. It's quick and easy to install, and is much more complete than the Gnome 3 fallback panel. You can be up and running in about 5 minutes, with a 12.04-based system that works exactly the same way as 10.x. See:

[http://mate-desktop.org/install/#ubuntu](http://mate-desktop.org/install/#ubuntu)

For illustrated installation guides and post-installation tips, see:

[http://ubuntuforums.org/showpost.php?p=11931784&postcount=20](http://ubuntuforums.org/showpost.php?p=11931784&postcount=20)

---

### Post by vwbug on 2012-07-09
Anyone looked at Oracle 6.3? I haven't but from the screen shots it looks like Gnome 2. Haven't seen any reviews of it yet either.  I'm still on 10.04 and will stay there until support runs out.

---


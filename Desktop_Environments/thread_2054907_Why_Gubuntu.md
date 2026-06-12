---
title: "Why Gubuntu?"
date: 2012-09-08
forum: Desktop Environments
---

### Post by yankeeDDL on 2012-09-08
Hi there,

a simple question, I hope: why would I want to install Gubuntu, instead of just downloading Ubuntu and:
sudo apt-get install gnome-shell

Thanks.):P

---

### Post by vasilbelarus on 2012-09-08
All in one and just from the box.

---

### Post by Frogs Hair on 2012-09-08
Unity is not included with Gubuntu and there are some default package differences . One article I read stated that there is a clear devision between Unity and Gnome shell users based  on a poll . I switch between both regularly so this is simply not true in my case.

---

### Post by MARP1961 on 2012-09-08
If you installed the proposed Gubuntu version you would obviously not have the Unity Desktop, you would have Gnome Shell and Classic only. Also you would lose the purple colour and Ambiance and Radiance themes. You will also lose the Unity Greeter screen at login. The login would be the simple LightDM GTK Greeter or the GDM screen. Also you would not get all the Unity updates coming through, just the Gnome ones and other packages.

If you only want to use Gnome as your DE then this will give you the lightest, cleanest option. If you want to try any other DE you always can install it anyway. If you only ever want Gnome Shell then install Gnome Shell Remix 12.04 now or wait for Gubuntu to be released.

[http://ubuntu-gs-remix.sourceforge.net/p/home/](http://ubuntu-gs-remix.sourceforge.net/p/home/)

---

### Post by yankeeDDL on 2012-09-08
Thanks everyone for the replies.
I don't really mind choice, on the contrary, but it seems to me that it's getting a bit out of control.
Wouldn't it be more consumer-oriented having one dirsto of Ubuntu that lets you choose which DEs to install during the installation process?

I don't mind having a couple installed (like I have now: Unity + Gnome shell) and give it some time before settling on one.

To MARP1961: I would imagine I could just purge Unity as easily as I installed Gnome-shell, no? Sure, there may be some bits and pieces (the themes?) that will be left behind, but then again, would it really matter?

Thanks again.

---

### Post by grahammechanical on 2012-09-08
Hi

Another answer to your thread title would be:

Because we can and because we want to.

Programmers can spend their free time and skills doing what they want. This is especially true in Linux as a lot of work is done by volunteers.

Ubuntu is Unity and Unity is Ubuntu. This is a decision taken by those with authority to make those kinds of decisions. They have also made the decision to limit the size of the Ubuntu download image to as close as CD size as possible. Programs get left out of the image as a result. This is why we have a Ubuntu Software Centre. To pull in those programs that are not on the CD image.

Now, you want them to change the policy by putting the desktop environments of other developers into their Ubuntu download image. This is not going to happen.

From 12.10 onwards Unity 2D will not be available either on the CD image or as an install through the Software Centre. So, there will only be one official desktop environment in Ubuntu not two as at present.

And you want Ubuntu to be responsible for making several desktop environments available during and after the install process. It is not going to happen.

Do you see the direction things are going? 

Regards.

---

### Post by PaulInBHC on 2012-09-08
If 2D is not available, what happens to people with poor graphics that currently defaults to 2D?

I also read that CD image is going away.

---

### Post by hictio on 2012-09-08
It's all about choice I guess... Personally don't like Unity, and I don't see the need to have something installed that I know I won't be using.
Right now I'm using [Gnome Shell Remix](http://ubuntu-gs-remix.sourceforge.net/p/home/), perhaps down the road, when Gubuntu gets out of beta I might give it a try.
For the moment, Gnome Shell Remix does a fantastic work... Precise Pangolin's LTS ontop of a totally GNOME 3 desktop.

---

### Post by markbl on 2012-09-08
> **yankeeDDL said:**
> 
a simple question, I hope: why would I want to install Gubuntu, instead of just downloading Ubuntu and:
sudo apt-get install gnome-shell
I personally don't understand the point of gubuntu and gnome shell remix etc because, as you say, installing gnome shell on regular ubuntu is one click (or command line) away.

The default ambiance gnome shell theme on ubuntu looks fantastic. Lightdm looks far nicer than gdm anyhow (and how often do you look at the login screen?). All the other "features" touted in those remixes look a net negative to me. Also, I occasionally log in to Unity to check where it is at. Sure you can delete Unity, but it is not as if we need those extra few MB or so on our TB drive nowadays! Staying on the mainline ubuntu distro makes the most sense to me even though I personally prefer gnome shell over unity.

---

### Post by yankeeDDL on 2012-09-09
I suppose it is a matter of preference.
I don't have anything against volunteers making their own distro to their likings, and it is even enjoyable to "shop" for the right distro, however, I simply am puzzled as of why nobody has created a flexible installer which:
- allows you to pick one or more DE
- allows you to pick which programs to be installed. For example, suggest to install "lighter" programs on a PC short on memory or CPU power (a netbook?) vs the more ... complete but heavier SW. For example, I liked to try XFCE so I installes Xubuntu (a while back ...) and saw it came with Abiword, Gnumeric rather than OpenOffice (it was before LibreOffice). I understand that XFCE is geared towards less powerful machines, but why do I need to wait for all this software to be installed (honestly, it doesn't take much, but you get the point) if I don't want/need it?

There are bugs that exist "forever", and many I am sure could be fixed in minutes by somebody that know coding, and yet there is so much effort creating nearly identical distros, some with questionable added value, rather than fixing things.
It just puzzles me.

---

### Post by MARP1961 on 2012-09-09
yankeeDDL, You're right, you can customize your Ubuntu 12.04 to make it 'Unity Free' within minutes probably. I suppose the Gnubuntu version would be for people who know they only want that DE and don't want to go through the process of purging all the Unity related stuff.

Funnily, I recently installed Gnome Shell Remix but found I quite missed the Unity Login Greeter! I reinstalled it from Synaptic and changed the LightDM configuration file to get it back! Unfortunately it has the unpleasant purple dotted theme and so far I've not been able to get it to show my wallpaper choice as it's background. Oh well, that's the price of fiddling around with things I suppose.

---

### Post by hictio on 2012-09-09
> **yankeeDDL said:**
> I suppose it is a matter of preference.
I don't have anything against volunteers making their own distro to their likings, and it is even enjoyable to "shop" for the right distro, however, I simply am puzzled as of why nobody has created a flexible installer which:
- allows you to pick one or more DE
- allows you to pick which programs to be installed. For example, suggest to install "lighter" programs on a PC short on memory or CPU power (a netbook?) vs the more ... complete but heavier SW. For example, I liked to try XFCE so I installes Xubuntu (a while back ...) and saw it came with Abiword, Gnumeric rather than OpenOffice (it was before LibreOffice). I understand that XFCE is geared towards less powerful machines, but why do I need to wait for all this software to be installed (honestly, it doesn't take much, but you get the point) if I don't want/need it?

There are bugs that exist "forever", and many I am sure could be fixed in minutes by somebody that know coding, and yet there is so much effort creating nearly identical distros, some with questionable added value, rather than fixing things.
It just puzzles me.

I guess this doesn't happen in order to keep things simple.
You pop your media on, boot, install after a couple short questions and you are done.
If you are willing to customize your system more, you are certainly willing to either install whatever you want after the main installation its done, or start from scratch with an Alternate Installer and selectively pick the stuff you want.

---


---
title: "Question for Xubuntu users"
date: 2012-02-28
forum: Desktop Environments
---

### Post by Ghost_Mazal on 2012-02-28
Lo All ,

I have a question about Xubuntu and have no idea where to post it as it is info needed. So bare with me if this is the wrong place.

Basically I am looking for a good ubuntu distro. I loved ubuntu , but Unity is a bif fail for me. So I went to Kubuntu , loved that but now they went backwards as well. (Things like my wi-fi and screen drivers that don't work anymore that worked before).

It seems every year ubuntu chases me away further. So now I am looking yet again for a different distro. Xubuntu is next in line , but I don't know how well the software support is on it.

How many of the apps that run on ubuntu and Kubuntu would work on Xubuntu ? For example , must haves for me are K3b , Handbrake , Grsync , thunderbird , firefox , bibletime , libre office.

Are there any Xubuntu users that use those apps successfully ?
Other comments about Xubuntu ?

Thanx

---

### Post by nothingspecial on 2012-02-28
> **Ghost_Mazal said:**
> 

How many of the apps that run on ubuntu and Kubuntu would work on Xubuntu ? For example , must haves for me are K3b , Handbrake , Grsync , thunderbird , firefox , bibletime , libre office.



All of them. Xubuntu uses exactly the same repositories as Ubuntu.

---

### Post by nothingspecial on 2012-02-28
*Thread moved to **Desktop Environments**.*

---

### Post by Ghost_Mazal on 2012-02-28
> **nothingspecial said:**
> All of them. Xubuntu uses exactly the same repositories as Ubuntu.

Thanx , so there won't be issues with some that is build for KDE for example (k3b) ?

---

### Post by nothingspecial on 2012-02-28
Well, it will pull in a load of kde libs/dependencies in exactly the same way that happens when you install kde stuff in Ubuntu or gnome stuff in Kubuntu. But other than that there is no issue.

---

### Post by Ghost_Mazal on 2012-02-28
> **nothingspecial said:**
> Well, it will pull in a load of kde libs/dependencies in exactly the same way that happens when you install kde stuff in Ubuntu or gnome stuff in Kubuntu. But other than that there is no issue.

Thanx a lot , appreciate it ;)

---

### Post by bob-linux-user on 2012-02-28
You can make it look similar to good old Gnome 2 and change all the themes to your taste as well. The default menu is a bit small but you can modify one of the configuration files to make it look bigger. Go for it.

---

### Post by sir.sargento on 2012-02-28
XFCE is a great DE... It is the only one I use and I prefer it to any other environment.. It is fast, light on resource and still feature rich. Also you can pretty much customize it any way you want.

---

### Post by Porcini M. on 2012-02-29
Ditto to everything - Xubuntu works great, and you can run any *buntu application on it.

---

### Post by Ghost_Mazal on 2012-03-01
Thanx for the replies.

I just started up the live cd and I must say I like what I see. A very clean and simple desktop. Exactly what I like.
If it wasn't for the loads of downloads to get everything installed I would have jumped into it right away. But as is I will wait for the 12.04 LTS before going through a build process.

From what I see I just might have found my next OS :)

---

### Post by 3Miro on 2012-03-01
As other people pointed out, programs are independent from your desktop environment (apart from some tools directly liked to the DE). The only issue is that QT apps (like K3B) would use a bit more ram on a not QT based DE (like XFCE and Gnome).

If you want to just try the DE, you don't have to install Xubuntu. What I do is I install Ubuntu (Gnome+Unity) and then I just install the xfce4 package from Synaptic (or the Software Center). You can do the same with KDE and you can have Gnome + Unity, Gnome + Gnome-shell, XFCE, KDE and LXDE all installed on one machine. Test them all and pick the one that you like. 

Check:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Ghost_Mazal on 2012-03-02
> **3Miro said:**
> As other people pointed out, programs are independent from your desktop environment (apart from some tools directly liked to the DE). The only issue is that QT apps (like K3B) would use a bit more ram on a not QT based DE (like XFCE and Gnome).

If you want to just try the DE, you don't have to install Xubuntu. What I do is I install Ubuntu (Gnome+Unity) and then I just install the xfce4 package from Synaptic (or the Software Center). You can do the same with KDE and you can have Gnome + Unity, Gnome + Gnome-shell, XFCE, KDE and LXDE all installed on one machine. Test them all and pick the one that you like. 

Check:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

That is a very good idea , didn't think about that. Does anybody know , if you install xubuntu-desktop how big the download is. I have seen it is well over 340 packages that will be installed and stopped there as I could not see how big it in total will be.

Anybody done it recently that can recall a rough estimate ?

---

### Post by nothingspecial on 2012-03-02
xubuntu-desktop will pull in xubuntu's music player, word processor, etc etc etc and you will find your self with lots of duplicate packages that do the same thing.

Some people don't mind that, personally I find it messy. I would use either Ubuntu or Xubuntu, not both.

As mentioned above, you can install xfce4 which will just pull in the packages that the xfce DE comes with.

It's entirely up to you.

---

### Post by Ghost_Mazal on 2012-03-02
> **nothingspecial said:**
> xubuntu-desktop will pull in xubuntu's music player, word processor, etc etc etc and you will find your self with lots of duplicate packages that do the same thing.

Some people don't mind that, personally I find it messy. I would use either Ubuntu or Xubuntu, not both.

As mentioned above, you can install xfce4 which will just pull in the packages that the xfce DE comes with.

It's entirely up to you.

I already did the "Install only Xfce4" thing. That didn't work to well. It looks like there are things missing. For example my wireless doesn't work when in Xfce and I can't even find a setting for it. So I am thinking to rather put in the complete xubuntu-desktop

---

### Post by nothingspecial on 2012-03-02
Well give it a go, you can always remove it all. See here

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by rojaasensei on 2012-03-02
> **sir.sargento said:**
> xfce is a great de... It is the only one i use and i prefer it to any other environment.. It is fast, light on resource and still feature rich. Also you can pretty much customize it any way you want.

+1

---

### Post by mikodo on 2012-03-02
I ran all those apps after installing the Xubuntu DE on top Ubuntu.

Yes, it was a little messy, having Gnome, KDE and Xfce apps, but everything worked. If you choose to do this for now, you can un-install what you don't want, to clean it up.

```
sudo apt-get install xubuntu-desktop
```Enter that, and you will have the Xubuntu desktop to try, upon log in. Your Unity Desktop will be there for choosing if you wish, too. I decided, to go back to my Lucid install alone, for now, untill Xubuntu 12.10, when I plan to clean install it.

I used the link noted above, in nothingspecial's post, to go back to pure Gnome in the Psychocats page, and it worked like a charm. I am right back in Ubuntu alone.

Give it a try, if you don't like it, remove it . I don't think you will not like it, though.

Oops, I haven't used Handbrake. So, I don't know, how well or not it runs, with Xfce.

---

### Post by Ghost_Mazal on 2012-03-02
I installed Xubuntu-Desktop , so far I love it. But I have 1 irritating issue. I can't find a way to set the compose key :confused:

---

### Post by mikodo on 2012-03-03
> **Ghost_Mazal said:**
> I installed Xubuntu-Desktop , so far I love it. But I have 1 irritating issue. I can't find a way to set the compose key :confused:
Maybe, start a new thread specific about this, or any other concerns, you need help ironing out. You may get more advice/help, if people are alerted to your problem(s), with new thread title(s).

I'm glad your liking, the Xubuntu DE so far.

Regards.

---

### Post by Ghost_Mazal on 2012-03-04
> **mikodo said:**
> Maybe, start a new thread specific about this, or any other concerns, you need help ironing out. You may get more advice/help, if people are alerted to your problem(s), with new thread title(s).

I'm glad your liking, the Xubuntu DE so far.

Regards.

Did exactly that and got it sorted.

I must say the more I work with Xubuntu the more I like it. I really am not a bells and whisles guy and this does the trick for me. :-)

Thanx for everyone's replies and help

---

### Post by Peripheral Visionary on 2012-03-04
It seems to me that if you have room on your hard drive for all the libraries and stuff that your favorite KDE, Gnome, and LXDE applications pull in, go for it!

The "heavyweight" applications (KDE) will run in any environment and your "lightweight" (Xfce, LXDE) stuff will still run as quickly and effortlessly in KDE or Gnome. But non-native applications pull in other stuff that doesn't necessary slow things down, just takes up room on your hard drive. If you have room for them, go for it! If storage space is an issue, stick to "native" apps.

---


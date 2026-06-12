---
title: "Is there a minimalistic Ubuntu?"
date: 2009-11-10
forum: Desktop Environments
---

### Post by Shibblet on 2009-11-10
I currently use Kubuntu, and really enjoy the K Desktop Environment.

But what I am looking for is a Ubuntu based OS that comes with nothing but the basics.  KDE, Ubuntu Kernel, pakage manager, basic OS utilities, and a simple web-browser.

I want to add the applications of my choice, without having to un-install the ones in place at first.

Is there such a creature?

---

### Post by snowpine on 2009-11-10
Hi Shibblet, yes, of course Ubuntu offers a minimal installer, check it out:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You can install exactly and only the packages of your choice.

Here is a neat tutorial: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by jollysnowman on 2009-11-10
Do a CLI install of Kubuntu, and build it up from there?

---

### Post by Shibblet on 2009-11-10
Thanks for the info!  What all is included in the 12.1Meg file?

---

### Post by XubuRoxMySox on 2009-11-10
> **jollysnowman said:**
> Do a CLI install of Kubuntu, and build it up from there?

I would do a CLI install of KDE *not* "kubuntu-desktop" which is the metapackage that will give you essentially all the same stuff (it installs the whole kubuntu system and apps and everything), leaving you with anything *but* a minimal install. Just put in the basic desktop environment, then add only the applications (beyond the ones that are native to KDE) that you prefer.

-Robin

---

### Post by snowpine on 2009-11-10
> **Shibblet said:**
> Thanks for the info!  What all is included in the 12.1Meg file?

It is a "net installer" that connects to the Ubuntu mirror and downloads the basic packages for a minimal, command-line-only install, then you can install whatever packages (KDE, a web browser, etc.) you choose. Did you read the help page and tutorial I linked to in my previous post?

---

### Post by Shibblet on 2009-11-10
I did.  But what I am missing is, when I go to download "kubuntu-desktop" isn't that the same as just installing Kubuntu right from the CD?

EDIT:  Never mind, I saw that post from dixiedancer.

Fortunately this is going to be on my Netbook, and I don't have to worry about messing up my main Kubuntu Desktop Computer.

---

### Post by XubuRoxMySox on 2009-11-10
> **Shibblet said:**
> I did.  But what I am missing is, when I go to download "kubuntu-desktop" isn't that the same as just installing Kubuntu right from the CD?

YES IT IS! Don't do it!

You can install KDE *without* having to install the whole Kubuntu desktop!

Install the minimal Ubuntu from the CD, then open a terminal and enter

```
sudo apt-get install kde-minimal
```

Done!

Okay, lol, by the time I finished typing this you got it. Cool.

-Robin

---

### Post by ratcheer on 2009-11-10
I would say, "Debian".

Tim

---

### Post by Shibblet on 2009-11-10
Would I be better off installing kde-core.  I want dolphin file manager, and such.  I just don't need the graphic editing programs, and other apps like kopete.

All I want is basic OS functionality, file manager, window manager, and such.  I'll choose the apps.

---

### Post by Shibblet on 2009-11-11
> **dixiedancer said:**
> Install the minimal Ubuntu from the CD, then open a terminal and enter

```
sudo apt-get install kde-minimal
```

-Robin

Thanks so much.  That was a lot easier than I originally thought!  Although, the ***kde-minimal*** package comes with Open Office included.  Fortunately for me, I am going to need that package also.  I also needed to get ***kpackagekit***, and then I can download whatever programs I like.

Woo hoo!  You people rock!  Thanks!

---

### Post by Shibblet on 2009-11-11
But I have to ask one more question.

How do I get the wireless up and running on this computer.  It's an MSI Wind.  

Which packages do I need to download?

---

### Post by jollysnowman on 2009-11-11
> **Shibblet said:**
> But I have to ask one more question.

How do I get the wireless up and running on this computer.  It's an MSI Wind.  

Which packages do I need to download?

I use wicd as a network manager. If you're driver isn't supported out of the box, also look into ndiswrapper.

---

### Post by Shibblet on 2009-11-11
> **jollysnowman said:**
> I use wicd as a network manager. If you're driver isn't supported out of the box, also look into ndiswrapper.

Wicd worked beautifully.

After doing all of this, I am starting to see why people prefer it.  The OS seems to run faster with a minimal installation... and there are a lot of apps that I don't really need to use with Ubuntu, like Kopete, I prefer aMSN.

Thanks again everyone for the amazing help.

---


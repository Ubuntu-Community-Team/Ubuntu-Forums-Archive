---
title: "problems installing dependancies"
date: 2012-04-23
forum: Desktop Environments
---

### Post by bcatt on 2012-04-23
I have recently done a fresh install of Ubuntu Lucid. I've not done a whole lot of extra configuration, just removed some default packages I don't use and set up LAMP.

I wanted to install dupeGuru ME, so downloaded the .deb, but the package installer says I have unmet dependencies: python (>= 3.2). Can only find 3.1 through repositories. Spent hours trying to find out how to install 3.2, finally find some promising instructions, but after following them, not only can I still not install dupeGuru (dependency still unmet for python 3.2), but a bunch of other stuff like software center, package manager, and update manager no longer work (everything depending on python, I'm guessing). Reinstall python 3.1, non-working stuff now working again, still cannot install dupeGuru.

A few days later, I want to install Amaya, download .deb, but package installer says I have unmet dependencies: libssl0.9.8 (>= 0.9.8m-1). Checked if libssl  is installed on my system, it is and I have 0.9.8. Try to find 0.9.8m-1, no go. Try installing through apt-get on the command line, says package doesn't exist. Scour the internet and can't find much information on 0.9.8m-1 at all, and certainly nothing about downloading or installing it. Most search results are for 0.9.8 (without the m-1).

What is going on here? I know I have used dupeGuru on 10.04 and earlier versions of Ubuntu. I've never used Amaya before, but the similarity of the problem makes me think it's connected. I've never had problems installing through gdebi before, or meeting dependencies (the necessary packages are always either there or obtainable). And this is a pretty fresh install, so it's not like I've done a bunch of stuff to mess up the system. Any help will be greatly appreciated. Thanks in advance.

---

### Post by Paddy Landau on 2012-04-24
If this is a fresh installation, can you try again?

If you need LAMP, why don't you install Ubuntu Server?

And you might as well go for 12.04, which will have the latest drivers. It's in final beta now, but it's only three days away from final release. Just be sure to run all updates before doing anything else.

---

### Post by bcatt on 2012-04-24
Thanks for the response Paddy.

I guess I'll try 12.04. I sort of shied away from it because it's still in beta and I had some major usability issues with 11.* (blank white screen in place of most of my applications with Unity, and inability to customize panels in Gnome), went back to 10.04 because it previously worked just fine for me.

I do install LAMP with lamp-server^, but do you mean the actual server edition of Ubuntu? I plan to do that in the future, but right now I don't have an extra box. Or am I missing something here?

Thanks again for helping out this total noob.

---

### Post by Paddy Landau on 2012-04-25
> **bcatt said:**
> Thanks again for helping out this total noob.
Don't take all of what I say as gospel -- I may not be a noob, but I do make some right clangers sometimes.

> **bcatt said:**
> I guess I'll try 12.04. ... I had some major usability issues with 11.*
Create a Live USB (instructions on the [download page]("http://www.ubuntu.com/download/ubuntu/download")), preferably with persistence -- you'll want at least a 4GB USB stick, preferably 8GB, to test nicely (or install onto an external USB hard drive -- be careful not to overwrite your Grub). Test it thoroughly before deciding whether or not to install.

If it doesn't work for you, you can try [Xubuntu]("http://xubuntu.org/") 12.04 -- it's not as pretty, but more likely to work with your hardware.

> **bcatt said:**
> I do install LAMP with lamp-server^, but do you mean the actual server edition of Ubuntu? I plan to do that in the future, but right now I don't have an extra box. Or am I missing something here?
As far as I understand, Ubuntu + LAMP is (approximately) the same as Ubuntu Server. I presume that Ubuntu Server will have extra tailoring, but as I've never used it, I am not sure. Why don't you try it (on a Live USB with persistence or on an external hard drive) to see what happens?

---


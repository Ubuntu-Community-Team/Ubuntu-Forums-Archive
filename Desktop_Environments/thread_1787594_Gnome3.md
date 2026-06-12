---
title: "Gnome3"
date: 2011-06-21
forum: Desktop Environments
---

### Post by ploft on 2011-06-21
Howdy!

I am sorry if this has been properly covered before, I don't think I can find it, and feel free to send me back to google.

I am running Ubuntu 11.04 on a 1201N Asus eeepc, and using gnome2 (Ubuntu classic(no effects )) and would like to try gnome3.

However, I read somewhere that installing it might break my system, or that it would replace gnome2.

How can I accomplish that?

Thanks in advance

---

### Post by FormatSeize on 2011-06-21
Did you somehow uninstall Unity from 11.04, or did it start in fallback mode (Gnome2) when you first installed it? If it automatically put you in fallback mode, that means that your machine can't handle Unity, and probably won't handle Gnome3 either.
 
If your machine can handle it, then you can install Gnome3, but there is a possibility that doing so will break Unity and make it unstable. So if you don't care for Unity, then I suppose that's fine since you will be using Gnome3 anyway. If you don't have Unity, I don't foresee anything being too out of control given a proper installation. As for it replacing Gnome2, I'm not sure. 
 
If you can, get a live cd of Fedora Core 15, which has Gnome3 and try it out. I've never had any experience with a Gnome3 installation in Ubuntu, but at the very least it will show you some of the things that Gnome3 is like (I find it to be fantastic, but it could just be my bias for Fedora).
 
If you find that you like it, [here is a guide](http://techhamlet.com/2011/05/how-to-install-gnome-3-on-ubuntu-11-04/) that you show you how to get it running on your system.

---

### Post by 3Miro on 2011-06-21
Gnome 3 isn't officially supported for 11.04. Expect bugs and limited support.

You can use this to install Gnome 3:

[http://blogs.gnome.org/rodrigo/2011/04/11/unofficial-gnome3-on-ubuntu-ppa/](http://blogs.gnome.org/rodrigo/2011/04/11/unofficial-gnome3-on-ubuntu-ppa/)

If you install Gnome 3, you will lose Gnome 2 and Unity. If your graphics card cannot handle Unity, you will probably be unable to handle Gnome-shell and you will be left with Gnome-classic, which is the same as Gnome 2 except less stable.

You can also wait until 11.10, which will come with Gnome 3 by default (with Gnome-shell and Gnome-classic available in the repos).

---

### Post by 23dornot23d on 2011-06-21
Good words ..... 3Miro.

The OP could also check out this there is a test DVD here ...... [LINK]("http://ubuntuforums.org/showthread.php?t=1754198")

There are a number of Dvd's now that run gnome shell and it is possible to download and try them like you would any other CD/DVD ...... and this runs on UBUNTU.

Running this live should give you a good idea if your computer is up to the task .....
without the need to install .....

But obviously if you find it works ok .... you could join in with the many people now running it ..... you could add it in a test partition on your drive - as stated its still in testing ......

(But so is E17 .... and I think that has been in testing for well over 5 years now - even though the desktop is stable)

But Gnome-Shell which runs on Gnome 3 works quite happily once set up properly - this has been in testing for around a year or 2 now and to me is quite stable on the right systems - usually Nvidia Graphics Cards and Dual core computers - but I also have it running on a old Acer Aspire 1350l with 512 Meg of ram and a desktop machine also with just 512 Meg of Ram. - (so who knows - without trying it out).

I have had few problems with it ...... but if you read through the thread I have supplied a [LINK]("http://ubuntuforums.org/showthread.php?t=1754198") to you will see what problems there have been and also how quickly and how far it has come on ......

As for breaking UNITY ...... from what I read altering the settings in compiz does this quite easily - but who knows what causes UNITY to break .... but I suppose GNOME3 is a good a reason as any.

I have 3 videos now where I swap between UNITY and GNOME SHELL .... 
Gnome Shell will run in Gnome 2 .... so there is no need to break your system - thats if you just want to use Gnome-Shell.

Gnome Shell will run in Gnome 3 .... and as far as I know its not that breaks UNITY ...... as I have both running in it too.

UNITY sits as an addon to compiz .... and works in a totally different environment to Gnome-Shell ..... but it does not work well with Gnome 3 at this moment in time ..... as some functions seem to be missing .

You may get a feel for what I mean ...... by trying a Live DVD though ......

I felt I should write this as some people seem to think that Gnome 3 .... is Gnome-Shell 
maybe because it appears to be the only successful desktop that runs on it at this moment in time.

Things change though ..... hopefully in 6 months time ...... we all will be using it. ;)

---

### Post by ploft on 2011-06-30
Thank you all for the feedback! Sorry for the long time between posts. College, exams and such..

Somewhere along the way I decided to switch to Openbox and fine-tune my .conkyrc. I am happy with the setup and don't think I will be using gnome2/3.

Unity works on my 1201N, but I was trying to make Ubuntu use as little memory as possible, to see where I can improve resources usage. (it is an eeepc after all...)

Openbox seems to be pretty neat, even if I still need gnome-settings-daemon for background/screensaver and nm-applet to manage wi-fi.

I will, however, give the Fedora LiveCD a try, thank you for that.

---


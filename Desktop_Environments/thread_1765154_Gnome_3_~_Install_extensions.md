---
title: "Gnome 3 ~ Install extensions"
date: 2011-05-22
forum: Desktop Environments
---

### Post by steigerjb on 2011-05-22
I install Gnome 3 with Ubuntu 11.04 using Gotbletu's video [http://www.youtube.com/watch?v=haCHS2LUH9Q]("http://www.youtube.com/watch?v=haCHS2LUH9Q") by running the following commands:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
sudo apt-get install gnome-session
```

```
sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard
```

reboot

```
sudo apt-get purge unity
sudo apt-get purge scrollbar*
sudo apt-get install gnome-tweak-tool
```

It worked for the most part.  I had to solve some dependency issues but overall, no big deal.  I got Gnome 3 installed.

Now I want to test out some extensions.  I installed these 4 without issues: [http://intgat.tigress.co.uk/rmy/extensions/index.html]("http://intgat.tigress.co.uk/rmy/extensions/index.html")

I couldn't seem to figure out this one:
[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html]("http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html")

For this extension:
[http://www.webupd8.org/2011/05/system-monitor-extension-puts-ram-swap.html](http://www.webupd8.org/2011/05/system-monitor-extension-puts-ram-swap.html)
I got to:

```
joe@joe-ubuntu:~$ mkdir ~/git_projects
joe@joe-ubuntu:~$ cd ~/git_projects
joe@joe-ubuntu:~/git_projects$ git clone git://github.com/paradoxxxzero/gnome-shell-system-monitor-applet.git
Cloning into gnome-shell-system-monitor-applet...
remote: Counting objects: 135, done.
remote: Compressing objects: 100% (134/134), done.
remote: Total 135 (delta 65), reused 0 (delta 0)
Receiving objects: 100% (135/135), 18.72 KiB, done.
Resolving deltas: 100% (65/65), done.
joe@joe-ubuntu:~/git_projects$ mkdir -p ~/.local/share/gnome-shell/extensions
joe@joe-ubuntu:~/git_projects$ cd ~/.local/share/gnome-shell/extensions
joe@joe-ubuntu:~/.local/share/gnome-shell/extensions$ ln -s ~/git_projects/gnome-shell-system-monitor-applet/system-monitor@paradoxxx.zero.gmail.com
joe@joe-ubuntu:~/.local/share/gnome-shell/extensions$ sudo cp ~/git_projects/gnome-shell-system-monitor-applet/org.gnome.shell.extensions.system-monitor.gschema.xml /usr/share/glib-2.0/schemas
[sudo] password for joe: 
joe@joe-ubuntu:~/.local/share/gnome-shell/extensions$ cd /usr/share/glib-2.0/schemas
joe@joe-ubuntu:/usr/share/glib-2.0/schemas$ sudo glib-compile-schemas  
You should give exactly one directory name
joe@joe-ubuntu:/usr/share/glib-2.0/schemas$ 

```
I don't know what that means.

Do you know of anymore extensions to try out?

UPDATE: Whoops lol.  I tried [http://www.webupd8.org/2011/05/gnome-shell-workspace-indicator.html]("http://www.webupd8.org/2011/05/gnome-shell-workspace-indicator.html").  Got through it no problem, no errors.  I did alt + F2 and then typing r to restart gnome 3 to make it appear.  It made the panel disappear so I logged and got this. 

[IMG]http://i55.tinypic.com/97lg5x.png[/IMG]

And that's why I am testing Gnome 3 in VirtualBox. :lolflag:

---

### Post by steigerjb on 2011-05-22
Deleting the system monitor extension with live cd didn't fix the problem.

---

### Post by steigerjb on 2011-05-22
Im wondering if I should just reinstall.

---

### Post by 23dornot23d on 2011-05-22
Just go into the [home directory] /.local/share/gnome-shell/extensions/... hidden files ....
look in here remove the ones that are causing you problems ...... 
remove them all and just put the ones you want in there will do it .........

No need to re-install .... even in virtual box.

---

### Post by steigerjb on 2011-05-22
> **23dornot23d said:**
> Just go into the [home directory] /.local/share/gnome-shell/extensions/... hidden files ....
look in here remove the ones that are causing you problems ...... 
remove them all and just put the ones you want in there will do it .........

No need to re-install .... even in virtual box.

I don't have access to my computer at the moment.  I deleted the system monitor extension earlier but it didn't resolve the issue.  I guess that must have not been the one causing the issue.  I'll try deleting all of them.

---

### Post by 23dornot23d on 2011-05-22
I start with just 2 in there .... the ones relating to themes .....

One of the panel ones has an error in it ...... but it does not always stop the system
working ..... but it does slow it down a lot ......... 

( It needs someone that knows java script to check it out ..... there are two in there with the name Panel in them its one of them )

will find it shortly ..... and put a screenshot here for someone to follow up on .......

---

### Post by steigerjb on 2011-05-22
> **23dornot23d said:**
> I start with just 2 in there .... the ones relating to themes .....

One of the panel ones has an error in it ...... but it does not always stop the system
working ..... but it does slow it down a lot ......... 

( It needs someone that knows java script to check it out ..... there are two in there with the name Panel in them its one of them )

will find it shortly ..... and put a screenshot here for someone to follow up on .......

So remove the themes extension? 

What do you want a screenshot of?

---

### Post by 23dornot23d on 2011-05-22
> 
So remove the themes extension? 
yep remove the extensions we can put them back later .... or zip them up .... up to you.

> 
What do you want a screenshot of?     
Do not need a screenshot now if you are going to zip them or remove them 

It should work again ok once you have done this .....

---

### Post by steigerjb on 2011-05-23
> **23dornot23d said:**
> yep remove the extensions we can put them back later .... or zip them up .... up to you.

Do not need a screenshot now if you are going to zip them or remove them 

It should work again ok once you have done this .....

Themes extension wasn't there.  I just deleted everything.  It's fixed now.

---

### Post by steigerjb on 2011-05-23
Now I just gotta figure out how to do this correctly.

---

### Post by 23dornot23d on 2011-05-23
Go to my footer and download the 32 bit version ..... its already all set-up ......

C Bowman has made a ISO to try to stop some of the confusion ......

It has a base that we all can start from ....

Hope this helps in some way

_____________________________

---

### Post by steigerjb on 2011-05-23
> **23dornot23d said:**
> Go to my footer and download the 32 bit version ..... its already all set-up ......

C Bowman has made a ISO to try to stop some of the confusion ......

It has a base that we all can start from ....

Hope this helps in some way

Yeah, I saw your footer.  I am stubborn.  I wanna learn how to set it myself.

---

### Post by 23dornot23d on 2011-05-23
Ok no problem ...... :confused:

---

### Post by steigerjb on 2011-05-25
> **23dornot23d said:**
> Ok no problem ...... :confused:

It is definitely the theme selector extension messing it up.  How do I install it?

---

### Post by 23dornot23d on 2011-05-25
Go down to where it says themes in [**my web page**]("https://sites.google.com/site/000menu/home/gnome---3") .... 
> 
This web-page is a little out of date now as a lot is happening  .... and the initial installation is set to take it back to 2.32
So just use the part where it says for the **THEMES** .... hopefully it will give you the information that you need

There is always a easy way too ..... but I know what you mean by wanting to do it yourself.
Thing is there is so much more already set up in the distro .... below .... v04 the 64 bit

I spent some time re-setting this up for 9 themes including the Tron one and the tweak tool all works as it should too ..... with the Tweak tools included and set up too .....

It is for people that want to try the 64bit version out on Dvd without installing it ...... and Unity is on there too and all works in 3D on Nvidia Systems ...... as far as I know.

---

### Post by steigerjb on 2011-05-25
> **23dornot23d said:**
> Go down to where it says themes in [**my web page**]("https://sites.google.com/site/000menu/home/gnome---3") .... 
So just use the part where it says for the **THEMES** .... hopefully it will give you the information that you need

There is always a easy way too ..... but I know what you mean by wanting to do it yourself.
Thing is there is so much more already set up in the distro .... below .... v04 the 64 bit

I spent some time re-setting this up for 9 themes including the Tron one and the tweak tool all works as it should too ..... with the Tweak tools included and set up too .....

It is for people that want to try the 64bit version out on Dvd without installing it ...... and Unity is on there too and all works in 3D on Nvidia Systems ...... as far as I know.

See I have my own website [JoeSteiger.com]("http://www.joesteiger.com").  I want to be able to post how to install the extensions all in the terminal like on webupd8's site.

Can you tell me what the extensions do it the gNatty Pack.tar.gz pack?  Are you going to add the cpu monitor?

---

### Post by 23dornot23d on 2011-05-25
> **steigerjb said:**
> See I have my own website [JoeSteiger.com]("http://www.joesteiger.com").  I want to be able to post how to install the extensions all in the terminal like on webupd8's site.

Can you tell me what the extensions do it the gNatty Pack.tar.gz pack?  Are you going to add the cpu monitor?

Nice website .......  there is a readme in the gnatty pack .... the pack belongs to CBowman and he is adding all the extensions onto the top panel .......

There are quite a few now ... weather indicator / battery / applications etc ..... 

I use cairo dock mainly as well as the panel  .... ( both work very well ) 

But for more information on the panel extensions you need to be looking at this [[COLOR=Red]**THREAD**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1754198&page=78") ..... as this is where the majority of the work was going on .... 

Gnome-Shell ...... was moved to other O/S s

---


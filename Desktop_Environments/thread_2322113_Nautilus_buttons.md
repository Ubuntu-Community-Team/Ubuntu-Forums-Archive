---
title: "Nautilus buttons"
date: 2016-04-26
forum: Desktop Environments
---

### Post by ThanosShadow on 2016-04-26
Hello
I am using Ubuntu Gnome 16.04, fresh installation

In other distributions like fedora and openSUSE, nautilus has 2 buttons on the right of the "search button"
In ubuntu I see 4 buttons. Of which the 2 last have a not very usable (for me) menu (the "view options" and the "location options" buttons)
 
How can I make nautilus look like what I am used to in other distributions? Which is just two buttons next to the "search" button.

Comparison (the above is the one I want and the one below is ubuntu Gnome)

[IMG]http://s32.postimg.org/jnxttk4ud/image.png[/IMG]

---

### Post by buzzingrobot on 2016-04-26
You might try installing dconf-editor and seeing if its Nautilus section offers any options to disable the display of those buttons.

---

### Post by vasa1 on 2016-04-26
From what I've read, Ubuntu's Nautilus isn't quite the same as that provided by other non-Ubuntu distros.

---

### Post by ThanosShadow on 2016-04-26
> **buzzingrobot said:**
> You might try installing dconf-editor and seeing if its Nautilus section offers any options to disable the display of those buttons.

Okay I will try
Any idea where should I look in dconf-editor? I always get lost in there...

> **vasa1 said:**
> From what I've read, Ubuntu's Nautilus isn't quite the same as that provided by other non-Ubuntu distros.

I guess so
It looks more like nautilus from unity

---

### Post by vasa1 on 2016-04-26
You could try the command line:```
08:05 PM ~ $ gsettings list-schemas | grep -i nautilus
org.gnome.nautilus.desktop
org.gnome.nautilus.window-state
org.gnome.nautilus.icon-view
org.gnome.nautilus.list-view
org.gnome.nautilus.preferences
org.gnome.nautilus
08:06 PM ~ $ 
```
And for more details try:```
gsettings list-recursively | grep -i nautilus
```

---

### Post by ThanosShadow on 2016-04-26
I couldn't find a solution using dconf-editor... :confused:

---

### Post by buzzingrobot on 2016-04-26
Follow the hierarchy Vasa posted in dconf-editor.  (Same settings, different tool.)  If an option to turn off the buttons is on offer, it will be in there.

---

### Post by ThanosShadow on 2016-04-26
Checked the description of all entries. None of them are the solution..

But I wonder how no one complained about this. These buttons are buggy. I actually had to wait 30 seconds when I clicked "enter location" from the menu of the first-from-the-right button, while pressing Ctrl+L allows me to instantly enter a location.

Anyway if you can think of something I will be grateful!
Thanks for the answers

---

### Post by mc4man on 2016-04-26
Your only possibility would be to alter the source code & rebuild. If removed then all those menu items would be gone as they're not available in the apt menu.
16.04 is using nautilus 3.14 as 3.18 had too many issues in an ubuntu session. I'd look at the gnome3 ppa to see if 3.18 nautilus is available, maybe it'll treat you better.

---

### Post by ThanosShadow on 2016-04-26
Hmm, yes that could be an option. 
 
But there are lots of buggy things in the new release, like the fact that I can't seem to install .deb files (tried a few). I have to use the terminal and install it with apt or download gdebi installer which didn't work the first time. 
Weird things... 

I will wait for an update maybe or something. But maybe it would be better for me to stick to unity or kubuntu even though I like the gnome applications ubuntu provides and their clean look under gnome 3...

---

### Post by mc4man on 2016-04-26
> **ThanosShadow said:**
> Hmm, yes that could be an option. 
 
But there are lots of buggy things in the new release, like the fact that I can't seem to install .deb files (tried a few). I have to use the terminal and install it with apt or download gdebi installer which didn't work the first time. 

That will be fixed in an SRU update to gnome-software, maybe sometime in the next week or 2.
I did check nautilus in a gnome session (gnome-shell) & yes, many menu items are slow to open, ect. I don't expect you'll see gnome session specific fixes at this point in 16.04. You could file a bug(s) about the crappy performance, you never know.

---

### Post by ThanosShadow on 2016-04-26
You mean there will be no fixes? No updates? :/ It is an LTS version so maybe someone decides to use it for the whole 4, 5 years it will supported. Isn;t it unfair to not get fixes?

edit: or are you referring to "at this point" specifically?

---

### Post by mc4man on 2016-04-26
> **ThanosShadow said:**
> You mean there will be no fixes? No updates? :/ It is an LTS version so maybe someone decides to use it for the whole 4, 5 years it will supported. Isn;t it unfair to not get fixes?

edit: or are you referring to "at this point" specifically?
What I said was, "don't expect you'll see gnome session specific fixes"
After release generally only security bugs are fixed, occasionally that is streched thru SRU's (stable release updates).
Your issues with Ubuntu Gnome aren't security related & don't affect Ubuntu. So I think it's unlikely you'd see an SRU update targeting gnome session specific issues. Not saying it's impossible, just unlikely.
(- if fixing gnome breaks ubuntu then it will never happen. This is one of the main advantages of ppa's where newer packages are available by user choice to use them.

---

### Post by ThanosShadow on 2016-04-26
Okay I think I understand. Thank you for your answers and time, too! 

Btw Ubuntu 10.04 was the first distribution I ever used. With gnome 2 back then. That's an old account, thus the old non-updated information on the top right of my posts, hehe. But now I can't decide which DE is better for me. They all have something that helps me for my work and something that annoys me a lil bit. And these differ from distro to distro. I get a headache from all the thinking and searching :P

---

### Post by mc4man on 2016-04-26
Ubuntu (unity7/compiz) has been in maintenence mode for quite some time. But for 16.04 a fair amount of effort was put in & a lot of bugs where fixed. There's a few things amiss but I'd expect them to be fixed over the coming months.
Ubuntu-gnome seems less than stellar but it may have been nothing of the dev's fault. That's why if I had 16.04 U-G I'd add this ppa, update sources & do a dist-upgrade. It may prove much better.
Worst case you could always install ppa-purge & use on the ppa.
[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3)

---

### Post by ThanosShadow on 2016-04-26
Hmm...I already moved to unity. I actually prefer to keep things simple when it comes to extra repositories and ppa's and stuff. Except when experimenting. But I'll give it a try soon

---

### Post by mc4man on 2016-04-27
> **ThanosShadow said:**
> Hmm...I already moved to unity. I actually prefer to keep things simple when it comes to extra repositories and ppa's and stuff. Except when experimenting. But I'll give it a try soon
Just don't use that ppa if using unity

---

### Post by ThanosShadow on 2016-05-14
I solved (partially) the issue. Just discovered that this style is just how nautilus 3.14 looks like. After 3.16 there are only two buttons. So it is just a version issue. Nautilus 3.14 has 4 buttons while nautilus 3.16 has only 2. 

Solved :popcorn:

---


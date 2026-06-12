---
title: "Installing Berly or compiz"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by Orbital75 on 2007-08-19
Hi..... I am currently running Ubuntu 7.04  in Virtual Box
and would like to install Berly or compiz.  I looked
in the repository and there are a ton of things
related to them.  What item do I need to check
and once installed how do I start it. 

Which is better, more stable
and easier to use.

I'd like to be able to do the BOX affect
along with task bar modifications 
and have a ton of eye candy.  

I'm new to linux only been using it for a little
over a week..... I have to say I really like Ubuntu

#( What a great Linux Distribution )

---

### Post by czepluch on 2007-08-19
> **Orbital75 said:**
> Hi..... I am currently running Ubuntu 7.04  in Virtual Box
and would like to install Berly or compiz.  I looked
in the repository and there are a ton of things
related to them.  What item do I need to check
and once installed how do I start it. 

Which is better, more stable
and easier to use.

I'd like to be able to do the BOX affect
along with task bar modifications 
and have a ton of eye candy.  

I'm new to linux only been using it for a little
over a week..... I have to say I really like Ubuntu

#( What a great Linux Distribution )

Hi mate

I would recommend compiz fusion :D I'm using it my self and im more that pleased with it.

Here is a link that tells you how to install it :  [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

Hope it will help you :D

---

### Post by oldos2er on 2007-08-19
This helped me: [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

---

### Post by walkerk on 2007-08-19
> **Orbital75 said:**
> Hi..... I am currently running Ubuntu 7.04  in Virtual Box
and would like to install Berly or compiz.  I looked
in the repository and there are a ton of things
related to them.  What item do I need to check
and once installed how do I start it. 

Which is better, more stable
and easier to use.

I'd like to be able to do the BOX affect
along with task bar modifications 
and have a ton of eye candy.  

I'm new to linux only been using it for a little
over a week..... I have to say I really like Ubuntu

#( What a great Linux Distribution )

Well if your using VBox and you don't want to bother with Compiz Fusion you can download Beryl and Emerald from Synaptic to get similar features. Composite plugins and window decorations. You'll need these packages from Synaptic:
```
beryl, beryl-core, beryl-plugins, beryl-manager, and emerald
```

---

### Post by Orbital75 on 2007-08-19
Well, I decided to just go ahead and use Beryl for now.

I installed:
 beryl, beryl-core, beryl-plugins, beryl-manager, emerald, and emerald themes.

Now I see that I have Emerald in my Preferences List
and Beryl in my System Tools list.

Now how do I make it activate and run.
Remember I am using VirtualBox so it may not
be possible. With my Virtual Machine I can
decide how much video Ram I want to give
it, how much would Beryl require to run well.
64,128 ?  My card is 128 So I can safely use
64 of it.

I'd like to do something like this.

[IMG]http://img405.imageshack.us/img405/17/berylsmallforestop9.jpg[/IMG]

---

### Post by walkerk on 2007-08-19
> **Orbital75 said:**
> Well, I decided to just go ahead and use Beryl for now.

I installed:
 beryl, beryl-core, beryl-plugins, beryl-manager, emerald, and emerald themes.

Now I see that I have Emerald in my Preferences List
and Beryl in my System Tools list.

Now how do I make it activate and run.
Remember I am using VirtualBox so it may not
be possible. With my Virtual Machine I can
decide how much video Ram I want to give
it, how much would Beryl require to run well.
64,128 ?  My card is 128 So I can safely use
64 of it.

I'd like to do something like this.

[IMG]http://img405.imageshack.us/img405/17/berylsmallforestop9.jpg[/IMG]

press alt-f2 and enter:
```
beryl-manager
```

Now click it (in systray) and ensure Beryl is the Window Manager and Emerald is the window decorator. To change your emerald theme use the menu item you mention above.


to load at boot up add it to System > Preferences > Sessions

You should be ok with 64..

---

### Post by Orbital75 on 2007-08-19
Gave it a try but a window popped up and said:

Could not open location 'file:///beryl-manager'

**( EDIT )** I see what happen.  For some reason,
Beryl Manager didn't not install the 1st time.  I went
back and made sure it installed and now it will
run as you stated.

I'll try the rest here in a second.

---

### Post by Lithium17 on 2007-08-19
Beryl is the better option, as beryl-manager is so easy to use.

---

### Post by Orbital75 on 2007-08-19
After I ran Beryl Manager it launched the Ruby icon in the System Tray.
Well there is an option that stated **Select Windows Manager**
Within this it has Beryl, Compiz, and Metacity. I tried to put the Black
dot in Beryl but it doesn't seem to take affect.  I choose it and nothing
happens.  I go back and MetaCity is chosen again. I can't get the
setting to stay.  Also, Windows decorator is Grayed out.

When I reboot it states that Emerald is but when I choose
Beryl as Windows Manager it grays out. It's like Beryl tried
to start and failed then feel back to MetaCity. After this
Emerald grays out in the Berly Manager

Not sure if this means anything but I went into Sessions
and I looked for Beryl ( I put it in the startup )
In the column state it has a ? mark

Any Suggestions?

---

### Post by Orbital75 on 2007-08-20
I guess it got to complicated because of the virtual Machine.
All of a sudden, I stopped getting responses.

Oh well, I was hoping I could get it to work. :KS

---

### Post by mysticmatrix on 2007-08-20
> **Orbital75 said:**
> I guess it got to complicated because of the virtual Machine.
All of a sudden, I stopped getting responses.

Oh well, I was hoping I could get it to work. :KS

VirtualBox has limited 3d capability. If you want to get real juice out of ubuntu but don't want to take headache of partitioning ,etc, try WUBI from [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Orbital75 on 2007-08-21
I don't want anything that messes with my Boot Loader.
Thanks for the advice though.

---

### Post by Orbital75 on 2007-08-22
Still can't get it to work

---

### Post by mysticmatrix on 2007-08-22
> **Orbital75 said:**
> I don't want anything that messes with my Boot Loader.
Thanks for the advice though.

Hmnn. although I had once tried Wubi and it worked fine. Even uninstalled fine.:lolflag:

---


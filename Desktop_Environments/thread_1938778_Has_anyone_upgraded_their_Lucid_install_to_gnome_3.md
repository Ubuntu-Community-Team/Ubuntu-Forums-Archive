---
title: "Has anyone upgraded their Lucid install to gnome 3?  How did it go?"
date: 2012-03-10
forum: Desktop Environments
---

### Post by MSPdwalt on 2012-03-10
So,

I've seen some videos showcasing gnome 3, I definitely want to try it, but it seems to me that upgrading desktop environments could have some undesired results.

I actually use Ubuntu/Gnome2x as my only OS, I'm very comfortable in it, and I've customized my panels and applets just so.  Is gnome 3 going to mess all this up or am I making a mountain out of a mole hill?

Also, gnome 3 looks a lot "prettier" than 2, usually prettier means needs more horsepower.  I'm rocking a single core Athlon 64 3800+ w/ 2 gig worth of dual channel pc3200 RAM. (I know, she's an old girl, saving up for a new build)

Is this gonna work? Is it gonna work well? Is it as hard as I think it is to fail back?  How did it go for you?

I'm defiantly OK with putting off Gnome 3  until I'm ready to do a new build on modern hardware, but the little kid in me really wants to try out the shiny new toy.

Thanks in advance for your responses,

Dylan

---

### Post by Frogs Hair on 2012-03-10
The Gnome 3 fall-back  session is not the same as Gnome 2 and Unity is the default desktop on 12.04 . I do not upgrade after attempting to only one time, but that was with my first i installation and I used Wubi . If you are happy with what you have keep Lucid .

I like the Gnome shell and Unity and have no desire to use Gnome 2 anymore or try to make another DE look like it . When the time comes I would suggest backing up your files and doing a clean installation . You can upgrade directly to 12.04 but waiting until the final release may be a good idea.

---

### Post by grahammechanical on 2012-03-10
That mole hill that you speak of is quite a big mountain in my opinion. I do not think that the upgrade process can make the switch from a heavily modified 10.04 or 10.10 to 11.10 or 12.04, not without causing some issues.

Some of your stuff will not work on Gnome 3. Developers of themes, icon sets and top panel applets are having to modify them so that they work on Gnome 3 and Unity. So, you will have to re-install some stuff. For example, I used to used Radio Tray in 10.10 but it would not work in 11.10 until the developer modified it to work as a Unity app indicator. Now, I have it working in the 12.04 Beta 1.

Ubuntu developers have no idea of the modifications that some us make to our desktops. Their starting point is a default install. For that is what they know.

So, yes, think seriously about a fresh install and be prepared for changes and differences. 12.04 is different in many ways to 11.10.

Think about it. How would one test an upgrade form 10.04 to 12.04? I could install 10.04 into another partition and then upgrade but that would be from one default install to another. I have no idea of the modifications that you have done.

In a few weeks a lot of people will be putting the upgrade process to the test. I cannot imagine how to set things up so that things do not go wrong for everyone or even for some.

Regards.

---

### Post by Marzata on 2012-03-10
We upgraded (clean install) all our machines from Ubuntu 10.04 LTS to Xubuntu 11.10 in order to wait for Xubuntu 12.04 LTS.

---

### Post by MSPdwalt on 2012-03-14
I think my original post was misinterpreted.

There's a 3rd party repository that will allow you to install gnome 3 on Lucid (what I'm contemplating doing).  So for me it would be a direct upgrade from gnome 2.x to 3.  It sounds to me like no one has tried this on an in use system.

I have a fairly large external hard drive, I've debated using clonezilla to image my system to it and fail back if I'm not happy with it, but I'm not sure I wanna wait around for a 200+ gig image to be created/restored lol.

---

### Post by Penguinnerd on 2012-03-14
My personal suggestion is not to do this.

It sounds like you (as I also am) are very well "settled in" with Gnome 2. After all, that's why I'm using LTS.

"Don't fix it if it ain't broken." If I were you, I'd keep the system as-is until the new replacement PC is done, or until 10.04 support ends, whichever comes first.

That's my 2 cents.

---

### Post by 3Miro on 2012-03-14
LTS releases are supposed to come with old but tested software so that you can enjoy extra stability. When you suggest to install cutting edge software from 3d party unofficial ppa, you are going against the very idea of LTS. Furthermore, you are not just updating one or two programs like Firefox or Libre Office, you want to change the entire desktop environment down to the foundation of its tool-kit (GTK2 -> GTK3). In addition, any such change will be irreversible, for you will not be able to just uninstall such a major change (some people were installing Gnome 3 on 11.04 and they had to reinstall the entire OS to revert back to Gnome 3).

Don't get me wrong, wanting to try Gnome 3 is perfectly fine, it is just that going for it on top of an LTS is a bad idea. You should install 11.10 or better yet make a separate partition and install 11.10 as a dual boot to test it. You can also simply wait a month and go straight for the next LTS. Either of those options would give you Gnome 3 and would be a much better option than messing with the existing LTS.

---

### Post by MSPdwalt on 2012-03-14
Cool.  I think I'll wait until I have the $$$ for new hardware.  These are the exact type of answers I wanted.  I'm getting to the point in Linux where I'm a little too confident sometimes lol.

---


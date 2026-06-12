---
title: "Mainly using gnome but I want to give KDE a spin"
date: 2011-01-09
forum: Desktop Environments
---

### Post by rpaskudniak on 2011-01-09
Greetings.

As the subject line implies, I have Gnome but I would like to install KDE and give it a spin.  In my previous installation of Ubuntu (10.04), they were apparently both installed and, while initially defaulting to Gnome, allowed me to choose my desktop environment (henceforth DE) at the login page.  With 10.10, nothing of KDE got initially installed; it's up to me to make the choice to install it.  The available KDE I see in Synaptec is 4:4.5.1

My first question is: Which package do I check to install the basic package?  I suspect it is **_kdebase-runtime_** because the name looks right and when I check that it tells me it will install a very large number of additional packages.  This is, of course, a rather unreliable criteria so I am asking for an explicit direction.  (Well, not too explicit; I'm likely to haver a child reading over my shoulder. :biggrin:  )

Second question: I just came out of a search for the strings {Installing, KDE, Gnome} in this forum and the stories are kinda scary.  So...
Has anyone experienced difficulties as a [n apparent] result of installing KDE after Gnome was already in place?

Thanks much for advice.

---

### Post by linuxman94 on 2011-01-09
Installing the kubuntu-desktop package will install all the packages you need for KDE.

---

### Post by rpaskudniak on 2011-01-09
> **linuxman94 said:**
> Installing the kubuntu-desktop package will install all the packages you need for KDE.

Thanks, Linuxman.

I see kubuntu-desktop under the Metapackagessection.

I was actually wondering why the folks who had reported all these *tzuris* to which I had alluded were talking about kubuntu-desktop.  And that seemed to be the cause of their problems.

On the other hand, out of so many users, there were only 8 such threads and at least 1 was a false alarm.

More question, owing to the nomenclature of the product: Isn't kubuntu already a variant of the Ubuntu I am already using, and therefore an invitation to trouble?  Of course, you know I just being a big [IMG]http://t2.gstatic.com/images?q=tbn:ANd9GcTZzmMtybuZF9qk1z7B7Tnht5wN-miQVuASUg9BbMUn853BZaMkuWl2Al4V5A[/IMG] here but I'm being cautions after being burned a few times by my own mistakes.

Again, thanks for the advice.

---

### Post by linuxman94 on 2011-01-09
Kubuntu is in fact a variant of Ubuntu.  It is an official variant maintained by Canonical.

---

### Post by Krytarik on 2011-01-09
The package "kubuntu-desktop" is the perfectly right one to install, also look here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

---

### Post by rpaskudniak on 2011-01-09
(SIGGHHhhh...)

OK, I installed the kubuntu-desktop meta package. I certainly have a prettier login screen but my desktop looks pretty much the same as my gnome desktop.  In fact, with the exception of some new facilities in my system menu - mainly, the Assistive Technologies menu item under System ->Preferences (and I'm not so sure that's new) I see no difference at all.  One telling item is that when I navigate the preferences menu to ScreenSavers, it is the Gnome screen saver set that comes up.  Another is that when I launch FireFox, I don't get the bouncing icon. While I consider that particular effect to be a waste of energy, it used to be one big signpost that I was running KDE.  It's not happening now.

My big issue here is that I was not presented with the choice of desktop environments at the login screen.  Yes, there were some options, related to Assitive but no menu of [KDE] or [Gnome], as I had come to expect from 10.04 on my previous box.

What have I missed?

Thanks.

---

### Post by Krytarik on 2011-01-09
Did you restart!?

EDIT: Is mentioned in some guides.

---

### Post by cascade9 on 2011-01-09
*sigh*

@ linuxman94 and Krytarik- You dont need to install kubuntu to get KDE4.X on ubuntu. In some ways, its a bad way to get KDE, as kubuntu-desktop pulls in a lot of stuff you dont need and adds all the kubuntu branding. 

kde-full will get you a workable KDE 4.X desktop enviroemnt, without all the extra dross, see the difference here- 

[http://packages.ubuntu.com/maverick/kde-full](http://packages.ubuntu.com/maverick/kde-full)
[http://packages.ubuntu.com/maverick/kubuntu-desktop](http://packages.ubuntu.com/maverick/kubuntu-desktop)

@ rpaskudniak- the reason why your login screen looks prettier is because you've changed from using GDM (gnome display manager, stock with ubuntu) to KDM (KDE display manager). 

As for why your desktop looks the sam..e..thats because it is! I dont know why you arent getting (or finding?) a choice at the login screen. Maybe you are poking the wrong place?

---

### Post by rpaskudniak on 2011-01-09
HOO BOY!

Well, installing the kubuntu-desktop did install 347 packages and download over 600 MB of stuff.  Should I undo all of that before going for KDE-full?  And how would I go about that endeavor?  Complete uninstall is likely to lose my whole ability to do any desktop.  (I've done it; I used to be braver and dumber. :oops: )

Right now, it appears that the step I should take now would be to just plunge ahead and install the KDE-Full, allowing the kubuntu-desktop packages to stay where they are, possibly to be overwritten by packages included with KDE-Full. Yeast in the beer, I think.

I'm open to suggestions - reminding me of a quote attributed to Winston Churchill: If you keep a sufficiently open mind, someone is going to throw a lot of trash in there.

Thanks.

---

### Post by hashbangfoo on 2011-01-09
Have you given any thought to installing Virtualbox, and running a KDE install within a virtual machine?
That way, if you like it, you can plan a migration to that window manager, and if not, you can just delete the vm without incurring any system bloat or change...
Just my $0.02...

Cheers! :)

---

### Post by Krytarik on 2011-01-10
I would leave it as it is. Now you have a full "Ubuntu" and "Kubuntu" version installed. What's the point, disk usage? Even with a some years old disk, you can easyly afford some 1,5 GB more for the system.

To finally find the option to log into KDE, simply change the display manager back to GDM:
```
sudo dpkg-reconfigure gdm
```

---

### Post by rpaskudniak on 2011-01-10
hashbangfoo,

Funny, I did recently download Virtual Box, having just heard about it from the How-To-Geek.  However, it's kinda late for that step now - I have already installed the kubuntu desktop and would like to know how to undo that.  Though I will admit it has not done any great harm to my machine.

I wonder if installing the Ubuntu-desktop now will undo some of the kubuntu branding.

Ah, I did find a couple of anomalies in the menus.  For example: [Applications]->[Accessories]->[{?} Akonaditray]
Now, I got no clue what Akonditray is or does but the menu item is still sitting there, grayed out.  If I edit the menu, I see that the command it runs is just "akonaditray", which is already running.  A daemon program?  It has no place in the applications menu anyway.

Another grayed-item:  bluedevil-monolithic, under [Applications]->[Internet].  This one is missing components  or just a screw.

So yes, I do have a bit of garbage in there and I'd like to get rid of it.  Preferably before I install the KDE-Full.

As alway, I'm open to ideas..

---

### Post by cascade9 on 2011-01-10
> **hashbangfoo said:**
> Have you given any thought to installing Virtualbox, and running a KDE install within a virtual machine?
That way, if you like it, you can plan a migration to that window manager, and if not, you can just delete the vm without incurring any system bloat or change...
Just my $0.02...

Cheers! :smile:

One problem with this is that OSes run slower in virtual machines than they do if its a normal install. So people who try this might think 'XXX DE/OS is really slow' when its just the virtual machine making it slow.

> **Krytarik said:**
> I would leave it as it is. Now you have a full "Ubuntu" and "Kubuntu" version installed. What's the point, disk usage? Even with a some years old disk, you can easyly afford some 1,5 GB more for the system.

To finally find the option to log into KDE, simply change the display manager back to GDM:
```
sudo dpkg-reconfigure gdm
```

I sort of agree, I wouldnt remove kubuntu to install kde-full (in part because IIRC adding kubuntu then removign it can cause system weirdness)

I dont think that the difference between kubuntu-desktop and kde-full is anywhere near as big as the difference between xfce4 and xubuntu-desktop. But its possible that kde-full would be quicker than kubuntu-desktop. 

You should be able to login to whatever DE you want from KDM, you dont need to use GDM.

---

### Post by rpaskudniak on 2011-01-10
Krytarik,

You and I made our previous remarks at the same time so I didn't see your contribution until after I finished entering mine.  Be that as it may..

When I installed the kubuntu-desktop meta package, I got that prompt and did indeed select gdm (not that I knew what that implied, or that I know now). In any case, I just followed your advice and ran that command; I was presented with a tiny menu of the default gdm or kdm.  I selected gdm and logged out.

Sorry, no login choice now either.

Is there, perhaps, an option to diddle in gconf-editor?  Or is that strictly a gnome configurator?

Still fishing for ideas, please keep 'em coming!

Thanks much!

---

### Post by Krytarik on 2011-01-10
The thing -at least with gdm- is: you have to enter/click your username first to get the session options, besides others.

Mind that?

---

### Post by rpaskudniak on 2011-01-10
No, I don't mind that.

Once I despaired of seeing the choices, I focused on the login box and didn't notice the panel showing the choice.  I guess I got [IMG]http://t2.gstatic.com/images?q=tbn:ANd9GcSlokwLAKRGUd7otvY9hyfTTtOzOgp_Wo1dDF5fPyqxthJ3SJW5giYtMSA-CQ[/IMG] over that. :P

I am in KDE now.  I see it will take some getting used to.  For starter, the menu editor shows a rich set of menu items - applications and all - but when I click on that icon at the left of the bottom bar,I get a very limited menu actually displaying.

And getting the items to sort? Not a clue.  Yet.

OK, where's the best How-To documentation on KDE?  Otherwise, I will consider this thread closed.  I will still probably install the KDE-full, for completeness.  I can afford the disk space.

Thanks for the help and huge [IMG]http://t0.gstatic.com/images?q=tbn:ANd9GcT-Rm2LB6hCnYKZSSZ18GF852fBts_CqJKgXPKOQ36FagbwNeQC[/IMG] for realizing what I was overlooking.

---

### Post by cascade9 on 2011-01-10
Try the 'classic' menu (right click on the 'K' button, 'switch to classic menu') I cant stand kickoff, its a mess. 

Mostly KDE 4.X is pretty easy to get your head around. The only thing that took me any time to find was how to change the KDM theme- 

alt + F2
kdesu systemsettings 

change login screen- advanced-> login manager.

*edit- I havent checked, but kde-full shouldnt add anything that is not in kubuntu.

---

### Post by rpaskudniak on 2011-01-30
OK, I guess I'll stay stuck with the kubuntu; I don't think it will damage anything if the option is there.

I did download and install KDE-full but so far I still find the gnome desktop easier to work with.

I will be visiting KDE every once in a while.  I am curious about how I might go about removing the Kubuntu installation without harming my KDE options but that's low priority.

As to VirtualBox:  I have downloaded it but I need to know a bit more about it so that I might see about running my native Windows-7 under its management while booted Ubuntu.  It ought to be better than wine! (I never had much success with that in my previous installation.)

Thanks.  I'm on to nastier stuff now; I'll be posting a new thread soon.

---

